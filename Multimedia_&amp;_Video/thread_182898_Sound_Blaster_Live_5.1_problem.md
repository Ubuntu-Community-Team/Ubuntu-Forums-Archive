---
title: "Sound Blaster Live 5.1 problem"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by rodrigo666 on 2006-05-27
Greetings,

I've never used a linux system before and decided to start with Ubuntu because of the hype I've been seeing around the internet about it.

I'm finding the experience very enjoyable and I hope to never more need a Windows system, unless there's no choice (for running some determined software, for instance).

Well, since I'm very new to all commands and such, I would like the answer to my question be written in a very simple way. (I know how to open the terminal, but don't know the commands properly).

I'm experimenting a sort of problem with my sound card, wich is a Sound Blaster Live 5.1. 

In WindowsXP I could control the volume of each of the channels (rear, front, center and woofer). But I can't do that in Ubuntu Volume control Alsa Mixer. I believe it's because it only work with two channels.

Another thing that I believe that might be a problem is that on the top of the window it says "Volume Control: SB Live [Unknow] (Alsa Mixer)" in wich I think that the "Unknow" represents a problem. Is that really a problem?

I hope to express myself well. If I didn't, sorry (I'm from Brazil).

---

### Post by kevin_hill54 on 2006-05-27
If you know how to use the terminal type in 

alsamixer -c 0

this will bring up the full Alsamix controls. See if you can set it from there?

You can add these controls via the preferences in the GUI menu.

I have an Audigy and can control 5.1 channels

---

### Post by rodrigo666 on 2006-05-27
I've already try the alsamixer -c 0 command, but I could not find any rear, front, center and woofer volume control there.

And what about the "unknow" in the window as I said, that's okay?

Thanks for the reply.

---

### Post by Ilias83 on 2007-12-07
First post here...
Have you fixed the problem?
In any case I think this is what you have to do:
Try to Open Volume Control.
Then from Edit->Preferences enable Wave Center and Wave Surround.
This will let you control the center speaker (from wave center) an rear speakers (from wave surround).
But unfortunately you can't control them all together from Master Control.
Any Idea???

---

### Post by Unterseeboot_234 on 2007-12-07
I had the exact same "Live" card in my old 32-bit box. Your alsamixer has to say Creative SBLive for ALSA to bridge between the driver and whatever software. My old 32-bit box ran Dapper and I added the specific ALSA driver from the ALSA web site matrix chart. Now I run Gutsy and use the onboard sound from my nVidia graphics card and I get 5 channels. The installation of Gutsy itself discovered my hardware. Whenever I have sound playback problems I make sure Gutsy points to the DIGITAL version and not the Analog of my sound driver. 

Did you add the card after you installed Ubuntu? A new install should discover that card.

For you, start out with Menu --> System --> Preferences --> Hardware information. For instance, if we don't see any mention of SBLive, Creative or whatever the TexasInstruments chip number is (see the ALSA matrix chart for that chip number), we might have an unseated board. If we do see the SBLive, then there could be too many drivers and maybe others on these forums will know what to delete or add. Don't give up. I'm a big fan of that sound card. I wished the Win98 demo software that came with my SB card could somehow install over on my 64-bit box. Look into this Forum link I went back and found. They are using the File System to try to fix things. I used the ALSA downloaded driver for my fix. Today, I use different hardware but I posted for you  because I like Creative Labs products.

[**Forums Sound discussion**]("http://ubuntuforums.org/showthread.php?t=622138")

---

