---
title: "mic jack on Inspiron 1300 not working? Plz Help."
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by vevak on 2006-06-22
I have recently installed Ubuntu 6.06 on Dell Inspiron 1300, everything works fine except two things; one is the mic jack where their is no response on inserting mic (contoller for sound is sigmatel Stac9200), headphones and laptop speakers work fine. If anybody has a solution please respond in a easy way as I am complete newbie to Linux.
Other problem is Intel pro wireless 2200 bg which is detected by the system and is not getting connected. I have installed ndiswrapper package through automatix. I don't know if I have done right. Still the same problem. Please help regarding this issue in simple terms because I am new to Linux.

After executing lspci through terminal window I had following:
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

---

### Post by user1397 on 2006-06-22
well as for your mic problem, try this:  open alsa mixer by double-clicking on your volume icon, and go to edit > preferences.  Make sure the following **are** ticked: Master, PCM, Line-In, CD, Microphone, Mic Boost, PC Speaker, Capture.  the mic has to do with the Microphone, Mic Boost, and Capture preferences.  just mess around with those three things (dont mute them) and see if your mic works.  you can test your mic using sound recorder (applications > sound & video > sound recorder)

---

### Post by vevak on 2006-06-22
[QUOTE=erik1397]well as for your mic problem, try this:  open alsa mixer by double-clicking on your volume icon, and go to edit > preferences.  Make sure the following **are** ticked: Master, PCM, Line-In, CD, Microphone, Mic Boost, PC Speaker, Capture.  the mic has to do with the Microphone, Mic Boost, and Capture preferences.  just mess around with those three things (dont mute them) and see if your mic works.  you can test your mic using sound recorder (applications > sound & video > sound recorder)[/QUOTE]
Thanks for the help, I tried what you wrote but it is not helping out as I have tried to search other forums for this problem where they have same problem and have given patch for alsa but thats for Gentoo and being newbie I have less idea how to use that for Ubuntu 6.06. I have the link for that website, so if anyone can help somehow I do appreciate it.
[http://www.disgruntledgoat.com/content/useful/gentoo_on_inspiron630m.php]("http://www.disgruntledgoat.com/content/useful/gentoo_on_inspiron630m.php")

---

### Post by trukker on 2006-08-08
Same problem here vevak

---

### Post by capriccio on 2006-08-09
Try this:

1. backup your existing /etc/modprobe.d/alsa-base
2. append the following to the end of the file:

options snd-hda-intel model=ref

Reboot, tweak your levels in alsamixer to your liking, record, playback.

Let me know if this works for you.  I have the Inspiron 1300 as well.

More info here: [http://ubuntuforums.org/showthread.php?p=1357412#post1357412]("http://ubuntuforums.org/showthread.php?p=1357412#post1357412")

---

### Post by el.tomo on 2006-09-29
Dell Inspiron 1300

IT WORKS!!! :) :D :p 

Cheers tomi

Thank you very much!!!

---

### Post by michelefrost on 2006-11-17
ciao

I have Edgy running on my inspiron 1300.

No problems with the mic, but I have the headphone jack muted and no way to unmute it (so that I can't hear anything on the headphones).
I have read something here about patching alsa:

[http://ubuntuforums.org/showthread.php?t=234418](http://ubuntuforums.org/showthread.php?t=234418)

but maybe you solved it otherwise or have different configurations that make it simply work.

@ vevak:

regarding the wireless connection, I have mine working fully under the ipw2200 driver, thru the couple Gnome-Network-manager / nm-applet:

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

the only issue is that I have no wireless led under linux, even while connected.

---

### Post by michelefrost on 2007-12-18
Just to let everybody know that "magically" the issue is solved after passing to Gutsy...
Now mic & headphones work perfectly, even using skype (with pidgin opened as well) etc.

Good news!

---

