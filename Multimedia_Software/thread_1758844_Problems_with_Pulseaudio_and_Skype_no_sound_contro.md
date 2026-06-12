---
title: "Problems with Pulseaudio and Skype: no sound control following ununstall of Pulse??"
date: 2011-05-15
forum: Multimedia Software
---

### Post by koraghallaigh on 2011-05-15
I'm new to Ubuntu 11.04 and had no mic capability when I was using Gmail chat or Skype. I followed these instructions:

[https://support.skype.com/en/faq/FA10964/How-can-I-adjust-my-audio-settings-to-run-Skype-for-Linux;jsessionid=C5E8BEA39298B543C34B37D6E080A217?frompage=search&q=ALSA&fromSearchFirstPage=false](https://support.skype.com/en/faq/FA10964/How-can-I-adjust-my-audio-settings-to-run-Skype-for-Linux;jsessionid=C5E8BEA39298B543C34B37D6E080A217?frompage=search&q=ALSA&fromSearchFirstPage=false)

After that my mic is now working. 

In the interim I also installed ALSA. 

The problem is now that I have no volume control. So when I'm on skype, I cant raise or lower the volume and if I'm listening to music online or watching tv, the only volume control I have is if the programme has its own one. This is obviously a bit shite.

ALSA vol controls dont seem to have any effect now, so although I've regained my mic I cant actually control any volume!

The sound icon on the panel is just '---' and when I click 'sound preferences it says 'waiting for sound system to respond'.

I dont know how to go about fixing this or reinstalling Pulse. Can someone help?!

---

### Post by norm.h on 2011-05-16
I don't know about the most recent versions, but my experience is that Pulse Audio and Skype don't get on.
I had to disable Pulse Audio (because of a Skype echo problem), and lost my panel volume control.

Go to Synaptic Package Manager and type *volti* in the search box, and install it. 
Then you'll find it in the Sound & Video menu. Right click and then click "add to panel"

Volti will give you a volume control, and allow you to choose between its own or the ALSA mixer. 

I found it helpful to make a note of both mixers default settings so its easier to reset if you run into problems.

I think that "waiting for sound system to respond" is because PA is disabled.

---

### Post by russelld on 2011-11-16
This is what worked for me!

**Remove pulseaudio**

```
$ sudo apt-get remove pulseaudio
```

**Then ran gstreamer-properties from a xterm**

```
$  gstreamer-properties 
```

**Then tested the output and input**

Then went to Skype > Options > Sound Devices
tested the default setting in Skype, then changed the default to the same settings as found to work in gstreamer-properties.

The working setting in gstreamer-properties was in the box called "pipeline" 
In my case for the microphone 
```
alsasrc device="hw:0,0"
```

**And then select the device in Skype with the same setting**.
In this case:  
```
HDA Intel: AD198x Analog (hw:0,0)
```

see screenshot here:

[[IMG]http://i.imgur.com/3chKL.png[/IMG]](http://imgur.com/3chKL)

now I can make Skype calls and be heard!! :guitar:

---

