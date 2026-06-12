---
title: "Nvidia GT 210 - Sound - Ubuntu 10.10"
date: 2010-10-28
forum: Multimedia Software
---

### Post by dream_coder on 2010-10-28
Hi, I am having trouble getting sound to work now swtiched to new Ubuntu release in Which previously I got working with LTS by 

Ppdating to Latest Stable Alsa 

Modifying Alsa-base.conf and adding "options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2"

This modification does not work with the new Ubuntu and have tried other options from [http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240) still no joy any tips would be appreciate thanks.

Forgot to mention am using latest ubuntu nvidia propriatary driver.

---

### Post by a-user on 2010-10-28
for me worked the following thing (having a gt220 though):
i changed absolutly nothing, meaning i kept the alsa that i got with ubuntu 10.10 (but i update the usual way if available).

the only thing i had to tweak was in /etc/modprobe.d/alsa-do-not-remember-filename.conf
(i forgot how the filename is exactly, but it is the only one with alsa prefix).

insert at the bottom the following line if you have onboard sound or a sound card (but onbord sound disabled in bios):
 enable_msi=0 probe_mask=0xffff, 0xfff2

if you have onboard sound and soundcard but both activated than i think this should work:
 enable_msi=0 probe_mask=0xffff,0xffff,0xfff2
but never tried this.

finally, after rebooting, start in terminal alsaconfig
select your nvidia hdmi. you should have only one control there. unmute it. if you have mutliple controls for the nvidia hdmi, than something went wrong with the above tweak. maybe you have to insert another 0xffff or remove one.

---

### Post by dream_coder on 2010-10-28
Yeah thats what I tried to start with not updating anything apart from usual system update, and manually edited /etc/modprobe.d/alsa-base.conf and added the lines hat I added previously with LTS but with no luck which is kind of strange as havent changed bios settings, think it is going to be a case of fiddleing and tweaking until it works or not work as the case may be, as I have the gt 210 maybe they are slightly different but I will keep trying thanks for the post though!

---

