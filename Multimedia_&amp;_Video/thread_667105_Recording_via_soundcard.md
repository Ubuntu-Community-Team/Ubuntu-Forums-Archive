---
title: "Recording via soundcard"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by boobahzone on 2008-01-14
I'm looking to find a way to record the audio from my computer into an .ogg or .mp3 file in order to record things like radio shows that might be presented as an audio stream or flash file.  After searching the web for solutions to this problem, I've found a few options that were available, none of which work.  Is there a simple way I can record from the sound card?  I should mention that I am somewhat new to Ubuntu and Linux, but eager to learn and to take advantage of all that Linux has to offer over a Windows/Mac environment.

Here are some of the options I've tried:

**Audacity**
I've read that Audacity will record from the sound card, which is exactly what I wanted.  I downloaded Audacity and under Edit > Preferences  changed the recording Device to "OSS: /Dev/dsp" and channels to "2 (Stereo)".  However, when I have an audio file playing via Firefox (or even in Rhythmbox) and go to record in Audacity, it just records silence.  I've read that "OSS: /Dev/dsp" is the right setting for this procedure, but perhaps the device is set to record from another device besides my sound card?

**sox/"rec" command**
Next, I installed sox and ran the "rec" command to record from the sound card.  Similar to what Audacity did, the command simply recorded pure silence rather than any audio which was playing on my computer at the same time.   Again, could this device be set to record from some other device besides my soundcard?

Here is the command line output, just in case anyone was wondering:
```
kevin@kevin-desktop:~$ rec test2.ogg

Input File     : 'default' (alsa)
Sample Size    : 16-bit (2 bytes)
Sample Encoding: signed (2's complement)
Channels       : 1
Sample Rate    : 48000

Time: 00:07.21 [00:00.00] of 00:00.00 (  0.0%) Output Buffer: 346.11K
Skipped.

Done.
```

**"arecord" command**
I am new to Ubuntu and didn't exactly understand what this command did, where it saves the data, or how it starts/stopping recording, etc. but I ran a "$ arecord -f cd -t raw | lame -x- out.mp3" command which I got online and said it was supposed to record.  This may or may not have worked, but I don't know how to read the output or know where the file would be.  

Here is the command line I ran for this:
```
kevin@kevin-desktop:~$ arecord -f cd -t raw | lame -x- out.mp3
lame: unrec option -
LAME 32bits version 3.97 (http://www.mp3dev.org/)

usage: lame [options] <infile> [outfile]

    <infile> and/or <outfile> can be "-", which means stdin/stdout.

Try:
     "lame --help"           for general usage information
 or:
     "lame --preset help"    for information on suggested predefined settings
 or:
     "lame --longhelp"
  or "lame -?"              for a complete options list

Recording raw data 'stdin' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
```

Also, I've looked into StreamRipper but since not all of the audio I'd like to record is in streaming audio, I figured this might not be an appropriate option.

Does anyone have any advice as to how I can record the audio or what I might be doing wrong in any of these methods I've tried?  

Thanks for any help!

---

### Post by ron999 on 2008-01-14
Hi
**arecord** works for me.
This is the command to use:-
```
arecord -f cd -t raw|lame -x - output.mp3
```
It puts a file named output.mp3 in your home area.

This is where I got my information:-[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")

Recording as mp3 doesn't work well for me, it 'skips'.
I prefer to record as wav then convert to mp3 afterwards. The wav file is huge!
To record as wav use this instead:-
```
arecord -f cd output.wav
```
8)
PS Your original command is correct, but you've put spaces either side of the pipe symbol by mistake. And one of the minus signs is in the wrong place.

---

### Post by boobahzone on 2008-01-14
Aha!  The website you posted worked exactly for what was the missing piece in what I was doing.  Thanks!  Also, I will try doing the .wav recording for better quality as well, very good idea.

Thanks again

---

### Post by boobahzone on 2008-01-14
Quick question:  When you use arecord without specifying a length of time to record (e.g., 10 seconds) how do you kill/interrupt the recording?

Thanks!

---

### Post by ron999 on 2008-01-14
Hi
I don't know if there is a 'correct' way to halt the recording.
I just close the monitor window.

---

