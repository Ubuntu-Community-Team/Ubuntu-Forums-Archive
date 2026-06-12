---
title: "Found sound card, wont use it."
date: 2006-03-04
forum: Multimedia &amp; Video
---

### Post by Michiba on 2006-03-04
Hi all.

I am new to Linux and Ubuntu. So please bear with my ignorance. I recently installed Ubuntu on a P3 466 256ram 13g hdd. I was expecting problems but was very suprised when everything installed like a dream. A much cleaner trouble free install than I would have gotten from windows. 

My only problem is that the sound card an Avance ALS300 is listed as a device in the device manager with full details, so I assume it is supported. If I try to run a player or adjust the volume it says no soundcard pressent? Within the GUI system I went to System\preferences\sound and there is no sound card listed. 

If some one can tell me what I'm missing I will be very gratefull

Many thanks
Michiba

---

### Post by MJoshi on 2006-03-04
Michiba,

What error message do you receive if you insert an audio C.D after it auto-loads?

---

### Post by Michiba on 2006-03-05
Hi Mjoshi,

I get a "Error playing CD- Reason could not open resource for writing"

If I try to adjust the volume I get the following:-

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I've tried ESD at the command prompt and get the following:-

ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default


So I guess it's a driver issue? 

Thanks for your reply.

Michiba.

---

### Post by MJoshi on 2006-03-05
O.K, i'm having a similar problem at the moment and cannot play any audio at all.

This should solve the GStreamer Volume Control problem you are having though:

Open a terminal window:

type > sudo gst-register *and then press the <tab> key*

You should have something like gst-register-0.8

Press enter/return.  You will be prompted for your password - press enter again after typing your password and then it should say something like 'Rebuilding registry'.

Your Volume Control function should work after this has finished!

---

### Post by Michiba on 2006-03-06
Thanks again MJoshi,

Typing "sudo gst-register" came straight up with enter password. Once the password was entered it came up with an "Command not found" Re-typing the command now comes  straight up with the "Comand not found" with out asking for the password. 

Back to the drawing board. 

If I sort out the issue I'll post here to let you know how, and if you think of anything else let me know. I quite like the feel of Ubuntu and I,m not ready to give up yet.

Thanks again for posting

Regards 

Michiba

---

### Post by MJoshi on 2006-03-06
I had a similar problem initially - The reason why you get that error message is because gst-register does not exist on its own.

You need to type sudo *gst-register* and then press the tab key maybe a couple of times.

That auto-completes the rest of the command which should be something like gst-register-0.8

You will then be prompted for your password and follow the steps as before.

---

### Post by Michiba on 2006-03-07
Hey MJoshi,

I feel like I'm milking you for info, it is appreciated though. Yep we're working on the "sudo-register" front. All went as you said it would. I still have to get my sound card recognised though. 

I will keep trying and thanks again for your help. Sound and Video hardware seem to be re-occuring areas within the listed threads. So I know I'm not an island.

Regards
Michiba

---

### Post by ashwillis on 2006-05-04
It is indeed a driver issue. The issue being that there IS NO DRIVER...well this used to be true, anyway. I recently wrote an ALSA driver for the ALS300/ALS300+ soundcards.

I don't know how up to date ubuntu is, but this new driver is now carried in alsa-driver-1.0.11 and it will be included in kernel-2.6.17.
Until this code makes it into the ubuntu distribution, these cards will not working under ALSA.

The driver is new and has been tested on a VERY limited range of hardware so bug reports are welcome...and a simple message to say "hey, it works" would be even more welcome :p

---

