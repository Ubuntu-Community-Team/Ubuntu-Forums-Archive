---
title: "Fix: Unable to Mute or Control Volume in Mythbuntu 8.04"
date: 2008-05-20
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-05-20
If you find that your remote will not control the volume and the mute button does nothing,  invoke the FrontEnd, then Utilities/Setup then Setup, then General.  Continue paging right until you arrive at the Audio page.  For my dated Sound Blaster audio card,  the Mixer Device had to be set to "Alsa:Default" and the Output Device was also set to "Alsa:Default". Then my streamZap remote buttons worked as I expected. 

Hope this helps someone.

---

### Post by jfenton78 on 2008-05-20
This would have helped me a few days ago, but some experimenting with each of the options solved the problem. Thanks for posting the info. I'm sure someone can benefit. 

My volume was low compared to regular TV. Once I changed both settings to default the sound was much louder.

---

### Post by adubas on 2008-05-21
The only thing on my microsoft USB remote that does not work is the volume control. The mute works fine and every other feature except the volume up and down. The volume indicator moves up and down when I press the remote but the sound out of my speakers stays the same. I tried the ALSA:default in both sections but no go. The ALSA default was default when I went in and the mixer settings said /dev/mixer and I tried the switch there and no luck... 

I have a sound blaster card as well... I have to check the model... not a fancy one...

---

### Post by uMuppet on 2008-05-21
I'm having the same problem, it used to work on an older install but has recently stopped.  Any insight into this would be great

---

### Post by LarryJ2 on 2008-05-21
In the Mythbuntu Frontend, Setup, the selection "MixerControls" is set to Master on mine. Pass through is set to Default.  My card is an old sound blaster value.  I had to disable the onboard audio (Intel chip or some such) before I got any Myth audio out of the green SoundBlaster output jack.

---

### Post by adubas on 2008-05-27
> **LarryJ2 said:**
> In the Mythbuntu Frontend, Setup, the selection "MixerControls" is set to Master on mine. Pass through is set to Default.  My card is an old sound blaster value.  I had to disable the onboard audio (Intel chip or some such) before I got any Myth audio out of the green SoundBlaster output jack.


I don't have any onboard audio... I still have not found a fix. The volume indicator moves but does not affect the sound. I tried a lot of settings and found this may be bug related [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382")

Sound does work out of all the oututs, but my only way to change sound level is to walk up and manually turn the physical knob on my computer speaker set...

big bummer so far...

I am using a Sound Blaster Audigy SE card

---

### Post by styrofoam cup on 2008-06-06
Thanks LarryJ2

You pointed me in the right direction. 

In my case I had the sound working but unable to control the volume. The graphic onscreen showed that it was going up or down and mute on or off, but was making no difference to the actual sound level.

In the audio section I left 
output device as ASLA:default
passthrough output device as devault

and had to change mixer device from  /dev/mixer   to
ALSA:default

the sound control is now working.  :guitar:

---

### Post by akendall1966 on 2008-06-09
> **styrofoam cup said:**
> Thanks LarryJ2

You pointed me in the right direction. 

In my case I had the sound working but unable to control the volume. The graphic onscreen showed that it was going up or down and mute on or off, but was making no difference to the actual sound level.

In the audio section I left 
output device as ASLA:default
passthrough output device as devault

and had to change mixer device from  /dev/mixer   to
ALSA:default

the sound control is now working.  :guitar:
Hi
I tried these settings with no luck my output is via hdmi  volume controls & mute react onscreen but actual vol is unchanged. 7.04 it was ok even dist upgrade to 8.04 was ok only since a disk failure forced a fresh install. Any ideas how to get myth to change the digital out vol?

AK

---

### Post by lhommemagique on 2008-06-15
Thanks worked for me.

---

### Post by tonyr1988 on 2008-06-22
Just wanted to say thanks for this pro-active help. I had this same problem (worked before, but not anymore), and this solved it perfectly. You saved me from much frustration.

---

