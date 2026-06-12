---
title: "SOLVED: USB 5.1 sound and mixing"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by PCalitrack on 2006-08-10
For those who have been looking for it (maybe newbies like me)... I have found the solution to getting 5.1 sound from an external sound card. Additionally, this allows mp3s and sound files to be played on all speakers as well as allowing multiple sound bites to be played at one (mixing). Specifically I have an SB Live External 24 Bit. This is a usb sound card. However, from reading the site below, this setup has worked on several different external sound cards. Enjoy.

This is just a quote from [http://ubuntuforums.org/archive/index.php/t-31829.html]("http://ubuntuforums.org/archive/index.php/t-31829.html")

SOLUTION:
gedit ~/.asoundrc

Comment out the link to .asoundrc.asoundconf like this:
# </home/patrick/.asoundrc.asoundconf>

Insert the following:
pcm.dmix51 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0666
slave {
pcm "hw:0,0"
channels 6
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
}

ctl.dmix51 {
type hw
card 0
}

pcm.stereo {
type plug
slave.pcm "dmix51"
ttable.0.0 1
ttable.1.1 1
}

pcm.!default {
type route
slave.pcm "dmix51"
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 1
ttable.1.4 1
ttable.0.5 1
ttable.1.5 1
}

pcm.duplicate {
type plug
slave.pcm "dmix51"
slave.channels 6
route_policy duplicate
}

---

### Post by rck_hitokiri on 2006-08-10
would this work if i only want sound mixing ?? i got mine ok its just i cant use two apps at the same time e.g. hydrogen and audacity at the same time on my desktop... errors on the sound driver. :)

---

### Post by PCalitrack on 2006-08-11
I think you wouldn't want this for sound mixing... but I think I may have the solution for just that. I forget where I got this from, but this worked for me before I got this other setup.

As a note, you might want to run the command
> aplay -l
to get your card # and device #.

In the following put your card # where mine says 0 and where it says hw 0,0.. replace the first 0 with your card # and the second 0 with your device #. This gave me 2.1 sound on my external card with sound mixing.
> pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}


---

### Post by PCalitrack on 2006-08-11
Reading this also helped me out a little.

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?company=Generic&card=Generic&chip=Generic&module=Generic]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?company=Generic&card=Generic&chip=Generic&module=Generic")

Gives you an idea of how these .asoundrc files work. Anyways, the dmix is the main part where the mixing code is. You may have to talor it to your settings. Call it as a slave from the pcm device.

---

