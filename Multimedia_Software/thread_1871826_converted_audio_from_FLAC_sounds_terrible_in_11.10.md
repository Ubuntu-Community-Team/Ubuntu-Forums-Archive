---
title: "converted audio from FLAC sounds terrible in 11.10"
date: 2011-10-29
forum: Multimedia Software
---

### Post by deruberhanyok on 2011-10-29
Whenever I get a new CD I rip it to FLAC then convert it to OGG ("Very High") or MP3 ("Very High" VBR) for use on portable devices.

Most of my audio library was converted in 10.10 / 11.04, but I just got a new CD and noticed the OGG sounded pretty bad. Same with MP3 format. There's popping and stuttering all over the place.

I checked the FLAC rip of the disc - it sounds perfect.

I decided to take a song I'd converted to OGG using 11.04 and compare the previous conversion to one performed using 11.10. Sure enough, the conversion performed on 11.10 has popping and stuttering that doesn't exist on the one performed on 11.04.

I'm using the "sound converter" program from the Ubuntu Software Center.

Any ideas what could be the cause? I was hoping to maybe narrow down things a little bit before submitting a bug report.

---

### Post by tartalo on 2011-10-29
There are a couple of bugs open in soundconverter that describe a similar problem, the work around they recommend is opening soundconverter with: 
```
soundconverter --jobs=1
```

The bugs:
[https://bugs.launchpad.net/soundconverter/+bug/721574](https://bugs.launchpad.net/soundconverter/+bug/721574)
[https://bugs.launchpad.net/soundconverter/+bug/508767](https://bugs.launchpad.net/soundconverter/+bug/508767)

---

### Post by qyot27 on 2011-10-29
Use FLAC to decode and pipe to either LAME or oggenc.  Or ffmpeg, if you don't want to mess with piping stuff (just make sure ffmpeg has libmp3lame and/or libvorbis support compiled in).

```
sudo apt-get install lame flac vorbis-tools
```

And then, for MP3:
```
flac -c -d filename.flac | lame [options] - filename.mp3
```
or Vorbis:
```
flac -c -d filename.flac | oggenc [options] filename.ogg -
```
(replace [options] with the relevant settings you prefer)

There's probably a GUI frontend that would make this easier for the non-Terminal-inclined, but basically, just decode/encode the stuff directly by using the format-specific tools.

---

### Post by deruberhanyok on 2011-10-31
Awesome, thanks for the info guys.

---

