---
title: "OBS Studio"
date: 2020-11-29
forum: Multimedia Software
---

### Post by cybrsaylr on 2020-11-29
Installed OBS today. Learning it but can't get any audio to play? 
Running Ubuntu 18.04 LTS.
How do you turn on the audio?

---

### Post by TheFu on 2020-11-29
Unfortunately, you haven't provided sufficient details about what you've attempted for anyone to help.  For all we can tell, you don't have it pointing to use PulseAudio
or
haven't pressed the "monitor" button
or
haven't setup an audio input stream so there isn't any audio available in the current project
or
have the system audio muted.

Or something completely else. Are you recording, live streaming? Which inputs are being used? Are those active? We can't tell and can't read your mind. Should we keep guessing?

OBS is pretty complex. I find watching a YT video about using it helpful when the online documentation isn't sufficiently clear to me.

---

### Post by cybrsaylr on 2020-11-29
Yes OBS is quite complex.

Discovered when drag and dropping a video file to work on while watching it, there is no sound. However when opening up that file after it being converted to a MKV file, audio on it does play and work. As I said this is the first time trying OBS out. Will check out YT which usually is a great help for things like this.

OBS gives you several choices for formats to save videos to. MP4, MKV, etc. Which is the best to use, as I plan using OBS to convert old home movies VHS analog tapes to digital files, on external SSDs or flash drives?

---

### Post by TheFu on 2020-11-29
> **cybrsaylr said:**
> OBS gives you several choices for formats to save videos to. MP4, MKV, etc. Which is the best to use, as I plan using OBS to convert old home movies VHS analog tapes to digital files, on external SSDs or flash drives?

avi, mp4 and mkv are just containers.  mp4 can hold limited types of video and audio encoded data. mkv can hold anything - literally.  You can put videos from 1995 into an MKV container or you can put the latest vp10 from google into it.

With VHS, the resolution will be low - something around 400i - 360i is more likely. For that type of video, I'd use xvid or divx for the video encoding.  Non-HD content compresses better that way.  As for audio encoding, there are lots of choices, but the players (hardware and software types) are usually the limiting factor.

Hardware decoders often only support very specific pairings of video and audio codecs - so DivX would be paired with either mp2 audio or mp3 audio. BTW, DivX and xvid are almost the same - 50:50 for either.  xvid is F/LOSS, if you care. I happen to have a video recording device that makes divx files.  I used it to convert all my VHS tapes years ago. It is a ConvertX PX-M402U.

Think I put all those videos into an AVI container with DivX video and mp3 audio. 
Today, I'd probably use DivX video, vorbis audio (though VHS audio is terrible) and mkv for the container.

---

### Post by cybrsaylr on 2020-11-30
TheFu

Thanks for all the helpful info.

---

