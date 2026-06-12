---
title: "[pulseaudio] how to play audio on two network devices simultaneously"
date: 2008-11-16
forum: Multimedia Software
---

### Post by nightfrost on 2008-11-16
Does anyone know how one goes about configuring pulseaudio to play audio on two sinks simultaneously?

I found [this]("http://www.pulseaudio.org/wiki/FAQ#CanIusePulseAudiotoplaybackmusicontwosoundcardssimultaneously") on the Pulseaudio FAQ:

> Can I use PulseAudio to playback music on two sound cards simultaneously?

    Yes! Use module-combine for that.

    load-module module-oss-mmap device="/dev/dsp" sink_name=output0
    load-module module-oss-mmap device="/dev/dsp1" sink_name=output1
    load-module module-combine sink_name=combined master=output0 slaves=output1
    set-sink-default combined

    This will combine the two sinks output0 and output1 into a new sink combined. Every sample written to the latter will be forwarded to the former two. PulseAudio will make sure to adjust the sample rate of the slave device in case it deviates from the master device. You can have more than one slave sink attached to the combined sink, and hence combine even three and more sound cards.


So I guess it should be possible to tweak that to be valid for two sinks on different clients. However, I don't understand how to assign names to the devices, so I can use those names with the module-combine.

Here's the pulseaudio configuration on the local machine: [http://dl.getdropbox.com/u/175461/pulse/default.pa.local](http://dl.getdropbox.com/u/175461/pulse/default.pa.local)
And here's the configuration on the other machine (which starts pulseaudio as a system service, FWIW): [http://dl.getdropbox.com/u/175461/pulse/default.pa.remote](http://dl.getdropbox.com/u/175461/pulse/default.pa.remote)

Thanks in advance!

---

### Post by unimatrix on 2009-03-12
I would VERY MUCH like to know this too. Subscribed.

---

### Post by markbuntu on 2009-03-12
You can use module combine or, if you just want simultaneous output to all output devices you can just open the pulseaudio device chooser and go to configure local sound server/simultaneous output and check the box.

---

### Post by unimatrix on 2009-03-12
How do I find the name of a network sink?

---

### Post by kwaanens on 2009-04-21
I'm also interested in finding out how I do this. Anyone?

---

### Post by 00arthuryu on 2009-04-22
I too would also like to know
:popcorn:
Subscribed

---

### Post by taphos on 2009-05-23
To see the module names run pulse audio with the shell from the terminal
```
pulseaudio -C
```

Use this command to get the list of local sinks in the pa shell
```
list-sinks
```

module-combine is able to combine only local sinks, so you need to create a tunnel sink that will send sound from local pa server to the remote one
```
load-module module-tunnel-sink server=soundserver.local
```

Now combine sinks 
```
load-module module-combine sink_name=combined slaves="tunnel.soundserver.local,alsa_output.pci_10de_26c_sound_card_0"
```
replace "alsa_output.pci_10de_26c_sound_card_0" and "soundserver.local" with your own values

Have fun ;)

---

### Post by unimatrix on 2009-05-23
Thanks taphos, but I have some further questions.

First of all, you don't need to kill pulseaudio just to get into the command prompt. You can use **pacmd**.
For example:
```

pacmd list-sinks
pacmd load-module module-tunnel-sink server=soundserver.local
pacmd load-module module-combine sink_name=combined slaves="tunnel.soundserver.local,alsa_output.pci_10de_26c_sound_card_0"

```


Second, where do I load these modules? On the remote client or on the machine that will play audio to the clients?
Also, what is *soundserver.local* anyway and where do I find out what my value is?

Thanks!

---

### Post by taphos on 2009-05-24
I didn't know about pacmd, thanks for the advice.

You load those modules on the machine which will send the sound stream (where you run your music player)
```

load-module module-tunnel-sink server=soundserver.local
load-module module-combine sink_name=combined slaves="tunnel.soundserver.local,alsa_output.pci_10de_26c_sound_card_0"
set-default-sink combined

```

On the remote sound server (which will receive a sound stream) you need to enable tcp protocol, I do it via gui application "padevchooser" 
Configure local server > Network access > Enable network access to local devices
Or this can also be done by loading modules (but I haven't tried it):
```

load-module module-native-protocol-tcp auth-anonymous=1
load-module module-esound-protocol-tcp auth-anonymous=1

```

The soundserver.local is the host name of the remote sound server where "soundserver" is the name of the machine, to get it run "hostname" command. You can use the IP address instead if you like (i.e. 192.168.0.2).

Btw. you can also transmit sound to remote servers by using RTP, 
if "padevchooser" Configure local server > Multicast/RTP
see also [http://pulseaudio.org/wiki/Modules#RTPSDPSAPTransport](http://pulseaudio.org/wiki/Modules#RTPSDPSAPTransport)
If you got a wired network, you should use this better.
But it does not work for me as I am using wifi and it can not handle the RTP broadcast traffic for some reason, sound becomes very choppy.

---

