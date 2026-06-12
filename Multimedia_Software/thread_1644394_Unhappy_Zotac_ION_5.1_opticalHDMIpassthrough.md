---
title: "Unhappy Zotac ION 5.1 optical/HDMI/passthrough"
date: 2010-12-13
forum: Multimedia Software
---

### Post by wardy277 on 2010-12-13
I hope you can help me as this has been driving me mad.

I have a Samsung HDTV (37" bought last year), Zotac ION HTPC and a new Samsung HT-C450N 5.1 Home Theatre System. My system is Ubuntu 10.10 x64, running xbmc stand-alone alongside gnome (so i can browse the web and download torrents). I have installed a fresh copy of ubuntu incase my previous settings with analogue screwed up and thing.

I have upgraded my old analogue 5.1 to this digital system to make everything integrated with anynet+. Now my original idea was to send 5.1 audio through the HDMI (which i believe to be possible with the Zotac), the same with my xbox, then get my tv to send the 5.1 audio to the amp via optical.

I did this, but the HTPC only let me send stereo, with ubuntu sound preferences only giving me combination of "Digital Stereo (HDMI output)". Upon researching apparently it might not even be possible to send the 5.1 from the tv to the amp via optical anyway, as the tv only bothers to send stereo(what a ridiculous hardware limitation). So i stopped trying to get the HTPC to send 5.1 via HDMI

So my second idea was to send the 5.1 via optical direct to the amp. Now this is where i am having trouble. I cant seem to see any settings for this in ubuntu and when i run XBMC and set the audio settings to send 5.1 through optical it plays my stereo movies but when it gets to a 5.1 mkv it errors saying there is a problem with my audio device.

I dont mind if i have to put the xbox out of the equation and use optical direct to amp. All i want is somehow, getting digital 5.1 from my HTPC to the amp.

Please help, else i may go crazy :cry:

---

### Post by wardy277 on 2010-12-13
anyone have any idea how to get this working?

---

### Post by wardy277 on 2010-12-13
Noone has any idea?

---

### Post by donsimon on 2010-12-27
I am in the same boat you are.  If I find an answer, I'll let you know!

---

### Post by donsimon on 2010-12-27
Working now

This is what I did:

Use synaptics to load “linux-backports-modules-als-2.6.32-25-generic”. 
Once installed and system re-booted, load “alsamixer” in a terminal window, press F6 to change to Nvidia sound, then unmute the channels. It will not display channels unless the backport is loaded.

At that point, I was able to get VLC and other stuff to do 5.1.

I had to continue searching because XBMC is my main reason for this box.  XBMC kept giving me "cannot initialize" error.  I found that if I changed the Ubuntu sound preference to use analog (any type) then XBMC worked perfect.

---

### Post by frankcm3 on 2010-12-27
Check these three links. Previous posts I have made. I have a zotac ion running 10.10 and xbmc. I started with the same problem.  The only thing I forgot to mention in these posts was to also check see that "digital audio" is selected in sound preferences.

[http://ubuntuforums.org/showthread.php?t=1637020]("http://ubuntuforums.org/showthread.php?t=1637020")

[http://ubuntuforums.org/showthread.php?t=1636597]("http://ubuntuforums.org/showthread.php?t=1636597")

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")
..
The last link gives info on how to change the config file (not as hard as it sounds!)
This is the line I used from that xbmc wiki page
..
GT240	 Zotac ZEGT240/DI/1024	enable_msi=0 probe_mask=0xfff2	 plughw:X,3

---

### Post by wardy277 on 2010-12-29
Thanks for your help,

I first looked for the alsa back ports but as i am on Ubuntu 10.10 i only see: linux-backports-modules-alsa-2.6.35-22-generic

my alsa version is 1.0.23 which i think is up to date

I have tried putting the following in /etc/modprobe.d/alsa-base.conf
options snd-hda-intel enable_msi=0 probe_mask=0xfff2
(turns out that i have already put this in but it did nothing so it was commented out)

and using what you recomended: options snd-hda-intel enable_msi=0 probe_mask=0xfff2 plughw:X,3 cause no  no devices to be shown in the sound preferences hardware tab

I dont have a digital audio option in sound preferences, just digital stereo (HTMI or IEC958

Kinda annoying as my tv can only send stereo to the speakers no matter the html audio input, so going direct from ubuntu box to speakers via optical is my only hope (and i have confirmed that my speakers can accept 5.1 via its optical input and my mobo can send 5.1 via optical) Could ubuntu be getting confused and showing stereo as my tv says it can receive only stereo, when it should ignore that and sent to the speakers


Chris

---

