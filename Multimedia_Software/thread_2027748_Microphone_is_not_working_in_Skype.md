---
title: "Microphone is not working in Skype"
date: 2012-07-16
forum: Multimedia Software
---

### Post by gaurav.alwaysur on 2012-07-16
I am using Ubuntu 12.04 and Skype.

My mic is not working. I have 1 mic attached to the system and another one in my headphone (Beats by Dr. Dre).

I followed these steps:

Turn PulseAudio autospawn off, normally: $```
echo "autospawn = no" > ~/.pulse/client.conf
```:confused:

```
killall pulseaudio
```
But this did not help me and it disabled my sound after my system restarted. I then tried

```
echo "autospawn = yes" > ~/.pulse/client.conf
```
then

```
pulseaudio -D
```
It fixed my system sound but still no sound on Skype microphone.

After that, I tried this command



```
echo "options snd-hda-intel model=acer" | sudo tee -a /etc/modprobe.d/alsa-base.conf > /dev/null
```


I've also upgraded alsa sound drivers by running:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

however on the last command:

```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
[sudo] password for gaurav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-3.2.0-27-generic-pae
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.2.0-27-generic-pae'
```


When I type pulseaudio in terminal it shows me

```
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

After all this, my sound system started behaving abnormally. Internal Speakers and headphone or 5.1 speakers both works at same time but still the microphone is not working. I even hear a noise when I don't play anything. It's freaking me out and my microphone problem is after 12.04 . Can I use my headphone microphone? I am having beats headphones.

---

### Post by Volens on 2012-07-17
Try running this to make sure your mic isn't muted and all your levels are up.

```
alsamixer
```

In my experience, if that doesn't work you need to fiddle with the 

```
options snd-hda-intel model=acer
```

line in /etc/modprobe.d/alsa-base.conf

I'm a quasi-noob, but this is one issue I've had some success with in a previous thread here:

[http://ubuntuforums.org/showthread.php?t=1582088](http://ubuntuforums.org/showthread.php?t=1582088)

Its a matter of getting the module to load with the correct config if this is the same issue.

Good Luck!

---

### Post by thejamesgroupinfo on 2012-07-17
I am also having the same problem.

[ad agency new york]("http://www.thejamesgroup.com/adagency.htm")

---

