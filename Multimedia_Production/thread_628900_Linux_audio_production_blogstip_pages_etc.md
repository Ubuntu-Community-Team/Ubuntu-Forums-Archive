---
title: "Linux audio production blogs/tip pages etc?"
date: 2007-12-01
forum: Multimedia Production
---

### Post by Stochastic on 2007-12-01
So has anyone come across any good Linux audio production pages.  Not just "how to use this program" style, but rather "how to effectively use a sidechain compressor in linux" style?  I'm looking for some that deals more with the art of audio production once you understand how to use everything rather than an explanation of getting the apps functioning.  Any suggestions?

---

### Post by Stochastic on 2007-12-05
nobody? nothing? anyone?

---

### Post by paulbuk on 2007-12-26
Hi there, yes I'm here for starters and will in the future try to give some objective views on the use of Ubuntu/Ardour in a Pro working environment compared to other audio systems.

I'm currently in the final build stages of a 42sq mtr home recording studio, 1 * sound booth, 1 * tracking room and a control room some 3.5*5mtr sized offering a range of audio/music production services including electronica, electro-rock, electro-dub genre recording.

Since the beginning of time (ok the mid '80s) I've mainly been Steinberg (atari??)  based but lately had my eye on Linux and came across Ubuntu Studio in August. My newly built AM2 comp whilst running winXP Steinberg Cubase 4 will also have a dedicated HD for Ubuntu and I'm keen to utilise it in a pro environment and 'fly the flag' for Ubuntu/Ardour, offering demo, training and Ubuntu audio system builds for local musicians looking for alternatives from PT & other DAW systems.
Ardour looks great to me and a serious contender, so once I have some sessions recorded, I'll post my experiences if any here, good or bad.

For those of interest, I'm running with Tascams, FW1884, FW1082/Behringer ADATs, M-Audio 24/96 Audiophile (the current Ardour output) and hope  to be able to get the Tascams to function fully with Ardour, once I can find out how.

For an overview of the studio, please visit my portal after Jan 20th '08 once things are fully operational: [http://www.elektromaticsound.com](http://www.elektromaticsound.com)

Again, I'll post my experiences here and on the website as a blog.
Regards,

Paul B,
Liverpool area, UK.
:)

---

### Post by Mblackwell on 2007-12-27
> **Stochastic said:**
> So has anyone come across any good Linux audio production pages.  Not just "how to use this program" style, but rather "how to effectively use a sidechain compressor in linux" style?  I'm looking for some that deals more with the art of audio production once you understand how to use everything rather than an explanation of getting the apps functioning.  Any suggestions?

I can't say anything Linux-specific, no. In general I've had good success using Ardour and some age old mixing techniques, which mostly equate to:

Double track the rhythm guitars and pan them hard left and right

bass in the middle
stereo drums

vocals front and center.

This applies to "modern" sounding recordings mind you.

I generally use a 10:1 compression ratio, personally. Everything else is as-needed. Reverb is really important, and Freeverb for the entire song (to create a room space) or stereo tracks, and Gverb for your normal individual mono-track will be really helpful. I've found that creating a room/reverb space for everything is nice for making things match up, but sometimes you need to add that little bit of extra reverb to a track (for instance, vocals, lead guitar, harmonies) to give them an extra push. This also helps things sound decent even when not wearing headphones, and even on crappier sound systems. 

One thing I discovered that's a nice feature is in Ardour you always know where something is clipping. It will show you on the track where part of the actual recording is clipping, and it will tell you in the meter when your track volume settings cause the recording to clip and by how much. I really liked this because when there was weird clipping in the song I could discover where the culprit was.

Being not exactly the wealthiest man alive I've always just stuck with simple equipment, that being a used V-Tech mic, my SB Live! Platinum 5.1 card (with the drive), my MG 15DFX amp, a Nashville Tele, Aria Bass, Washburn Acoustic,  and some misc cables... and I was really surprised recording in Ardour. I had previously used Acid Pro, and was fairly satisfied, but with Ardour there were a lot of nice features and everything came out really clean sounding. In fact, it seems as if Linux processes audio with less background hiss than Windows does, although I'm not sure why.

In fact, you can hear the difference yourself (sorry if you don't like alternative rock, or my singing... ha!). [This is something recorded in Windows via Acid Pro](http://mb.mirage.org/Chemical_Imbalance.mp3). And [this is something recorded in Linux with Ardour](http://mb.mirage.org/Dust_In_The_Bag.mp3) just a few days ago.

It's not exactly that the first one sounds completely awful so much as there's not as much (or maybe any) warmth to it somehow.

I don't know if my post was particularly helpful, but it does express my current thoughts on the whole matter.

---

### Post by moron on 2007-12-27
> **Stochastic said:**
> So has anyone come across any good Linux audio production pages.  Not just "how to use this program" style, but rather "how to effectively use a sidechain compressor in linux" style?  I'm looking for some that deals more with the art of audio production once you understand how to use everything rather than an explanation of getting the apps functioning.  Any suggestions?

The art of recording has zero directly to do with Linux so any of the gajillion online recording FAQs and how to's will answer your questions there if you are wanting to know about these things conceptually.

The Linux part of your question *IS* the applications, if you don't need help on say, setting up a side chain in Ardour (i.e. an application specific question) then you are not asking about anything specific to Linux.   Any discussion of Linux based recording by the very nature of the fact that you are talking about software will ahem, require discussion of software.

=)

For general recording help you could start with these:

[http://www.harmony-central.com/Recording/faqs.html](http://www.harmony-central.com/Recording/faqs.html)
[http://www.soundonsound.com/articles/Technique.php](http://www.soundonsound.com/articles/Technique.php)

As to Linux specific stuff, basically you are looking at Jack (audio daemon), Ardour (multitrack recording), Jamin (mastering) and Audacity (audio editor) as the core.  From there it depends whether you need to do anything with MIDI or want to run soft-synths.

In case you like abrasive industrial music, the CD I released recently was entirely recorded and mastered using Ubuntustudio (Ardour, Audacity and Jamin):

[http://deterrent.net](http://deterrent.net)

Recording with Ardour is awesome.  Mastering under Linux with Ardour and Jamin is still a bit of a pain due to the Jack routing but the results are worth it. 

Cheers

---

### Post by theorganloft on 2007-12-28
> **Stochastic said:**
> So has anyone come across any good Linux audio production pages.  Not just "how to use this program" style, but rather "how to effectively use a sidechain compressor in linux" style?  I'm looking for some that deals more with the art of audio production once you understand how to use everything rather than an explanation of getting the apps functioning.  Any suggestions?

I have been working on building systems and testing applications.  I can offer some good tips on using the plugins, sends and returns since I have a working system.  I am also willing to share my lab by trying some of the things that you would like to get working.  

Best of Luck,
:guitar:

---

### Post by alx010 on 2007-12-29
A couple of  links you might find useful;
 
[http://linuxaudio.org/](http://linuxaudio.org/)

[http://www.linuxjournal.com/user/800764/track](http://www.linuxjournal.com/user/800764/track)

And a long running Linux DAW thread is stickied at KVR;

[http://www.kvraudio.com/forum/viewforum.php?f=16](http://www.kvraudio.com/forum/viewforum.php?f=16)

---

