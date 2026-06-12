---
title: "no sound"
date: 2010-08-20
forum: Multimedia Software
---

### Post by bbb125 on 2010-08-20
hi all,

I'm having an issue where I can't hear any sounds in Ubuntu 10.04 (64-bit). In the Sounds Preferences, under Hardware it correctly lists "SB X-Fi Xtreme Audio". The sound is not muted, and I've tried cycling through various Profile options in the hardware tab. Since it is correctly detected, I'm thinking that there might be something simple that I'm missing here. The motherboard is an MSI P6N Diamond: [http://www.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=&cat3_no=&prod_no=1168](http://www.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=&cat3_no=&prod_no=1168)

Anyone have any ideas?

**$ sudo aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

The following is shown using the** lspci -v** command:

09:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
    Subsystem: Creative Labs Device 0010
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [dc] Power Management version 3
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by bbb125 on 2010-08-20
I found my sound card on the ALSA list (it is not a separate physical sound card. sound is onboard):

X-Fi Xtreme Audio (PCI)      CA0106    
 [[PCI]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-PCI") snd-ca0106; [ ] supported  [ ] not supported 

I followed the manual on this forum and tried:

**sudo modprobe snd-ca0106**

There was no output indicating anything happened. I am still not hearing any sounds and I am out of ideas. Could anyone help?

Note: If it matters, I am using headphones, but I have tried selecting Analog Headphones in the Output tab. No luck.

---

### Post by silbak04 on 2010-08-20
try this in a terminal ```
$ sudo aptitude install alsamixer
```

---

### Post by bbb125 on 2010-08-20
I installed this software. When I run it, it shows the headphone volume at 100/100. I have tried turning the volume up on all the options but no go.

---

### Post by bbb125 on 2010-08-21
bump since i'm stuck in windows until i can get my music working in ubuntu.

---

### Post by silbak04 on 2010-08-21
try running this in the terminal```
$ sudo /sbin/modprobe snd-ca0106
``` tell me if that works

---

### Post by bbb125 on 2010-08-22
No luck. Still no sound. :(

---

### Post by bbb125 on 2010-08-23
I have also tried manually compiling the ALSA drivers as per the instructions found here:

[http://lne.byexamples.com/?p=39](http://lne.byexamples.com/?p=39)

But I am still without sound. Could any experts out there please advise? Not having sound is sort of a showstopper for a music person like me. :frown:

---

### Post by bbb125 on 2010-08-24
I have also tried editing:

/etc/modprobe.d/alsa-base.conf

adding the line:

options snd-ca0106 model=auto enable_msi=1

No luck. I do not have speakers to test sound; I am only using headphones. Sound should be supported by ALSA:

X-Fi Xtreme Audio (PCI)      CA0106    
 [[PCI]]("http://www.alsa-project.org/main/index.php/Matrix:Tag-PCI") snd-ca0106; [ ] supported  [ ] not supported 

Please help.

---

### Post by Castle_Romeo on 2010-08-24
I am having the exact same issue. NO SOUND, Grrr. 
I installed Ubuntu 3 times and still no sound!
My system is using the onboard Realtek motherboard sound chip, BTW.
 
I thought Ubuntu was supposed to be easy.  Please send me a PM with WORKING FIX.
 
Thank You.

---

### Post by bbb125 on 2010-08-25
Yeah, I understand your frustration. I've been posting for a week trying to get some help but nobody seems to know how to fix this. If you find a fix, please send it to me. Otherwise, I might try Fedora.

---

### Post by ivanlo2 on 2010-08-27
I am having the very same issue, also with the onboard realtek alc888. Before the hardware was detected with no sound but I fiddled with compiling ALSA drivers and now I don't even get that.

-Ivan

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by ivanlo2 on 2010-08-28
Here you go: [http://www.alsa-project.org/db/?f=5e2962d98fce9dce310fbb9166467b1091f11903](http://www.alsa-project.org/db/?f=5e2962d98fce9dce310fbb9166467b1091f11903)

I should mention that my board is the 770TA-UD3, an AM3 board and I also have an ATI HD 5770 graphics card with HDMI, and my sound settings detect the onboard audio on that card as well.

---

### Post by lidex on 2010-08-29
> **ivanlo2 said:**
> Here you go: [http://www.alsa-project.org/db/?f=5e2962d98fce9dce310fbb9166467b1091f11903](http://www.alsa-project.org/db/?f=5e2962d98fce9dce310fbb9166467b1091f11903)

I should mention that my board is the 770TA-UD3, an AM3 board and I also have an ATI HD 5770 graphics card with HDMI, and my sound settings detect the onboard audio on that card as well.

If you have alsa-backports installed, please remove. Now use the alsa-upgrade link in my sig to get v 1.0.23

---

