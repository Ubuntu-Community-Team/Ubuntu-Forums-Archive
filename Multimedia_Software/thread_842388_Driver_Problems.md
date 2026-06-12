---
title: "Driver Problems"
date: 2008-06-27
forum: Multimedia Software
---

### Post by Conjord2 on 2008-06-27
Hello.

Earlier this week Windows Vista ticked me off for the last time. I would imagine you all know the story, it's slow, likes to crash, bringing his little friend "Blue screen of death" for a visit all too often, not to mention that most of the software I used was open source anyway. I must say, I very much like Ubuntu but, and now to the point of my post, I am having some driver problems. :confused:

I am running the 64bit Ubuntu.

I have more or less lived on the Ubuntu IRC for a couple of days, and I thought I would make a post here.

First of all is my sound card. The much hated (from what I can gleam off the IRC chat) Creative X-Fi.

I downloaded the driver from [http://opensource.creative.com/](http://opensource.creative.com/). And after following the readme instructions (Here: [http://paste.ubuntu.com/22599/](http://paste.ubuntu.com/22599/)) got nowhere. 

I got this for my (and that of the nice people talking me through it) effort. [http://paste.ubuntu.com/22596/](http://paste.ubuntu.com/22596/)

After posting that someone said "ick. I bet you don't have a fully-configured kernel source tree lying around?"

"config-2.6.24-19-generic appears to be the latest kernel config file

"If you type uname -a, does the kernel version match this?

 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux"

I have to say, I don't understand any of that. I don't know where to start, what to do, my knowledge of Linux is..0.

I had a look at the forums and followed some instructions posted in one of the stickied posts and got 

Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Unknown device 0029
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at df00 [size=32]
	Memory at efc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at e8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
------------------------------------------------------------------

I also have problems with my printer, Cannon MP140. No idea where to start there.

----------------------------------------------------------------------

And last of all my graphics card. Nvidia Geforce 8800 GTS. I got the linux drivers. One is named NVIDIA-Linux-x86_64-1.0-9746-pkg2.run. When I exit gnome (Using the command "sudo /etc/init.d/gdm stop"), the site tells me to type "sh NVIDIA-Linux-x86_64-1.0-9746-pkg2.run " It isn't working. In fact, nothing happens, I change directory, nothing, I get no information what so ever.

--------------------------------------------------------------------

If you need more information or have any ideas at all I would be happy to read your replies. :) Thank you. :)

---

### Post by Conjord2 on 2008-06-29
Bump :)

---

### Post by abhilashkumar on 2008-07-07
TRY THIS

1. install alien Symaptic Package Managerunder System, Administration.
2. Go to [HTTP://www.canon.com](HTTP://www.canon.com), Support and get the 4 required Linux Drivers. cuijfilter common and cuijfilter MP140 series, scangearmp common and scangearmp 140 series drivers. Download them to your desktop. Get the .rpm version only for this to work.
3. These files are in the .rpm format and they need to be converted to .deb.
4. use the terminal window. cd ~/Desktop. That will put you in the desktop.
5. Convert the files to .deb by using sudo alien --scripts scangearmp-common-1.10-1.i386.rpm and sudo alien --scripts cuijfilter-common-2.80-0.i386.rpm. These are only examples and you need to be exact or it will not work.
6. Double Click the .deb files and they will be installed. Install the common files first then the 140 series next.
7. Reboot the computer and the scanner will show up in the GIMP Image Editor, File, Qcquire, Scangearmp.
8. You then need to go to System, Administration, Printing and configure the MP 145. It is called the MP 140 series and Make and model is a Canon PIXMA MP150 CUPS ..........

---

