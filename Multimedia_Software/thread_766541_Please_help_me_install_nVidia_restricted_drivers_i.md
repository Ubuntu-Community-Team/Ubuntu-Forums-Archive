---
title: "Please help me install nVidia restricted drivers in 8.04"
date: 2008-04-25
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2008-04-25
UPDATE:  SOLVED

Hi, all.

I just completed a fresh install (repartitioned/reformatted disk) of Ubuntu 8.04 Hardy Heron.  The first thing I did after installing Ubuntu was to go enable the restricted driver for my nVidia GeForce FX 5200 AGP.  However, now that I've installed the driver and rebooted, the maximum screen resolution Ubuntu will allow me to choose is 640x480.

I thought perhaps installing nvidia-settings would allow me to play with options till I got the video card working, but nothing I could think of solved the problem.  I've also tried various terminal commands suggested in other threads, but to no avail.  I even re-installed Ubuntu itself, without luck.

The FX5200 worked great in 7.10 Gutsy Gibbon; why not now in 8.04 Hardy Heron?

Any help would be much appreciated!

Thanks in advance,
--Ben

---

### Post by nirudha on 2008-04-25
Try what I suggested at

[http://ubuntuforums.org/showthread.php?t=766489](http://ubuntuforums.org/showthread.php?t=766489)

If you need more detailed info let me know.

Cheers!

---

### Post by hurtstotalktoyou on 2008-04-25
> **nirudha said:**
> Try what I suggested at

[http://ubuntuforums.org/showthread.php?t=766489](http://ubuntuforums.org/showthread.php?t=766489)

If you need more detailed info let me know.

Cheers!

Thank you for the link, but unfortunately I do need more detailed info (I've been using Gutsy regularly for ~5 months, now, but I'm still a newbie in many ways).

Consider:

> **nirudha said:**
> In the end I opted to download the beta driver from NVIDIA itself and install it.

Is that this:

[NVIDIA-Linux-x86-169.12.pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)

?  That's the driver the nVidia website tells me to download for the FX 5 series and 32-bit Linux (I'm running i386, not x64).  However, I do not know how to install it.  Alien doesn't recognize *.run files, and chmod doesn't seem to help, either.  I managed to gksudo nautilus and run it as a program, but it tells me that I need to close Xorg before I can install it.  This is problematic since I can't get the *.run file to install without nautilus.

Or do you mean some other driver?  If so, which?

Please keep in mind that I'm really pushing the limits of my Ubuntu knowledge.  I only barely know what I'm talking about in the above paragraphs.

Thanks for your help!

---

### Post by nirudha on 2008-04-25
Hey, Let me see if I can give you a step by step guide. I suggest you print it out or jot it down if your not sure of the commands etc.

The driver you downloaded isn't the sort of package you can install with alien or other package manager. It is a script which you run and it installs the required files, at times compiling bits it doesn't have. So we start by installing the tools needed to compile programs by issuing the following command (I think it has an S at the end but if it gives an error try without)

**[INDENT]sudo apt-get install build-essentials[/INDENT]**

The next step is to stop linux from loading the open source Nvidia drivers. This is done by opening a file for editing
[B]
[INDENT]sudo nano /etc/default/linux-restricted-modules-common[/INDENT][/B]

this brings up a simple text editor. You use the arrow keys to move your cursor and just type in what you need. When your done CTRL-X will prompt you to save. Press Y and then Enter when it asks for the filename as it defaults to the original filename. Edit the line that says

DISABLED_MODULES=""

to read

DISABLED_MODULES="nv"

Now for good measure I would go to "System->Administration->Hardware Drivers" and disable the use of the Nvidia driver listed there.

Then go to "System->Administration->Synaptic Package Manager" and search for nvidia. Look to see if any of the following are selected (marked with a green box)

nvidia-glx
nvidia-glx-new
nvidia-kernel-common

If you they are marked right click on each and mark for removal.

Apply the changes. I found that until I did this the driver I downloaded didn't load.

Now you have to install the downloaded driver. Make sure you know the path to where it is.

Press CTRL+ALT+F2 to get a text session and login. Once you do stop the X server by

**[INDENT]sudo /etc/init.d/gdm stop[/INDENT]**

now run the downloaded driver installation script by

[B][INDENT]cd <path where driver is located>
sudo sh ./NVIDIA-Linux-x86_64-169.12-pkg2.run[/INDENT][/B]

Of course the filename of your driver will be different!

Hint: you can start typing part of the file name and hit tab and it will try and autocomplete it. This works if there are no other files with a similar name in the directory.

Follow the on-screen instructions and let it run the X config program as when it asks you.

Once this is done reboot and keep your fingers crossed!
[B]
[INDENT]sudo reboot[/INDENT][/B]

I hope this works for you. Let me know either way.

---

### Post by hurtstotalktoyou on 2008-04-25
edit - duplicate post

---

### Post by hurtstotalktoyou on 2008-04-25
Thanks for the help, but it turns out the nVidia driver was working just fine.  Ubuntu 8.04 wasn't recognizing my old 17" CRT display for some reason.  Apparently many others have been having this problem, too.  This is how I fixed it:

[http://ubuntuforums.org/showthread.php?t=766681](http://ubuntuforums.org/showthread.php?t=766681)

Thanks again!

---

### Post by cor2y on 2008-04-25
I tried that the minute i selected the correct monitor the desplay went all wonky so i had to fall back to the open source drivers which after selecting the correct monitor displayed correctly but fullscreen video playback is really terrible.

---

