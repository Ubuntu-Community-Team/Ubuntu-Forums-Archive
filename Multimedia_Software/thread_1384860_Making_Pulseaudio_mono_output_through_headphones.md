---
title: "Making Pulseaudio mono output through headphones"
date: 2010-01-18
forum: Multimedia Software
---

### Post by Windows Nerd on 2010-01-18
So, as the question suggests, I wish to make pulseaudio output Mono sound through the headphones. To be more specific:

I am deaf in one ear. When I listen to sound through headphones, I can only hear the L or R earbuds, not both. For some songs this is okay, as the same sound is output through the both earbuds. But for some songs (notably ones recorded a longer time ago) the sound is thus: I can hear the lyrics through one earbud nice and loud and clear, but everything else _very faintly_ (or possible one of the instruments such as the bass guitar), and it is the other way around in the other way around. This is extremely annoying, especially if I am listening to the Beatles (many of thier songs play in this fashion). I know listening through the speakers solves this problem, but my laptop speakers are not the greatest quality, hence why I use headphones.

Is there a way, through Pulseaudio, or some other program, or through any other method you could imagine, to solve this?

Thanks in advance,

Scott

---

### Post by VertexPusher on 2010-01-19
It is possible to configure ALSA to mix all audio down to one channel before sending it to the sound card. Note however that a lot of today's music is not mono-compatible, i.e. when the two stereo channels are mixed into one, some signals from the left and right will cancel each other out and become inaudible. I guess the best solution is to reduce the width of the stereo signal, i.e. simulate some degree of cross-talk between the channels. The result will not be entirely mono, but there will be no complete separation between the left and right channel either. This should be acceptable for both old and new recordings.

The first thing you'll have to do is get rid of PulseAudio:

```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```

Then you'll need to put the following configuration file into your user home directory. Save it as ".asoundrc":
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type route
            slave.pcm "dmix:0"
            ttable.0.0 0.66
            ttable.0.1 0.33
            ttable.1.0 0.33
            ttable.1.1 0.66
        }
        capture.pcm "hw:0"
    }
}
```
Log out and log in again, then open a terminal window and run the following test:

```
speaker-test -t wav -c 2
```

This will play back two sound clips ("front left" and "front right"). You should be able to hear both clips on either channel, with one being slightly louder than the other.

---

### Post by Windows Nerd on 2010-01-21
Will the method you suggested lower the quality of sound much? I make it important that I listen to music through headphones because my speakers are poor laptop quality. If the method you suggested lowers my sound quality, I would just rather play it through my speakers without much hassle.

---

### Post by VertexPusher on 2010-01-22
No, it won't affect sound quality.

If you are not happy with the result, just delete the .asoundrc file and run this command:
```
sudo apt-get install ubuntu-desktop
```This will restore PulseAudio and any other package that was removed in the process.

However, I doubt that there is a way to configure channel crosstalk in PulseAudio.

By the way, you can control the amount of crosstalk by modifying the ttable lines in the file. For example,
```
ttable.0.0 0.5
ttable.0.1 0.5
ttable.1.0 0.5
ttable.1.1 0.5
```
will produce 100% cross-talk, i.e. the result will be mono. Likewise,
```
ttable.0.0 1
ttable.0.1 0
ttable.1.0 0
ttable.1.1 1
```
will result in full channel separation, i.e. stereo. You can choose any values between 0 and 1. Just make sure that the sum per channel does not exceed 1, otherwise the mix will be too loud and clipping may occur.

---

### Post by RedfishBluefish on 2010-04-26
Oh hey, I was looking to do the same thing, and I found this thread.

In fact you **can** make pulseaudio mix the left and right channels to mono, with module-remap-sink. For example, by a magic incantation such as this:

```

load-module module-remap-sink sink_name=mono master=<the name of your main output sink> channels=4 channel_map=left,right,left,right master_channel_map=left,left,right,right

```

you can create a virtual sink which mixes both left and right into both left and right channels in the output sink. You'll have to reduce the volume (put a gain of 0.5 on it), though, or else you might get clipping, since the left and right channels are just being added, doubling the volume.

---

### Post by 5349U11 on 2010-05-11
> **RedfishBluefish said:**
> Oh hey, I was looking to do the same thing, and I found this thread.

In fact you **can** make pulseaudio mix the left and right channels to mono, with module-remap-sink. For example, by a magic incantation such as this:

```

load-module module-remap-sink sink_name=mono master=<the name of your main output sink> channels=4 channel_map=left,right,left,right master_channel_map=left,left,right,right

```you can create a virtual sink which mixes both left and right into both left and right channels in the output sink. You'll have to reduce the volume (put a gain of 0.5 on it), though, or else you might get clipping, since the left and right channels are just being added, doubling the volume.

is there any way to make this only apply when a hot key is pressed?

---

### Post by Darxus on 2011-08-28
> **RedfishBluefish said:**
> 
```

load-module module-remap-sink sink_name=mono master=<the name of your main output sink> channels=4 channel_map=left,right,left,right master_channel_map=left,left,right,right

```
This worked wonderfully for a while.  Recently it stopped working.  When I select it, I get no sound.  The master sink it uses is still working fine.  Any tips on debugging would be appreciated.  For those still trying to figure out what goes in master=, you can get a list of options by running ```
pacmd list-sinks | grep master
```

In the mean time I've found a much simpler solution to get mono output when using mplayer:  Just add the argument "-channels 1" to the mplayer command line.  It causes mplayer to ask the audio decoder to return a single audio channel.  

Now if only pulseaudio could just give me a check box to do this.

---

