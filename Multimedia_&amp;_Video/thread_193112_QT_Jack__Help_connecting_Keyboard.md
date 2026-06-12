---
title: "QT Jack:  Help connecting Keyboard?"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by jay_mac on 2006-06-09
Hope someone can help with my setup...

I've setup the Ubuntu Studio, Rosegarden, etc, and have all working except I can not get my midi keyboard to connect.
I can use the Virtual Keyboard with Qsynth and play just fine, but I'm uable to succeed in using my actual keyboard.

When using Jack connect , I attempt to join the MPU-401 UART MIDI to Qsynth,
but it does not connect, the connection line just disappears, without errors?

Any suggestions, maybe my jack settings are wrong? Here's some screenshots...

(Using the midi connector on a Asus p4p800 mother board with its internal sound)

---

### Post by slugkilla on 2006-06-09
I have basically the same problem, just I have a lot of info with it. [http://www.ubuntuforums.org/showthread.php?t=188167](http://www.ubuntuforums.org/showthread.php?t=188167)
The link just goes away and the message screen gives me an exrun.

---

### Post by jay_mac on 2006-06-09
[QUOTE=slugkilla]I have basically the same problem, just I have a lot of info with it. [http://www.ubuntuforums.org/showthread.php?t=188167](http://www.ubuntuforums.org/showthread.php?t=188167)
The link just goes away and the message screen gives me an exrun.[/QUOTE]

Yes, I read your thread, and learned a lot from it and others. As a result I was able to get Rosegarden4 working, except with my external keyboard.

Problems seem similar except I don't get the exrun errors. So I think we are very close to success? Maybe we just need a modprobe or change some config file,  but its a mystery to me...

I read on another linux board about running sndconfig to setup midi, but cant find any Ubuntu help on that, dont know if that's needed or not.

---

### Post by slugkilla on 2006-06-09
In the setup, I changed things a bit so it is not as strict, and now there are no xruns. yey. I hope there is someone who can help, this is like the 4th thread I have linked my problem to....

---

### Post by bwanab on 2006-06-12
I don't know if I can actually be of help. Here are a couple of screen shots of midi connections through qjackctl that work. UM-2 is my Edirol USB midi adaptor.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=11129&stc=1&d=1150162223[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=11128&stc=1&d=1150162342[/IMG]

---

### Post by jay_mac on 2006-06-18
[QUOTE=bwanab]I don't know if I can actually be of help. Here are a couple of screen shots of midi connections through qjackctl that work. UM-2 is my Edirol USB midi adaptor.[/QUOTE]

Hi, Thanks for the post, was using your USB Midi adaptor as simple as plugging it in, or did you have to install / compile drivers etc?

Could you post a link to the adapter you have?

Thanks, I think I'll just buy one if its easy to get it going...

---

### Post by dolson on 2006-06-18
I use a E-MU Xboard49, and it is plug-and-play, and is set up the same way.

---

