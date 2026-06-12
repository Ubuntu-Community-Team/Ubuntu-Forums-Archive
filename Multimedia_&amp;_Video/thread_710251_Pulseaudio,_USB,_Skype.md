---
title: "Pulseaudio, USB, Skype"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by mcarro on 2008-02-28
Hello, all.  I have a couple of questions about PulseAudio & Ubuntu 7.10 I have not seen answered.

The first one is related to Ubuntu & Skype.  After manually updating my /etc/asound.conf, the 'pulse' device appears in Skype.  While I can hear sound from Skype, when I speak the other party receives only fragmented sound, and from then on the sound I get from Skype is also very irregular, while the CPU usage goes up to nearly 100%.  I do not think it is due to lack of speed in my laptop.  Any idea of what may be happening and what could I do to solve it, or to get more information towards a diagnoses & solution?

The second question is related to USB.  I cannot get USB headphones work with PulseAudio.  I am not really sure where PulseAudio sits in the general audio system, but I would guess that it should be possible to redirect some application's sound to the USB audio subsystem (that'll be ideal), or, perhaps (and non-exclusively with the former), get all applications which select PulseAudio as sound server physically use USB.  But I cannot seem to find where this is to be activated.  I tried changing the default sound card in Gnome to no avail.  Any hint?

Thanks a lot in advance for any and all answers!

Best.

---

### Post by hyperair on 2008-02-28
Waaait a minute. You got Pulseaudio to work with Skype?!! Which version did you use?! As for USB audio... have you tried seeing if it appears in Pulseaudio's volume control as a sink?

---

### Post by mcarro on 2008-02-29
> **hyperair said:**
> Waaait a minute. You got Pulseaudio to work with Skype?!! Which version did you use?!

Yes, I've go PulseAudio work with Skype.  It's Skype 2.0 Beta (the latest as far as I know).  PulseAudio is 0.9.6-1ubuntu2 . There are instructions elsewhere to make PulseAudio and Skype work together: I just had to create (or edit) /etc/asound.conf to contain


[FONT="Courier New"]pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}[/FONT]

and then "pulse" appears among the devices Skype shows me.  I do not remember having done anything else.

> **hyperair said:**
> As for USB audio... have you tried seeing if it appears in Pulseaudio's volume control as a sink?

Arg!  You are right.  It is all so clearly written.  Shame on me.  Thanks a whole lot!

---

### Post by hyperair on 2008-02-29
That's exactly what I have too! What sound device did you choose in Skype?

Could you post the following output?
```
dpkg -l skype*
```

---

### Post by mcarro on 2008-02-29
> **hyperair said:**
> That's exactly what I have too! What sound device did you choose in Skype?

Could you post the following output?
```
dpkg -l skype*
```


A "pulse" device appears in Skype.  Forgot to mention: in my ~/.asoundrc the following lines appear, before including ~/.asoundrc.asoundconf

pcm.pulse { type pulse }
ctl.pulse { type pulse }


And, at the bottom of /.asoundrc.asoundconf the following two lines appear as well:

pcm.!default { type pulse }
ctl.!default { type pulse }

I suppose these should be redundant as /etc/asound.conf looks like a global config file, but I am not 100% sure.


$ dpkg -l skype*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  skype          2.0.0.43-0medi A VoIP software
ii  skype-common   2.0.0.43-0medi A VoIP software - common files
un  skype-static   <none>         (no description available)

---

### Post by hyperair on 2008-02-29
It works with the default device you say? O.o I've never managed to make it work! And I'm using the same version of Skype! Also, does it work with proper mixing and all? Like when music is playing.

---

### Post by 3togo on 2008-03-03
Have u tried?

pasuspender skype

---

### Post by hyperair on 2008-03-03
That's precisely what I DON'T want to do. Pausing Pulseaudio will defeat the purpose of having Pulseaudio and Skype together. I wanted mixing!

---

### Post by mcarro on 2008-03-11
> **3togo said:**
> Have u tried?

pasuspender skype

pasuspender is (afaik) not in the stable 7.10 Ubuntu distribution, and I would rather prefer not to start a (partial) upgrade since my system is right now in a very stable status - as stable as it has ever been.  If I want to do that, I just kill (by hand) the pulseaudio daemon, and I can restart it by hand as well.

