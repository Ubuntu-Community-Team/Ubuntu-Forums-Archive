---
title: "Cinelerra installed, but non functional?"
date: 2008-05-19
forum: Multimedia Software
---

### Post by AngelKnight on 2008-05-19
I recently followed the directions at [http://cinelerra.org/getting_cinelerra.php#hardy]("http://cinelerra.org/getting_cinelerra.php#hardy") for getting Cinelerra installed on my machine, and installed the cinelerra-k8 package (I'm running on an AMD 64 3200+), and I'm beginning to wonder if I shouldn't have picked the regular cinelerra package....

But at any rate, all installed OK (no errors), and I was able to start the application and get all the windows (4 of them) showing on my screen. BUT, I am unable to do ANYTHING at all in the windows. They completely appear to be locked. None of the menus work in the main window, and even attempting to close the windows using the title bar ('x' and also right clicking and selecting to close window) on any of the windows does nothing. I ended up having to kill -9 the cinelerra process (twice -- first time it just reset the parent process to be 'init', so had it do it a second time for it to properly go away).

Anyone run into this trouble? Should I be using the regular cinelerra package, or should I be ok with the k8 one?

Thanks in advance!

(system is Ubuntu 8.04 Hardy Heron x86_64 running on AMD 64bit 3200+ CPU [single core])

---

### Post by KoenW on 2008-05-28
Try installing the new updated kernel. This might solve your problem (did with me on the 32-bit versionà. 

Koen

---

### Post by ubundah001g on 2008-05-28
You are not alone! The same thing happened to me too. I installed Cinelerra from the instructions given at the Cinelerra Community.

The instructions for Ubuntu Studio 8.04 worked to install the software using Synaptic package manager. In trying to run the software from either the command line or the menu option under video, the Cinelerra 2.1 version did bring up the splash to load the program and the four windows did start. All that looks good. Trying to select the File menu with the mouse does nothing. Trying to select any other menu items does with the mouse does nothing. Trying to close the window does not close it.

Ubuntu Studio 8.04 amd64 version,  2.6.24-17-rt #1 SMP PREEMPT RT Thu May 1 15:21:57 UTC 2008 x86_64 GNU/Linux

> Try installing the new updated kernel. This might solve your problem (did with me on the 32-bit versionà. 

This is with the upgraded kernel and updates to Ubuntu Studio applied. The version of Cinelerra tried was the plain verison and the K8 version. Both gave the same results.

Trying the command listed on some web pages to "echo "0x7fffffff" > /proc/sys/kernel/shmmax" did not solve the problem. Trying to run Cinelerra in gdb did not give any meaningful output, as gdb complained that there was "no debug symbols." Cinelerra was built without the debug symbol option.

What is the solution to this problem? The program is being run in user mode. Isn't that the way that it is supposed to work?

For Ubuntu Studio 8.04, getting the non-Community sources and trying to build them causes errors because the configure script uses the "arch" command and Ubuntu Studio does not have that command in its packages for the standard installation. Making a script using "uname -m" does not solve the problem either.

I have Cinelerra installed, and want to run it. What is the solution to the unresponsive widgets? What configuration can make it work the way that it is supposed to in Ubuntu Studio? This must be a common problem. Trying to run cinelerra --help does not bring up a help menu text but launches the program. What does Cinelerra need to be run from user mode, as in Ubuntu Studio?

If this helps, I also tried "sudo chown -R youruser:yourgroup ~/.bcast" and no change.

It DOES run as root. If you do not care about security, run it as root. If someone knows how to get it to run in user mode, please tell us in the forum! thx.

---

### Post by ubundah001g on 2008-05-28
Problem may be in using the RT kernel. Check to see what kernel you are running. If it is the RT kernel, then it only runs as root, unless you adjust other settings. 

> uname -a

Use Synaptic Package Manager to add plain kernel (latest) and apply. Then reboot, and select the generic kernel. If you do not get a selection menu, then you will need to edit your timeout on the boot prompt menu configuration (lilo or grub). 

My problem was solved by not using the RT kernel, and Cinelerra runs in user mode. Cool. Now, to see if it will edit DV without crashing.

---

### Post by deflagmator on 2008-08-13
Hello,
For me the only solution to work as normal user (instead of root) is to install the rt kernel.

I have tried all the possibilities and this is the only that work. The other generic kernel hanged cinelerra. (also as root)

I use hardy 2.6.24-19-rt kernel amd64 with the akirad repo and cinelerra-k8 package. Sound perfect with pulseaudio.

Today 3 hours working perfect.

---

