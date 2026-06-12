---
title: "Speakers not working in 14.04"
date: 2015-01-10
forum: Multimedia Software
---

### Post by wanderingarticfox on 2015-01-10
I have Logiteck THX Model Z623 speakers and they are correctly wired to my Gigabyte GA-990XA-UD3 MB.
I have accessed the ALSA Mixer  V1.0.27.2 which shows the card as  HDA ATI SB and chipset as Realtek ALC889 and my Advanced Linux Sound Driver  version is K3.13.0-43-generic
I have run in terminal sudo update, upgrade and dist-upgrade so I am up to date
My sound is not a card but intergrated with the MB

When I unplug and replug the speaker connection from the MB plug I can hear the subwoofer hum then silence.

In Sound settings I am set to "Digital Output (S/PDIF)  Built-in Audio" 
TEST SOUND button in sound settings gives no results.

I have Sound Juicer installed and set to install from CD to Banshee.

I have made sure all ALSA MIXER settings are activated but when I install an album from CD to my Music it does not play.

Any suggestion? Thanx in advance.

---

### Post by marseille2 on 2015-01-11
>> In Sound settings I am set to "Digital Output (S/PDIF)  Built-in Audio" 
TEST SOUND button in sound settings gives no results.

Can you change the sound settings to something like "**Analog Duplex**"?

You can always double check to see if your on-board speaker output uses analog with:
$ **aplay -l**

Also ... I just upgraded to 14.04 last month, and noticed that alsmixer turns off the output of my wired speaker set and headphones if I use *bluetooth* audio. Don't know if this is happening to others but just in case, bring up the command-line:

$ **alsamixer**

Hit the **F3** key to see the playback options. Then **disable** **Auto-mute **if it's on.

---

### Post by wanderingarticfox on 2015-01-13
Thx for the reply; I'm loosing my on-line access for 3-4 months so I will close this thread.

---

