---
title: "WG111v2 refuses to work in 9.10"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by SylverFyre on 2010-04-25
I'm a noob here and to linux/ubuntu so I tried using the search options here but can't find a solution.

I replaced a broken WinXP install with Ubuntu 9.10 x32 on my kids PC and the install and OS itself seems to be fine. When connecting the Netgear WG111v2 USB dongle so that they can get internet access things aren't so good. Firstly the startup and shutdown of the machine get big pauses (around 2 minutes at a time)  and there are also big pauses and a general slowdown of the machine while in use that doesn't happen with the dongle disconnected. I wouldn't mind that so much but I can't get the damn thing to connect under ubuntu to our home network. I left an old Win2k partition intact on the machine and I'm glad I did as it means that I've been able to install the drivers to make sure that it all works under Windows, which it does.

It probably makes little difference but the light on the dongle is off for the majority of the time and only lights up briefly on seemingly random occasions. Also, I have no entries for Network Manager in my menus, and the system tray applet doesn't give me the options and tabs that are mentioned in some peoples posts in this forum (ie I can't change the computer name for example), sometimes the system tray applet disappears altogether.

With the dongle attached typing lsusb into the terminal sometimes shows just the USB hubs and sometimes also shows an entry with the WG111 included (and sometimes with big pauses).
nm-tool sometimes shows just the motherboard NIC (disconnected), sometimes the WG111 too (also disconnected) and sometimes it just throws up several error messages with pauses between each one.
dmesg showed an entry for the dongle on the occasion that I tried it.

Any help or suggestions that anyone can offer would be greatly appreciated - I have little hair left to pull out :)

---

### Post by Cowboybebop79 on 2010-04-25
Had a quick rummage on google and found some info two things to try are 

1. don't plug the dongle in till the computer has finished booting bit of a poor excuse for a fix but if it works it works

2. replace ubuntu's default network manager with wicd either by hooking up a temp ethernet or if that isn't possible visit there site [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")(from another computer) and download the appropriate deb file for karmic transfer the file cd - usb stick etc. and double click the deb in ubuntu. The reason for suggesting wicd is that it handles the connection in a different way to ubuntu's standard net manager.

Hope this helps.

---

### Post by SylverFyre on 2010-04-25
appreciate the post - thanks.

I've been playing around without the dongle plugged in and the PC responds as I would expect it to, as soon as I plug it in the whole thing slows down or stops responding altogether. Windows don't respond, I can log into a virtual console but on typing something like "sudo lshw -C network" nothing happens then I get a message saying that net:<PID> has not responded for 120 seconds (or something like that).
As soon as I disconnect the dongle the PC starts working normally again.

I tried to copy the system message log onto a USB stick, but I can't even get that to work, either the system doesnt recognise the stick or there's something flakey going on with the USB driver or something. I can't see where to paste the report file anyway - sorry if I'm being a huge noob :) I'll try grabbing wicd and see how I get on, though if I spend any more time mucking about with this today I'm likely to lose Mrs Sylver as well as my wireless connection ;)

Thanks for your help, I'll post with how I get on tomorrow :P

---

### Post by SylverFyre on 2010-04-25
mm just thought in case it might help the PC specs are:

AMD AthlonXP 2000+
1Gb DDR RAM
Gigabyte GA7VRXP motherboard
nVidia GeForce 4 Ti4600
SoundBlaster Live! Value
Maxtor 64Gb HDD
 - 10Gb Windows 2000 partition (NTFS)
 - 48Gb Ubuntu 9.10 partition (ext4)
 - remaining is swap space

USB is the motherboard onboard controller

---

### Post by Cowboybebop79 on 2010-04-26
Seems like a fairly standard system nothing stands out as an OMG situation with the system alltho just thought of a possible thing to check is if the dongle is USB 2.0 and if you have any 2.0 ports on the pc. I don't think it should make that much difference but it could be the solution and I would kick my self if I didn't mention it now. Having read through a few forums it seems like there are 2 different WG111v2 dongle's with slightly different chip sets one works fine the other takes a bit of work. Another thing to think about is 10.04 is coming out in about 3 days time and it may solve the problem but in the mean time if wicd works then you will know what to do if you later upgrade to 10.04 and you find you have the same problem.

---

### Post by SylverFyre on 2010-04-26
Thanks again :)

I'm considering scrapping this install and trying a fresh one again just in case I did something noobish.

The USB ports on the back panel are USB 1.1, but considering the fact that the dongle works via windows, but not in ubuntu, I'm going to assume that hardware wise backward compatibility shouldn't be a problem.

One slightly related question if that's Ok :) On plugging in a USB memory stick (2Gb), what should happen in linux? Should I see a desktop icon, or some form of menu entry for it? Is it only accessible via one of the "folders" in the filesystem?

I know that linux systems are different to windows in this regard, but being able to copy files to and from ubuntu would obviously be handy/vital to try to sort this issue out :D

---

### Post by Cowboybebop79 on 2010-04-26
When I plug in a USB mem stick/card/hard disk it is automatically mounted

(and amazingly there is absolutely no double entendre in that last sentence :) )

and it then shows up as an Icon on the desktop and should be listed in your places menu it might have a goboldeygook title but if you open the file manager (Called Nautilus) by clicking on either the home folder or computer Icon in the places menu then in the left hand column of your file manager if you have any usb drives or cd/dvds inserted :) they will have a grey eject style Icon next to them just click on the main icon not the eject icon to browse the contents.

I am still a noob as far as Linux is concerned but I'm a vintage noob

ps. if you have any more noob type questions send me a private message ( yet again no double entendre)

---

