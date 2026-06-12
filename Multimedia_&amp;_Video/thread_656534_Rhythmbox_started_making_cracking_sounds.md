---
title: "Rhythmbox started making cracking sounds"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by pranami on 2008-01-02
I recently installed Ubuntu 7.10 and I was using Rhythmbox music player. The sound was perfect on it; no cracking sound at the maximum volume possible. Then I was fiddling with the volume control properties (Ubuntu desktop, not the Rhythmbox volume) by right clicking on the volume icon at the top-right corner of my desktop. All of a sudden I noticed strong cracking sounds :(. This happens even at low volumes, I tried lowering the master volume and player volume but to no avail. I am 100% sure that there was no cracking earlier. Moreover there is no cracking when I tried playing this song in Totem. Clearly something went wrong with Rhythmbox. Does anyone of you have a clue :confused:? I am playing mp3 music files. Cracking sound is more conspicuous on percussion instruments.

I found some cracking sound issues with Rhythmbox when I searched the forums but I did not see anyone report that sound worked fine and then suddenly it started cracking.

---

### Post by jeffus_il on 2008-01-02
If the disturbances are at low volumes, there is a chance that they may be external, not in your box, I once had my wireless antenna interfering with directly with the speaker, move any antennas, transformers, electrical equipment away from your speakers, might just help.

---

### Post by pranami on 2008-01-02
> **jeffus_il said:**
> If the disturbances are at low volumes, there is a chance that they may be external, not in your box, I once had my wireless antenna interfering with directly with the speaker, move any antennas, transformers, electrical equipment away from your speakers, might just help.

This occurs at the same portion of songs again and again. Besides, I don't have any other electronic device working except my laptop and refrigerator. I do have the wireless internet available for all residents in my building but I have always used it, so I doubt that this will affect sound. Totem plays the same song without any cracking. Any other ideas? Thanks for your reply.

---

### Post by jeffus_il on 2008-01-02
Is totem using the same driver as rhythmbox, I think rhythmbox is gstreamer, totem can be xine or gstreamer.

---

### Post by pranami on 2008-01-02
> **jeffus_il said:**
> Is totem using the same driver as rhythmbox, I think rhythmbox is gstreamer, totem can be xine or gstreamer.

I am not sure, how can I check that?

---

### Post by jeffus_il on 2008-01-02
In Totem do Help->About
It tells you there.

---

### Post by pranami on 2008-01-02
> **jeffus_il said:**
> In Totem do Help->About
It tells you there.

Okay, thanks. I'll check that and let you know. Thanks for your help.

---

### Post by pranami on 2008-01-04
> **pranami said:**
> Okay, thanks. I'll check that and let you know. Thanks for your help.

Hi, Sorry for being late but I got busy with work. I checked Totem, it is running on Gstreamer 0.10.14. Totem does not make any cracking sounds on any song. I don't understand why Rhythmbox is giving me cracking sounds and it started happening suddenly. It was working fine before. Any help in this regard will be greatly appreciated. Thanks.

---

### Post by pranami on 2008-01-04
Seems like no one else is having this problem. If you have any clues, please help me. Thanks.

---

### Post by jeffus_il on 2008-01-04
Can't think of any cause, both use the same driver, had an idea, go into the Rythmbox setup and disable all plugins. If this stops the noise, reenable one by one and maybe you can find the culprit.

---

### Post by mrtrick on 2008-01-05
I have the same issue. Just installed the latest ALSA driver to get sound back after the latest kernel upgrade and started experiencing this problem. I have not tested anything besides Rhythmbox yet. Anyone have input on this as of yet?

---

### Post by pranami on 2008-01-06
> **jeffus_il said:**
> Can't think of any cause, both use the same driver, had an idea, go into the Rythmbox setup and disable all plugins. If this stops the noise, reenable one by one and maybe you can find the culprit.

I tried doing turning on the plugins one by one but that did not help. Thanks for all your suggestions, I appreciate your the time and thoughts that you put in to help me. I noticed that once in a while when I boot Ubuntu, Rhythmbox wouldn't give the cracking sound and on other occasions with same settings sound cracked. That was frustrating.

While I was having trouble with Rhythmbox's cracking sound I was also trying to install TuxGuitar application. Initially I was not getting any sound on TuxGuitar so I tried the suggestion given by **nalmeth** in the thread: [http://ubuntuforums.org/showthread.php?t=303017](http://ubuntuforums.org/showthread.php?t=303017)

[HTML]If you are planning on using MIDI at all, you will want to load the ALSA sequencer module.
sudo modprobe snd-seq

To have your system load it at bootup, you have to add it to the /etc/modules file.
sudo su -c 'echo snd-seq >> /etc/modules'

Timer Resolution

The Ubuntu kernel currently is set to 250Hz timers, which is insufficient for MIDI. We can correct this:
sudo sysctl -w dev.rtc.max-user-freq=1024

To make it persistent across reboots, you need to add a line to the /etc/sysctl.conf file.
sudo su -c 'echo dev.rtc.max-user-freq=1024 >> /etc/sysctl.conf'[/HTML]

I also implemented the suggestion given by **Recker**in the thread: [http://ubuntuforums.org/showthread.php?t=255089](http://ubuntuforums.org/showthread.php?t=255089)

[HTML]What I did was downloaded the sounbank deluxe from http://java.sun.com/products/java-me...oundbanks.htl
. Set tux guitar to use a custom soundbank and pointed it at the deluxe file.
I then added alsa-oss from the repos.

$sudo modprobe snd_seq
$aoss ./tuxguitar[/HTML]

Then I disabled the Alsa plugin that came with TuxGuitar. After this I got sound in TuxGuitar. When I was done doing all this I noticed that the Rhythmbox sound was not cracking!! I don't know how this happened. May be this is temporary and Rhythmbox might start cracking again. 

However, if you see something that I did, which could affect the Rhythmbox, please  share it with others. Cracking sound in Rhythmbox is a known issue experienced by others, so I am going to wait for next release of Ubuntu and hopefully Rhythmbox on that will run flawlessly.

I don't know if I should mark this post answered or not. As of now Rhythmbox sound on my laptop is not cracking, so that problem that I started this thread for does not esist anymore (albeit fluke). Any suggestions?

---

