---
title: "find sound card name"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by giginho on 2008-04-11
Hello!

Is it possible to find some information regarding the hardware name of an audio device associated with /dev/dsp file?

:confused:

Thanks,
Giginho

---

### Post by Claus7 on 2008-04-11
Hello,

I would propose you to go to synaptic and type lshw-gtk. Install the homonymous package and then open a terminal and type:

```
sudo lshw-gtk
```
give your password and you can easily see information about the hardware that is installed in your system. 

What you are looking for probably it will be under Computer->Motherboard->Host Bridge->Multimedia audio (do double left click to move from one to the other).

Hope this helped,
Regards!

---

### Post by giginho on 2008-04-11
Actually i need to find this information programatically.

I'm writing some code and I need to obtain this information given the /dev/dsp file.

How can i find out to which sound device /dev/dsp refers to?

---

### Post by Claus7 on 2008-04-11
Hello,

does this help you to find out what you are looking for, for dsp devices?
[http://linux.dsplabs.com.au/lsof-grep-snd-how-to-free-a-linux-sound-device-p25](http://linux.dsplabs.com.au/lsof-grep-snd-how-to-free-a-linux-sound-device-p25) 
I have an onboard sound card so I cannot find out exactly if this gives the output you want.

Regards!

---

### Post by giginho on 2008-04-11
Thanks, I think this is what i was looking for.

The command "cat /proc/asound/cards" returns information about my soudcards.

I think that in normal situations it is safe to assume the device #0 from /proc/asound/cards corresponds to  /dev/dsp, #1 to /dev/dsp1 and so on.

A more accurately solution is to check the minor code of /dev/dsp and if is 3 then it should be the first sound card from /proc/asoun/cards, 19 the second etc.

---

### Post by aeiah on 2008-04-11
this may be useful, but it depends what you really need to accomplish with regards to finding out what is at /dev/dsp

```
asoundconf is-active
```

---

