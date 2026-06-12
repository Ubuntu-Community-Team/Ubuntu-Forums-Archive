---
title: "Configuring a microfone to use an other soundcard than the one used for playback"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by mattegeniet on 2007-06-04
Hi! I've been trying to configure my sound cards correctly, but got into some trouble, since there are more than one 'em (two in fact). The first one is a SB 7.1 live! 24 bit, using the driver CA0106. The second one is integrated in on the motherboard. I've got to few ports on my SB live, and that's why I have to connect my microphone to the one on the motherboard. 

I've finally managed to get the SB one to always be card0, and playback works fine, but when I try to use my microphone it doesn't work. If I start the sound recorder and try to say something in the microphone, and then try to listen to the recording, it doesn't want to play anything (suppose this is because it didn't capture anything). 

One the other hand, if I start Audacity and try to record something, I can see that something is captured from the microphone, but when trying to play it, I get an error message saying "Error when trying to start audio device. Please check the outputs of the device and the projects sampling frequency." (Probably not exactly like that, since I translated it from Swedish.) If I check the preferences for the program, it says that the device used for recording is "OSS: /dev/dsp1", which is weird, since I use ALSA... On playback, there are lots of devices to choose from, among them three different CA0106 cards (hw:0,1; hw:0,2; hw:0,3). There's also things like ALSA: rear, ALSA:  center_LFE and ALSA: side. 

On the top of the list there's also an alternative for OSS, and when using this setting, it's possible to play the recording, but I don't get any sound...

So there's a couple of questions:
[LIST]
[*]What device should I choose for recording in System -> Preferences -> Audio?
[*]Why doesn't the audio recorder play my recordings, even if they are empty?
[*]Why does Audacity use an OSS driver?
[*]Why does it work with the OSS device, but not with any of the other ones?
[*]Which device should I use, and how to get it work?
[*]Why doesn't the ca0106 device work in audacity?
[/LIST]

I'll post the outputs of aplay -l and cat /proc/asound/modules here:

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Underordnade enheter: 0/1
  Underordnad enhet #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
card 1: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
card 1: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
```

cat /proc/asound/modules:
```
 0 snd_ca0106
 1 snd_intel8x0

```

Very thankfull for any kind of help or even explanations of some of the problems:D

---

### Post by sensimilla on 2007-06-07
Hello 

I have almost the same 2 cards as you, same drivers anyway. I have been googling around for the last few days trying to set  the default capture device to be different from the default playback device under alsa. This is because I want to use a couple of apps that use the alsa default capture device and to actually have a working microphone.

I found a .asoundrc that  sets up a 'virtual sound card' called duplex, which will use the output of one card and the input of another and set it to be the alsa default. This seems to be working for me although I haven't fully tested it with OSS or anything yet


I found it on [http://alsa.opensrc.org/Intel8x0]("http://alsa.opensrc.org/Intel8x0") near the bottom labeled as Fujitsu Siemens Lifebook E8020 intel8x0 + snd-usb-audio. I think it will work with any 2 sound cards.
```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card0 {
     type hw
     card 0
     device 0
}

pcm.snd_card1 {
     type hw
     card 1
     device 0
}

# Allow mixing of multiple output streams to this device
pcm.output {
     type dmix
     ipc_key 1024
     ipc_perm 0660 # Sound for everybody in your group!
     slave.pcm "snd_card0"

     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 8192
          # buffer_size 4096
          # buffer_size 2048
     }

     bindings {
          0 0
          1 1
     }
}

pcm.input {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card0"

## Possible artsd full duplex fix:
#     slave {
#          period_time 0
#          period_size 1024
#          buffer_size 8192
#     }

     bindings {
          0 0
          1 1
     }
}
# Allow reading from the default device.
# Also known as record or capture.
pcm.input1 {
     type dsnoop
     ipc_key 2049
     slave.pcm "snd_card1"

## Possible artsd full duplex fix:
     slave {
          period_time 0
          period_size 1024
          buffer_size 8192
          # buffer_size 4096
          # buffer_size 2048
     }

     bindings {
          0 0
          1 1
     }
}
# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "output"
     capture.pcm "input"
#     capture.pcm "input1"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).
pcm.!default {
     type plug
     slave.pcm "duplex"
}
########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "output"
}

#
pcm.dsp1 {
     type plug
     slave.pcm "output1"
}
```

In sound preferences you can set default sound capture as ALSA I always got an error before when doing this, I think maybe the CA0106 drivers have some problems with sound capture.

I have never got sound recorder to work at all seems like it is buggy at best. You can test if your capture is working with: 

**# arecord -f dat tester.wav ** 
and
**# aplay tester.wav**

There also a little program in the applications menu called Recording Level Monitor, though I think it may be hidden by default, which shows you activity on the default capture channel.

In Audacity try setting the **project rate:** to **48000**. You can change it permanently in the preferences. Set the playback and recording device to be  **ALSA : duplex ** this will then use the default device(s) set up in the .asoundrc file. Or you can set it to use directly for playback the CA0106 by selecting the (hw:0,1) likewise you can set the recording device directly by choosing something like (hw:1,1) labeled as the other card.
Make sure that the correct input is selected for capture on your Intel8x0 card and that it is not muted or low using the volume control mixer or if this is tricky use:

**# amixer -c1 cget name='Capture Source'**  
to view the capture settings on the second card and something like

**# amixer cset name='Capture Source' 0,0**
to set which input to use.

I has taken me 2 months to get my sound working almost how I want it :) . I wish there was an easier way :( 
I hope this helps, Good Luck

---

### Post by offchance on 2007-09-07
I've got almost the same problem. setting oss in sys>pref>sound got me some response in audacity, but no playback.  did the multiplexing suggestion work for anyone?

```
damion@deck:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
damion@deck:~$ 
```

---

### Post by SyncMaster on 2007-11-18
Hi, 
I need to run  asoundconf to fix the default soundcard (asoundconf list, etc)

But I still could only play back and not record. But this I solved by enabling Microphone Capture (and Mic Boost) in the Volume Control (Edit > Preferences, Microhphone,)
Close this and go to Switch and enable the two new options...

In fact I still have no clue which device is meant by "capture" in the "Sound Recorder". Skype and Audacity use different names, which made more sense.

I could imagine the two switches should be on by default, but I dont really understand the whole sound thing, I just wanted to use skype....

Rainer

---

