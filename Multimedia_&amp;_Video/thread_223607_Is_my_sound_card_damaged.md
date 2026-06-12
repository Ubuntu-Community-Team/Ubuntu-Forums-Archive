---
title: "Is my sound card damaged?"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by Aninhumer on 2006-07-26
Whenever sound is played on my computer, he right channel sounds fine, but the left channel is just a high pitched whine. It might be a driver issue, but I'm increasingly worried that the sound card may actually be damaged. I am about to send another unit back which certainly did have faulty parts, and I would like to know if there is an easy way to find out if I have a funtioning but incompatible sound card, or a broken compatible sound card.

It's listed in sound settings as "HDA VIA VT82xx" and the lspci line is:
0000:04:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller

---

### Post by Aninhumer on 2006-07-27
Good news, it's not a hardware issue. I installed windows to test, and (after locating the driver disk) the sound worked fine on both channels.
What's more, I no longer get any whine on the left channel, although I don't get anything else so there is still an issue.

What could be causing it?

---

### Post by Aninhumer on 2006-07-27
Arrg!
While changing the voulme settings, my sound now will not play at all :(

EDIT: It returned after I rebooted for the second time, but still only right channel.

---

### Post by shinta42 on 2006-09-04
i have the same card and same problem as you...have you fixed it yet?

---

### Post by dannyboy79 on 2006-09-05
I am having the same issue but with a different onboard sound card I believe. I have started a thread over here [http://www.ubuntuforums.org/showthread.php?t=250140](http://www.ubuntuforums.org/showthread.php?t=250140), if you'd like to subscribe, maybe with both of us getting hits we can solve it together. What's weird about our situation is that the sound works fine out of both sides in WINXP but when I go over to dapper it only works out of the left side??? What's with that!! I went to realtek's website and they do have a linux download, I am going to try and see what I am suppose to do with it tonight after work and golf. I'll definitely come here and let you know if I figured it out and I hope you do the same, us linux newbies have to stick together just to survive :-)
 Thank you.

---

### Post by zx80user on 2006-09-16
I have exactly the same problem with the same card/motherboard. Does anyone know if there is a fix? Will a more recent ALSA driver download fix this?

---

### Post by Lord Illidan on 2006-09-17
I have the same prob, too..
I'll see Realtek's site.. They have a fix for Fedora Core 5...hope it works..

---

### Post by Lord Illidan on 2006-09-17
Excellent, it worked!!
Try it out...
[http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs)

---

### Post by dannyboy79 on 2006-09-17
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 225
        I/O ports at e000 [size=256]
        I/O ports at e100 [size=128]
        Capabilities: <available only to root>

---

### Post by dannyboy79 on 2006-09-17
I am not sure why you wanted to see the results of what you wanted but I think this is better, aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
Subdevices: 0/1
Subdevice #0: subdevice #0

Hopefully this is what you wanted to see.

---

### Post by Lord Illidan on 2006-09-19
Sorry mate, but you have the wrong type of card...my post was for Intel High Definition Audio Integrated cards...

---

