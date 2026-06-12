---
title: "Audio over network using pulseaudio"
date: 2010-06-22
forum: Multimedia Software
---

### Post by ebp on 2010-06-22
Hi

I would like to be able to send the system audio from my laptop to my server which have a pair of speakers connected to it. The laptop is running Ubuntu 10.04 and the server is running Debian Squeeze and can only be accessed from the commandline. I'm pretty sure this can be done but i can't figure out how to do it. 

I have tried to look at this [_guide_]("http://www.unixmen.com/linux-tutorials/582-stream-music-wirelessely-using-pulseaudio-server-device-chooser") but it only describes how to do it using a gui, which i don't have on my server.

I really hope you can help :)

---

### Post by kangarooks on 2010-08-26
you can forward X11 over ssh

ssh -X [email]user@server.lan[/email] 

it will allow gui applications launched via command line to pop up  on your laptop.

i think theres some need for setting up /etc/pulse

tho let me know if you find another way since I'm looking at making similar setup myself :)

---

