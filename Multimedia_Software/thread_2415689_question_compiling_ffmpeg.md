---
title: "question compiling ffmpeg"
date: 2019-03-29
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2019-03-29
I am trying to compile a local version of ffmpeg, tried a few versions (4.1.1, 4.1.2, master) and a few  ./configure options, all built successfully. 
But if --enable-shared, make check always errored out with 

```
GEN    tests/data/hls-list.m3u8
tests/fate/filter-audio.mak:202: recipe for target 'tests/data/hls-list.m3u8' failed
make: *** [tests/data/hls-list.m3u8] Error 127
make: *** Waiting for unfinished jobs....
```

I have tried this with no configure options (all defaults) other than --enable-shared. Otherwise (only static libraries are built) all tests passed.

I tried googled and didn't find much info, is this a problem or expected? 

Ubuntu 16.04

Thanks.

(also --enable-libaom => build faild if shared is enabled, but if only build static libs then build was successful, this seems to be expected)

---

### Post by mc4man on 2019-03-30
Personally I never run the tests so just conjecture
A quick test here has it fail even earlier, i.e.
> 
 TEST    api-threadmessage
Test api-threadmessage failed. Look at tests/data/fate/api-threadmessage.err for details.
tests/Makefile:220: recipe for target 'fate-api-threadmessage' failed
make: *** [fate-api-threadmessage] Error 127

The reason is because the test program is looking for libavutil.so.56 in the installed system libs (doesn't exist), not in the build dir. where it does exist (but not yet installed), 
> ldd  /home/doug/Desktop/ffmpeg-static/new7/ffmpeg-static/ffmpeg/tests/api/api-threadmessage-test
	linux-vdso.so.1 =>  (0x00007fffb0788000)
	libavutil.so.56 => not found
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f09dd100000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f09dcd36000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f09dd31d000)

So I'd gather tests can fail for any number of reasons, compiler used, linker, existing installed libs, ect. 
Look for any .err files or you could try to fix a test or you can ignore specific tests with a configure option.
```
--ignore-tests=TESTS     comma-separated list (without "fate-" prefix
                           in the name) of tests whose result is ignored
```

Or just use make .. sudo make install .. then do a make check  (- tested here, all tests passed on a shared build.., minimal configure..

---

### Post by monkeybrain20122 on 2019-03-30
Hi,

You are right, run make install first then make check now all tests passed for shared built. Thanks!

---

### Post by mc4man on 2019-03-30
I gather that make check will use the configured or default  $PATH (S)  for  any libraries used by the test programs, so to actually test the built .so's they'd need to be installed 1st.

As far as libaom,  from here I only see it's value for encoding and that's tenuous at best as encoding times are Pretty Poor.
For decoding I find libdav1d superior.

---

