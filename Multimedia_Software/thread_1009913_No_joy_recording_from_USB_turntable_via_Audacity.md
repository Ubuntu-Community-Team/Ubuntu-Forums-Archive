---
title: "No joy recording from USB turntable via Audacity"
date: 2008-12-13
forum: Multimedia Software
---

### Post by b9k9kiwi on 2008-12-13
I have acquired a Sony PS-LX300USB turntable and have managed to record vinyl to .WAV and created CDs using Audacity in WindowsXP - but no such luck with Ubuntu (8.10).

With output set to ALSA: C-Media CMI8738 PCI IEC958 (HW:0,2) and input set to ALSA: USB Audio CODEC: USB Audio (hw:1,0) - and Software Playthrough either enabled or disabled - there is no input to record.

As Windows does the business this is not mission critical, but I would rather do this through Ubuntu.

Any help appreciated.


AMD Athlon X2 64 4800+
Asus M2N-ME SX Plus motherboard
Samsung 500Gb HDD Sata II (drive a)
Western Digital 250Gb HDD Sata (drive b)
2x1Gb DDR2 667 RAM
Genius 5.1 Value Soundcard
nVidia GeForce 6600 256Mb PCIe graphics card

---

### Post by b9k9kiwi on 2008-12-13
I've sort of resolved the primary problem by fiddling around with the source settings in PulseAudio - it's a pity that setting up a USB device can be such a pain in Linux.

Now, however, although I can record from vinyl (software playthrough in Audacity doesn't work for me), when I playback the track plays back at a very slow speed (although, for example, if I save it as a .WAV and play it through Totem it plays back at the right speed).  Wierd, can'tm understand the problem let alone think of a fix.

---

### Post by lensman3 on 2008-12-13
I have a ION turntable I just bought and it works fine.  I have software play through.

There is a button on the front of my turntable for 33/45.  If you record a 78 vinyl, then audacity has a setting to slow the "fast" sound down.  I'm just wondering if Audacity is set correctly?  

I'm also using the Alsa sound mixer which seems faster than OSS sound interface.  I have a quad-core 64 and I found that I had to essentially stop all extraneous processes so that the sound wouldn't skip.  I like the USB input much better than a analog input.  The sound level is much more consistent and the sound wasn't plagued with a 60 cycle hum.

Hope this helps.

---

### Post by b9k9kiwi on 2008-12-14
[QUOTE=lensman3;6364260]I have a ION turntable I just bought and it works fine.  I have software play through.

... I'm just wondering if Audacity is set correctly?  

/QUOTE]

ION seem to be the flavour of choice in USB turntables - the Sony won't do 78s but, as I don't have any, it shouldn't matter too much :)

It would seem that Audacity isn't set up properly - the Windows version is easier to learn and use and responds to mouse/keyboard control more reliably (pity that) so I'll do my training on that before committing to the Linux version alone.

I can live without software playthrough.

---

### Post by pizzafarmer on 2008-12-14
Like you, I can use my Windows box to use Audacity, but would like to get it working in Ubuntu.

I was able to get playback to work by disabling Pulseaudio and setting playback to Alsa default in Audacity. Open a terminal window and:

pasuspender -- audacity

My problem after that is that the turntable sounds like a cell phone in a low spot. Must be something with the codec, but I haven't figured out what.

---

### Post by Farmer of Bricks on 2008-12-21
> **b9k9kiwi said:**
> Now, however,... when I playback the track plays back at a very slow speed (although, for example, if I save it as a .WAV and play it through Totem it plays back at the right speed).  Wierd, can'tm understand the problem let alone think of a fix.

In there should be a small green arrow with a slider next to it. That slider will adjust playback speed. It could be that your slider has been mistakenly set below 1x.

---

### Post by Boat on 2009-06-27
> **lensman3 said:**
> I have a ION turntable I just bought and it works fine.  I have software play through.



I just got an Ion turntable and after some uninformed playing with the settings I have it recording with play-through. Only problem is that after about 10 seconds the recording and playback stop. Perhaps someone who has one of these turntables working, could share some settings tips.

---

### Post by dogroferifno on 2010-09-18
Like all of you, I had Audacity working great but slow through Windows, I can not get any sound when I run the Audacity program through Ubuntu. This may be the one thing that forces me to keep Windows because I have a large collection I would like to digitize for use and cataloging. If anyone has a solution please post so I may stay with Ubuntu.

---

### Post by pizzafarmer on 2010-09-18
dogroferifno, I had a lot of trouble getting my turntable to work at first. Upgrading to Karmic and Audacity 1.3.9 solved most of my problems, but I still had to get everything optioned correctly. Basically, I have the Audacity device settings set to ALSA for the host and then record and playback set to "default" and channels set to 2 (stereo). I left everything in the Quality tab set to the defaults. Then, right click on the volume control icon and click "Sound Preferences". Under the Input tab you will see the devices available. There should be a PCM Audio Codec listed. If it isn't, plug in the turntable and start playing an album. After you bring up the Sound Preferences window you should now see the PCM codec listed. When you select it the input level meter should register. If you want to play through, select the PCM codec under the Output tab as well. Hopefully this will work for you.

---

### Post by dogroferifno on 2010-09-18
Pizza, The settings are the same as I have them, The problem is when I start the album, i get nothing in Audacity, i can hear the needle playing but no sound from the computer, and no hint of recognition of it playing in Audacity.I am new to Ubuntu, so I am not sure if there are steps required to get it to recognize my turntable which is an ION TTUSBO5. I have been trying to figure this out for several days with nothing happening as of yet. Thanks for the help.

---

### Post by dogroferifno on 2010-09-19
Pizza, Thank You, I got it finally, Ubuntu 10.4 has things in different places, found the sound control settings and changed them, I can now record and hear the album while I am. Thanks Again, I was about to give up and use windows for transferring my albums, glad I don't have to go there. Sweeet.

---

