---
title: "Multiple Sound Cards and Routing"
date: 2013-02-19
forum: Multimedia Software
---

### Post by HaasEffect on 2013-02-19
Hi,

I'm new to ubuntu/linux and am trying to come up with a solution for the following problem. But first I'd like to describe what I'm trying to achieve. Basically I'd like to record something via a microphone on soundcard A and output it immediately on soundcard B. I'd prefer to do that with gstreamer.

My setup:

I have two sound cards (one internal on board card and one sound blaster usb dongle). Both cards are being recognized:

```
user@pc:~/Desktop $ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7f30000 irq 51
 1 [Pro            ]: USB-Audio - Sound Blaster X-Fi Go! Pro
                      Creative Technology Ltd Sound Blaster X-Fi Go! Pro at usb-0000:00:14.0-2, full 

```



```
user@pc:~/Desktop$ aplay -l
**** list of hardware-devices (PLAYBACK) ****
Card 0: PCH [HDA Intel PCH], device 0: ALC886 Analog [ALC886 Analog]
  Sub-devices: 1/1
  Sub-devices #0: subdevice #0
Card 1: Pro [Sound Blaster X-Fi Go! Pro], device 0: USB Audio [USB Audio]
  Sub-devices: 1/1
  Sub-devices #0: subdevice #0
user@pc:~/Desktop $ 
```

So I guess they've been recognized by ALSA. I also ran the tests for each card in ubuntu's Audio settings - which works. I went ahead with a little test and took a wave audio file and tried to play it back on each card using the following command:

```
aplay -d 'hw:0,0' audio.wav // play back on internal sound card
aplay -d 'hw:1,0' audio.wav // play back on usb sound card
```

Now, this is where the troubles start. The device parameter 'hw:0,0' and 'hw:1,0' seems to have no effect on which card should be used. The sound comes always out of the most lately selected sound card in the audio settings panel. 

To me this looks like that ALSA is using only one soundcard - depending on which got selected the last. But I have to use both simultaneously. 

In the end I'd like to be able to do something like this:
```
gst-launch-0.10 alsasrc device='hw:1,0' ! queue ! alsasink device='hw:0,0' // hope this pipeline is correct
```

Any idea how to solve this?

Thanks in advance!

---

### Post by gordintoronto on 2013-02-19
What version of Ubuntu are you using? There have been significant changes to the sound user interface from version to version, which makes this question important.

Pulseaudio controls sound. Click on the sound icon and select Sound Settings. Tell us what you see in the Input and Output tabs.

---

### Post by HaasEffect on 2013-02-19
Hi, 

thanks for your help! I'm using Ubuntu 12.04 LTS. I see the following information in the sound settings:

Output:
1) Digital Output (SoundBlaster X-Fi Go! Pro)
2) Analog Output (SoundBlaster X-Fi Go! Pro)
3) Analog Output (internal audio)

Input:
1) iec958-stereo-input (SoundBlaster X-Fi Go! Pro)
2) Microphone (SoundBlaster X-Fi Go! Pro)
3) Microphone (internal audio)

As mentioned before the system seems to use the sound card selected in the sound settings.

I guess Pulseaudio is one option out of many (ALSA, OSS, etc.). But if it suits the task I'm trying to achieve I don't really care which option gets the job done.

Thanks again!

---

### Post by gordintoronto on 2013-02-19
If you select the appropriate input and output, does it do what you want?

---

### Post by HaasEffect on 2013-02-19
Well, I'm able to record something with the microphone and play it back in real-time on the same (selected) audio interface. Like this for example:

```
gst-launch-0.10 alsasrc device='hw:0,0' ! queue ! alsasink device='hw:0,0'
```

But if I want to record something on the first audio interface and play it back on the other like this:

```
gst-launch-0.10 alsasrc device='hw:0,0' ! queue ! alsasink device='hw:1,0'
```

it doesn't work. What it does now is  that it's being recorded and played back on the selected audio interface. This means, that somehow the "hw:1,0" and "hw:0,0" is being ignored.

---

### Post by HaasEffect on 2013-02-20
How about JACK? Could this solve my problem? Thanks.

---

### Post by Yellow Pasque on 2013-02-20
Try suspending pulseaudio temporarily when doing this.
```
pasuspender bash
```
Then, run your commands. Joy?

---

### Post by HaasEffect on 2013-02-20
Thanks Temüjin! This fixed the problem. Can you explain why this is the case? How did Pulseaudio interfere? Should I just deinstall pulseaudio or is it that necessary?

---

### Post by Yellow Pasque on 2013-02-20
No, don't remove pulseaudio (you'll break a bunch of stuff). There's probably a way to accomplish what you want using pulseaudio, like using gst pulsesrc/pulsesink, and getting the device names from:
```
pactl list short sinks
pactl list short sources
```

---

### Post by HaasEffect on 2013-02-22
Thanks for the pulseaudio advice. All my questions were answered and the thread can be closed now.

---

### Post by Yellow Pasque on 2013-02-23
While searching for another issue, came across:
[http://www.freedesktop.org/wiki/Software/PulseAudio/FAQ#How_do_I_connect_an_input_source_to_an_output_sink.3F](http://www.freedesktop.org/wiki/Software/PulseAudio/FAQ#How_do_I_connect_an_input_source_to_an_output_sink.3F)

---

### Post by cladisch on 2013-03-04
> ```
aplay -d 'hw:0,0' audio.wav // play back on internal sound card
aplay -d 'hw:1,0' audio.wav // play back on usb sound card
```
The option for specifying the device is not [FONT=Courier New]-d[/FONT] but [FONT=Courier New]-D[/FONT].

---

