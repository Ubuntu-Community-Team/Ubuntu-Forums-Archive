---
title: "Mplayer plug-in doesn't work"
date: 2008-05-24
forum: Multimedia Software
---

### Post by AmadeusOK on 2008-05-24
Hey All, 

Does anyone know what can I do? The mplayer plug-in always start connecting but after a few seconds it stops for no reason. Since it doesn't work, I changed the Firefox preferences to use anything but mplayer. My problem is that no matter how many times I do this, some video or audio links start automatically with mplayer. That's so annoying.

Thanks for your help.

---

### Post by Bubba64 on 2008-05-24
> **AmadeusOK said:**
> Hey All, 

Does anyone know what can I do? The mplayer plug-in always start connecting but after a few seconds it stops for no reason. Since it doesn't work, I changed the Firefox preferences to use anything but mplayer. My problem is that no matter how many times I do this, some video or audio links start automatically with mplayer. That's so annoying.

Thanks for your help.

Have you enabled in add remove ubuntu restricted  extras or any of the gstreamer stuff, are you talking about movie player I can't find a plugin function on mplayer.

---

### Post by gandaran on 2008-05-24
mplayer and vlc are two very good players for playing video files but not for online streaming, for online streaming it's best you keep the totem plugin installed, (remove any other media player mozilla plugin) if you find the totem gstreamer is not up to your needs, just un-install totem gstreamer and install totem xine, the totem xine engine plays real video or any other format and in fact is just the best plugin for online streaming.

---

### Post by AmadeusOK on 2008-05-24
Thanks for your reply. How can I remove the other media players? I've been changing the media players to Totem using Edit --> Firefox Preferences but the changes don't take place. The online streams for some websites open only with Mplayer plug-in for Mozilla, which is not working.

---

### Post by gandaran on 2008-05-24
> **AmadeusOK said:**
> Thanks for your reply. How can I remove the other media players? I've been changing the media players to Totem using Edit --> Firefox Preferences but the changes don't take place. The online streams for some websites open only with Mplayer plug-in for Mozilla, which is not working.
 
use synaptic to install and uninstall what ever you want, if you want to un-install mplayer completely, just find mplayer and check mark for complete removal, then click the apply button, if you want to keep mplayer, but just remove the plugin then find mozilla-mplayer and check mark for complete removal.

one question, did you install the w32codecs package from the medibuntu repository?
mplayer only works if the codecs are installed!

---

### Post by ubuntu-freak on 2008-05-24
Personally, I think Gecko Media Player is the best plugin for streaming audio/video, by far. It's made by the same guy who made mplayerplug-in, but doesn't need configuring at all. Copy and paste this command into the terminal:
 
**sudo apt-get remove mozilla-mplayer totem-mozilla mozilla-plugin-vlc xine-plugin && sudo apt-get install gecko-mediaplayer**
 
Then restart Firefox. Take a look at my [how-to](http://ubuntuforums.org/showthread.php?t=766683) if you still have problems.
 
Nathan

---

### Post by AmadeusOK on 2008-05-25
@ gandaran:
Oh okay, thank you. I just removed the mplayer plug-in. I wasn't aware that I needed to install the w32codecs package. If I don't use mplayer, do I still need the package?

@ reassuringlyoffensive:
Thanks for suggestion. I'll give Gecko a try.

BTW, the changes I made finally worked. There are still a few sites for which the online streaming don't stat.

---

### Post by wolfen69 on 2008-05-25
> **gandaran said:**
> mplayer and vlc are two very good players **for playing video files but not for online streaming**, for online streaming it's best you keep the totem plugin installed, (remove any other media player mozilla plugin) if you find the totem gstreamer is not up to your needs, just un-install totem gstreamer and install totem xine, the totem xine engine plays real video or any other format and in fact is just the best plugin for online streaming.

how did you come to this conclusion? ive installed ubuntu on *alot* of computers and i remove totem and totem-mozilla and install mozilla-mplayer and vlc. guess what? ive **never** had a problem with streaming media. please dont spread misinformation.

---

### Post by gandaran on 2008-05-26
> **wolfen69 said:**
> how did you come to this conclusion? ive installed ubuntu on *alot* of computers and i remove totem and totem-mozilla and install mozilla-mplayer and vlc. guess what? ive **never** had a problem with streaming media. please dont spread misinformation.

how did you come to this conclusion? I will give you just one example :
nasa tv and bbc webpage, using mplayer plugin on both these sites, mplayer plays real video stream fine , but won't play the wmv stream ( there's some kind problem connecting to the stream, it just stops! but sometimes after insisting a lot it works), yet on other sites it plays wmv very well, if I use the totem plugin there's no problem at all playing the wmv stream on nasa tv and bbc! plus, this same problem I have as been reported here on the forum by many users, so wolfen69, it's not misinformation, it's facts!

---

### Post by ubuntu-freak on 2008-05-26
> **gandaran said:**
> how did you come to this conclusion? I will give you just one example :
nasa tv and bbc webpage, using mplayer plugin on both these sites, mplayer plays real video stream fine , but won't play the wmv stream ( there's some kind problem connecting to the stream, it just stops! but sometimes after insisting a lot it works), yet on other sites it plays wmv very well, if I use the totem plugin there's no problem at all playing the wmv stream on nasa tv and bbc! plus, this same problem I have as been reported here on the forum by many users, so wolfen69, it's not misinformation, it's facts!

 
Trust me, both of you give Gecko Media Player a try, it's basically an evolved and improved version of mplayerplug-in.
 
Nathan

---

### Post by bjdiaz1 on 2008-06-02
Anyone with this problem follow what "reassuringlyoffensive" says... IT WORKS!!!  A million thanks!

---

