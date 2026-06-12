---
title: "Soundblaster X-Fi drivers?"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by Dark Damo on 2006-10-07
Hello everyone. I cant seem to find any drivers for my SoundBlaster X-Fi XtremeMusic sound card. Have any been released? If so could you help me find them and install. Thank you very much.

---

### Post by maccam94 on 2006-10-08
Hey, I'm in the same boat as you. Unfortunately, Creative has not released any documentation or drivers yet, and they aren't planning to release their Linux drivers until next year. Use onboard sound or another card if possible.

---

### Post by lewisskinner on 2007-12-04
OK, so over one year after this thread was first started, can Creative released any drivers yet for SB X-Fi?

---

### Post by cipher_nemo on 2007-12-04
Scroll down to X-Fi section:

[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

---

### Post by lewisskinner on 2007-12-04
Thanks pal.

For an absolute beginner here, how to I extract it, where to, and how do I run it?

---

### Post by Melcar on 2007-12-04
I just can't seem to even get the installer to start for the damn thing.  I'm thinking of giving this X-Fi to my bro in exchange for his Audigy 2ZS, just to avoid the headaches.  I doubt Creative will release a stable, functional driver anytime soon.

---

### Post by cipher_nemo on 2007-12-04
From their site, they state: "*To install the driver, do the following:    *[LIST=1]
[*]*Download the XFiDrv_Linux_US-1.04.tar.gz package onto your local hard disk.*
[*]*Double-click the downloaded package to unpack its contents.*
[*]*Read the README file and follow the instructions.*"[/LIST]Make sure you download and extract it somewhere inside your home folder so you can access it without having to worry about file permissions.

Apparently a readme file exists when it's extracted. I'm at work, so I'm stuck on a Windows PC and can't test the install of it, but I can post the contents of the readme file for convenience.

Readme file (you'll be using the 2.6 kernel instructions):

[COLOR=Blue] ====================================================================

  Sound Blaster X-Fi Linux x86_64 Beta Driver Readme File

  September 2007

====================================================================

The purpose of this document is to describe how the X-Fi Linux device 
driver is built, packaged, and released.


 Quick install

=============


1) You must have the fully configured source for the Linux kernel and 
   ALSA which you
 want to use for this device driver. Partial installed 
   kernels (e.g. From distribution makers) may be unusable for this 
   action.

 2) Run one of the following commands as root in the terminal:



   ./installer



   OR


   ./installer --with-alsainc=<ALSA_include_directory>



  * ALSA Source Tree



   On 2.6 kernels, the location of the ALSA source include directory

      is parsed automatically from the running kernel.

      If it is not in the standard place, specify the path via

   --with-alsainc=<ALSA_include_directory>.



  On 2.4 kernels, the location of the ALSA source include directory

      must be specified via --with-alsainc=<ALSA_include_directory>.



  * Note
      If integrated ALSA is to be used to build, --with-alsainc option

      must not be specified.




Uninstall

=========


In the terminal,


1) Change directory to /opt/Creative/XFiDrv_Linux_US-1.04



2) Run the following command as root


   ./configure

   make uninstall



 * Note

      For GNOME users, You may need to close the Volume Control
      applet before uninstalling. Right-click the Volume icon on the
      GNOME panel and select "Remove From Panel"



3) Manually delete all files in /opt/Creative/XFiDrv_Linux_US-1.04






Copyright (c) 2007 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================[/COLOR]

---

### Post by lewisskinner on 2007-12-04
I've downloaded it, move to the / drive, hit extract, and then typed ./installer into the Terminal, and it wont work.  Do I need to begin sudo or $ or anything like that?  It just says no such directory

---

### Post by cipher_nemo on 2007-12-04
Yup, the readme states that you'll need to run it as root (which is not feasible in ubuntu), so running it with the prefix "sudo" as you mentioned should work. You'll need to change the directory to the current location of the file you downloaded and extracted. For example (replace "my_user_name" with your current user name) if it's on the desktop:

