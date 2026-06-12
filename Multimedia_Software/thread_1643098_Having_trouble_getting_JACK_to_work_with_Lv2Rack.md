---
title: "Having trouble getting JACK to work with Lv2Rack"
date: 2010-12-11
forum: Multimedia Software
---

### Post by anthony62490 on 2010-12-11
I installed the package "lv2vocoder" earlier today. After a bit of searching, I realized that lv2vocoder is only a plugin, so I also downloaded Lv2rack to run the plugin.

Also installed
Qjackctl
patchage

So now my setup looks like this:
[IMG]http://i30.photobucket.com/albums/c335/anthony62490/Anthony/vocoder.png?t=1292085506[/IMG]

The main problem I'm having is that I have no idea how to configure these to work together. I have found no documentation for any of these programs, so I'm not even sure if I have everything I need.

Does anyone here have experience with these programs?

---

### Post by cchhrriiss121212 on 2010-12-11
What it is you would like to achieve? For example if you want to record your voice with an effect on it you will also need a recording program like Ardour or Qtractor.

Jack works by allowing you to connect one audio signal to another, and this must be done manually. So for the example above you would connect things like this:

System Capture - lv2rack - Ardour

If you just want to hear your own voice with the effect, do this:

System Capture - lv2rack - System Playback

---

### Post by anthony62490 on 2010-12-11
I think for now I'd just like to hear the effect, so I set up the connections like so.
[IMG]http://i30.photobucket.com/albums/c335/anthony62490/Anthony/Screenshot-2.png?t=1292091971[/IMG]
Well, now what? I don't seem to have any program set up to capture or play any audio. 
Also, my knowledge of vocoders says that I also need a carrier sound to be mixed with the mic input. I assume that this is why lv2rack has 2 inputs and only 1 output.

---

### Post by cchhrriiss121212 on 2010-12-11
> Also, my knowledge of vocoders says that I also need a carrier sound to  be mixed with the mic input. I assume that this is why lv2rack has 2  inputs and only 1 output.
That's right. You can use a synth or something, there are plenty about in the repos (just search for synth). You could use a sound file as well, it is up to you.
> I don't seem to have any program set up to capture or play any audio. 
To hear sounds you don't need any extra program, whatever you connect to the playback ports will come out your speakers. Make sure your sounds levels are high enough using alsamixer. I already mentioned how to capture audio in the last post.

---

### Post by anthony62490 on 2010-12-11
Well, if I connect both capture_1 and capture_2 to a channel on lv2rack, I can get sound through the speakers, but there is still no carrier for the vocoder. The most I can do is mess with the band filters and cut out certain frequencies. 

What I would like to do is connect a MIDI keyboard (virtual) to the vocoder and control the carrier from there, but Patchage won't let me connect the keyboard program (vmpk) to the second vocoder channel.

I saw a few people say that in order to connect MIDI channels and audio channels, I would need a program called "a2jmidid". Downloading the program added 2 groups of red channels to Patchage, but they don't seem do do anything either.

EDIT: A sound file sounds quite a bit simpler. Only problem is, there is no place in any of these programs to specify a carrier sound. Playing the sound through VLC doesn't have any effect either. I would expect that while VLC is running, it should show up in Patchage as an available source of audio.

---

### Post by cchhrriiss121212 on 2010-12-11
The carrier signal must be audio, so you can't use MIDI. MIDI signals do not contain any sound, they are just patterns that require a synth or soundfont in order to make noise. 

What you need to do is connect your keyboard to a synth via MIDI, then connect the synth's audio output to the carrier input.

Edit: I have just tried testing the vocoder plugin and it does not seem very good at all. It is very poor quality sound and does not produce enough volume to be useful. If you can reproduce this on your machine I will look into filing a bug report.

---

