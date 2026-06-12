---
title: "Ubustu questions &amp; 24-bit/96 kHz WAV"
date: 2010-09-02
forum: Multimedia Software
---

### Post by Th3Professor on 2010-09-02
Hi!

So, wow, it has been a long time since I've been in these forums!

Do people still discuss audio recording via home recording set-ups in this "Multimedia & Video" forum? I'm looking for a forum that has lots of people with experience at recording with Linux-based applications. I'm avoiding those forums that have a lot self-proclaimed overly-zealous "audiophiles" types of people who think that they're god's gift to recording. ;)

Anyway, so question...

I've gotta Zoom H4n on order, should be arriving today actually, and it has a 24-bit/96kHz setting for recording.

I'm familiar with the whole debate of do/don't use it (some people say don't go higher than 44.1, some say max out at some picky number like 88.2, some say go as high as possible), though putting that aside...

Can the software that comes with Ubuntu Studio handle 24bit/96kHz recordings?

(Can it edit it, etc. etc.?)

I have home recording gear... nice cardioid condenser mics, a Mackie mixer, a Delta 1010 rack, a few other things, and I'm running Ubuntu Studio.

Due to my real life responsibilities, I have not had a chance to actually get my li'l home recording studio fully set up. Sadly all of that great gear is collecting dust. :(

A long, long time ago in a galaxy far, far away I studied recording... and I've basically forgotten just about all of what I learned. And so, I have to essentially start over.

Where can I get some very easy and very user-friendly interactive help with learning how to use the recording software in Ubustu and setting up the recording gear/hardware to work with it?

I know that my gear is compatible. I just need help with learning how to use all of the software built into Ubuntu Studio.

(And I need to upgrade my system, I think I'm running 2009 Studio.)

The 24/96 thing, if I can edit at 24/96 and mix down in Ubuntu Studio what I record on my "handy" portable recorder - that Zoom H4n (I think "n" is for "next", anyway) - then that will be very, very cool.

I understand CDs are at 44.1, though that of course gets back into the whole debate of which frequency and bit-rate to use.

So, yep, summarized:
* Ubustu interactive help for recording music?
* Can I edit & mix-down 24/96 recordings in Ubustu apps?

Thanks! ):P

---

### Post by cchhrriiss121212 on 2010-09-03
For good on this help you should try the ubuntu studio sub-forum.
Regarding bit-rates: yes it is possible to record at 24/96 using linux audio production programs. Most of what you record will done with jack which is very adjustable in that regard. You certainly seem to have enough quality hardware to get recording with!
I'm not sure about the Zoom though, it would depend how you were hoping to use it. Do you just connect it up as an external hard disk and load the audio from it?

I would also advise you to stick with the version of studio you have now as upgrading will only add more work for you (unless you enjoy all that customisation/installation work).

---

### Post by Th3Professor on 2010-09-03
> **cchhrriiss121212 said:**
> For good on this help you should try the ubuntu studio sub-forum.
Regarding bit-rates: yes it is possible to record at 24/96 using linux audio production programs. Most of what you record will done with jack which is very adjustable in that regard. You certainly seem to have enough quality hardware to get recording with!
I'm not sure about the Zoom though, it would depend how you were hoping to use it. Do you just connect it up as an external hard disk and load the audio from it?

I would also advise you to stick with the version of studio you have now as upgrading will only add more work for you (unless you enjoy all that customisation/installation work).

Hi! Thank you for your response!

Where's the Ubuntu Studio sub-forum at? I couldn't find it.

I'm glad to hear that 24bit/96kHz works in JACK. Does it work in software like Ardour? I'd definitely like to learn how to use Ardour. It looks like a Linux version of Pro Tools, which I learned how to use waaaay back but I've since basically totally forgotten, hence looking for interactive help with things like Ardour, JACK, etc.

My recording gear - it really is collecting dust, literally. I'm going to have to get canned-air to blow some of that dust off and hopefully that'll get it out of the little spaces inside, like inside the vents on the rack unit.

It'll be great to finally get around to actually *using* that gear. heheh

Regarding the Zoom H4n - here's their [info page]("http://www.zoom.co.jp/english/products/h4n/").

The device arrived in my mail yesterday. It's great! I ended up spending several hours using it right after it arrived.

What attracted me to the H4n specifically were features that went beyond the typical "handheld digital stereo audio recorder".

Some of the things that the H4n has -
* "true x/y stereo" mic placement with adjustable 90° and 120°.
* 24 bit & 96 kHz audio "resolution" (which is what I'm curious about).
* runs off of SD & SDHC cards (which will hopefully make moving recordings to Ubuntu Studio easy).
* the h4n preamp is an improvement from the older h4 version.
* playback speed control.
* low-cut filter & limiter.
* option for "stamina" mode for when not plugged in and when using batteries, which supposedly nearly doubles battery life (though I wonder if it really does). lol
* 2 XLR/TRS inputs! (This really attracted me to the device.) :D
* 3 of the basic recording modes:
- stereo/2 channel.
- 4 channel (this caught my interest).
- multi-track recorder/4 track (and this really got my attention).
* auto-record & pre-record options.
* can edit without computer (though I'd like to use Ubustu).
* various playback features, including a nifty loop option, even karaoke lol (I don't need that feature but it's a neat bonus).
* supports "broadcast wave format" (bwf), has time stamping and track markers.
* has punch-in/punch-out and "auto" punch -in/-out (when pre-setting it for hands-free).
* a bunch of onboard effects.
* various features for guitar and bass.
* tuner & metronome.
* speaker (not that good, though there's an 1/8" jack for headphones or speakers, which really is better anyway for this type of device).
* USB & also works as a USB audio interface (which I really like).
* wind screen (though it's only so-so, something [like this]("http://www.redheadwindscreens.com/") would probably be better).
* etc.

My particular order came with a package of other things, like a nice hard case for protecting it. The device is over $300, though I put nearly $400 into it for the extra items I got with it and I paid for next-day-air (which was $$$, I needed it ASAP for upcoming events (today and tomorrow)).

Anyway, enough about the H4n. :popcorn:

So, I think I have 2 ways of getting the audio recorded on my H4n onto the computer... USB or SD/SDHC.

I tested the SDHC card, popped it into my laptop's SD card reader, and my old version Ubuntu Studio recognized it so I copied files over. My main computer though, the multimedia desktop that I built, the SD card reader on that isn't working. :( So I'll have to either put files on laptop, then on CD or something (which might be good for backing up anyway), then copy over to desktop via CD.

...or... if Ubuntu Studio works with the general USB file transfer feature and USB audio interface feature on the Zoom H4n, then I'll just use that. But I don't know if it'll work. Any ideas?

---

### Post by cchhrriiss121212 on 2010-09-03
[The studio forum]("http://ubuntuforums.org/forumdisplay.php?f=335"). You should see it if you click on the "Ubuntu Forums" link on the top left, and look underneath Multimedia & Video in the main support category.

Ardour will be fine with 24/96 as it uses jack, and anything using jack will be able to use those same settings. Jack will actually use 32 bit depth by default and you choose your own sample rate from 22-192KHz.

Pro-audio on Windows tends to have one program that will perform all your needs for you i.e. Pro-Tools. 
Pro-audio with linux works like this: jack is the control center that connects all the programs and hardware ports together (and determines how fast they can transport data to each other). You then use a variety of smaller apps connected through jack to build a complete DAW, i.e. Hydrogen for a sequencer, zyn as synths, and Ardour to record and edit it all. Does that make sense?

The zoom looks like a nice piece of kit, I have no idea whether the USB transfer will work, it should be OK unless it is bundled with some kind of Windows only transfer software.
Good luck with your days recording!:popcorn:

---

### Post by Th3Professor on 2010-09-03
> **cchhrriiss121212 said:**
> [The studio forum]("http://ubuntuforums.org/forumdisplay.php?f=335"). You should see it if you click on the "Ubuntu Forums" link on the top left, and look underneath Multimedia & Video in the main support category.

Ardour will be fine with 24/96 as it uses jack, and anything using jack will be able to use those same settings. Jack will actually use 32 bit depth by default and you choose your own sample rate from 22-192KHz.

Pro-audio on Windows tends to have one program that will perform all your needs for you i.e. Pro-Tools. 
Pro-audio with linux works like this: jack is the control center that connects all the programs and hardware ports together (and determines how fast they can transport data to each other). You then use a variety of smaller apps connected through jack to build a complete DAW, i.e. Hydrogen for a sequencer, zyn as synths, and Ardour to record and edit it all. Does that make sense?

The zoom looks like a nice piece of kit, I have no idea whether the USB transfer will work, it should be OK unless it is bundled with some kind of Windows only transfer software.
Good luck with your days recording!:popcorn:

Cool, thank you for the link to the Studio forum.

Glad to know everything handles 24-bit 96 kHz fine.

Speaking of that audio resolution, I went ahead and asked a professional at recording (with multiple degrees and years of professional experience in the field), and he said that 24-bit 96 kHz is often used for high end mastering but otherwise it's not necessary, that 16-bit 44.1 kHz is fine (and it can transfer directly to audio CD). Some people say record higher res and change it when putting it on CD but, like that individual told me, for many situations going higher than 16-bit 44.1 kHz is overkill. I'm not doing "high end mastering" for these particular recording sessions that I have, so I'm going to just stick with 16-bit 44.1 kHz. :D

That's crazy that JACK supports 32-bit! And 192 kHz?! Dang! What are the advantages to that? My hunch would be the whole idea of high end mastering, and otherwise it'd be overkill.

Re: Pro Tools and similar apps across different platforms -

I've used Mac-based recording/editing programs, though that was pre-OSX. And I've forgotten all of it. :/

I've never used Windows-based recording software. I've toyed around with some freebie light-versions of apps a long time ago, like things that'd come with new hardware, though never actually used them for recording scenarios.

So, I get the idea now on the process for Linux digital audio workshops... I think I had the basic idea a while back but totally forgot...

{Instruments & external gear -> JACK -> all the other audio programs}

That make sense.

I wonder why JACK is even required, or if there is a way to just implement it into all of the *nix-based audio software. That sounds like it'd be a major task of course, though it'd be a pretty sweet collaboration and make for a nice union of audio data through-put with editing/recording/etc.

I'll have to test the Zoom H4n's USB features. At the moment I'm without a desktop (the dang power supply died), so once I get that back up and running I'll have to test it out.

The H4n did not come with any software or bundled stuff. Thankfully. Well, it came with "Cubase LE 5" but I don't think that is required for file transfer.

Thanks for the input on things. Much appreciated! :D

---

