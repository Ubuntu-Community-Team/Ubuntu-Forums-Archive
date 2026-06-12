---
title: "Sound Issues"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by x__dark on 2006-02-07
I'm having trouble getting my sound to work in Enemy Territory. I know this problem is probably out-dated or over-asked, but I can't find any helpful information. So far, from what little I have gathered, I'm using ESD (i think?). I've read I should try the ALSA or OSS drivers, but how would I do so?

Weird thing is, when I goto System--> Preferences --> Sound it lists two sound cards and I only have the onboard sound.

the sound cards listed are:

NVidia CK8S
MPU-401 UART (maybe the little speaker in the front of my computer? lol)

Any help would be very much appriciated.:-D

Edit: This is the error message I recieve in terminal when running ET

> ------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------

---

### Post by wncben on 2006-02-08
Hiya, I am a noobie to ubuntu/linux, so I am not sure how much help I will be but here goes:

   Do you have any sound?  

I am experiencing similar problems with my sound card, I have an nvidia ck8 myself, and I have an intermittant recurring problem where, except for the drum beats on the log in screen I don't have any sound at all. What i have found is that there is an iec device in alsamixer that is not disabled, and this seems to cause some sort of conflict with the sound card.  Try going to alsamixer (in terminal), and making sure nothing is muted, except the iec devices, which should be muted (unless you have some sort of fiber optic high end sound devices).  My problem is intermittant, sometimes I can fix it, sometimes not, sometimes when I fix it, it reverts back to the silent treatment.  

  Also, the default start up mode for ubuntu is mute, so you might want to check to make sure that your volume control is not muted.  

  Have you gone to the multimedia system selector  and tested your alsa, oss, and esd?  give that a try system/preferences/multimedia system selector...

Also, have you installed the nvidia drivers?  they need to be installed serepately.  A good place to get them, and lots of other great ubuntu flava is through automatix, which will automatically install the nvidia drivers and lots of other goodies for your ubuntuing pleasure.  

Hope this helps, and if there is anyone else out there with any nuggets of wisdom, I hope they share!

~Ol' Ben

---

### Post by x__dark on 2006-02-08
Yeah, I have sound, it works great, although it only works in one application at a time.

---

### Post by f4ll3n on 2006-02-08
Hi there!

I'm having the same problem in enemy territory, If I'm running Teamspeak I can hear and talk no problems at all, the thing is that when I start enemy territory I have no sound at all of the game while Teamspeak is running, If I close Teamspeak I have sound in the game, any ways to get this fixed? Thank's

---

### Post by wncben on 2006-02-13
Hey, I found a pretty good howto:
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)
Hope this helps:) 

~Ol'Ben

---

### Post by wncben on 2006-02-13
I found that if I go back to sound preferences, and re enable 'enable sound server' that I get my system sounds back.

~Ol' Ben

---

### Post by f4ll3n on 2006-02-13
[QUOTE=wncben]Hey, I found a pretty good howto:
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)
Hope this helps:) 

~Ol'Ben[/QUOTE]


I did try the one that Gandalf wrote, like he said and I quote:

[QUOTE=Gandalf]This is just a clean and better organised guide of varunus's[/QUOTE]
This is the How To: [http://ubuntuforums.org/showthread.php?t=32063]("http://ubuntuforums.org/showthread.php?t=32063")

It solve my problems of playing mp3 with xmms and playing Enemy Territory at the same time, but it didn't work for my problem with Teamspeak and Enemy Territory, still looking for a solution. 

Peace

---

### Post by wncben on 2006-02-13
Thanks, the gandalph howto showed me how to switch to 48htz, which is what my system uses.  It seems like there are so many different possible configurations that what works for one person might not work for another.  As for me, a combination of a couple of different howtos has made all the difference.

Here is my asound.conf:
```

# Set default sound card 
# Useful so that all settings can be changed to a different card here.
 pcm.snd_card {
      type hw 
      card 0 
}

# Allow mixing of multiple output streams to this device
pcm.dmixer { 
      type dmix 
      ipc_key 1024 
      slave.pcm "snd_card" 
      slave { 
           # This stuff provides some fixes for latency issues.
           # buffer_size should be set for your audio chipset. 
           period_time 0 
           period_size 2048 
           buffer_size 32768
           # rate 48000 
	} 

	bindings {
            0 0 
            1 1 
	} 
} 

# Allow reading from the default device. 
# Also known as record or capture. 
pcm.dsnooper { 
	type dsnoop 
	ipc_key 2048 
	slave.pcm "snd_card"

	bindings {
            0 0
            1 1 
	} 
} 

# This is what we want as our default device 
# a fully duplex (read/write) audio device. 
pcm.duplex { 
	type asym 
	playback.pcm "dmixer" 
	capture.pcm "dsnooper" 
} 

################### 
# CONVERSION PLUG # 
################### 
# Setting the default pcm device allows the conversion 
# rate to be selected on the fly. 
# duplex mode allows any alsa enabled app to read/write 
# to the dmix plug (Fixes a problem with wine). 

pcm.!default { 
	type asym 
	playback.pcm "dmixer"
	capture.pcm "dsnooper" 
} 

######## 
# AOSS # 
######## 
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)

pcm.dsp0 { 
	type plug 
	slave.pcm "dmixer" 
} 

# OSS control for dsp0 (needed?...this might not be useful) 
ctl.dsp0 { 
	type plug 
	slave.pcm "snd_card" 
} 

# OSS control for dsp0 (default old OSS is mixer0) 
ctl.mixer0 { 
	type plug 
	slave.pcm "snd_card" 
}

```

~Ol' Ben

---

