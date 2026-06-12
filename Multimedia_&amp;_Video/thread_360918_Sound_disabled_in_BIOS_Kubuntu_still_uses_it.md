---
title: "Sound disabled in BIOS Kubuntu still uses it"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by nfinitone on 2007-02-13
I hope someone can help. I've just switched to Kubuntu 6.10 after using SuSE for 4 years now, and I am really loving it so far. SuSE has really tried my patience with it's 10.2 release. Anyhow....

My problem is with my VIA AC97 integrated sound card. I have a SoundBlaster Live! 5.1 PCI installed, and it suddenly started to work after a few reboot cycles. But some applications are sending sound to the integrated sound card. System sounds are currently playing through the SB card, but everything else is not.

When everything was installed, I had the VIA card enabled in the BIOS, and disabled it afterwards. Apps are still playing audio through the integrated card although it's disabled in BIOS. I have Windows XP running in VMware Workstation 5.5.3 and device manager shows the sound device as Creative PCI, but it too is sending the sound to the disabled VIA card.

lspci *does* show the VIA card active. I've read other posts, but nothing specific to a device being disabled and still being used. What can I change in Kubuntu to remove the integrated card and only use the SB Live 5.1? Also, any ideas as to how the OS can still use a device even when it's disabled in BIOS? I didn't think that was possible.

Lastly, at random times, I could reboot and the system feeds ALL sounds to the VIA card. Reboot again, and system sounds may be playing through the SB.

Thanks!

---

### Post by nfinitone on 2007-02-15
Also, I've reinstalled all drivers and followed various Sound How-To's in this forum. Nothing seems to fix it. Whenever I edit any config files, to remove the VIA card, it shuts down the SB as well. Any help at all would be greatly appreciated. Thanks.

---

### Post by adibudeen on 2007-04-06
I had a similar problem with a different soundcard.  Doing the following fixed it for me.

Edit:  /etc/modprobe.d/blacklist

Add:

#disable onboard sound which interferes with soundcard
blacklist snd_via82xx

(or whatever the name of your sound onboard sound module is).

My soundcard has worked fine ever since.

---

