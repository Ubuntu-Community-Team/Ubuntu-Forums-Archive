---
title: "ConvertX 5 on Linux using Wine"
date: 2014-01-18
forum: Multimedia Software
---

### Post by gunslinger2 on 2014-01-18
Okay, this question was originally posted by joemama123 back in 2008 - 

I'm new to Linux, so I'm just learning, but I'm willing to learn and use Linux!  I'm trying to run ConvertXtoDVD using Wine  emulator.  I have Ubuntu 8.04.  When I run the program, it will convert  the avi file to DVD format fine.  But when it comes to burning it won't  recognize my internal DVD drive.  This is on a Dell Studio 15.  My  drive is there and I can burn with native Linux software.
[http://http://ubuntuforums.org/showthread.php?t=920455&highlight=convertx+wine](http://http://ubuntuforums.org/showthread.php?t=920455&highlight=convertx+wine) is the original post, but it has been closed after he was advised to use devede and other programs.

It is now 6 years later, and I still can't find an answer to the fundamental question here - **How do I get ConvertX to see the DVD drive?** Obviously I am running a newer version of Ubuntu (13.something raring), Zorin OS, PlayOnLinux 4.22 - but the problem is exactly the same. CXTD installs and does it's job flawlessly, until it comes time to burn. It is a better program even after 6 years of work on devede, DVD Styler and all of the other tools that are available, and there is no need to use multiple tools when the single program is capable of performing all the tasks. I can do all that needs to be done, yes - but it is slow, cumbersome and a pain in the *** when I know that I can just re-install Windows as a solution.

Please Help! If CXTD would not install or run under Wine, I would just move on - but it does, I just need to know how to add the DVD drive! There is an option to add a drive, but it wants a drive letter and I cannot find such a thing.

Thank you to anybody who reads this, and Double Thanx to anyone that can actually help!! :P

---

### Post by worldwide7477 on 2014-02-21
Answer to your question above is that by defult wine nor Playonlinux will see the drive with ConvertXtoDVD but there is a alternative which i have figured out today and hope it works for you..
If you have ConvertXtoDVD on your playonlinux or you have it installed with wine..open the configuration for convertx by clicking the wrench.. goto burning tab..you will notice no dvd drive which is normal and we will not be able to add it!! so add a check mark where it says "add iso file destination to drive list"...this will create a ISO image file after it has converted the file...when it opens after conversion add your dvd to be burned... right click the ISO file and select burn and whooo hooo there it is with chapters and everything that you have selected..hope this helps everyone out who likes to use "ConvertXtoDVD" and yes i'm using version 5.

I also added a video and hope its not against the rules.
[http://www.youtube.com/watch?v=HkHia41EAKk&feature=youtu.be](http://www.youtube.com/watch?v=HkHia41EAKk&feature=youtu.be)

---

### Post by PLowran on 2014-03-08
Hi Guys! Ive been trying to get this program to work for quite a while myself as Im not a fan of DeVeDe or DVDStyler... They look nice but ConvertDVDtoX is a lot Faster. Ive done as you suggested and set the Default to ISO but is there a way to trigger K3B or Brassero to automatically burn it? Thanks!!! Phil

---

### Post by mrsfixit on 2014-03-12
> **PLowran said:**
> Hi Guys! Ive been trying to get this program to work for quite a while myself as Im not a fan of DeVeDe or DVDStyler... They look nice but ConvertDVDtoX is a lot Faster. Ive done as you suggested and set the Default to ISO but is there a way to trigger K3B or Brassero to automatically burn it? Thanks!!! Phil

I use ConvertXtoDVD version 4xxx under WINE on Xubuntu. I have always simply converted with that program and burned with another, in this case Nero Linux. But you can use whatever works for you.

Quality wise nothing can touch ConvertX, although I have found Bombono comes very close, and it does also burn as far as I know. I burn with Nero so I can't say for sure how well it works. I never had any luck with DeVeDe, the output quality was horrible every time I tried it.

I have a question for you- using ConvertX 5- can you do menu's? ConvertX after version 3.0 does not do menu's under WINE. It throws a "templates not found", then "list index out of bound" error. Just wondering, as I'd like to upgrade if the menu function works.

---

