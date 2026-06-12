---
title: "General question about Ubuntu's audio architecture and M-Audio Firewire Solo"
date: 2008-11-11
forum: Multimedia Software
---

### Post by kozmikyak on 2008-11-11
I've already figured out how to run my M-Audio Firewire Solo on Ubuntu, it involves getting freebob and jack running.  So I can at least get some kind of sound in and out of the device, using jackd.

However, I don't understand Ubuntu's audio architecture well enough to move on farther from there.  I'd like very much for this device to be the system's default audio device.  In the system's audio control panel I don't have the choice to select jackd as a sound server, only ALSA, OSS, and PulseAudio.

Since the freebob driver doesn't work with any audio server except jackd at the moment, is there some convenient way to forward ALSA, OSS, or PulseAudio to jackd short of choosing only applications which use jackd internally?

I did try to search the forums for informaiton on this, and I found a few links about people forwarding from PulseAudio and ALSA to jack with Ubuntu 7.*, but the instructions are outdated enough and my knowledge of the whole audio architecture is limited enough that those were not sufficient to help me.

I see that there is a successor project to freebob named ffado, I'll try researching there too.

I'm really looking more for pointers on "What basics do I need to understand about how audios is handled in Ubuntu in order to more efficiently hunt for this information".  I'm not a complete Linux n00b, but my experience has been limited to servers and the RedHat/Centos side before now.

This is on a Thinkpad Z61P, by the way.  I have successfully configured it to deal with dual-head monitors through the docking station, and the internal sound card was automatically detected just fine, so I'm not dead in the water.  Ubuntu is working quite nicely for most purposes, so this isn't just an "Ubuntu 5uX0rz" message.

---

### Post by Mariano Oliveto on 2008-11-18
Not sure if I'll be of any help but here I go (Disclaimer: I'm not an expert and I made a lot of assumptions during the explanation so if anyone knows better please feel free to correct me... it'll be profitable for all of us!! :p ):

> In the system's audio control panel I don't have the choice to select jackd as a sound server, only ALSA, OSS, and PulseAudio.

AFAIK, jackd is not a sound server, so it really shouldn't be listed there. I think jackd jut connects the different audio software so it can direct audio signal from one program to another. For instance, you can instruct it to get the audio input from your sound card where you might have plugged a guitar and then send that audio signal to a program like Rosegarden or Ardour to record it and then the signal from these programs back to the sound card's output so you can hear them on your speakers. These seems simply enough but you can do more interesting things with it.

Now, back to your problem, if the sound card is installed, which I guess it is since you can use it with jackd and freebob, then (theoretically) you should be able to select it in the System->Preferences->Sound menu.

Notice that you can select different sound servers for each sound "situation", but also notice that in the "Default Mixer Tracks" section (near the bottom of the "Devices" tab) you can select the physical device that will be processing audio by default. Also notice that the same device might appear with different sound servers. I guess that this could be because the default Ubuntu installation includes all of them so you can select the one that fits your needs better.

Nevertheless, something in your post tells me that the problem might be a little more complex than this. Are there any other M-Audio FireWire users out there willing to help?!?! :)

Regarding understanding the basics of Linux Audio... I can't really help you since I'm sort of trying to figure it out myself. All I can suggest is to Google and search the forums like hell and post any remaining doubts (I actually came across your post searching for M-Audio Solo + Ubuntu experiences because I am thinking of buying one soon). ;-)

---

### Post by aeiah on 2008-11-18
as stated, jack isnt a sound server. its more a virtual audio interface. you use it instead of your soundcard, not instead of alsa or pulse audio. so what you're really wanting is a method for getting pulse audio to play through jack. i have no experience, and this seems to be for 8.04, but there'll be little difference i imagine:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

do a ctrl+f for 'pulse audio through jack'

it all looks pretty complicated and hopefully you wont get intimidated :p why did you have to be awkward and have a fancy pants audio interface instead of a normal soundcard?

---

### Post by nezurian on 2009-11-03
Hello! 
I'am having the same problem too. 

I can record tracks with my FW SOLO, and can hear my recordings on Ardour, but I cannot hear anything more. 


A friend of mine told me that a line written in /etc/modprobe.d/blacklist.conf can solve the situation (like blacklist intel8xx), but I don't have any experience and knowledge about this, and I don't know whether it is useful for this problem or not. 

I know there's someone outside who can help us :)

---

### Post by red13 on 2009-11-03
There is some software in the repositories the one you want first would be Jack Control it lets you set up and start Jack on the fly other stuff to for the more complex needs. 

If I haven't helped you then I don't understand your question and appologize for my ignorance.

---

### Post by nezurian on 2009-11-03
I am using qjackctl already. Nothing happens. I cannot find any means to direct the sound to the jack.

---

### Post by red13 on 2009-11-03
Check and see if you have alsaplayer-jack, I think thats what your missing it will be in the repositories.

---

### Post by nezurian on 2009-11-03
I have installed it now. nothing happens. what must I do? just install it and start qjackctl ? nothing more? what? :)

---

