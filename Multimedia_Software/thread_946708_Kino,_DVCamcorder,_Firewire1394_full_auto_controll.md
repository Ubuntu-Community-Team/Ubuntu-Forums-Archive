---
title: "Kino, DVCamcorder, Firewire/1394 full auto controll"
date: 2008-10-13
forum: Multimedia Software
---

### Post by remeeraz on 2008-10-13
I have just set up an Acer Aspire 7520 with Ubuntu 8.04, KinoDV 1.3.2 and firewire capabilities for someone who wanted to do video editing without "Gatesware" and those money grabbing software publishers.

I'm not surprised that many people can't get firewire (ieee1394) to work with Kino in Ubuntu, because the instructions I've found available are in-accurate and incorrect.

You don't need DVGrab, although you could use this instead. Follow from STEPS 9...

It also doesn't matter what version of Ubuntu you are using as (stating the obvious ) they are all LINUX and the core language is the same. But this info is written for users of Gnome.

[COLOR="DarkRed"]**If you want to be able to get firewire to work for total control of DV cams, follow STEPS 9 & 10 in the instructions.**[/COLOR]

STEPS 1 through 8 in this post will tell you how to install the Latest (as of 12 October 2008 ) version of Kino (version 1.3.2) from source code downloaded directly from KinoDV's website.

It looks a lot, but it's not really. :)

1) [COLOR="Red"]Bookmark this page so you can come back to it as we will need to restart X at some point.[/COLOR]

2) Download Kino 1.3.2 from here;
[http://downloads.sourceforge.net/kino/kino-1.3.2.tar.gz](http://downloads.sourceforge.net/kino/kino-1.3.2.tar.gz)
I'm using this version because it's the latest release at this time, and the current version in Ubuntu is "rumoured" to not work.

3) Extract the Kino folder onto your Desktop. (We'll Delete this when it's finished with.)

4) Make sure you have the following Packages installed, you may need to enable the "universe" to install them all, and you can remove them when we've finished if you want;

    * build-essential
    * cvs
    * make
    * autoconf
    * intltool
    * libtool
    * libavformat-dev
    * libiec61883-dev
    * libavc1394-dev
    * libsamplerate0-dev
    * libdv4-dev
    * libquicktime-dev
    * libasound2-dev
    * libglade2-dev
    * libxv-dev
    * ffmpeg
    * ffmpeg2theora
    * sox
    * vorbis-tools

    * nautilus-open-terminal (For ease of access to folders from a GUI,
                              without this, my instructions won't work.)

Might need to enable Multiverse for these packages, but these packages aren't essential to the build.

    * lame
    * mjpegtools
    * qdvdauthor (for advanced DVD Video authoring)


5) Close any programs and save any work and press Ctrl+Alt+Backspace to restart your X Server so that the nautilus-open-terminal plugin is loaded. Then log back in and continue...

6) Right Click on the Kino Folder on your Desktop and Select "Open In Terminal".

7) Enter these commands to start compiling the Kino Source;

```
**./configure --sysconfdir=/etc --enable-quicktime**
```
then
```
**make**
```
then
```
**sudo make install**
```

8 ) Close the Terminal and Delete the Kino Folder from your Desktop, that's done with now.

9) Add your username (the person who will be logged in and doing the Video Capturing) to the group "disk".

To do this, click **System** -> **Administration** -> **Users and Groups**

Click the appropriate username, then click the **Properties** button,
in the new window called "User Properties", click the **Group** tab.

Locate **disk** in the list and put a tick next to it.
Now click ok, and close the "User Manager".

10) Open a terminal and type;

```
**sudo gedit /etc/rc.local**
```
add the following line of text to it and save then close the file.
> [COLOR="Indigo"]**/sbin/modprobe raw1394**[/COLOR]

Now type;

```
**sudo modprobe raw1394**
```
then
```
**sudo chown** "the username concerned" **/dev/raw1394**
```

Now restart your computer and get on with it! heh :popcorn:

---

