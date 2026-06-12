---
title: "How can I redirect sound to bluetooth headset"
date: 2009-01-16
forum: Multimedia Software
---

### Post by dmendizabal on 2009-01-16
I've been trying to use my bluetooth headset to hear music and to connect to skype without any luck.

I reviewed some helps, but doesnt seems to work. I have the following so far:

Ubuntu intrepid
I can pair my laptop with my headset and I tested the bluetooth with other devises and it works perfectely.
I have pulse audio working good and I have also installed some additional tools to manage it: padevchooser
I would like to use my bluetooth headset through Pulse Audio to make it transparent for my applications.

Thanks for your help

Daniel

---

### Post by John Jason Jordan on 2009-01-18
> **dmendizabal said:**
> I've been trying to use my bluetooth headset to hear music and to connect to skype without any luck.

I reviewed some helps, but doesnt seems to work. I have the following so far:

Ubuntu intrepid
I can pair my laptop with my headset and I tested the bluetooth with other devises and it works perfectely.
I have pulse audio working good and I have also installed some additional tools to manage it: padevchooser
I would like to use my bluetooth headset through Pulse Audio to make it transparent for my applications.

I hate to do a "me too" post, but I have the same situation. I have a Sony DR-BT50 headset that worked fine in Hardy but I can't get them working in Intrepid. They are paired up fine and when I turn them on the little power plug icon appears in the bluetooth preferences window. But nothing I have been able to do can get the sound to come out of them. The sound comes out of the speakers instead.

The biggest how-to is here:

[http://forums.overclockers.com.au/showthread.php?t=694010]("http://forums.overclockers.com.au/showthread.php?t=694010")

However, it is written for Hardy and I suspect some things may have changed. At this point I got to the pactl commands in instruction 18. The pactl commands time out, which I understand means that pulseaudio is not running. If I try to start it from the command line I get:

jjj@Devil7:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.

I am stuck. Google turns up a lot of posts on "failed to find original dlopen loader," but so far none of them have given me instructions for what is wrong and how to fix it.

---

