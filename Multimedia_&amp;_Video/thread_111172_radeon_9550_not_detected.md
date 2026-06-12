---
title: "radeon 9550 not detected"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by porsher_puddles on 2006-01-01
i'm a newbie to linux, i have 2 machines running ubuntu machine 1) has a nvidia graphics card i installed the driver through synaptic and its all good, i have 3d acceleration. machine 2) has a radeon 9550 256 mb card it's not being detected properly, i have the fglrx driver installed, and in devices it has unknown device, when i reditect it it is calling it a 9600 which it isn't, acceleration is very poor.
now i have read through the posts till my head is about to explode, i see i'm not the only one with this trouble, but i can't seem to get a definite answer i understand. basically i need to be told in simple steps what to do, i have been trying to sort this out for ages and seem to be getting knowhere, everything else is working fine, and i have managed to read through the posts and sus it out but this is driving me crazy!

---

### Post by Fibre on 2006-01-02
I don't know whether this will solve your problem but I had a problem where I couldn't even see my card and realised that I had to install fglrx but just couldn't do it correctly.

In particular - [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] and select "fglrx" instead of "ati".

It gives you a choice of allowing it to automatically choose the driver I think from what I remember - you say no to that and then choose the fglrx instead of ati.

Then it came up with " generic graphics card" or something similar. After which I just typed in ATI Radeon 9550, following the rest of the screens I just hit enter all the way, not making any other choices. I didn't pick anything just got through it, then rebooted.

It picked it up fine -  One suggestion though if this doesn't work, I'd uninstall what you've done and then try it again from the beginning of the instructions 'cause I know that it worked a treat from scratch for me.

If you do start from scratch and you can't use [COLOR="Red"]fglrxinfo[/COLOR] in your terminal to see what's happened, just install from synaptic package manager ( fglrx-command ) place fglrx in search and it should come up as first choice in the list.

I hope it works out for you I spent way to long on trying to get it to work also.

Oh here's the site I was given ----  [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

The suggestion I put at the top of page is in step 3 of the - 

Hoary Hedgehog (Ubuntu 5.04) and Ubuntu 5.10 (Breezy Badger)

of the HOW TO. It worked for me and nothing else did. 

I think if I would have just chose to pick the type of driver myself instead of letting it automatically do it I would have probably gotten through it a lot quicker.

---

### Post by porsher_puddles on 2006-01-03
well i'm not sure if it worked correctly or not, i seem to have acceleration, and when i type fglrxinfo at terminal i seem to get the correct output, i can't post exactly what it says cause i'm on another machine,but it basically says card is detected.
on the other hand when i go to devices and have a look in there it still says unknown ati device
so whats the go?.

---

