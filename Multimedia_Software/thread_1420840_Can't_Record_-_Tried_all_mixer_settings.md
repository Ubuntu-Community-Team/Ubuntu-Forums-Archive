---
title: "Can't Record - Tried all mixer settings"
date: 2010-03-03
forum: Multimedia Software
---

### Post by rmlrml on 2010-03-03
[COLOR="Indigo"]((Thanks so much in advance to anyone who can help me out.  I promise I've been searching these forums for two hours and I can't find an answer to my problem.  I don't want to waste anybody's time if I can find the solution already in here somewhere))[/COLOR]

I cannot record with my microphone.  I used to be able to, now I can't.  I don't know what update may have caused it because there was a long period where I wasn't ever trying to record anything and now I'm trying again, but I know I was able to record as late as summer 2009.

I'm using a Toshiba Satellite laptop.  I was running regular Ubuntu, and when I couldn't get the mic to work, after I tried messing with mixer settings, I downloaded UbuntuStudio to see if it would somehow help (since I wanted to try it anyway), no luck.

People's advice in these forums seems to be centered around finding the right setting in a mixer to toggle, so I've downloaded a few different mixers and toggled every single option in each of them to see if I can get my mic to record, but no luck.

Here are the mixers I have tried, along with what each calls my soundcard:

GNOME Alsa Mixer - [COLOR="SeaGreen"]"Realtek ALC660-VD"[/COLOR]
PulseAudio Volume Control - [COLOR="SeaGreen"]"HDA Intel - ALC660-VD Analog"[/COLOR]
QAMix - [COLOR="SeaGreen"]"HDA-Intel (hw:0)"[/COLOR]
Mixer - gives me the option to choose between these:
[COLOR="SeaGreen"]"HDA Intel (Alsa mixer)"
"Realtek ALC660-VD (OSS Mixer)"
"Playback: HDA Intel - ALC660-VD Analog (PulseAudio Mixer)"
"Capture: Monitor of HDA Intel - ALC660-VD (PulseAudio Mixer)"
"Capture: HDA Intel - ALC660-VD (PulseAudio Mixer)"[/COLOR]

I should also tell you that for some reason there are two different "Sound Preferences" programs available under my System>Preferences> menu.  In one the only device available is "HDA Intel - ALC660-VD Analog", but in the other it lets me choose from these:
[COLOR="SeaGreen"]"Autodetect"
"HDA Intel - ALC660-VD Analog (Alsa)"
"HDA Intel - ALC660-VD Analog (OSS)"
"HDA Intel - ALC660-VD Analog (OSS)" (yes, it appears twice)
"ALSA - Advanced Linux Sound Architecture"
"OSS - Open Sound System"
"PulseAudio Sound Server"
"Test Sound"
"Silence"[/COLOR]

When I check/uncheck the Mic Mute option in GNOME ALSA Mixer it switches between my hearing fuzz and hearing nothing, but my voice won't go through the mic.  Nothing happened to the mic, I didn't drop it in water, I have no pets, live alone, etc...

Thanks to anyone who can help :)

---

### Post by donut123 on 2010-03-03
Hello...i am having the same issue..i will find the page you can try something....

[http://forumubuntusoftware.info/search.php](http://forumubuntusoftware.info/search.php) 
I have Ultimate...and have the same problem...I am looking for a solution also...perhaps ...on here you can find one...
Donut :p

---

### Post by rmlrml on 2010-03-09
I got it working.  I followed the instructions on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568).

But actually I'm not sure if that's what got it working or the fact that I played with the mixer settings using the program alsamixer.  in there i switched from int mic to ext mic, and that might have also had something to do with it.

---