### Post by Erlander on 2008-10-14
In my opinion it is better and simpler to use the method in the official Ubuntu Community Documentation at [https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

Method 5 worked well for me on 8.04.

Rob

---

### Post by remeeraz on 2008-10-14
> **Erlander said:**
> In my opinion it is better and simpler to use the method in the official Ubuntu Community Documentation at [https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

Method 5 worked well for me on 8.04.

Rob

Good for you rob! :) I am surprised, many people have followed those instructions and still can't get anywhere.

Steps 1 through 8 are for installing Kino from Source Code. Nothing to do with getting Firewire to work.

The method I have provided (STEPS 9 & 10) will make sure that the user is able to control their camera with the software's own control features, and it makes sure that they can keep doing it, reboot after reboot.

Search a little more and you'll see what I'm on about.

PS The community documentation is not "Official" as anyone can edit them, hence the name "Ubuntu Community Documentation"

---

### Post by kinu on 2008-11-26
Hi reemeraz,

Great post. It work for me the first time I tried. After reboot, I captured some video, using Kino.

But now I'm lost. I turned off the camera, and next time I trid to use it Kino can see the camera,  I got the "no camera exists" message with dvgrab, and dmesg have this message

```
[  924.077661] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0800FFC0
```

every time I try to connect or turn on the camera. I've tried to reproduce the right process, but I got same thing again and again.

Could you please help me?

---

### Post by macpointman on 2008-12-04
> **Erlander said:**
> In my opinion it is better and simpler to use the method in the official Ubuntu Community Documentation at [https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

Method 5 worked well for me on 8.04.

Rob

This

[I]Ubuntu 8.04 (Hardy Heron)

The only reason that Kino cannot capture from Firewire in Hardy is that the software was compiled incorrectly. A correctly compiled version is available here: [kino_1.3.0-2ubuntu0_i386.deb]("ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu-packages/hardy/kino-video-editor/kino_1.3.0-2ubuntu0_i386.deb"). This will not install on Ubuntu 8.10.  [/I]

Worked like a charm.  Now all I need to do is get flash to see the DV Camcorder and to be able to use it as a webcam.  Got Any Ideas?

Thanks
MacPointMan

---

### Post by trapet on 2008-12-13
Hi, thank you for the information. I'm a nubie to Linux. Re step #4, how do I check if any of the required packages are installed? Also, I tried another instruction, which was to type ./configure. I did that, and my system gave me this error

"checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details."

Any ideas? Here's what I really need to do. I have a mindv camcorder. I'd like to import the videos from the minidv to my computer. I believe firewire can do that. I bought a firewire cable, plugged it into my WindowsXP desktop, nothing happened. I plugged connected my xp desktop to my ubuntu desktop, nothing happened. I stumbled upon info about Kino, which I presume can help me. Well, right now, I'm stuck. Any help would be greatly appreciated.

---

### Post by kinu on 2008-12-14
> **macpointman said:**
> This

[I]Ubuntu 8.04 (Hardy Heron)

The only reason that Kino cannot capture from Firewire in Hardy is that the software was compiled incorrectly. A correctly compiled version is available here: [kino_1.3.0-2ubuntu0_i386.deb]("ftp://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu-packages/hardy/kino-video-editor/kino_1.3.0-2ubuntu0_i386.deb"). This will not install on Ubuntu 8.10.  [/I]

Worked like a charm.  Now all I need to do is get flash to see the DV Camcorder and to be able to use it as a webcam.  Got Any Ideas?

Thanks
MacPointMan

I've tried all the solutions, step by step, and same thing. Sometimes it works, but most of the time, it fails with the "no camera exists" message. So I will try with another linux, and I'll tell you what happens.

Thank you anyway.

kInU

---

### Post by Bucky Ball on 2008-12-15
Yep, I am in exactly the same boat. I've tried everything. Camera works fine in windoze, but can't get a peep out of it in Kino or Cinelerra. Odd thing - the only AV control that works for me is 'stop' in Kino. That is what I am trying to get happening. If I manually operate the camera, Kino works fine (I have stop!). But what fun is that? A drag actually as I have hours of stuff to review and edit and I would *reeally *like to do it in Ubuntu. But have spent too much time trying to nut it out already so just about time for windoze ... :(

My full saga is here:

[http://ubuntuforums.org/showthread.php?t=1011774](http://ubuntuforums.org/showthread.php?t=1011774)

---

### Post by DrewT on 2009-02-20
I just tried this and my new version of Kino is still blind to my camera. I hope I can get it to work because otherwise I added an awful lot of developers' code to my installation for nothing. (I am not a coder and don't expect to become one in this life.)

I do note that the instructions for adding a group to a user (or vice versa, whatever the correct usage is) don't apply to 8.10, which does not have a Groups tab under Users and Groups/[user]/Properties, but instead has a Users and Groups/Manage Groups tab, which requires using the Unlock button to work. I did that, but there was no "disk" group listed. So I made one and added myself (and sudo) as members. But as I say, no joy.

Not sure if this is diagnostic but the "make" command ran a long time and produced an awful lot of warnings (unintelligible to me, and hopefully harmless) before it was through. Unfortunately I didn't think to copy the contents of Terminal before closing it, and I wouldn't know what part to post anyway -- it was an enormous amount of text.

---

### Post by DrewT on 2009-02-20
Here's a thought. Do I need to do more than is specified above to activate the rc.local script? Like, uncomment the first line maybe? Here's my rc.local file in its entirety:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# following line added by *** 2/20/09 per 
# http://ubuntuforums.org/showthread.php?t=946708&highlight=video+capture+1394

/sbin/modprobe raw1394

exit 0
```

---

### Post by Bucky Ball on 2009-02-21
Adding to my problems ... I just finished a video course at uni. We had a camera each for three weeks and guess what? Kino had better control of the camera than the Macs in the Media Lab at uni so I captured everything at home on my Ubuntu box! Kino recognised the newer camera from uni  immediately (a Sony HD something ... I can get the details if anyone's curious) so I had everything right with the Ubuntu set-up after all. It was my old Panasonic camera that was (and is) the problem. Good luck with it all. :)

---

### Post by bamitt on 2009-02-21
I was hoping this worked for me but no go.  I am runing Ubuntu 8.1 with Kino 1.3.0.  I am to see or control my mini DV camera (both the Panasonic PV-DV900 and the Sony Handycam DCR-HC32)

Is there a way I can check to see if the firewire hardware in my system is working properly?

I have tried different cameras and firewire cables with no change.

Thanks in advance for the help.

---

### Post by Bucky Ball on 2009-02-21
I think you might perhaps have you ieee permissions wrong. Make sure you are in the right group in Users and Groups.

Is Kino (or whatever you are using), or Ubuntu for that matter, identifying the camera correctly and you just don't have AV control from your desktop? If so, it is probably the permissions.

---

### Post by DrewT on 2009-02-23
> I think you might perhaps have you ieee permissions wrong. Make sure you are in the right group in Users and Groups.

Is Kino (or whatever you are using), or Ubuntu for that matter, identifying the camera correctly and you just don't have AV control from your desktop? If so, it is probably the permissions.

I hope this isn't addressed to me, 'cause I have no idea what the first paragraph means. As to the second, no, the machine isn't seeing the camera at all. But now neither is my Mac. I need to make sure I've got a good cable before I try to troubleshoot this further.

---

### Post by bamitt on 2009-02-23
> **Bucky Ball said:**
> I think you might perhaps have you ieee permissions wrong. Make sure you are in the right group in Users and Groups.

Is Kino (or whatever you are using), or Ubuntu for that matter, identifying the camera correctly and you just don't have AV control from your desktop? If so, it is probably the permissions.

The user account is part mof the "root" group.

I have run the following commands to try to be sure the properties and permissions are correct:

sudo modprobe raw1394
sudo chown "username" /dev/raw1394

I am unsure how to check it further.

I have also started kino as root and it did not have any impact.

The camera doesd not show up in kino as an avaialble 1394 device and Ubuntu says it is not running any proprietary drivers.

Being new to ubuntu I am unsure where to look but it appears that the system is not seeing anything connected to the firewire port or does not have the interface active.

Any help is appreciated.

---

### Post by DuncanNZ on 2009-02-23
Hi there, I've updated the instructions on [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) and would love it if you could take a look and let me know if you hit any problems. I'll try and help you in this thread.

---

### Post by Bucky Ball on 2009-02-23
Way to go, DuncanNZ. I have my desktop working fine with it all, but as it happens, I have just built a machine for someone else and they want to do some video editing. I am gonna be putting the firewire card in and getting the camera up within the next few days so I'll try by following your instructions and let you know how I go ... :)

---

### Post by Bucky Ball on 2009-02-26
Hey, DuncanNZ, I followed your instructions for getting the camera up. This is what worked for me, and it took about five minutes. Because this machine is for my mother-in-law, ie she doesn't want to be going to a terminal and typing 'gksudo kino' all the time, I created an application launcher for kino in the toolbar, right clicked the launcher, went to properties and changed the command to 'gksudo kino %F'. The '%F' was already there so I thought I'd better use it. And my Panasonic NV-DS60 camera works as good as it is going to in Ubuntu (works the same on my desktop which I know is set up correctly from my experience with the newer camera from uni which worked better in Kino than on the Macs at uni, perfectly). It doesn't have much of a record from what I've seen in my research so I am glad the camera works at all. Works no problem if you control it from the camera, not the AV controls in kino.

Your page is good and concise. Got me up in no time but I only needed that one command. Cheers.

---

### Post by DrewT on 2009-02-27
Just an update from here. All efforts stalled while I tried to figure out whether my 1394 controller is functional. Apparently it is not. My best guess is that it was fried as the result of a bad cable. It is not alone. The controller on one of my Macs also appears to be dead, along with ports on a couple of external drives and on two Digital8 cameras, one of which I recently bought on eBay because the 1394 controller on the first had died. Also apparently destroyed is the 1394 controller on my Canopus ADVC300. Probable repair bill: $500 or more. 

All of this comes as a shock to me. Apparently the dangers posed by six-conductor Firewire connections have been recognized, especially where it is used all the time for business reasons. (See [http://www.wiebetech.com/whitepapers/FireWirePortFailures.php](http://www.wiebetech.com/whitepapers/FireWirePortFailures.php).) But I sure didn't see anything about this on Apple's or Sony's pages. 

I'm on a bit of a crusade now to warn everyone using it:  If you suspect you might have a bad Firewire cable, and if it has the six-conductor connector at either end (i.e., the standard bullet-profile connector), throw it away NOW and try a brand new one from a reliable manufacturer.  The alternatives just aren't worth it.

---

### Post by Bucky Ball on 2009-02-27
Damn, DrewT. That sucks bad ... :(

---

### Post by remeeraz on 2009-04-10
> **kinu said:**
> Hi reemeraz,

Great post. It work for me the first time I tried. After reboot, I captured some video, using Kino.

But now I'm lost. I turned off the camera, and next time I trid to use it Kino can see the camera,  I got the "no camera exists" message with dvgrab, and dmesg have this message

```
[  924.077661] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0800FFC0
```

every time I try to connect or turn on the camera. I've tried to reproduce the right process, but I got same thing again and again.

Could you please help me?

Are you still having this problem? Sorry for the "delay" in response, I've been busy with Fedora. Reason I asked is that I will have to Set-up a machine capable of simulating this error before I can figure out what to do, but until you let me know I will not do anything.

---

### Post by alwayshere on 2009-05-07
this may help someone ? kino working good as for me [http://ubuntuforums.org/showthread.php?t=1149054](http://ubuntuforums.org/showthread.php?t=1149054)

---

### Post by mannequin on 2009-05-14
> **remeeraz said:**
> 
```
**sudo chown** "the username concerned" **/dev/raw1394**
```
I don't think this is the best route to take, especially with multi user systems where two people may want access (at different times) to a / the camera.

Since you are already a member of the 'disk' group (via step 9), why not have '/dev/raw1394' be part of that group?  Works for me and, personally, I think this is a more elegant solution:

```
sudo chown root:disk /dev/raw1394
```-M.

---

### Post by BloomingNutria on 2011-11-21
I am attempting to use this fix, and I could not even get past compiling the version of Kino you instructed us to download. I got the following error after the "make" command (it went through a 4 minute process first):

v4l.h:43:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[3]: *** [kino_common.o] Error 1
make[3]: Leaving directory `/home/sam/Desktop/kino-1.3.2/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sam/Desktop/kino-1.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sam/Desktop/kino-1.3.2'
make: *** [all] Error 2

I followed your instructions exactly and downloaded every single package you asked for. I am very new to Linux, but I really want to be able to do this. What could be wrong? Can you please help me?

I am using Xubuntu 11.10 with the 3.0.0-13-generic-pae kernel.

---

### Post by Bucky Ball on 2011-11-21
Post a new thread. You will have more luck. This thread is three years old and very dead.

---

