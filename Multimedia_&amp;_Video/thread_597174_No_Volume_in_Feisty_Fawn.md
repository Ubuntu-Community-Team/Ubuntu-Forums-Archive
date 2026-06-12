---
title: "No Volume in Feisty Fawn"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by Scottty on 2007-10-30
Hello

I have just installed Feisty Fawn again after a not so fun experience with 7.10. I don't know what is going on but I had a much easier time with Ubuntu when it was in version 6. None the less I still like Ubuntu and would like to eventually use it as my main OS

Right now I have no volume and when I double click on the volume icon in the upper right hand corner I get the following message
> 
No volume control GStreamer plugins and/or devices found.


I have gone into Add/Remove programs and searched for gstreamer and found that all the files have been installed.

It might be because I'm Running Ubuntu on Virtualbox so maybe that is the issue. 

Any Ideas where the problem lies.

Regards
Scott

---

### Post by dysonsphere23 on 2007-10-30
I have the same problem running Ubuntu Studio 7.04.

Everything was working fine (for over a week since install) then I shut down my laptop after work restarted at home and now volume control won't work, still after start again this morning. The sound card is functional, I am getting sound, but when I try to open the volume control from the pannel I get that same message:

"No volume control GStreamer plugins and/or devices found."

and

"The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I tried reinstalling all the gstreamer stuff from Symantec and nothing.

I can start and stop alsa in the comand line.

I find it odd that this just happend between a shut down and restart, what gives?

Exaile player won't start since this problem. Whn I try opening in terminal it gives some output about not finding playbin. Tried uninstall and reinstall, no help.

Sound and video files work fine in VLC player.

DVD won't play in Totem, get the message:"Totem could not startup.  Failed to create a GStreamer play object. Please check your GStreamer installation."

If I try to open the disc using VLC it just doesn't play.

Thanks in advance for any advice/insight.

---

### Post by buntunub on 2007-10-30
> **Scottty said:**
> 

It might be because I'm Running Ubuntu on Virtualbox so maybe that is the issue. 

Any Ideas where the problem lies.

Regards
Scott

You have to ensure that you change the volume of the Virtual Machine from "null" to "ALSA". Do this before you start the virtual machine.

---

### Post by Scottty on 2007-10-30
Thank you buntunub

I checked my sound settings in VirtualBox and sure enough audio was turned off.

I turned it on, and started up Ubuntu and it works. 

So again thanks

Scott

---

