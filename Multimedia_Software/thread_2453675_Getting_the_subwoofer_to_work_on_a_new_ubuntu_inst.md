---
title: "Getting the subwoofer to work on a new ubuntu installation. Pulseaudio"
date: 2020-11-15
forum: Multimedia Software
---

### Post by georgetasker on 2020-11-15
This is marked as solved as I am simply sharing how I got the subwoofer to work on my sound system.

So I was having trouble getting the sub-woofer to operate on a 5.1 sound system after freshly installing ubuntu.

I use Pulse Audio to drive my sound card and system.

At the beginning of my effort the entire system was function except for the subwoofer.

The answer lies in the configuration settings in the file  /etc/pulse/daemon.conf


I found these options.  It looked suspiciously to me like the subwoofer was actually turned off.
```
;  remixing-produce-lfe = no
;  remixing-consume-lfe = no
;  lfe-crossover-freq = 0

```

Uncommented the three lines and changed the options as shown below.
I set the crossover frequency at 200 but it can be as low as 40 if that is what floats your boat.

```
remixing-produce-lfe = yes
remixing-consume-lfe = yes
lfe-crossover-freq = 200
```

Ran the command 

pulseaudio -k

Presto  Sufwoofer works!

Hopefully others with a >= 5.1 sound card will find this helpful.

---

