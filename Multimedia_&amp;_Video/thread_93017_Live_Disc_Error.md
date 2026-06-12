---
title: "Live Disc Error"
date: 2005-11-21
forum: Multimedia &amp; Video
---

### Post by Tim... on 2005-11-21
When I attempt to boot Ubuntu 5.10 from the live disc, I get the following error:
> Failed to start the X server. It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem
I cannot viewer the X server output, because the message is quickly covered up by some command line text. I noticed that before this message appeared, It reads 
> Temporary failure in name resolution    [ fail ]

My computer is as follows:
Intel 3.0ghz 2mb cache
1gb Generic Ram
160gb WD HD (with two partitions)
Saphire 256mb Radeon X800GT

I found a similar case of this here: [http://ubuntuforums.org/archive/index.php/t-80064.html](http://ubuntuforums.org/archive/index.php/t-80064.html)

But this is my first time using linux, and I have no clue how im meant to edit the xorg file.

---

### Post by aysiu on 2005-11-21
Do you have a blinking cursor at what looks like a DOS prompt?
If so, type ```
sudo dpkg-reconfigure xserver-xorg
```

If the cursor is after the word **login**, go ahead and log in and type in your password. Then, type the command above.

---

### Post by Tim... on 2005-11-21
I tried what you said, and followed through with the instructions displayed. btw, the writing before the flashing underscore looked as followed:
> ubuntu@dhcppc2:~$
anyways, at one point in the config, it popped up with this:
> The answer to this question has been preseeded (). If you see this template, you've found a bug in the installer; please file a report.

dummy template for preseeding unavailible questions.

And an input below with the test "false" written in it.

Continuing on, I got past the config for colour depth, and directly after i think it buggered up. It popped up with the following message:
> xserver-xorg postinst warning: overwriting possibly - customised configuration file; backup in /etc/x11/xorg.conf.200511210830
ubuntu@dhcppc2:~$
and then the flashing input thing.

The first time i tried typing in something random to see what it was, and it caused it to go phsycho, the right column of the screen began filling with the letter y, and if i pressed a button, it would put the letters all over the screen, until i typed a word and hit enter, which made the screen go red. The second time i typed a few words (as i said i have no experience with linux) such as boot, and the screen didnt skitz, it just acted as if it was a prompt.

---

### Post by Tim... on 2005-11-24
Does anyone know?

---

