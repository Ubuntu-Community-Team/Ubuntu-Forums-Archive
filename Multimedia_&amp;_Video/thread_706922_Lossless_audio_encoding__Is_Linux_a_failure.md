---
title: "Lossless audio encoding:  Is Linux a failure?"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by warbread on 2008-02-24
This has been eating me alive all weekend.  I'm wanting to re-encode all of my music into .flac.  Yes, I have the hardware to hear the difference .flac makes and yes, I think it sounds better than VBR .mp3 and 320kbps vorbis.  So far, Soundjuicer, Grip and ripperx have all failed me;  playing back their rips, I can hear pops and crackles.  I've even tried some  Windows solutions.  CDex failed me just as Grip and the others have.  The other was  EAC, but the problem there lies with freedb.org: EAC refuses to access the server database even though Grip can just fine, and EAC won't let me change the server to anything other than its malfunctioning list.  

So, is there anyone who can help me either: 

1) find an open source option for ripping and encoding perfect, lossless rips of my cds or 

2) get EAC to access something other than the address list that quite obviously doesn't work.

Someone's got to know something.  Please help, I'm at wit's end.

](*,)

---

### Post by hugmenot on 2008-02-24
Try RubyRipper.

---

### Post by hurtstotalktoyou on 2008-02-24
> **warbread said:**
> This has been eating me alive all weekend.  I'm wanting to re-encode all of my music into .flac.  Yes, I have the hardware to hear the difference .flac makes and yes, I think it sounds better than VBR .mp3 and 320kbps vorbis.  So far, Soundjuicer, Grip and ripperx have all failed me;  playing back their rips, I can hear pops and crackles.  I've even tried some  Windows solutions.  CDex failed me just as Grip and the others have.  The other was  EAC, but the problem there lies with freedb.org: EAC refuses to access the server database even though Grip can just fine, and EAC won't let me change the server to anything other than its malfunctioning list.  

So, is there anyone who can help me either: 

1) find an open source option for ripping and encoding perfect, lossless rips of my cds or 

2) get EAC to access something other than the address list that quite obviously doesn't work.

Someone's got to know something.  Please help, I'm at wit's end.

](*,)

It could be that it's your playback program which is whacked, and not the rippers.  For example, I've found VLC to render FLAC audio with crackles and skipping.  I usually use Winamp--obviously not possible with Ubuntu, unless perhaps you use Wine.  Try testing your rips this way:

1.  Install Audacity
2.  Rip an audio track to *.wav
3.  Encode that track to *.flac, but keep the original *.wav file, too
4.  Decode the *.flac file back to a second *.wav file
5.  Open the first *.wav file in Audacity
6.  Invert it
7.  Open the second *.wav file in Audacity (do not invert it or otherwise mess with it)
8.  Mix the second *wav and the inverted first *.wav down to a new waveform
9.  If that new waveform is blank (IE, completely silent), then your flac encoder is working fine

