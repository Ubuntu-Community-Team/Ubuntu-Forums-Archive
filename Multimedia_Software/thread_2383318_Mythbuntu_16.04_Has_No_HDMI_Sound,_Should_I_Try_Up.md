---
title: "Mythbuntu 16.04 Has No HDMI Sound, Should I Try Upgrading to 17.10?"
date: 2018-01-23
forum: Multimedia Software
---

### Post by jamoody on 2018-01-23
I have a brand new hardware build (Z270 chipset, Intel 7th gen processor, and GTX 1050 GPU) on which I installed Mythbuntu 16.04.  Fixes are up to date as of Saturday:
        Ubuntu    16.04.3
        nVidia     384.111
        kernel     4.13.0-26
VLC plays video but no sound on GPU HDMI (onboard HDMI doesn't work at all, but not really worried about that at this time since nVidia card is what I want to use).  After a few mins the video hangs and Xorg goes to 100%.

Should I try upgrading to Ubuntu 16.10/17.04/17.10 while I wait for LTS 18.04 or has all the needed fixes been ported back to the levels I have?

---

### Post by Autodave on 2018-01-24
Have you gone into the volume control -> sound settings and made sure that it is turned on there?

I have also run into a few GPUs that need the TV/monitor turned on before booting the PC.

---

### Post by jamoody on 2018-01-25
Thanks for the suggestion, but unfortunately I have no Sound Setting option anywhere that I could find on the desktop pull down menus.  

However, I did stumble across a solution.  During VLC playback (without sound) I noticed in top a task called PulseAudio which intrigued me.  Internet search revealed that app pavucontrol could be used to select the output device and control the volume.  So on a prayer I installed it
     sudo apt-get install pavucontrol
and started it in a command shell.  On the resulting panel I opened the Configure tab and found my HDA NVidia profile was set to something shown as "unplugged".  I found an option that indicated HDMI without the unplugged description and selected that.  On the Output Devices tab I made sure that this new device was selected and that did the trick.  I now get sound out of VLC.

---

### Post by Autodave on 2018-01-26
Glad you got it going. And I apologize: I assumed that Mythbuntu installed pavucontrol by default! Ubuntu and Xubuntu both have it installed and I believe that Ubuntu Studio does as well. Not sure why Mythbuntu doesn't.  Sorry 'bout that!

---

