---
title: "[SOLVED] HDTV Lockup"
date: 2008-07-20
forum: Mythbuntu
---

### Post by Carrot06 on 2008-07-20
I am currently having a problem with watching HDTV in Australia. SDTV works fine, but as soon as I change to a HD channel my whole system freezes and I have to use the reset button. With my hardware listed below, anyone got any ideas on how to get this to work?

Also, any ideas on how to get SPDIF passthrough and the analog line out to work at the same time? currently if the audio source is digital, analog sound will only work when passthrough is turned off.

Mythbuntu 8.04 - fully updated
AMDXP 2600+
768mb RAM
Leadtek DTV2000H Tuner Card
Asus V9999GT 256mb GF6800GT AGP using Composite TV-Out
AOpen Cobra AW-870LP 7.1 Channel PCI Sound Card
160GB IDE HDD for Recordings Only
Micrsoft USB Remote & Keyboard working with lirc_mod_mce

---

### Post by jbman on 2008-07-21
What playback profile are you using. When I was using a similar spec amd chip I had to have CPU-- to get HDTV to work which made it use XVMC.

---

### Post by Carrot06 on 2008-07-21
Originally I had it on CPU++, but have now changed to CPU-- exactly for that reason of using XVMC.

---

### Post by Carrot06 on 2008-07-21
Just for extra info, in case it makes a difference, the 160gb HDD for recodings is formatted as ext3. Also, I know that HDTV can work as I had it working in Mythbuntu 7.10 without changing any background settings.

---

### Post by Lester_Burnham on 2008-07-21
Hi,

Does XvMC work at all? Have you seen the greyscale OSD?

I see it's an AGP card too.
Have you tried adding the bottom two device options to your xorg.conf, to see if it helps.

```
Section "Device"
    Identifier "Videocard0"
    Driver  "nvidia"
    Option "UseEvents" "true"
    Option "XvmcUsesTextures" "false"
    Option "NVAGP" "1"
EndSection

Section "Extensions"
    Option "Composite" "Disabled"
EndSection

```

Taken from here [http://ubuntuforums.org/showthread.php?p=4903557](http://ubuntuforums.org/showthread.php?p=4903557)
We fixed our XvMC problem on the weekend and I am now running CPU+

---

### Post by Carrot06 on 2008-07-22
Got it working, and am now using CPU+ to prevent distortion. Thanks Lester_Burnham.

---

