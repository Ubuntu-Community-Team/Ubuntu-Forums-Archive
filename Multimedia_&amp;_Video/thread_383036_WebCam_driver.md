---
title: "WebCam driver"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by 75sausage on 2007-03-12
I have a Vicam (HomeConnect) USB cam that I am trying to configure on my Edgy.

I downloaded a driver source code file but am having problems compiling it. the *make* command has no effect and I do have *compiler-essentials*.

can I have some guidance please?

see attached

thx

---

### Post by Scunizi on 2007-03-12
You lucky dog!  I've also got the same camera but by its original manufacturer ViCam.  It one of the best I've ever seen.  As for your compiling issue, search in Synaptic for "make" and install that.  Keep us posted here on your success of driver installation and functionality.  I haven't had the time to put into it.

---

### Post by 75sausage on 2007-03-12
I have done just what you suggested but I am having problems with this drive source code. I do not know how to install it. I realizer I have to compile it but the make command has no effect.

I guess someone with a lil more know how would have to look at the attache file and tell me if I can make it work somehow, at least install it to see if it works.

---

### Post by 75sausage on 2007-03-14
help, anyone?

---

### Post by Scunizi on 2007-03-14
From the terminal type "sudo apt-get install build-essential" then read the infomation here  [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall).  Careful, it will tell you one way to do it then it will tell you another way to do it.  The second way actually creates a .deb file.  Once that's created, double click it and follow the propmts.

---

### Post by 75sausage on 2007-03-15
the make command gives an error message: Nothing to do...

the checkinstall command gives: 
> [FONT="System"]========================= Installation results ===========================
/var/tmp/DHjnaoifplMkXaVQDXBhB/installscript.sh: 4: /home/maja/Desktop/vicam.c-2.6.16-agc-Nikolov: Permission denied

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.[/FONT]


---

### Post by Scunizi on 2007-03-17
Try running the make command prefaced with sudo and see.

---

### Post by 75sausage on 2007-03-17
I did that also, here's the output:
> make: Nothing to be done for `/home/maja/Desktop/vicam.c-2.6.16-agc-Nikolov'.

---

### Post by 75sausage on 2007-03-19
I appeal to the uber 1337 gurus of linux to help me compile and run the code attached in my post... PLEEZ!

---

### Post by Scunizi on 2007-03-19
Sorry I can't help you more. After looking at what is required, this is above my head... this is more than just compiling the file you downloaded.  It's suppose to be a kernal patch which means you'll have to re-compile your kernal with the patch included... I think.  If you're running Dapper you're probably safe because Dapper will probably not have too many, if any, kernal upgrades between now and its end of life.  On the other hand, if you're running 6.10 you might get some.  Every time you have a kernal upgrade you'll have to recompile it with the patch.  

I may be totally off base here.  Hopefully someone will chime in and lend a hand.  It might be easier than I think.  I use my machine for work so I really don't want to break anything by recompiling the kernal.

I (hopefully) changed the Title a little in the hopes it will attract more interest for us both.

---

### Post by nalmeth on 2007-03-19
Have you followed the instructions here?
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Slim Odds on 2007-03-19
Ok, first off, this file is a C file, not a makefile. So you can't "make" it.

Secondly, when you untar it, it does not get a C extension (i.e.,   .c) so I still won't compile until you change that.

Thirdly, this appears to be a device driver (as a kernel module?). So it's needs to be moved into the kernel source and compiled with the kernel.

Fourthly, where did you get this file? Didn't it come with instructions?

Have fun......

---

### Post by 75sausage on 2007-03-19
Yey!

:shock: 

Time to roll up my sleeves I guess. Thanks for the detailed information.

As far as the source of teh file, sourceforge and no it did not come with instructions just the source you see, and not even tared but just like that, there was the 6.10 kernel version and the one I attached 6.10.18. Should I stick with the 6.10 version to compile with kernel? That aditional .18 version throws me off.

(Maybe one of yo9u knows a good kernel :popcorn: popping tutorial link?) <ducks>

Source of files: [http://arron.dnip.net:81/files/](http://arron.dnip.net:81/files/)
Linked from: [http://sourceforge.net/forum/forum.php?thread_id=1443009&forum_id=69637](http://sourceforge.net/forum/forum.php?thread_id=1443009&forum_id=69637)

---

### Post by 75sausage on 2007-03-23
Ok I have figured out that I have to put the source code attached in this post (with .c extension) to my usr/src/drivers/usb/ folder and recompile.

But which folder and how to recompile?

I have linux-headers-2.6.17-10, ...-10-generic, ...-11, ...-11-generic, in the /usr/src/ folder.

---

### Post by drpaul on 2007-03-24
this goes way beyond the header files. you need to get the src files for the kernal. much bigger dl.

HTH

Paul

---

### Post by 75sausage on 2007-03-26
I downloaded the source using the Git Guide [https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)

It seems however that this compiling requires more than just a simple guide. I keep on reading the wiki, guides, help pages, posts and cannot put this thing together.

I guess it is beyond the scope of this thread, bu any helpfull links would be appreciated.

edit: I am looking at the source and it seems I have to add my .c source to the drivers/usb/ directory then add the info to one of the debian/commit-templates/ but which one and how. I am guessing here.

Tahnks

---

### Post by drpaul on 2007-03-27
The help you need with the kernel compilation does not seem to be available on this forum. I would suggest that you look in forum pointed at drivers and custom kernels.

Sorry. :( 

Paul

---

