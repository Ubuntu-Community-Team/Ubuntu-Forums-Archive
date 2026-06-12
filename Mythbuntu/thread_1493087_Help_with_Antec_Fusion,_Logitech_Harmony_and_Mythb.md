---
title: "Help with Antec Fusion, Logitech Harmony and Mythbuntu 10.04"
date: 2010-05-25
forum: Mythbuntu
---

### Post by oct on 2010-05-25
Hello

I have an Antec Fusion Silver case with a fresh install of Mythbuntu 10.04. Also, I have a Logitech Harmony remote wich I'm not able to make it work. I have tried to select different IMON remotes in MCC and irw doesn't display any keypress. If I try to use mode2, I receive a message saying that I have to use the raw mode. If I do so, I see all the keypresses, including the Antec Wheel, but with a 16 digit code.

Anybody with the same setup? Do I have to patch/compile something? I read that the remotes work out of the box.Can you help me troubleshoot the problems?

Thanks

Oct

---

### Post by LowSky on 2010-05-25
The Logitech Harmony needs to be programed to work as a media center remote. And can only be done from a Windows PC form my experience. I set mine as a Windows media center remote and it works great.

IMON is a different story, but should work according to these:
[http://www.mythtv.org/wiki/Imon](http://www.mythtv.org/wiki/Imon)
[http://codeka.com/forums/viewtopic.php?f=3&t=22](http://codeka.com/forums/viewtopic.php?f=3&t=22)

---

### Post by Monsieur Gonzalez on 2010-05-25
Well, I have an Antec case with the VFD display (not the LCD), and a Harmony remote (885), and it all works here. 

If your setup is similar, I can provide the settings files.

---

### Post by oct on 2010-05-26
I have programmed my Logitech Harmony 555 to work as Media Center and as a Antec case. Both give the same codes to mode2 application. I also tried to select Soundgraph Imon PAD at Logitech's software but mode2 didn't capture anything. So I'm using Media Center selection.

Monsieur Gonzalez, does it work out of the box? Didn't you have to change or edit any config file? What remote did you choose at MCC's Infrared secction? It would be great if you provide your config files to see what I'm missing.

Thanks all

Oct

---

### Post by Monsieur Gonzalez on 2010-05-26
Hi! No, it didn't work out ot the box, I had to spend some time reading how-to's, forum posts... It was some time ago, and I don't recall all the details, but what I remember is :

1 - You have to use [Logitech's webpage]("http://members.harmonyremote.com") (Windows only) to get the remote to behave as a MCE usb remote (I think it's called Windows Media Center, but I might be wrong). 

2 - I used irrecord (man irrecord) to create the config file for lircd, but maybe you can use the attached lircd.conf file. 

3 - In /etc/lirc/hardware.conf , point the REMOTE_LIRCD_CONF to the location of the created file (of course you can place it wherever you want)

4 - Create/modifiy your mythtv file (normally in .lirc) to assign the buttons. 

5 - Hopefully it works and you can fine tune. 

Files 

[lircd.conf]("http://pastebin.com/UDh1jkY2")
[hardware.conf]("http://pastebin.com/0SgJjBes")
[mythtv]("http://pastebin.com/xyWpdKLG")

---

### Post by alien878 on 2010-05-26
> **Monsieur Gonzalez said:**
> 3 - In /etc/lirc/hardware.conf , point the REMOTE_LIRCD_CONF to the location of the created file (of course you can place it wherever you want)In 9.10, REMOTE_LIRCD_CONF is ignored (this caused me half a day of headaches).  You need to put the changes into /etc/lirc/lircd.conf (or change the include in this file to point to your file).  I'm not sure if it is fixed in 10.04 or not.

"irw" is a nice command line tool to see if lircd is translating ir signals correctly.

---

### Post by oct on 2010-05-26
Thanks for your files, Monsieur Gonzalez. I'll give them a try as soon as I can. Anyway, can you explain how to use irrecord? I have tried it a bit, but I don't understand hoe it works. It would be nice to know how to generate custom files in case of a hardware replacement.

Alien878, I think it's not fixed in 10.04. This helps explain a lot of things... :)

By now, irw doesn't show anything. I'll post the results after testing M. Gonzalez files.

Oct

---

### Post by oct on 2010-05-28
Hello

I tried your configuration files and they worked! Now irw shows the codes. I think the problem was the first lines of lircd.conf that didn't match my hardware. Some buttons still don't work, as they are not defined (Volume up/down, mute, etc.) but now I can use irrecord to map all the buttons in my remote. As soon as I have a full working configuration, I'll post my files here, in case somebody needs them.

Thank you

Oct

---

### Post by Monsieur Gonzalez on 2010-06-01
Glad it helped. Remote configuration, in my opinion, needs a GUI.

---

