---
title: "Why no MIDI auto-configure?"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by tonymoloney on 2007-12-02
After a bit of work, I've got MIDI to work on my Lenovo lap-top, but why did I have to go to all that trouble?
MIDI has been around since day one, before the mouse and colour screens. I even had MIDI working on an ATARI so why is it not just automatically set up when you install a system?

---

### Post by tonymoloney on 2007-12-11
Bump!

---

### Post by christhemonkey on 2007-12-11
What about midi do you want setting up?

Most people do not need Midi at all. And those that do tend to be the sort of people who would know where to look to work out how to get it working. (IMHO, with myself being one of those people)

---

### Post by tonymoloney on 2007-12-12
<<What about midi do you want setting up?>>

Well, I think that midi should just work! When I tried to play my first midi file (of which I have hundreds), nothing happened. I then found out that I needed timidity and when I installed that, once again nothing happened until I found out how to set it up and them downloaded Kmid and got everything working.
As I said, I got midi to work, but why didn't it just work straight away like a keyboard or mouse? Not everyone, especially those noobs just converting from Windows, knows how to  set things up. Hey, some of them have never even seen a cli command before.

---

### Post by Cuppa on 2007-12-13
I agree with Tony. Midi should just work out of the box. I'm trying to run a game with wine and it wants to play midi music clips. When I try to play a midi file with playmidi I get a message about not being able to use /dev/sequencer or something like that (I forget the exact wording--I'm at work now). I'd like to know the minimum I have to do to play a simple midi file through my sound card. I don't see why I have to download a sequencer and a software synth and a lot of KDE libs. Do I also have to enable KDE services on startup? Do I have to do something manually every time I log on? This is much more complicated than it should be on a modern desktop distro. It's not like midi is a proprietary interface (or is it?). For the record, I'm using Xubuntu Edgy with an Ensoniq AudioPCI card.

---

### Post by LittleTyke on 2008-01-23
> **tonymoloney said:**
> .....but why did I have to go to all that trouble?
MIDI has been around since day one....

I heartily agree with you! I am a newcomer to Linux. With previous versions I tried (SuSE, Mandrake) over the past five years I would have given up already, but Ubuntu 6.06 and now the 7.10 I installed yesterday looks promising - the first Linux that does. I've got movies working, streaming video off the BBC, YouTube...

...and then I tried playing a MIDI file!!

Talk about hitting a brick wall at ninety miles per hour! This is such a standard in Windows that one never even thinks about playing MIDI files. They just DO (under Windows).

Now I've got KMid installed, and it looks very nice. Trouble is, it "plays" the sound (the progress bar thingie moves along), but nothing comes out the speakers (yes, the speakers are working if I play a DVD).

I checked in KMid's Settings/MIDI Setup and it says: Select the MIDI device you want to use: MIDI Through MIDI Through Port-0 - ALSA device" (There is no other device to select; just that one.)

Then: "Use the MIDI map: /usr/share/apps/kmid/maps/gm.map"

Dunno what to try next. I looked in Synaptic Package Manager and there are a couple of entries starting with "ALSA...." so maybe I should install either or both of those.

Others have claimed they got KMid working on Gnome. But, like you said, WHY is such a bog-standard requirement so totally arcane in Linux? Beats me!

---

### Post by shane2peru on 2008-01-26
I would have to agree, that midi should just work. I'm an experienced user on Linux, and have successfully installed Slackware, Gentoo, but getting midi to work for me has always been a pain, there isn't (at least to my knowledge) good clean documentation on it.  My wifes comptuer has the same issue, I installed kmidi and set the settings correct, and nothing, no sound.  Installing Timidity too, but I must say, she is not impressed.  Midi is all over the web for various music files, and should be a standard part of the OS, or at least very easily installable.  

Shane

---

### Post by Melcar on 2008-01-26
Yeah, totally agree.  The problem seems to be that only certain card models and makes support hardware MIDI decoding, which as I understand, "just works" on Linux (in this case Ubuntu), and if yours doesn't then you have to get software synthesizers which are not available on default installs.   I imagine "bigger" distros like the Fedoras and Suses do include some type of software MIDI sequencers, but Ubuntu in an effort to minimize itself doesn't, since most people don't really use it nowadays. 
Still, after some clarification by some helpful members here, I was able to get basic MIDI playback working, but I must say that for some reason, it was much easier to do in KDE rather than in Gnome.

---

### Post by Chappy7777 on 2008-03-01
Well, grrrrrr. I came here to ask how to play midi files. The answer seems to be that I don't. I play blues guitar and harmonica and I just clicked on a "play basic 12 bar blues midi" and it wanted to default to Amarok. That was a joke.

I know that my friend across the road had an old Mac, the kind that had a tiny screen built into the tiny Mac PC. This was like 18 years ago or more. He used it to practice bass guitar to midi files. Every version of Windoze I've had since 3.1 has played midi. 

I am not mad, just dumbfounded that Ubuntu has no ez way to play midi files. Either thru FFox or by downloading the file. Neither worked.

Someone out there who does programming should do us all a favor.

Oh, and to say that no one uses midi is silly. Anyone learning to play an instrument or wanting to know the melody of an old tune will be trying to use a midi file.

---

### Post by Melcar on 2008-03-01
On KDE I just use Kmid (frontend) and Timidity (synthesizer), and under GNOME Audacity with the Fluidsynth synthesizer; note that if using the Fluidsynth backend you will need to provide your own soundfont, while timidity already comes with simple samples to play.  I only use it for playback, thought.  But I agree; one would expect for such a thing as MIDI to "just work" (everything else seems to "just work" so why not MIDI?).

---

