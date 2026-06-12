---
title: "Standard java sound fix doesn't work on 11.10.. Need help."
date: 2011-11-11
forum: Multimedia Software
---

### Post by Truckerpunk on 2011-11-11
In all the previous releases of Ubuntu I've been able to get my java sound working nicely by adding an audio-wrapper to the java script. It has always been successful to do the following work around:

cd /usr/lib/jvm/java-YOURVERSION-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java

And then making the script:

#!/bin/bash
padsp /usr/lib/jvm/java-YOURVERSION-sun/jre/bin/java.bin "$@"

you can change the padsp to aoss for your setup.

But in 11.10 forcing java to use an audio wrapper seems to fail.
Sound does play form the java  app, for a little while, but no simultaneous audio output is possible. And after a minute or so, the sound from the java app stops too. 
In the sound preferences -> sound -> applications the java app generates a new output for EVERY single sound it plays, denoted as ALSA-plugin [java.bin]. I believe that this might be what eventually makes the audio stop (pure overload). I've been able to generate his error in the terminal due to the problem:

"ALSA lib pcm_pulse.c:746:(pulse_prepare) PulseAudio: Unable to create stream: Too large" 

I'm no pulse-audio-guru, but it also seems to point to an overload of the output. though I might be mistaking. I have tried to completely reinsatll Pulse, and also tried to switch to pure ALSA, without and change to the problem.

Any help is appreciated.

---

### Post by BillyBoa on 2011-11-11
You have the option to change to Java 6, according to WebUpd8:

```
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

Or install manually Java 7

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by Truckerpunk on 2011-11-11
Thanks for the reply... Clearly, I forgot to mention that I am running Oracle's latest java 7 (1.7.0 update 1). It makes no difference, wither I use Oracle java or the OpenJRE. The problem persists in both cases.

---

### Post by pel on 2012-04-22
I have a very similar problem since about a month ago. My problems started when I installed oracles java7 (not sure about the causation-relation here though). It does not help to remove it.

The difference here is that I get **no** apparent sound from java applications (other applications work just fine). I see no stream in pavucontrol.

I don't have the exact same error message either. My .xsession-errors says ```
18:06:01.643 E [audio_driver_pulseaudio.cpp:287] can't write to stream, Connection terminated
```

My java setup is the same as Truckerpunk's

Running pulseaudio with```
echo autospawn = no >> ~/.pulse/client.conf
killall pulseaudio
LANG=C pulseaudio -vvvv --log-time=1 > ~/pulseverbose.log 2>&1
```

I repeatedly see this in the log```
(  56.293|   0.000) I: [pulseaudio] client.c: Created 6 "Native client (UNIX socket client)"
(  56.293|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client6
(  56.293|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 24, local 24
(  56.293|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(  56.293|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(  56.293|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(  56.293|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for java.bin
(  56.293|   0.000) I: [pulseaudio] client.c: Freed 6 "ALSA plug-in [java.bin]"
(  56.293|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  56.293|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client6
```

---

