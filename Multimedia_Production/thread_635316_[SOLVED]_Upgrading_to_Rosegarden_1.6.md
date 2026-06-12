---
title: "[SOLVED] Upgrading to Rosegarden 1.6"
date: 2007-12-08
forum: Multimedia Production
---

### Post by greyfox1 on 2007-12-08
Hi all, I'm having trouble upgrading to the new Rosegarden v1.6, which was released this week.  I'm running 1.5.1 now but there are some important fixes/updates I want to take advantage of in 1.6.

I can't find 1.6 in Synaptic or Update Manager (I presume because it's so new) and I haven't been able to find any .deb packages to use, so I'm left with compiling from the source code that I got from Rosegarden's SourceForge page.  The instructions provided with the binary recommend I use cmake which I found and installed but I am having trouble using it.  I've never compiled binary myself so I'm at a loss. I extracted the tarball to my desktop and here's what I get when I try to compile using "cmake ."

```
$ cmake .
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken
CMake Error: The C compiler "/usr/bin/gcc" is not able to compile a simple test program.
It fails with the following output:
 /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCompileExec.dir/build
make[1]: Entering directory `/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.o
/usr/bin/gcc   -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.o   -c /home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c
/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c:4:19: error: stdio.h: No such file or directory
/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c: In function ‘main’:
/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp/testCCompiler.c:12: warning: incompatible implicit declaration of built-in function ‘printf’
make[1]: Leaving directory `/home/rick/Desktop/rosegarden-1.6.0/CMakeFiles/CMakeTmp'
make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.o] Error 1
make: *** [cmTryCompileExec/fast] Error 2


CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done
```

If there is an easier way to do this, then by all means please enlighten me!  Otherwise please let me know what I need to do.  I presume I need to do some configuring in cmake but I don't really know what I'm doing.

I am using Ubuntu Studio 7.10.

I already posted this once  in [this thread]("http://ubuntuforums.org/showthread.php?t=635262") but it of course does not belong in the Art forum.  That was a mistake on my part.  If a mod comes across this, please lock or delete my other thread.  Sorry about that!

---

### Post by Unterseeboot_234 on 2007-12-09
Rosegarden, in my experience, was always a monster to compile. I broke Dapper trying to force a Fiesty lib to replace the installed Dapper lib and it broke Dapper. But, if you are determined...

Make sure you have** build-essential**

sudo apt-get install build-essential

Use synaptic to get the kde (not the kde4) and the kde-dev, which is about a gig download. I was trying to compile just to see if I can still do it. I gave up because I didn't want to download the kde-dev packages after I spent all that time downloading kde4, uninstall kde4, got the kde and stopped at the kde-dev, but you will need kde-dev also. :)

I've got other work in progress and I just can't crack my current Gutsy-64. If I was determined, I would partition, install a new Gutsy that I can trash if I crack the Linux kernel.

After all that.

sudo cmake .

if that doesn't work, we have to try the alternate ccmake to figure out the paths that it wants. But, I estimate you have at least 4 hours of crunch time ahead of you. "make" after the cmake will take a long while.

---

### Post by greyfox1 on 2007-12-10
Yikes.  I was afraid that I might get an answer like that.  Thanks very much for the advice but I don't think I'll be able to take something like this on.  I'm still a newbie with Linux and I just don't feel comfortable with a project like that.

I guess my best bet will be to give it some time and hope someone else out there creates a deb that I can use instead. ><

For the curious, I'm trying to get started making chiptunes and I haven't been able to find any other way on Linux than using the YMCK VST plugin via a program such as Rosegarden.  There are plenty of viable solutions for Windows but sadly I haven't been able to find many options under Linux.

---

### Post by stmiller on 2007-12-12
To fetch all packages required to build rosegarden, issue this command:
```

sudo apt-get build-dep rosegarden

```
then try that
```

cmake .

```
command again.

---

### Post by greyfox1 on 2007-12-12
Thanks a million stmiller, I followed your instructions, then ran ```
cmake . 
```  

That took a couple of minutes.  After the compile was finished (I didn't choose any extra options during the compile) I ran: 
```
sudo make install
```

And presto!  Rosegarden 1.6.0 installed with nary a hitch.  I owe you one !=D>

---

### Post by nayen on 2008-03-16
I cannot get cmake to run. What folder do I need to be in? Where were the rosegarden packages saved?

---

### Post by eric71 on 2008-03-18
You can get a gutsy .deb for Rosegarden 1.6.1 at [www.getdeb.net](www.getdeb.net). Haven't tried it yet.

---

