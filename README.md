Documentation
-------------

Follow Google's instructions for setting up the build environment, including downloading the toolchain, which can be downloaded in full from the NDK via https://developer.android.com/tools/sdk/ndk/index.html (Linux users may have to chmod +x the .bin file before running it to automatically extract the entire prebuilt toolchains inside it).

How to Compile mkbootimg
------------------------

get Android source code: `git clone https://android.googlesource.com/platform/system/core.git`

$ cd /path/to/android-src
$ cd system/core/libmincrypt/
$ gcc -c *.c -I../include
$ ar rcs libmincrypt.a  *.o
$ cd ../mkbootimg
$ gcc mkbootimg.c -o mkbootimg -I../include ../libmincrypt/libmincrypt.a
$ cd ../cpio
$ gcc mkbootfs.c  -o mkbootfs -I../include

copy system/core/mkbootimg/mkbootimg, system/core/cpio/mkbootfs to a directory in your path.

solution from: https://gist.github.com/jberkel/1087757