However, what happens in my case is that I can hear Skype perfectly when pulseaudio is chosen as audio device.  Skype can record (i.e., register and send), too, but in this case audio is unclear and a bit garbled -- as if packets were being lost, which I do not think is the case, since I can hear myself perfectly in the echo test when pulseaudio is stopped and I use either a USB device or the audio device of the laptop.

One thing that I just realized is that when Skype opens the sound record device (the default in my laptop, not an USB device),  CPU usage goes to 100% and the CPU speed jumps to 1.8MHz (the maximum in my laptop).  May it just be that recording & mixing through PulseAudio is too much for my CPU?  I did not think so, bt maybe there is some options (buffer sizes, type of interpolation, whatever) which I can tweak.  I do not know whether this really makes sense,  but any hint would be appreciated.

---

### Post by hyperair on 2008-03-11
I'm talking something along the lines of Skype using Pulseaudio for mixing, such that I can hear my music from players which are using Pulseaudio at the same time.

---

### Post by mcarro on 2008-03-11
> **hyperair said:**
> As for USB audio... have you tried seeing if it appears in Pulseaudio's volume control as a sink?

Yes, it does.  That is great, thanks.  I can redirect sound output to m headset by clicking on it with the left mouse button.  But, is there any way to redirect the sound input from the USB headset mic to Skype?

---

### Post by udude on 2008-03-12
I don't think that the problem is skype specific. 
I've noticed that with pulseaudio installed, even the voice recording app doesn't work well.
i.e. start applications->sound&video->SoundRecorder record voice and listen to result.

Does the sound recorder work well for anyone who installed pulseaudio?
How about systems with usb-headset?

---

### Post by hyperair on 2008-03-13
Sound Recorder works well for me. If I'm not mistaken, you need to configure GStreamer to use Pulseaudio. Then Sound Recorder should work well. This problem here is that Skype's ALSA libraries refuse to properly use Pulseaudio's plugin, and it does not support Pulseaudio natively.

---

### Post by udude on 2008-03-14
> **hyperair said:**
> Sound Recorder works well for me. If I'm not mistaken, you need to configure GStreamer to use Pulseaudio. Then Sound Recorder should work well. This problem here is that Skype's ALSA libraries refuse to properly use Pulseaudio's plugin, and it does not support Pulseaudio natively.

Interesting... so, if I understand correctly - skype 2.x does not require the gstreamer pulseaudio plugin (gst-pulse...)?

I am assuming you are running 8.04 and therefore have the plugin installed.
I'm running 7.10 here and noticed that the plugin depends on packages with higher version numbers then those used by 7.10. Anyone knows if installing the plugin on a 7.10 can be performed without severe bleeding? Perhaps I should just abandon the idea of using 7.10 and switch to 8.04...

---

### Post by hyperair on 2008-03-14
Skype is not related to gstreamer in any way. Gst-Pulse is only for gstreamer applications. Also, yes I am running 8.04. However, I wouldn't recommend switching to 8.04 just yet. Just last night I got hit by one hell of a bug in glibc and lost the ability to boot into my system as well as to chroot into the system from a LiveCD. Needless to say, without very specific instructions, I didn't know how to fix my system. >.<

---

### Post by mcarro on 2008-03-18
> **udude said:**
> I don't think that the problem is skype specific. 
I've noticed that with pulseaudio installed, even the voice recording app doesn't work well.
i.e. start applications->sound&video->SoundRecorder record voice and listen to result.

Does the sound recorder work well for anyone who installed pulseaudio?
How about systems with usb-headset?

I do not know if this is going to help, but I have a mostly working setup for pulseaudio + skype by adjusting /etc/asoundrc as advised in many places (see before in this thread) + editing /etc/pulse/daemon.conf so that

high-priority = 1
no-cpu-limit = 1

This gives a somewhat better sound when I speak - not as clear as when the alsa driver is directly used, though.  I suppose that this means that the amount of CPU that pulseaudio needs in my case (a thinkpad T40 with a pentium M @ 1.6GHz) is more than what the default setup gives.  It may be the case that other people are using faster machines and therefore they do not need this tuning.

On the other hand, and if this is so, maybe pulseaudio needs some parts compiled with specific flags, or even coded in assembler used SSE instrutions for the Intel family, assuming this is not already done?

Cheers.

---

