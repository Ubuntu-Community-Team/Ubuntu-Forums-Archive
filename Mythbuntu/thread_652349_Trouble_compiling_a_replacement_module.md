---
title: "Trouble compiling a replacement module"
date: 2007-12-28
forum: Mythbuntu
---

### Post by BLKMGK on 2007-12-28
I'm attempting to compile a replacement udf.o to add [UDF2.5]("http://sourceforge.net/project/showfiles.php?group_id=295") support to my Gutsy 7.10 MythTV install. I have followed various [guides]("http://www.howtoforge.com/kernel_compilation_ubuntu") in order to get kernel source (from kernel.org) using the version reported at the console (2.6.22-14). However after doing so when I attempt to compile the module I get an error message stating "the kernel source tree is version 2.6.22.9" and that the running kernel is "2.6.22-14-generic" as expected. Thinking that perhaps there was an issue with the source I was pulling I reloaded the machine from backup (I'm a newb, I make lots of backups!). Upon reloading I looked through the package manager and pulled both the kernel source and the source headers for this specific kernel (there was an option that looked like it would pull something more current, I didn't use that one. Upon trying to compile udf.o I received the same error:confused:

The only thing I can think of that might have screwed with things was my installing the latest NVIDIA binary driver. Their .run file screwed my system up pretty good so after restoring:rolleyes: I used ENVY. ENVY did everything perfectly for me (still have 1080P issue however) but it looked like it was downloading source for the kernel too. It's working well however so I don't think that's it.](*,)

Am I going about this the wrong way? Could it be an issue with the way the UDF2.5 driver script detects the kernel from the source tree? Is there another\better way for me to get source for doing this compile? Is there some way to tell what source version I have downloaded? Looking in /usr/src/ I see nothing labeled anything other than 2.6.22-14 including some NVIDIA stuff.

Lastly, am I correct in assuming I can simply create this new module and insert it to get UDF2.5 readable? Am truly new at linux so I'm not 100% solid on how to update modules yet.

Thanks!

---

