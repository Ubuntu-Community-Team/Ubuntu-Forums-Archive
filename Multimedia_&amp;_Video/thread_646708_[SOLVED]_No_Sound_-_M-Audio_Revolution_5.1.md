---
title: "[SOLVED] No Sound - M-Audio Revolution 5.1"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by pickboy87 on 2007-12-21
[I'm at work, so I'll try to do this the best I can before I can be at home again. I'm also a Linux n00b, I can do anything I want in Windows, but Linux I'm still very much learning]

I can't get sound out of the M-Audio Revolution 5.1 soundcard...well I did at one point, but now I can't. Here's what went down:

1. Installed the card into my computer.
2. Could only get sound out of the right speaker using the default ALSA drivers that Ubuntu 7.10 came with.
3. Installed the newest OSS drivers from 4front.
4. Soundcard worked just fine, could get sound out of both speakers.
5. Messed around with the sound settings a bit, but still could get sound.
6. Hadn't rebooted since installing my card.
7. Ubuntu wanted a new kernel update, so I updated and rebooted.

Now I don't get any sound out of that card, but the computer shows it as there. Just using Klipsch 2.1 Promedia speakers plugged into the speaker jack in the back. Any suggestions guys?

Thanks in advance,
Nathan.

---

### Post by pickboy87 on 2007-12-21
lspci -v|grep Audio gives:
> 00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: VIA Technologies Inc. M-Audio Revolution 5.1

The first device is my onboard sound, which currently works. I just can't seem to get sound out of the M-Audio device.

What other information do you guys need?

---

### Post by pickboy87 on 2007-12-22
I hate to do this, but "bump".

No one has any ideas on how to fix this?

---

### Post by Yellow Pasque on 2007-12-22
Log in to a failsafe terminal (change the session by clicking the icon in the lower-left of the login screen)
Run ossinfo and ossdetect -v Are they detecting the card?

---

### Post by pickboy87 on 2007-12-22
[quote=ossinfo]Version info:   (0x00000000)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (nathan-desktop)

Number of audio devices:        0
Number of audio engines:        0
Number of mixer devices:        0


Device objects


Mixer devices

Audio devices[/quote]

[quote=sudo ossdetect]/usr/lib/oss/etc/devices.list: No such file or directory[/quote]


Ah...no devices found, huh? That would explain why I'm not getting sound. I looked at your sig and am going to try that and see if that works. Oh, and thanks for the reply.


Edit: Couldn't get OSS to install...and can't seem to remove it from the Synaptic Package Manager.

---

### Post by Yellow Pasque on 2007-12-23
Follow the instructions here and try the install again.
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

---

### Post by pickboy87 on 2007-12-23
Awesome. That worked. I had to google some of the stuff on the list to work, but I got it working. Here's what I did to anyone else who might have this problem:

[quote=4front Forums]
1) cd /var/lib/dpkg/info
2) sudo rm oss-linux*
3) sudo gedit /var/lib/dpkg/status 

and look for (ctrl-F in gedit) oss-linux and delete the entire section that looks like:

Package: oss-linux
Status: install ok installed
Priority: extra

....

(Converted from a rpm package by alien version 8.64.)

4) Now you should be able to run dpkg --purge oss-linux and it should
say: dpkg - warning: ignoring request to remove oss-linux which isn't installed. [/quote]

**Note**: I modified this quote a little so others should be able to run this in Ubuntu without trouble.

I downloaded the newest OSS package from 4front and saved a copy of it to my desktop. I than logged out, selected the Failsafe Terminal from the lower left corner of the log-in screen and logged back in. I than ran the following and got it to run:

[change the name based on the file you downloaded]

1) sudo dpkg -i oss-linux_v4.0-1011_i386.deb
2) I let it install and than tried this command in the terminal:
3) sudo soundon

It had told me that Open Sound System was already running. Exited from Terminal than relogged back in and Voila! Sound!!!


Thanks for the reply Temüjin I felt soooooooooo freaking lost on why I couldn't get it to uninstall.

---

### Post by trixter76 on 2008-05-03
I just wanted to thank you for posting this information.  I recently made the switch to Ubuntu (from windows) and I really enjoy it.  The fact that there are so many people who have already gone through my issues and are willing to post them is what convinced me to switch.  

I know there will be growing pains, but I really enjoy the community support.

---