```
cd /home/my_user_name/Desktop/XFiDrv_Linux_US-1.04
sudo ./installer
```

---

### Post by lewisskinner on 2007-12-04
Getting error message:

[I]This product only support 64-bit Operating Systems
Setup will now exit[/I]

I do have the 64-bit OS.  What's wrong this time?

---

### Post by cipher_nemo on 2007-12-04
When you first downloaded Ubuntu to burn the iso image on a CD (if you installed that way), it asks you...

"What type of computer do you have?"

And then it gives you a choice of one of these three options:[LIST]
[*]Standard (x86, Pentium, Celeron, Athlon, Sempron, Duron)
[*]64-bit AMD and Intel computers
[*]Sun UltraSPARC[/LIST]Most people would probably install the 32-bit version. Only newer CPUs such as Intel Core 2 models and AMD Athlon 64, Turion 64, Sempron 64/LE, and Opteron can run 64-bit version of Linux.

What CPU do you have, and are you sure you installed the 64-bit version of Ubuntu?

It looks like Creative Labs in all of their wisdom released this only for 64-bit Linux systems. I guess they figured no one would use an X-Fi chip on a regular Pentium or Athlon?

---

### Post by lewisskinner on 2007-12-04
Yep, I downloaded and installed the 64-bit version.  I was originally only going to use the 32 bit, until I spotted this:

[img]http://i4.photobucket.com/albums/y122/darkeyes_lewj/systemspec.jpg[/img]

and thought better of it (just in case something like this came up)

It is entirely plausible that I downloaded the 32-bit in error, or installed from the 32-bit CD (I borrowed a CD from a mate before I realised I had a 64-bit chipset).  Is there any easy way to tell if the linux is 32- or 64-bit, and is there any way to check whether the liveCD I'm using hold the 32- or 64-bit system?

---

### Post by Melcar on 2007-12-05
> **lewisskinner said:**
> Getting error message:

[I]This product only support 64-bit Operating Systems
Setup will now exit[/I]

I do have the 64-bit OS.  What's wrong this time?

I get the same thing, even thought I'm running Ubuntu 64bit.  Their is an installation how to somewhere on the 64bit Users section of this forum, and it mentions something about a patch; I will try that later.  
I did manage to get the installer to work on OpenSuse (the whole process goes without errors) but sound still doesn't work.

Edit:
It seems that you indeed have to [jump hoops]("http://ubuntuforums.org/showthread.php?t=571656") to get this thing working.  I don't mind compiling kernels, but right now I don't feel like it; I much rather switch to an old 2ZS.

---

### Post by cipher_nemo on 2007-12-05
Yup, then I'd lay some pressure on Creative Labs. If you know you have the 64-bit version of Ubuntu installed, then may be Creative Labs has a command line option for the installer that kills the 64-bit detection so you can install it?

It's really sad to see Creative Labs so behind on their Linux side. They at least have open-source drivers, but I'd personally rather have up-to-date closed-source (Ubuntu restricted) drivers than all open-source drivers that are 1+ years behind.

I'm glad I have an old Audigy 2ZS card in my HTPC and a C-Media chip based Auzen X-Meridian (C-Media Oxygen HD CMI8788 ) card in my gaming rig. Both supported natively in ALSA.

I hope Creative Labs will be able to help, or if worse comes to worse, may be a software engineer can look at the open source for the installer to see if any command line parameters toggle 64-bit detection warnings?

---

### Post by lewisskinner on 2007-12-05
Can you tell me if there is a window that will tell me whether I am running the 32- or 64-bit Ubuntu?  I am fairly sure, (95%) but just want to check!

---

### Post by cipher_nemo on 2007-12-06
Let me know what this tells you in a terminal window:
```
uname -m
```

---

### Post by lewisskinner on 2007-12-06
> **cipher_nemo said:**
> Let me know what this tells you in a terminal window:
```
uname -m
```

