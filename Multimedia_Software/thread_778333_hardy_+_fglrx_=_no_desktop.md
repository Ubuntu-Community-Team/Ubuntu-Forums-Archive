---
title: "hardy + fglrx = no desktop"
date: 2008-05-02
forum: Multimedia Software
---

### Post by guildofghostwriters on 2008-05-02
I'm pretty new to all this and currently very tired so please forgive any stupidity.

I have a clean install of Hardy and a radeon 9800 pro agp - I think there are actually two of them, a secondary shows up in the hardware info anyway.

I've tried various methods of installing the proprietary fglrx driver - following the ATI binary driver how to in community docs, following the Hardy how to at wiki,cchtml.com, using envy and just clicking the enable thing in the restricted drivers manager. All produce the same result: when it boots into ubuntu, all I get is a cursor and a white screen and have to ctrl-alt-backspace, go to a failsafe terminal, gedit xorg.conf to use the ati driver and start all over. I don't know if it's relevant but after I've installed the driver and done the depmod thing, it usually fails to execute the gedit command to fiddle with xorg.conf, saying something about a screen.

Is there a solution to this or must I make do with the open source driver? Is there a way to tweak the os driver for better performance? All advice and suggestions gratefully received and attempted upon my return from the land of nod.

Cheers

---

### Post by mstreibe on 2008-05-02
> all I get is a cursor and a white screen

Sounds familiar to me, see my post from yesterday:

[http://ubuntuforums.org/showthread.php?t=777504](http://ubuntuforums.org/showthread.php?t=777504)

In my case it was compiz hanging up. Do you have xserver-xgl installed? You may need to disable or deinstall it. Xgl is crashing on my box, causing trouble for compiz. Maybe it is the same for you too.

---

### Post by guildofghostwriters on 2008-05-02
Thanks. I just checked in synaptic and I don't have xserver-xgl installed. I'll dig around your thread and see if anything there and at combat wombat works.

---

