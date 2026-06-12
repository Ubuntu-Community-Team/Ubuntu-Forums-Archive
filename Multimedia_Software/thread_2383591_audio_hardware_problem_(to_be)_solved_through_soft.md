---
title: "audio hardware problem (to be) solved through software"
date: 2018-01-27
forum: Multimedia Software
---

### Post by david-brenner3 on 2018-01-27
Hi.

I just installed Ubuntu 16.04 LTS 64 bit.
A few years back I used Slackware and Fedora on another hardware configuration. So I'm not a newbie or a pro in Linux, just something in between...

Motherboard: FUJITSU SIEMENS D2151-A2
Audio card (in motherboard): Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)

In any OS on the output connector I can hear only the right speaker.
In Windows I solved by plugging the connector into the Line In and selecting "Speaker out" in the popup window. So I "forced" the Line In to be Speaker out.
But I don't know how to do that in Ubuntu too...
In sound configuration I can use Line in only as input, not as output.

Can anyone help me, please?
Thank you.

---

### Post by Yellow Pasque on 2018-01-28
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

---

### Post by david-brenner3 on 2018-01-28
Thank you.

I wanna try it to see if works but now I  have another problem: the OS won't start anymore. 
I delete it and installed Kubuntu, same problem.

What I did each time: installed updates, restarted, installed video driver, restarted, couple of small tweaks in system settings, restarted a few times to check if it's ok, shutdown, an hour later on again >> maintenance mode.

This is the log file:
[ATTACH]278353[/ATTACH]

I know this is not the appropriate area to ask help for such a problem so in which area should I start a new thread for it...?


Later edit: found and solved the OS start problem...
Tested your solution for my audio card problem >> works fine :)

Thank you very much.

---