It says:

 *x86_64*

---

### Post by lewisskinner on 2007-12-06
OK, I searched around, and I found a problem in the installer file.  I need to change:
```
platform=$(uname -i)
```
to 
```
platform=$(uname -m)
```

I did so, and the installer started to work, but now I have:

```
Installation is in progress. Please wait...
tar: XFiDrv_Linux_US-1.04: time stamp 2009-09-20 07:31:00 is 56436919.017131657 s in the future
/opt/Creative/XFiDrv_Linux_US-1.04
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
Makefile:16: /tmp/xfisrc/Makefile.conf: No such file or directory
make: *** No rule to make target `/tmp/xfisrc/Makefile.conf'. Stop.
Makefile:16: /tmp/xfisrc/Makefile.conf: No such file or directory
make: *** No rule to make target `/tmp/xfisrc/Makefile.conf'. Stop.
Installation Unsuccessful
lewis@Lewis-Jen:~/Desktop/XFiDrv_Linux_US-1.04$ 
lewis@Lewis-Jen:~/Desktop/XFiDrv_Linux_US-1.04$ 
lewis@Lewis-Jen:~/Desktop/XFiDrv_Linux_US-1.04$ 
lewis@Lewis-Jen:~/Desktop/XFiDrv_Linux_US-1.04$ 
lewis@Lewis-Jen:~/Desktop/XFiDrv_Linux_US-1.04$ 
```

I cannot open the said config.log file.  Any more ideas?

---

### Post by cipher_nemo on 2007-12-07
It looks like you have gcc, but the C compiler is unable to create the files the installer needs, probably due to Creative Labs' error. That stinks.

So what are the contents of the config.log file it generated?

---

### Post by lewisskinner on 2007-12-07
> **cipher_nemo said:**
> It looks like you have gcc, but the C compiler is unable to create the files the installer needs, probably due to Creative Labs' error. That stinks.

So what are the contents of the config.log file it generated?

As I said, it wont let me open it.  I always get one of the following:

[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot-nautilus.png[/IMG]

[IMG]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot-1.png[/IMG]

I did try again though, having edited the *platform=$(uname -i)* to *platform=$(uname -m)*.  I now get this:

```
lewis@Lewis-Jen:~/Desktop/XFiDrv_Linux_US-1.04$ sudo ./installer
./installer: 104: more: not found

Enter Yes to indicate that you have read and accepted all the terms of the above agreement.
If you enter No, the installation will abort.
[Yes/No]
```
**y**

```
./installer: 139: more: not found

Enter Yes to indicate that you have read and accepted all the terms of the above agreement.
If you enter No, the installation will abort.
[Yes/No]
```
**y**

```
./installer: 321: more: not found
Installation is in progress. Please wait...
tar: XFiDrv_Linux_US-1.04: time stamp 2009-09-20 07:31:00 is 56394308.465818132 s in the future
/opt/Creative/XFiDrv_Linux_US-1.04
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
Makefile:16: /tmp/xfisrc/Makefile.conf: No such file or directory
make: *** No rule to make target `/tmp/xfisrc/Makefile.conf'. Stop.
Makefile:16: /tmp/xfisrc/Makefile.conf: No such file or directory
make: *** No rule to make target `/tmp/xfisrc/Makefile.conf'. Stop.
Installation Unsuccessful
lewis@Lewis-Jen:~/Desktop/XFiDrv_Linux_US-1.04$
```

---

### Post by pfunkman on 2007-12-07
Full how to [here]("http://ubuntuforums.org/showthread.php?t=571656")

---

### Post by zzHanks on 2008-01-09
> **lewisskinner said:**
> Getting error message:

[I]This product only support 64-bit Operating Systems
Setup will now exit[/I]

I do have the 64-bit OS.  What's wrong this time?
Same here. 
Help would be awesome.

**Edit: Wow, I didn't see the otther pages**

---

