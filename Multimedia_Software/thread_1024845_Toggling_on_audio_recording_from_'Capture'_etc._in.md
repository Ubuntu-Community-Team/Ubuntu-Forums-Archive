---
title: "Toggling on audio recording from 'Capture' etc. in Volume Control fails"
date: 2008-12-29
forum: Multimedia Software
---

### Post by Pagnol on 2008-12-29
Hello,

I am using Intrepid Ibex on my M1330. The sound works fine but when recording, the result is very quiet. To solve this problem a member of this forum recommended unchecking all the check boxes about audio recording in the recording tab of the Volume Control. Well, I did this several times but they are still crossed. So my toggling does not take effect. I guess there is something wrong with my sound configuration.

By the way: These forums are really great!

---

### Post by Userisk on 2008-12-29
I am also experiencing a similar problem with gnome-volume-control. My microphone didn't/doesn't work, but I know which settings I need to get it going (disable "CAPTURE Feedback" and toggle audio recording from Microphone) BUT recently these changes are not being saved (I close volume control and open it immediately only to see that changes were not made.)

Everything was working fine for a while (which means I had to keep making these changes after reboot if I wanted my microphone) for a week or three. I didn't use it for a while only to discover this problem. Quite possibly I may have installed the following packages in this time (I don't have evidence of the last successful use of my microphone and my memories are quite hazy about the dates)
> libpulse-browse0 (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
libpulse-mainloop-glib0 (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
libpulse0 (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
libpulsecore5 (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
pulseaudio (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
pulseaudio-esound-compat (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
pulseaudio-module-gconf (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
pulseaudio-module-hal (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
pulseaudio-module-x11 (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
pulseaudio-module-zeroconf (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2
pulseaudio-utils (0.9.10-2ubuntu9.1) to 0.9.10-2ubuntu9.2

I have just established that I cannot disable/enable/toggle any of my settings in volume control, cannot change the volume of any recording channels but I can change the volume of all playback channels.

Thanks for any help!

Edit: Otherwise audio works fine (Pulseaudio with CA0106 on ALSA)

---

### Post by Userisk on 2008-12-30
I stumbled upon the gnome-alsamixer and tried it for a comparison of the problem. Surprise, surprise! Everything which I said that wasn't working, got it's own error message (and check-boxes for toggling were missing).

> ** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Analog Source"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Digital Source"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Shared Mic/Line in"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Surround Jack Mode"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Select"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mono Output Select"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Channel Mode"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source Select"!

** (gnome-alsamixer:19722): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source Select"!

I got the following message in a popup:

> An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'

I am not up to fiddling with configurations without assistance - does anyone have an idea?

---

### Post by Userisk on 2009-01-01
Another failed attempt to understand and fix the problem.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
In the part titled "Refreshing/Reinstalling the drivers" I ran the command to purge and reinstall the alsa packages and others. Nothing seemed different.

I can't find any other similar problem descriptions and would really, really appreciate getting this working. Can anyone help?

---

### Post by Pagnol on 2009-01-02
For testing purposes I installed Open Suse 11.1 (Gnome and 64 bit) and faced the identical problem. What sound card or chip do you use?

---

### Post by Userisk on 2009-01-02
> $ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS

> $ cat /proc/asound/modules
 0 snd_via82xx
 1 snd_ca0106
As I mentioned, I am quite successfully able to hear music using the ca0106 module.

---

### Post by Userisk on 2009-01-04
And it doesn't seem to be part of the kernel as I booted with kernal 2.6.27-7.16 instead of 2.6.27-11.22 ... and no change.

I'm scraping the barrel and don't know what to do/check.

---

### Post by Userisk on 2009-01-05
> alsamixer -c 0
that command proved quite helpful (as I have two soudcards, but alsamixer will configure pulseaudio by default, not helpful). I now know that alsamixer _itself_ refuses to (un-)mute the aforementioned channels (m/M does nothing). When I turn the sound down all the way, it shows for example:
>  Item: CAPTURE feedback [dB gain=mute, mute] 
which is both new for me/my computer AND obviously insufficient as a mute-signal. So, for some reason, ALSA has decided my card doesn't need mute signals, even though it did until a few weeks ago. (And I need to mute feedback to get my microphone working properly.)

Yes, all packages are up-to-date. Stuffed if I know what to do.

---

### Post by lenards on 2009-02-18
Was there any progress with this issue?

---

### Post by Findarato on 2009-05-05
I have exactly the same problem. Did anyone manage to solve it?

---

### Post by mdshaver on 2009-05-13
I think my problem is similar. I am using Jaunty and downloaded recordmyDesktop. The video recording worked fine but no audio. Since the audio box is checked within the program itself, I suspect my problem has to do with the Capture option in the volume control not being checked. Whenever I do check it and close it, it does not remember it. Thus, I cannot record audio with this, or presumably, other programs. Any solutions yet?

---

### Post by mdshaver on 2009-05-17
bump

---

### Post by Pagnol on 2009-05-20
With Jaunty I face the exact same problem, no matter wether i am using the 32 or 64 bit version.

---

### Post by mdshaver on 2009-05-22
Does anyone have an opinion if this same problem would continue using KDE (i.e., Kubuntu)?

---

### Post by markbuntu on 2009-05-22
The only thing i could reccomend is either downgrading or upgrading alsa or waiting for the next update with crossed fingers. There have been some updates recently that have fixed some and broken some of the sound drivers.

---

### Post by Pagnol on 2009-07-01
The problem persists.

---

### Post by MetroPietro on 2009-08-26
Same or closely related problem here: while recording with Gnome Sound-recorder or Xvidcap, I cannot mute built-in mic, nor can I record from "Digital" source accessed through Volume Control panel via sound-recorder. 
~$ lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

System:
Ubuntu Release 9.04 (jaunty), Kernel 2.6.28-11-generic, GNOME 2.26.1;
HP Pavilion dv2000 laptop, 2GB RAM, dualcore Intel T5600 CPUs

~$ pulseaudio --version
pulseaudio 0.9.14

---

### Post by MetroPietro on 2009-08-26
Weird fix: I have never seen this suggestion through hours of Googling different fora regarding Ubuntu sound, PulseAudio, etc for months:
Assume you have a default, vanilla config of Pulse for Ubu 9.04. If not, please refer to:
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
Then in PulseAudio Applet, go to Volume Control. Under the Recording tab, you may see only a grayed-out "No application is currently recording audio." 
Start gnome-sound-recorder and begin recording a DVD or web browser playback. 
You will then see the gnome-sound-recorder show up under the Recording tab. On the right are three icons: a Mute Audio, Lock Channels, and a "v"-shaped 'Open menu' button.
From this third, 'Open Menu' button you have the choice of 'Move Stream' or 'Terminate Stream'.
Under Move Stream, I have three choices (you may have others): 
     Monitor source of simultaneous output, Monitor of HDA Intel, or simply HDA Intel. 
gnome-sound-recorder was set to HDA Intel, which is my built-in mic. I changed it to Monitor HDA Intel, and it began recording from the system! Without recording simultaneously from the mic!

Maybe in some dark corner of some PulseAudio manual this fuction is explained, but not by any search string I used in Google over the last six months. Hopefully the text I am posting will enable other regular, mortal users to find this Pulse function.

---

### Post by JOshea on 2009-09-14
I know this thread came out awhile ago but for AMD64 users with jaunty

one very important thing that is not covered here is using 
audacity to record whats coming through the speakers ie 
how to record songs playing on the web or wherever if you are using amd64 
jaunty - including flash files that are encoded ...

I switched everything to pulse audio from preferences on the main menu 
the "sound" selection on the main menu - sound preferences - except the main mixer - leave as is ...then 

use the pulse audio device chooser - go under the volume control 
and fire up audacity ...go under preferences there and choose pulse for audacity under both playback and record 

under the device chooser/ volume control -  go to recording tab - 
and hit record on audacity ...my card does not have a mix setting - but you can move the stream to the simultaneous from both playback and record tabs setting - and then you will see Audacity recording whats playing 

this took me way too long to figure out and you don't have to do any fancy work arounds or scripts to get it to work - I followed the link for jaunty but did not get rid of flash by adding the extra 32bit plugs to replace them but the others don't hurt to have - jack audio is not necessary and you can still save and load the wav files into something like Ardour 

cheers

---

