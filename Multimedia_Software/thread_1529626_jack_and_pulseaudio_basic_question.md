---
title: "jack and pulseaudio: basic question"
date: 2010-07-12
forum: Multimedia Software
---

### Post by linuxgrrl on 2010-07-12
Hello, 

I want to experiment with Hydrogen, Rosegarden and other music apps ... it seems that jack is a useful program to do that.  I have a standard install of Lucid. 

When I start Jack, it gives a message "suspending Pulseaudio ..."   The jack apps I am using have no sound.  I assume that I need to set up an ALSA device to connect Jackd to? Is that correct?

[Note: I found these instructions for "running Pulseaudio on top of jack" ([http://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK](http://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK)) but they look more complicated than I need.  I'm only using jack a little each day so I am fine with turning off Pulse during those times.]

What is the simplest way to get sound out of Jack apps? If it is to set up an ALSA device, how do I do that without interfering with Pulse which will be running the other 90% of the time?  Or am I totally misunderstanding the setup?

---

### Post by cchhrriiss121212 on 2010-07-12
Jack is a sound server that runs on top of ALSA, and pulse is also a sound server that runs on top of ALSA, so one will suspended when you use the other.
Here is how linux sound works in simple terms:
Sound card>ALSA>Pulse/Jack>Client Programs

The bad news about jack is that it is a pain to configure, but it is a powerful tool when you get it going. Does jack run OK when you press start?
If not you should follow these steps:
 	Code:
 	sudo gedit */etc/security/limits.d/audio.conf* 
and add this at the bottom:
@audio - rtprio 99
@audio - memlock unlimited

[This guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation") will be of further reference for you if you want to install an rt kernel (very useful for low latency audio), or other audio stuff.

You should also check out the studio forum for things like this.

---

### Post by linuxgrrl on 2010-07-12
So with a standard Lucid install, you're saying I already have an ALSA device set up?  That's good news ... if that's true I just have to find out what the device is named so, and point the Jack output to that device.  Again, if I'm understanding things.

How do I figure out what my Alsa device is called?  with prior versions of Ubuntu I used to just open the volume control and it would list the devices, but that no longer seems to be the case.

---

### Post by cchhrriiss121212 on 2010-07-13
If you have functioning sound from your regular apps (rhythmbox etc) then ALSA is working fine. 
To find out available sound devices put "aplay -l" into a terminal. If you are using your onboard sound card, then the default option should work in jack, this will be hw:0,0.

---

