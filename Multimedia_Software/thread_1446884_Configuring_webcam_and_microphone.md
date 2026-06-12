---
title: "Configuring webcam and microphone"
date: 2010-04-04
forum: Multimedia Software
---

### Post by galobuntu on 2010-04-04
Hi, everyone.

I'm a new ubuntu user and I've been having problems setting up my microphone and webcam for internet use. I won a Microsoft LifeCam VX-6000 on the internet and it doesn't work on ubuntu. I'm sure it works because I also have Windows Vista installed on my laptop and it works perfectly well when using Skype, Windows Live Messenger and even Gtalk. 

This webcam model has an integrated microphone, which doesn't work either, even though it works just fine on Windows. I have tried to configure the mic, but when I test-record the sound all I can hear is just noise. I have test-recorded using a headset (which also works on Windows), but I didn't have any success, so I have to believe that I haven't configured something the way it was supposed to be or that a driver is missing. 

Does anyone have a clue on how to solve this issue? I hope somebody can give me a hand on that one. :p

Thanks in advance.

---

### Post by ajgreeny on 2010-04-04
Try the webcam with cheese to see if it is seen by that.

As regards the microphone, I suggest you run alsamixer in terminal and check that the mic level is set right, it is not muted, and also perhaps that mic boost 20db is on, if needed.  You may even have more that one mic listed so make sure you try both, if two are shown in "mic select".

You don't say which version of ubuntu you're using, but this problem seems to rear its head quite often in 9.04 and 9.10, and I even had it exactly the same in 10.04.  Fiddling with the pulse configuration settings in the various GUIs available for that did get it working.

---

### Post by xc3RnbFO8P on 2010-04-04
Read this:
[http://ubuntuforums.org/showthread.php?t=1118056]("http://ubuntuforums.org/showthread.php?t=1118056")

---

### Post by beyercj on 2010-05-14
This is how I got my Microsoft **[COLOR=#ff0000]LifeCam[/COLOR]** VX-6000 to work under Ubuntu 9.10 on a [[COLOR=#444444]Gericom Frontman[/COLOR]]("http://download.gericom.com/LCD-PC/FrontmanForce-L372/DATASHEET/L732.pdf") computer:



Download Skype from website and install


Locate libv4l (Library video for linux)
user@desktop:~$ locate libv4l 
/usr/lib/libv4l 
/usr/lib/libv4l1.so.0 
/usr/lib/libv4l2.so.0 
/usr/lib/libv4lconvert.so.0 
/usr/lib/libv4l/ov511-decomp 
/usr/lib/libv4l/ov518-decomp 
/usr/lib/libv4l/v4l1compat.so 
/usr/lib/libv4l/v4l2convert.so 
/usr/share/doc/libv4l-0 
/usr/share/doc/libv4l-0/README.gz 
/usr/share/doc/libv4l-0/README.multi-threading 
/usr/share/doc/libv4l-0/TODO 
/usr/share/doc/libv4l-0/changelog.Debian.gz 
/usr/share/doc/libv4l-0/changelog.gz 
/usr/share/doc/libv4l-0/copyright 
/usr/share/lintian/overrides/libv4l-0 
/var/lib/dpkg/info/libv4l-0.list 
/var/lib/dpkg/info/libv4l-0.md5sums 
/var/lib/dpkg/info/libv4l-0.postinst 
/var/lib/dpkg/info/libv4l-0.postrm 
/var/lib/dpkg/info/libv4l-0.shlibs 
/var/lib/dpkg/info/libv4l-0.symbols 
user@desktop:~$ 


if not already installed, you need to install [[COLOR=#444444]libv4l[/COLOR]]("https://launchpad.net/ubuntu/+source/libv4l"), a collection of libraries which adds a thin abstraction layer on top of video4linux2 devices presumably best via Synaptec (System > Administration > Synaptec Package Manager, enter "libv4l" into Quick search, reload, rightclick to mark for installation and apply)



change entry skype in System>Preferences>Main Menu>Internet>Skype>Properties>Command to 
env LD_PRELOAD=/location/v4l1compat.so skype, I.e.
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


Close
Start Skype by double clicking icon in Applications>Internet


This worked ok for me on 9.10 Karmic Koala as well as 10.04 Lucid Linux.

The picture quality can be much improved by installing v4l2ucp using synaptic. Start program in terminal with v4l2ucp /dev/videoX (X is the number shown for your video device in Skype > Options > Video. Go in the menu panel of v4l2ucp to preview > configure preview... and change Application to use to Skype. Exit with ok and start preview. This will start Skype and then you can see the changes in image quality in the preview of Skype > Options > Video as you change the settings in v4l2ucp.

Hope this makes sense.

---

### Post by Ron_ on 2010-05-16
This post duplicates one that I just made here: [http://ubuntuforums.org/showthread.php?t=1321194&highlight=vx-1000&page=3](http://ubuntuforums.org/showthread.php?t=1321194&highlight=vx-1000&page=3) .

I am using Ubuntu 9.10 amd64.  Has anyone tried   [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2) drivers on a 64-bit system?  I _really_ don't want to break what I've got (including proprietary nVidia drivers for my monitor.)

Hang on....  I just plugged in the webcam, fired up Cheese and got a decent picture _without_ installing new drivers. This is different from the last time that I tested it (a couple of months ago.), as far as I remember. Can't tell if this will be stable. PulseAudio Volume Control recognizes the webcam mic. 

Installed 64-bit Skype. Audio doesn't work. Tried LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so . Did not help audio, but it may have helped send video during calls, so I left it in. Also, I'm getting TCP and UDP hits on port 13647. Don't know how to interpret any of this.
 
Additional observations on the webcam mic:
1) I wanted to see if I needed the camera on to make the mic work. Ran Gnome Sound Recorder with and without Cheese. No sound either way.

2) Skype Options, Sound Devices shows Microphone = PulseAudio server (local) -- _not_ LifeCam VX-1000. I edited /home/xxxx/.Skype/yyyy/config.xml by hand, changing PulseAudio to LifeCam. This seemed to make no difference in the Options menu when I restarted Skype.

3) A very interesting idea appears here: [http://ubuntuforums.org/showthread.php?t=1348604](http://ubuntuforums.org/showthread.php?t=1348604) . Ghost|BTFH suggests that certain apps don't work with PulseAudio. He shows how to restore asoundconf from Intrepid's ALSA-utils. This enables toggling between two sound cards. Much to my surprise, gnome-alsamixer tells me that I have two "sound cards": Realtek ALC888 and USB Mixer. (The webcam mic is obviously on the USB Mixer.) I am too inexperienced to take this approach, but perhaps it will lead to a solution for other users.   (I tried to accomplish the same thing by installing padevchooser, without success.)

5) I also found this Known Issue at [https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype) : "When [PulseAudio]("https://developer.skype.com/PulseAudio") is enabled in the audio settings, only that specific entry will be available."

---

### Post by Ron_ on 2010-07-07
Kyle just showed me how to produce sound here: [http://ubuntuforums.org/showthread.p...72#post9560972]("http://ubuntuforums.org/showthread.php?p=9560972#post9560972") (post #12.)  Many thanks.

---

### Post by j8a on 2010-07-27
> **Ron_ said:**
> Kyle just showed me how to produce sound here: [http://ubuntuforums.org/showthread.p...72#post9560972]("http://ubuntuforums.org/showthread.php?p=9560972#post9560972") (post #12.)  Many thanks.
Today I installed a NOGANET NGW-6642 webcam with microphone incorporated.
I also installed Skype and made a Test Call, all worked fine!!

---

