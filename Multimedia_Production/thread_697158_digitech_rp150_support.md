---
title: "digitech rp150 support?"
date: 2008-02-14
forum: Multimedia Production
---

### Post by indiekid97 on 2008-02-14
First of all, thanks in advance for any responses. Recently, I have become interested in using my Digitech RP150 through the USB cable to record onto my box. This works fine under winblows (xp) when using Audacity. However, I cannot seem to be able to find a way to duplicate this functionality in Ubuntu. The purpose for recording the audio was to do further editing in Ardour.

P.S. i read on a previous thread to run 
```
lsusb
```
and then copy the results into the forum
(this tread dies however so i never got my answer :[)
anyway, if its helpful here is what it replied 

```

Bus 004 Device 003: ID 059b:0272 Iomega Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 047d:106e Kensington 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1210:000e  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by studiesinsound on 2008-02-15
Hello indiekid97

Forst off, I'm a complete noob to Linux so take this all with a grain of salt.

I was also interested in the other thread and noticed it died.  I have not had the time to plug in my rp350 and do the lsusb command.  I'll try it this weekend.

Based on your output I'm guessing the IOMEGA is an external HDD or media device.

I'm guessing the Kensington is a USB hub of some sort?

If that's true than it looks like the rp150 is not showing up.
You don't have the rp150 plugged in via the usb hub do you?
If it is try plugging directly into a usb port on your computer.

Anyways like I said just guessing but I think what the other guy was getting at i nthe other thread was to see if the rp150 would show up on a usb port.  Looks like it's not. 

Not sure what to do next.

---

### Post by Stochastic on 2008-02-15
hmm, this thread [http://www.daniweb.com/forums/thread107470.html](http://www.daniweb.com/forums/thread107470.html) seems to claim that ALSA will recognize the pedal provided it's up to date.

I know that ALSA needs to have a USBAudio driver for most usb soundcards.  This is housed (I think) in the alsa-firmware-loaders package, so do ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install alsa-firmware-loaders
```

does that do it?

---

### Post by indiekid97 on 2008-02-16
First, sorry for not giving details earlier:
the IOMEGA is indeed my external HDD 
and the Kensington is my USB mouse so no USB hub worries

Second, I did run all the updates for apt-get and also installed the ALSA loaders package. Alas, it still does not even recognize that i have connected a device

---

### Post by Stochastic on 2008-02-16
well the Bus 001 Device 003: ID 1210:000e line is probably the address of your pedal.  Can you go into System->Preferences->Hardware Information and try to find any info on that device?

Do you have any windows drivers for it, or just the program you speak of?

The other avenue you should persue, is e-mailing digitech and ask them if there's any linux drivers for their pedal.  They'll probably respond with "we dont' support linux" but I've been surprised a few times with some actual help from a manufacturer.  And you'll be showing digitech that their customers are using linux and they should consider getting a driver going.

---

### Post by Stochastic on 2008-02-18
does this post help at all?
[http://ubuntuforums.org/showthread.php?t=678521](http://ubuntuforums.org/showthread.php?t=678521)
It's in regards to recording from a different digitech usb pedal on ubuntu studio.

---

### Post by wtc on 2008-02-21
> **Stochastic said:**
> hmm, this thread [http://www.daniweb.com/forums/thread107470.html](http://www.daniweb.com/forums/thread107470.html) seems to claim that ALSA will recognize the pedal provided it's up to date.

I know that ALSA needs to have a USBAudio driver for most usb soundcards.  This is housed (I think) in the alsa-firmware-loaders package, so do ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install alsa-firmware-loaders
```

does that do it?

Hi Guys,

I finally got my Digitech RP250 pedal working under Ubuntustudio Gutsy (64bit AMD, kernel-rt), using instructions of Stochastic above. For RP150 and RP350 pedals installation should be same, as they belong to the same family.

After installing alsa-firmware-loaders I rebooted, connected RP250 and in terminal **lsusb** shows the device under ID 1210:000d. For RP150 ID is 1210:000e; for RP350 - anybody can update?

RP250 details are shown in terminal with **aplay -l**, or under System -> Preferences -> Hardware Information. Pedal is recognized as external USB soundcard. 


**Recording in Ardour**

I started the Jack with QJackctl, in Setup - I checked "Realtime" (since I use realtime kernel), Frames/Period "128" ("64" on my 2GHz Athlon64 / 512MB RAM PC doesn't work properly), Sample Rate "48000", Driver "alsa" and Interface "hw:1" which is the 2nd sound-card, i.e. RP250 device. Now, Jack PCM connections window show 2 input lines and 2 output lines - in fact all belong to RP250.

Recording is done smoothly, recording level can be monitored in Ardour Mixer window. While recording, sound output goes back to RP250 pedal and can be heard there via headphones or lineout.

HELP Needed!! - I also tried to get sound monitoring via PC loudspeekers. So in QJackctl setup I checked Input device "hw:1" and Output device "hw:0" (i.e., my Onboard sound device Intel 8x0). When starting Jack, error window comes, saying "samplerate 48000 cannot work with output samplerate 44100". In QJackctl setup, I tried Samplerate 48000, 44100 - result the same. Can anybody comment?... Maybe Onboard soundcard supports only 44100 and RP250 only 48000Hz?? 

In general, does anybody know how to configure Ubuntu to receive sound from 2nd soundcard (hw:1), and output sound to default (hw:0) soundcard or vice-versa?


**Recording in Audacity**

Recording is Ok until Audacity screen becomes filled with recording stream. Then, the Hard Disk starts working for whatever reason, and if I hear the whole recorded track - on that place sound is broken. Anybody, ideas why this happens?

Sound monitoring in Audacity: options -> I/O has a checkbox "Play current track while recording" or similar. I checked it - during recording, sound really comes out of speakers, but quality is terrible... (because of the same 48kHz vs 44.1kHz problem?..)


**Recording in Rosegarden**

Done similar as in Ardour, i.e. when Jack is running. Select "Input" instead of "General MIDI Device" (default setting), and you are ready to record. Sound level can be monitored in Rosegarden Mixer. I love this app, it also has a Metronome:)


To do next - find solution how to download/upload patches for Digitech RP devices. I've read, guys made this possible for Line6 Pod devices.


cheers!

---

### Post by Stochastic on 2008-02-21
hmm maybe some Ubuntu Studio devs should get going on a hot-pluggable device detection/installation system for these pedals.  Though they may have enough on their plate as it is.

---

### Post by studiesinsound on 2008-02-26
wtc: are you able to now use the x-edit software via wine for the rp device?
that'd be awesome!

I have an rp350 but due to massive overtime at work no time to try this out.

---

### Post by wtc on 2008-03-28
nope, x-edit doesn't run under wine - actually MS.Net2 installation under wine fails, and this is required for x-edit to work. while googling I found that .Net is not yet supported under wine, although is on to-do list. 
There should be simple way indeed to upload patches to RP pedals - the patches are simple text XML files.
I also tried java tool JSynthLib ([www.jsynthlib.org](www.jsynthlib.org)) which works with many different patch formats, but even when it checks connection to RP pedal (Midi device) - check fails, no idea why. 
I didn't have much time yet to do more, comments from others very wellcome!

---

### Post by ubnewbie2 on 2008-06-21
Hi,

I just wanted to say that I bought an RP150 this morning and plugged the usb into my computer (running 8.04 with ubuntu studio audio programs loaded - the latest because I only downloaded them last night).

Well, it just works.  Alsa sees it as hw:1,0, so I just change the jack setup to use it for the "interface". The pulldown in the jackd setup dialog identifies hw:1 as Digitech RP150, and hw:1,0 as USB audio right below that, so it's easy to see what to do. I left the input device set to "default" and changed the output device to hw:0,0 so sound would come through my computer sound system, then saved it and restarted the jack server.

I started up patchage and connected the system capture to the system output, and could play my guitar through my computer !!!

I then started ardour and was able to lay down 3 tracks, one at a time, with me playing bass, rhythm, and lead.  The sound is very very good.

Another thing, jack also sees the RP150 as a midi device.  Must be able to control it via midi then I expect.  I wonder where/if they documented that?

Hmmm just had a thought.  I should be able to use the pedal for audio out as well by just leaving the jack config at default for the output device, and the sounds would all come from my guitar amp via the pedal's line-outs. Didn't think of that- must try it soon.

---

