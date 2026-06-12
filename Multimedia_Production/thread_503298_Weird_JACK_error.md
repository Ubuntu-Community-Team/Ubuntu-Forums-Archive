---
title: "Weird JACK error"
date: 2007-07-17
forum: Multimedia Production
---

### Post by Mblackwell on 2007-07-17
Unfortunately after months of trying to get JACK working so I can try my hand at audio production in Linux (and being in Windows XP because I had no luck), I made sure JACK was completely removed from my system and tried it fresh. Now my problem is worse than ever.


No matter how I start JACK (via jackd or qjackctl) I always get the same error:

```
jackd: symbol lookup error: jackd: undefined symbol: _jack_get_microseconds
```

My only guess is a broken or missing dependency? No idea what it might be though. I'm out of ideas at this point.

---

### Post by fredj on 2007-07-17
This is a strange error. You don't say what version of Ubuntu you are running. Usually I just install Jack and
Qjackctl through the synaptic package manager. I have installed it on at least 6 machines all running
Ubuntu Feisty and have no problems with it. So two questions 1. What version of Ubuntu are you running
and how did you install Jack.

---

### Post by Mblackwell on 2007-07-19
Fiesty Fawn. 7.04, with the latest low-latency kernel. I installed JACK via the ubuntustudio-audio meta.

---

### Post by fredj on 2007-07-19
Well now that you have removed jack, install it again and qjactctl from the System ->Aministration ->
Synaptic Package Manager. Do a search for jack and mark jackd and qjackctl for installation. Any other 
packages you need will be picked up automatically. Then run jack through qjackctl from the application 
menu.

---

### Post by Mblackwell on 2007-07-20
How is that different from removing JACK, setting up the ubuntustudio repo, and then pulling down the audio meta which includes JACK and is giving me that error....

---

### Post by fredj on 2007-07-21
I don't know, but since I have installed Jack using synaptic on six very different machines without problems
I think you should at least try it. If it doesn't work you won't be any worse off than you are now.
This is how I set up my machines.
1. I install Ubuntu and get it working including networking, multimedia (see Sticky at top of multimedia forum)
and lame.
2. I install the realtime kernel using the instructions in the Sticky at the top of this forum.
3. I install Ubuntu studio OR
3. I install the audio programs I want individually since studio includes more programs than I want.

---

### Post by kayosiii on 2007-07-22
Sounds like you have more than one version of libjack installed... IE the old one is still there and being linked too.

The call is something that was added or removed from jack a little while back.

try removing libjack from the package manager...
if that fails remove it manually

Open a terminal and navigate to /usr/lib

cd /usr/lib

delete all versions of libjack

rm -r libjack*

reinstall libjack... Let me know if you are doing this from source or from packages
if applications aren't starting properly or cant be seen to be linked to
you will probably have to create a symlink...

good luck

---

### Post by Mblackwell on 2007-07-22
It was able to be removed from the package manager (or it said it was removed), and I attempted to reinstall through packages but have the same error.

Tomorrow if I have time I might try getting rid of the package and checking to see if it still exists somewhere in another version and then installing again, unless you have other advice.

---

### Post by SmallIsland on 2008-02-23
Hello Mblackwell

I had the same problem on openSUSE 10.3...

I solved it by removing version 1.09 of jack & libjack0 and then installing version 1.03 of jackd and libjack.

Can't say whether it is a bug or whether  jack (Version 1.09) and jackdmp need to be manually configured to work correctly.

---

