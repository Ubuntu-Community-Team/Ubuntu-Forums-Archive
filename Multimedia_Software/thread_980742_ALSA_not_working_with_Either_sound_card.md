---
title: "ALSA not working with Either sound card???"
date: 2008-11-13
forum: Multimedia Software
---

### Post by m3sSh3aD on 2008-11-13
Hi,

i have a problem with ALSA in Ubuntu Studio. I have a 'HDA INTEL ALC262' in my laptop and also a 'EDIROL UA-25' USB sound card. Both work with OSS but i really need ALSA working as i use many programs that require it to work.

The response i get when i TEST is:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback

I'm new to ubuntu and cant seem to find anything to help me online when i have searched.


Thanks in advance
Ian

---

### Post by GrantsV on 2008-11-13
Me too...  with M-Audio Audiophile 2496 only since 8.10

---

### Post by m3sSh3aD on 2008-11-13
It worked at first for me, Then just stopped and now im stuck with OSS which is useless :(

This is a major problem as im doing a degree in music tech and need get this fixed :(

---

### Post by Kevbert on 2008-11-13
This looks like bug [[COLOR="Red"]#296738[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/296738"). Please add comment as the more comments made the sooner it will be fixed. What kernel are you using ? In terminal, if you enter
```
uname -a
```
you'll get the kernel version you are using. I bet it's 2.6.27-7 which is common to both Intrepid and Jaunty at the moment.

---

### Post by m3sSh3aD on 2008-11-13
Bang on mate,

2.6.27-7

Does this mean there is no solution? How long do these things tend to take iron out?

Thanks

EDIT: Is it safe to use this Kernal?

[http://www.icewalkers.com/Linux/Software/515380/Linux-Kernel-2.6.html](http://www.icewalkers.com/Linux/Software/515380/Linux-Kernel-2.6.html)

RC4 one?

Thanks again

---

### Post by Tleilax on 2008-11-13
I am experiencing the exact same problem here:

kernel - 2.6.27-7

I had this problem with 8.04 but was able to work around it with an asound.conf file which looks like this:

```
# Get device handles from aplay -l

pcm.connectiv {
	type hw
	card 1
	device 0
}

pcm.!default connectiv	
```

(I have an M-audio Connectiv)

This workaround no longer works sadly.

Anyone who has made any progress in this area, I'd like to know how ya did it!

Chris

---

### Post by m3sSh3aD on 2008-11-13
I downloaded kernal 2.6.28-rc4 but i dont know how to install, I read somewhere that RC3 had fixed this issue for someone so im persuming RC4 will too, But i have never installed a kernal, Can someone advise on how to?

Thanks again, WOrth a try isnt it

---

### Post by Kevbert on 2008-11-13
If you want something that still works you could install the long term support Ubuntu 8.0.4 Hardy Heron which will be maintained until 2011. Some features and bug fixes may be backported (backdated and added) to Hardy. Intrepid is due to be superceded by Jaunty Jackalope on 30th April 2009.

---

### Post by m3sSh3aD on 2008-11-14
So using ubuntu studio 8.04 is the answer? and ill be ok using that until the next fully working edition is out in therory?

---

