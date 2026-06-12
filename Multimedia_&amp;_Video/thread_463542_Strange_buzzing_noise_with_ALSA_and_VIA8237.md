---
title: "Strange buzzing noise with ALSA and VIA8237"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by theCSapprentice on 2007-06-03
Okay, I've been struggling with this issue for about a week now. I've read forums, wikis, and a whole host of documentation, but none of it has been any help. No one else seems to have this problem.

On to the details...

I recently switched over a computer of mine from Windows to Ubuntu 7.04. After many tweaks getting the system up to where I want it, only a few remain. A major issue is the sound. I have two audio devices.  One is a on-board sound card, the VIA8237, and the other is a pair of USB headphones from Logitech. As far as I can tell, the headphones work fine. However, I also have in this machine a ATI TV tuner, listed by **lspci** as ```
00:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

```

Now the tuner uses an external sound cable that plugs into the line-in connection on the motherboard. After getting the sound to actually be picked up, (requiring much fiddling with alsamixer), I find that whenever the TV is played, the audio is overlaid with a high pitched buzzing sound. It seems to be interference, but I can't figure out from what. All other channels of the card have been muted, so I don't think they are the problem.

I have one last wrinkle to add to this story. Last night I was trying to get the sound to come in again, by playing with alsamixer, and was using audacity to record the output. To my utter amazement, the sound recorded by audacity was perfect. No distortions. But when I played through the headphones when watching TV with VLC, it was back to the buzzing sound. So I suspect the headphones are to blame, but I really don't know enough about alsa and the sound system of Linux to be sure.

---

### Post by theCSapprentice on 2007-06-11
=;Do not be alarmed, fellow forum members, this is just a BUMP to keep this thread current.=;

But seriously, any advice you guys can give me would be greatly appreciated.

---

### Post by ridgeland on 2007-06-11
I've recorded from the TV to a file and gotten a buzz noise.
Then used Audacity's filters to clean it up.  It did a fine job.
I saved a noisy WAV and cleaned up and saved it as a MP3.
I did not see how to prevent the buzz, just cleaned up after it.
I expect the source relates to common grounds, shields etc.

---

### Post by theCSapprentice on 2007-06-12
I'm not sure that's the problem here. I mean if it was purely a hardware issue, wouldn't Audacity have the same problems as the VLC? Perhaps my issue lies more with the software mixer and VLC than with my sound card.

---

### Post by Erlander on 2007-06-12
An earthed audio input will produce a typical deep buzz.

It may be a faulty cable or a cable not fully plugged in.

Rob

---

### Post by theCSapprentice on 2007-06-14
Alright, I checked my connections and they all seem fine, and the cable I'm using is fine as I've used it on a Windows box and the sound comes through without a problem.

So the question still stands: What is it about my software is causing my sound to be messed up?

I've used both kdeTV and VLC. I can not get any sound to play from kdeTV what-so-ever. I can get sound from VLC, but it is distorted by the buzzing. But given my history with the card and Audacity, I still maintain that the problem lies with either the mixer or my video players. So, ruling out hardware issues, what else could be causing my issues?

---

### Post by ukripper on 2007-11-05
> **theCSapprentice said:**
> Okay, I've been struggling with this issue for about a week now. I've read forums, wikis, and a whole host of documentation, but none of it has been any help. No one else seems to have this problem.

On to the details...

I recently switched over a computer of mine from Windows to Ubuntu 7.04. After many tweaks getting the system up to where I want it, only a few remain. A major issue is the sound. I have two audio devices.  One is a on-board sound card, the VIA8237, and the other is a pair of USB headphones from Logitech. As far as I can tell, the headphones work fine. However, I also have in this machine a ATI TV tuner, listed by **lspci** as ```
00:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

```

Now the tuner uses an external sound cable that plugs into the line-in connection on the motherboard. After getting the sound to actually be picked up, (requiring much fiddling with alsamixer), I find that whenever the TV is played, the audio is overlaid with a high pitched buzzing sound. It seems to be interference, but I can't figure out from what. All other channels of the card have been muted, so I don't think they are the problem.

I have one last wrinkle to add to this story. Last night I was trying to get the sound to come in again, by playing with alsamixer, and was using audacity to record the output. To my utter amazement, the sound recorded by audacity was perfect. No distortions. But when I played through the headphones when watching TV with VLC, it was back to the buzzing sound. So I suspect the headphones are to blame, but I really don't know enough about alsa and the sound system of Linux to be sure.

i am wondering where did you get drivers for 8237 as I couldn't find it. your help much appreciated

---

