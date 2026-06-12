---
title: "Upgrade to 10.10 = No sound in mythtv"
date: 2010-10-13
forum: Multimedia Software
---

### Post by grondinmf on 2010-10-13
Hello all,
I will warn that i am no super linux guru. i know my way around but not every nook and crany.

that said on to my problem. 

I have a Hauppauge hvr 950-q that I had been using with 10.04(64-bit) since it came out with no issues at all(non that i could not fix anyways) had mythtv set up using mythubuntu and all was great. I upgraded to 10.10(64-bit) last night and cannot get sound to work during live tv. If i watch an old recording the sound works. Sound also works everywhere else on my system. Before the upgrade the audio setting in the backend configuration of the tv card was set to /dev/dsp2 this no longer works. if i put it at that(i have to enter it manually) then i have no sound and if i try to change Channel the tv feed crashes.

I have tried /dev/dsp2,1 i even tried /dev/snd/contolC1 wich i got from browsing around in /dev and found this to point to my 950-q all with same results.

If i use alsa:default as the audio device in the backend i still get no sound but i am at least able to change channel.

everything works in TVTime.

i am simply at a loss. My next step was going to be a clean install of 10.10 but i thought i would check here before taking such a drastic step.

---

### Post by thecapsaicinkid on 2010-10-13
I believe /dev/dsp* is using the OSS setup, change mythback to route sound to Alsa instead

---

### Post by grondinmf on 2010-10-13
i am a little confused is that not accomplished by entering alsa:default as the audio device in the backend config for the tv card?

---

### Post by grondinmf on 2010-10-13
so i went ahead and did a clean install still no sound...any ideas?

ok so i see that tvtime is finding this Found "HVR-950Q : USB Audio (hw:1,0)" as audio input...how can i get mythtv to use this input?

---

### Post by swells5 on 2010-10-15
similar problem, mythtv was working well prior to upgrade, my sound was fine on my tv card input, firewire worked intermittently also with sound. After upgrade to 10.10...no sound with mythtv using tv card input. Now firewire works all the time with sound. This is the same on all of my frontends. When I record, mythtv uses my tvcard input and records with no sound. I have sound with vlc, movie player, rythmbox etc. Alsamixer show all on, no mute, Sound preferences, tried many combinations, speaker test works but no sound in mythtv. 
Any help would be appreciated
Thanks
Steve Wells, long time user and fiddler

---

### Post by eljeffe on 2010-10-15
> **thecapsaicinkid said:**
> I believe /dev/dsp* is using the OSS setup, change mythback to route sound to Alsa instead

This issue also affects me, I have my audio routed to line in, a requirement of the tv-card I use; /dev/dsp was the only way to avoid an audio lag. 

Changing to ALSA still does not provide sound for me.

---

### Post by markackerman8@gmail.com on 2010-10-16
arghhh mythtv and pulseaudio and my hvr-950q don't work together

tried /dev/dsp1
works in tvtime and everything else?

I know it is a PA mythtv incompatibility, there must be a fix and a billion other people with this problem ...
... HELP!

Mark

---

### Post by lidex on 2010-10-16
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1407448](http://ubuntuforums.org/showthread.php?t=1407448)

---

### Post by Kanji_Man on 2011-01-26
Sorry to dust off an old thread but I keep coming here when googling about this problem and others probably are too.  I also have a mythtv based htpc setup and lost sound from the tuner when I upgraded to 10.10.

I did a bit of research and this is what I found out.

- According to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300"), OSS support in the ubuntu kernel has been killed and we have lost our /dev/dsp1 type devices.  We were using these devices in mythv-backend to capture the audio for our tuners.

- Fortunately, newer versions of MythTV allow us to define ALSA: paths for the sound and not just /dev/ devices. Look all the way at the bottom of [here]("http://www.mythtv.org/wiki/PCI_TV_audio").

- In Myth-Backend, for my video capture card, I changed the audio from */dev/dsp1* to *ALSA:plughw:1,0* and magically I had sound on my tuner again.  From what I can gather, the "1,0" part comes from the output of the command "cat /proc/asound/cards" mentioned earlier in the documentation.

Hope this helps, I know I was banging my head against a wall for a few months with this.

---

### Post by huggs on 2011-08-10
The method in the previous post doen't seem to be able to apply to me. My output from the command : cat /proc/asound/cards was:

 0 [CA0106         ]: CA0106 - CA0106
                      Live! 7.1 24bit [SB0413] at 0xdca0 irq 16
 1 [U0x20400x7240  ]: USB-Audio - USB Device 0x2040:0x7240
                      USB Device 0x2040:0x7240 at usb-0000:00:1d.7-3, high speed

and nothing matching any of these 2 devices was listed in the linked page.

I have tried ALSA:default, ALSA:front, ALSAplughw:1,0, /dev/dsp0, and /dev/dsp1, but none have given me sound in MythTV.

I am pretty new to Myth, I just struggled the last couple hours to even get video from US Cable TV to play, and now at least an hour and a half trying to get audio.
I am using a WinTV Hauppauge 850 USB tuner, and both sound and video work in Windows, so the tuner is functional. In Synaptic I see Pulse and ALSA items installed, so I am guessing that from what I have read around the web that Pulse isn't totally compatible with MythTV?

I am using Ubuntu 10.10 Wubi installed on a stock Dell Dimension 4700 (ughhh) with the Myth Backend and Frontend installed.

  :)....................TIA for any help at all....................:)

---

### Post by Adam_GUI on 2011-08-10
> **Kanji_Man said:**
> Sorry to dust off an old thread but I keep coming here when googling about this problem and others probably are too.  I also have a mythtv based htpc setup and lost sound from the tuner when I upgraded to 10.10.

I did a bit of research and this is what I found out.

- According to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300"), OSS support in the ubuntu kernel has been killed and we have lost our /dev/dsp1 type devices.  We were using these devices in mythv-backend to capture the audio for our tuners.

- Fortunately, newer versions of MythTV allow us to define ALSA: paths for the sound and not just /dev/ devices. Look all the way at the bottom of [here]("http://www.mythtv.org/wiki/PCI_TV_audio").

- In Myth-Backend, for my video capture card, I changed the audio from */dev/dsp1* to *ALSA:plughw:1,0* and magically I had sound on my tuner again.  From what I can gather, the "1,0" part comes from the output of the command "cat /proc/asound/cards" mentioned earlier in the documentation.

Hope this helps, I know I was banging my head against a wall for a few months with this.

Bumping an older thread, I know.
Last night, I upgraded from 10.04 to 11.04.
I've set MythTV to use ALSA:plughw:1,0 to no avail.

However, I did keep my old tvtime config.
"tvtime | arecord -D hw:1,0 -r 4800 -c 2 -f S16_LE -M | aplay -"
This runs tvtime and pipes audio out.  
If I remove the tvtime and pipe and run "arecord -D hw:1,0 -r 4800 -c 2 -f S16_LE -M | aplay -" while MythTV is open, I get audio again.

If there's a way to point MythTV's backend at arecord and save some time at program start up, I'm all ears.

---

### Post by markackerman8@gmail.com on 2011-08-10
I am respondonding to the previous post, and understand I am not a Linux guru but like to help where I can. 

I noticed that in your "cat /proc/asound/cards" your usb device is not named as the hvr850 ... Perhaps the driver is not installed or not properly,

my "cat /proc/asound/cards", shows ...

0 ...
1 ...
2 [HVR950Q        ]: USB-Audio - HVR-950Q
                      Hauppauge HVR-950Q at usb-0000:00:1d.0-1.4.6, high speed

---

