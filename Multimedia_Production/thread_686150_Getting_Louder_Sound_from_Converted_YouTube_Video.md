---
title: "Getting Louder Sound from Converted YouTube Video"
date: 2008-02-02
forum: Multimedia Production
---

### Post by SuperMike on 2008-02-02
I grab a YouTube video for my wife so that she can show math videos in class. I use the technique where I copy it from /tmp/Flash* to ~/mymovie.flv, then run it through ffmpeg like so:

ffmpeg -i ~/mymovie.flv ~/mymovie.wmv

Unfortunately she reports that the sound is too dim. So I started looking around and I think people use **mencoder** to give the audio some gain (aka volume). However, this is incredibly complex for me to understand the command and my attempts at it failed.

I give up. What's the trick to simply take an FLV or WMV file and increase the sound at command line, saving the video as another FLV or WMV file?

---

### Post by SuperMike on 2008-02-03
Okay, I found something with a lot of tinkering. If you have a WMV file that you've converted from a YouTube FLV like so:

ffmpeg -i ~/mymovie.flv ~/mymovie.wmv

...then you can increase the volume like so:

mencoder mymovie.wmv -o mymovie.avi -oac mp3lame -ovc copy -ofps 30 -af channels=1 -lameopts mode=3:cbr:br=64:vol=3 -srate 22050

Okay, but here are the catches. I haven't figured out how to get mencoder to save in WMV format instead of AVI. As well, if you go much higher than vol=3, you'll end up with distortion especially on loud pounding sounds like rock music, bass guitar, or loud drum. However, vol=3 does increase the sound a little.

Note that the above command works with mono video like you have on YouTube, if you want it for stereo, then you'll probably (AND THIS IS A GUESS) want to make it like:

mencoder mymovie.wmv -o mymovie.avi -oac mp3lame -ovc copy -ofps 30 -lameopts cbr:br=64:vol=3 -srate 22050

Anyway, I'm off and running with this, but if you have suggestions on increasing the sound more than 3 without adding much distortion, or saving in WMV format instead of AVI, let me know.

As for the proprietary video formats, realize that we use Ubuntu to do the conversion, but at her school she uses a SmartBoard that only works with Windows and we're not permitted to install anything extra on her school computer in the form of software. (Doesn't that suck?)

---

### Post by eye208 on 2008-02-03
Use the **-af volnorm** or **-af comp** audio filters. From the MEncoder manual:
> **volnorm[=method:target]**
Maximizes the volume without distorting the sound.
*<method>*
Sets the used method.
1: Use a single sample to smooth the variations via the standard weighted mean over past samples (default).
2: Use several samples to smooth the variations via the standard weighted mean  over  past  samples.
*<target>*
Sets the target amplitude as a fraction of the maximum for the sample type (default: 0.25).

**comp**
Compressor/expander filter usable for microphone input.  Prevents artifacts on very loud sound  and  raises the volume on very low sound. This filter is untested, maybe even unusable.

---

