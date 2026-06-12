---
title: "kernel update broke sound"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by shizow on 2007-06-27
i am using kubuntu

the last kernel update from 2.6.20-16.28 to 2.6.20-16.29 broke my sound

if i boot my laptop with the also installed 2.6.20-15 kernel sound still works

what can i do?

---

### Post by reckless2k2 on 2007-06-27
stay with the older kernel. hahahahaha.

---

### Post by shizow on 2007-07-09
can anyone help

---

### Post by GFC2 on 2007-07-09
Could the update have reset your Alsamixer? Are your device lists under aplay-l and lspci-v in order?  What's the status of your sound module?  Further guidance linked:  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by reckless2k2 on 2007-07-09
i know there was a "patch" released as well last week i believe to the kernel that corrected a lot of the kernel upgrade issues. are you still have the problems with the machines completely patched? try the alsamixer suggestion as stated in previous post as well as making sure you did not change your sound drivers.

---

### Post by shizow on 2007-07-09
machine is completely patched

my alsamixer cannot be the problem,
because i still have sound when booting the old kernel
or?

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

sudo lspci -v
...
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: IBM Unknown device 0567
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]
        Memory at a8000800 (32-bit, non-prefetchable) [size=512]
        Memory at a8000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
...

```

---

### Post by reckless2k2 on 2007-07-10
well if you ran alsamixer again and bumped up everything and you are still not getting a sound output, i would think many other people would be posting something similar. a short term fix which might not be ideal for you is to continue running on the older kernel. there's probably nothing you are taking advantage of on the newer kernel anyway. out of curiosity, is the sound issue specific to a program or everything in general? i noticed in previous updates that there were issues going to a newer application version in some programs that caused issues. i know using amarok a few times i had to make sure the settings were set to alsa because it would switch to another sound driver on an upgrade. also, browser updates have caused similar issues as well. 

are there specific benefits you need from the newer kernel? i know there were a lot of issues across the board with several different things with the latest kernel. i just defaulted back to the previous kernel and kept using that. it may be that there's an issue with intel and alsa in the new kernel. not sure. sorry i couldn't be of more help. you could always compile ala from the source. that might correct the problem.

---

### Post by reckless2k2 on 2007-07-10
seems odd but i did see a few others had similar issues. try these guides:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=alsa+new+kernel](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsa+new+kernel)

and or

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

try this 2nd link 1st. might help.

---

