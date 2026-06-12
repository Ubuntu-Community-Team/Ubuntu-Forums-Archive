---
title: "my sound card doesn't work in ubuntu 9.10,would any one help me?"
date: 2009-11-10
forum: Multimedia Software
---

### Post by csunature on 2009-11-10
i lately update my ubuntu 9.04 to 9.10 and found that the nvidia sound card failed to work,then i removed alsa and installed oss following as a trial. 
then i reinstalled alsa,but it seems useless.
but it is still silent, then i checked the information of the card which was shown as follows:
> 00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
yet i don't know how to solve  my problem,could any one help me?
thanks a lot!

---

### Post by nishant.singh28 on 2009-11-10
try pulseaudio

---

### Post by csunature on 2009-11-10
i've try it,but it doesn't work either..


```
nature@nature-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': &#26080;&#27861;&#25171;&#24320;&#38899;&#39057;&#35774;&#22791;&#25773;&#25918;&#12290; [gstalsasink.c(690): gst_alsasink_open (): /GstPipeline:pipeline0/GstAlsaSink:alsasink3:
Playback open error on device 'default': &#27809;&#26377;&#35813;&#25991;&#20214;&#25110;&#30446;&#24405;]


```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135677&stc=1&d=1257913043[/IMG]

---

### Post by frank_acies on 2009-11-10
I have the same nvidia chipset and mine seems to work fine, have you checked the Bios and made sure you have onboard audio set to external? are you trying to get sound out of hdmi or regular plug? 

sorry I can't be of much help, but good luck

---

### Post by csunature on 2009-11-11
> **frank_acies said:**
> I have the same nvidia chipset and mine seems to work fine, have you checked the Bios and made sure you have onboard audio set to external? are you trying to get sound out of hdmi or regular plug? 

sorry I can't be of much help, but good luck

thanks,man. i've set external to my bois,and the bios version is the latest one.but it still seems fail to work.i feel frustrated..
 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135726&stc=1&d=1257948802[/IMG]
in terminal i was told the sound card is configured.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135727&stc=1&d=1257948802[/IMG]
but when i typed 'alsamixer' i can only to get the reply of 'no such a file or directory'

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135728&stc=1&d=1257948802[/IMG]
and in the option of sound,the field of hardware is as blank as in white snow...

---