Otherwise, you can try [FLAC Frontend](http://downloads.sourceforge.net/flac/flac-1.2.1b.exe) in Wine.

EDIT:  In the mean time, or if you fail to ever get FLAC working, you can try alternative lossless formats such as SHN or WavPack.

---

### Post by warbread on 2008-02-24
Initial tests are promising, but I'm still having trouble with freedb.org.  Does anyone have any working database servers?

---

### Post by warbread on 2008-02-24
> **hurtstotalktoyou said:**
> It could be that it's your playback program which is whacked, and not the rippers.  For example, I've found VLC to render FLAC audio with crackles and skipping.  I usually use Winamp--obviously not possible with Ubuntu, unless perhaps you use Wine.  Try testing your rips this way:

1.  Install Audacity
2.  Rip an audio track to *.wav
3.  Encode that track to *.flac, but keep the original *.wav file, too
4.  Decode the *.flac file back to a second *.wav file
5.  Open the first *.wav file in Audacity
6.  Invert it
7.  Open the second *.wav file in Audacity (do not invert it or otherwise mess with it)
8.  Mix the second *wav and the inverted first *.wav down to a new waveform
9.  If that new waveform is blank (IE, completely silent), then your flac encoder is working fine

Otherwise, you can try [FLAC Frontend](http://downloads.sourceforge.net/flac/flac-1.2.1b.exe) in Wine.

EDIT:  In the mean time, or if you fail to ever get FLAC working, you can try alternative lossless formats such as SHN or WavPack.

Ah, yes.  I thought this myself, but Audacity plays the exact same errors that I get in AmaroK, RythymBox and even Totem.  Whether or not a Windows program can play it fine is not relevant to me since I use Linux as my main OS and prefer to not rely on proprietary software.  

Thank you for thinking outside the box, though.  This is the sort of help I need.

---

### Post by hugmenot on 2008-02-24
FreeDB seems to have problems at the moment. At least I cannot really reach the website.
Try again tomorrow?

---

### Post by oomingmak on 2008-02-25
> **hurtstotalktoyou said:**
> EDIT:  In the mean time, or if you fail to ever get FLAC working, you can try alternative lossless formats such as SHN or WavPack.
WavPack definitely gets the thumbs up from me.

It would certainly be worth a try if you're having no joy with FLAC.

[http://www.wavpack.com](http://www.wavpack.com)

---

### Post by cbrigstocke on 2008-06-10
I know this is an old thread, but did you enter in an email address in EAC?  You need one to access the database.

---

### Post by stchman on 2008-06-10
> **warbread said:**
> This has been eating me alive all weekend.  I'm wanting to re-encode all of my music into .flac.  Yes, I have the hardware to hear the difference .flac makes and yes, I think it sounds better than VBR .mp3 and 320kbps vorbis.  So far, Soundjuicer, Grip and ripperx have all failed me;  playing back their rips, I can hear pops and crackles.  I've even tried some  Windows solutions.  CDex failed me just as Grip and the others have.  The other was  EAC, but the problem there lies with freedb.org: EAC refuses to access the server database even though Grip can just fine, and EAC won't let me change the server to anything other than its malfunctioning list.  

So, is there anyone who can help me either: 

1) find an open source option for ripping and encoding perfect, lossless rips of my cds or 

2) get EAC to access something other than the address list that quite obviously doesn't work.

Someone's got to know something.  Please help, I'm at wit's end.

](*,)

All of the applications are going to use the same package for FLAC.  Sound Juicer uses a gstreamer command to RIP CDs for all music.


I have some pretty decent quipment and I cannot hear the difference between FLAC, VBR MP3, and OGG.  You must have the hearing of a beagle.

Since Windows does the same thing I guess you can say PCs fail at ripping CDs to FLAC to your discerning ear.

---

### Post by stchman on 2008-06-10
> **cbrigstocke said:**
> I know this is an old thread, but did you enter in an email address in EAC?  You need one to access the database.

I thought EAC uses LAME which is VBR MP3.

---

### Post by warbread on 2008-06-10
> **stchman said:**
> All of the applications are going to use the same package for FLAC.  Sound Juicer uses a gstreamer command to RIP CDs for all music.


I have some pretty decent quipment and I cannot hear the difference between FLAC, VBR MP3, and OGG.  You must have the hearing of a beagle.

Since Windows does the same thing I guess you can say PCs fail at ripping CDs to FLAC to your discerning ear.

It isn't just about the encoder, it's about how and what information gets to the encoder.  CDs spinning at 40-50 times what your car stereo or boom box does to read music data can easily result in erroneous chunks of information reaching the encoder.  My options are to 1) rip each cd at low speeds, resulting in hours of computer babysitting that I really don't want to do or 2) get a program that reads the information, compares it to what's on the cd and corrects errors.  Windows has such a program, as does Linux.

But your right, to ask if Linux is a failure is fallacious.  After all, even if there were no programs with decent error correction, that's not the kernel's fault.  There are plenty of programs that can read the data straight off of a cd, so it's not beyond what can be done in Linux.  Frustrated college students will say anything for attention, it seems.  

Anyways, RubyRipper is exactly what I needed.  I can encode my cds to totally lossless quality without the artifacts that SoundJuicer, K3B and the others introduced.  The difference between VBR, ogg and flac is subtle, and mostly not there.  I don't really have the ears of a beagle, just some descent monitors, a pair of expensive headphones and Meshuggah.  Most people would prefer ogg to flac for very good reasons, but I'm a perfectionist.

---

### Post by cozmicharlie on 2008-06-12
I'm with you warbread - the only way to listen to music is lossless and for me (and most audiophiles), flac is the codec to use.  I have over 2 TB of live music I downloaded (all lossless) so I needed a ripper/tanscoder that would handle flac and shn.  I found PACPL fits my needs.  It is command line but it is easy to use (I have written a How To on the forums).  It transcodes, rips, tags and it has a lot of codec options including shn and flac.  I have found the quality to be excellent and the developer is very good about responding to help questions and releasing updates.  If you are pleased with Ruby Ripper then by all means stick with it,  I just wanted to mention PACPL so folks know their are plenty of options in Linux for lossless music fans.

---

