---
title: "Can't get resolution 1366 x 768"
date: 2012-12-29
forum: Multimedia Software
---

### Post by JoeSabido on 2012-12-29
I've found a few other threads about this but don't seem to apply to my case because I'm using LTSP (10.04)

I'm using this as a thin client:
[http://www.foxconnchannel.com/ProductDetail.aspx?T=NanoPC&U=en-us0000004](http://www.foxconnchannel.com/ProductDetail.aspx?T=NanoPC&U=en-us0000004)

And I'm using this as a monitor:
[http://www.viewsonic.com/us/monitors/17-19/va1912a-led.html](http://www.viewsonic.com/us/monitors/17-19/va1912a-led.html)

At the moment I'm stuck with those two components and I need to make them work.

Currently the thin client will boot properly and it all works just fine, but the screen looks distorted (current resolution is 1280x1024) and I've tried everything I've found online to try to change the resolution to 1366x768 (the monitor native resolution) without success.

I'm willing to try anything.

Thanks.

---

### Post by SR_ELPIRATA on 2012-12-30
Something that might help you is finding the video chipset and making a search with it. I once installed Lubuntu in 2 Acer Aspire netbooks and in one of them (were different models) I was able to get the widescreen native res to work but in the other never could. After doing a search with the video chipset I found (for that model) that it was simply impossible at that moment to get it to work past what I had.

ELP

---

### Post by JoeSabido on 2012-12-30
I downloaded the Windows VGA Drivers and started peeking in the INF files that come with it.

I found one file that says:

KMDName    = "Intel Technologies"
DiskSource = "Intel Technologies Display Driver disk"
Intel      = "Intel Corporation"
iPNWD0      = "Intel(R) Graphics Media Accelerator 3600 Series"

Which means this is an Intel GMA 3600/3650, with almost no support in Ubuntu (as far as I know)?

Sigh...

---

### Post by cwsnyder on 2012-12-30
I take it the method outlined in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) doesn't work for you?

What is the output of **xrandr** on a line by itself in a terminal?

---

### Post by JoeSabido on 2012-12-30
> **cwsnyder said:**
> I take it the method outlined in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) doesn't work for you?

What is the output of **xrandr** on a line by itself in a terminal?

Thank you for your reply.

I certainly remember one of the things I've tried involving adding a new resolution using xrandr.

I'll go through it again when I get to the office and let you know.

I also read somewhere that the kernels above 3.4 have (at least basic) support for that chipset/GPU, so I will also try the following:

1 - Clean install
2 - apt-get update && apt-get upgrade
3 - Reboot
4 - Update kernel to latest 

And see what happens.

---

