---
title: "Getting back stock ALSA"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by Obfuscator on 2007-10-01
Hi!

I followed the instructions at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and installed alsa from source to make my sound card work. Every time there is a kernel upgrade, I now need to recompile ALSA, since the module won't fit anymore :(. I would therefore like to uninstall my custom ALSA, and get stock ALSA from ubuntu repositories.

I tried to do 'make uninstall' on all alsa stuff (alsa-driver, alsa-lib, alsa-utils), and reinstall alsa-base and alsa-utils through synaptic. That didn't work unfortunately. I still don't get the kernel module that I need :(

How can I revert to stock ALSA? Any help is appreciated.

---

### Post by jmc1024 on 2007-10-02
I am in the same situation you are.  I installed alsa from source and each kernel update breaks sound.  In addition to 'make uninstall', I used synaptic to reinstall alsa and the kernel package to get the correct modules.  Everything appears to be in order, but there is no sound output.  I see in /var/log/messages:
Oct  1 21:09:32 pineislandsound kernel: [   37.500000] hda_intel: azx_get_response timeout, switching to polling mode...
Dropping back to kernel 2.6.20-15 sound work fine.
Mark

---

### Post by Obfuscator on 2007-10-02
> **jmc1024 said:**
> I am in the same situation you are.  I installed alsa from source and each kernel update breaks sound.  In addition to 'make uninstall', I used synaptic to reinstall alsa and the kernel package to get the correct modules.  Everything appears to be in order, but there is no sound output.  I see in /var/log/messages:
Oct  1 21:09:32 pineislandsound kernel: [   37.500000] hda_intel: azx_get_response timeout, switching to polling mode...
Dropping back to kernel 2.6.20-15 sound work fine.
Mark

Hi Mark,

Thanks for replying. It's great to hear that someone else is in the same situation :)
I thought that I might need to reinstall the kernel, but I was unsure, and since I'm quite new to Linux i didn't know if that was safe. I figured that the kernel upgrade must have skipped the alsa drivers since it aready found a custom one laying around. Is that how it works? So then I basically just need to uninstall my custom alsa, and after that reinstall the kernel? Could you please tell me how you reinstalled the kernel? I don't really know how to do that properly, and I could only find limited info on google.

Thanks

---

### Post by jmc1024 on 2007-10-02
From within synaptic, find the linux-image-2.6.20-16-generic package.  Mark it for reinstall and then apply.  Well this is what I did, but as I said, I still don't have sound working.
HTH,
Mark

---

