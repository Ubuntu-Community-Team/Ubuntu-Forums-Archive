---
title: "Skype, cannot choose sound sources"
date: 2009-11-08
forum: Multimedia Software
---

### Post by mooreted on 2009-11-08
Using Skype 2.1.0.47 on Ubuntu 9.10.

I have a USB headset and a sound card. I need Skype to play through the earphone on the headset and receive voice through the mic and ring through the speakers. All other sound and music should go through the speakers only.

When I go to choose my audio hardware I only have one choice "Pulse Audio (local)"

In the sound settings I can either have the headset or the speakers, I can't have both.

How do I set this up?

---

### Post by Arup on 2009-11-08
The Skype that ships with KK only allows Pulse, you need to make the selection physically here.

---

### Post by mooreted on 2009-11-08
I'm sorry, what does "Physically Here" mean?

I can't find anywhere to choose input/output sound devices.

---

### Post by Arup on 2009-11-08
Right click on the sound icon on your top taskbar, in input column you will see the choices for input.

---

### Post by mooreted on 2009-11-08
And that is where I can choose either speakers or headset. I need both. I need Skype to ring through the speakers and the voice call to go through microphone and earphone. If I switch to Internal Audio, my Skype call rings on the speakers and then you can hear the person talking on the speakers. If I choose Audio Adapter, I can hear the person speaking in the headset and they can hear me, but if the phone rings I can't hear it because it's ringing through the headset, not the speakers.

---

### Post by mooreted on 2009-11-08
I'm going to have to get paid Ubuntu support when I get paid. This is ridiculous. I cannot use Ubuntu if I can't get Skype to work.

I paid for an Ekiga phone number, but they haven't given me one yet. Maybe it works better.

I'm really getting frustrated with having to go back to Windows because of Skype.

---

### Post by mooreted on 2009-11-09
Going to try OSS4. PA is crap, I don't care what the geeks say.

---

### Post by mooreted on 2009-11-09
Great, now I don't have any sound at all.

---

### Post by Arup on 2009-11-09
Try this, remove the regular skype and install skype static and see if this issue goes away. Skype works fine here with my Microdia chipset webcam and Yamaha sound card. I stay connected for hours without any glitches. The only thing is I have to adjust the video color via v4l2ucp and it works out fine.

---

### Post by VertexPusher on 2009-11-09
> **mooreted said:**
> Going to try OSS4. PA is crap, I don't care what the geeks say.
You are right about PA being crap, but why going OSS4?

All you needed to do is remove PA using Synaptic, then choose ALSA audio devices in Skype.

---

### Post by mooreted on 2009-11-09
> **Arup said:**
> Try this, remove the regular skype and install skype static and see if this issue goes away. Skype works fine here with my Microdia chipset webcam and Yamaha sound card. I stay connected for hours without any glitches. The only thing is I have to adjust the video color via v4l2ucp and it works out fine.

When I use Skype-Static I can only choose /dev/dsp1 or /dev/dsp2.

---

### Post by mooreted on 2009-11-09
> **VertexPusher said:**
> You are right about PA being crap, but why going OSS4?

All you needed to do is remove PA using Synaptic, then choose ALSA audio devices in Skype.

Some people were going on and on about how great OSS4 is. So far, I'm not impressed. I'm not an uber-geek; I just want things to work.

---

### Post by mooreted on 2009-11-09
Skype and sound are working. I did so many tweaks trying to get PA or OSS4 to work that I just reinstalled Ubuntu then removed PA. I hope the next update doesn't try to put PA back on.

---

### Post by VertexPusher on 2009-11-09
> **mooreted said:**
> I hope the next update doesn't try to put PA back on.
Regular updates don't, but full distro upgrades do, unless the maintainers finally get a clue and make PA an optional package.

PA is probably the most frequently uninstalled package in Ubuntu's history. :lolflag:

---

### Post by mooreted on 2009-11-09
It's frustrating because so many people claim PA is great and you're an idiot if you don't think so. If removing a program fixes an issue, it would seem that that program has a problem.

Thanks for putting up with my ranting. I was about to throw my computer out in the street.

---

### Post by Arup on 2009-11-09
Pulse Audio has come a long way since its introduction with Hardy and now generally works quite well with majority of sound cards, it works nicely with my ancient Yamaha sound card but then there are always exceptions. Thankfully being Linux, you have workarounds and choices. The Yamaha card has been unsupported since the introduction of x64 OS from MS, from XPx64 ownards, I had no other resort but to throw away this expensive pro sound card which probably has the best sound out there. Lucky for me there was Linux.

---

### Post by scotty64 on 2009-11-09
I had the same problem and solved it by rolling back to Skype 2.0. Working audio is more important for me than SMS. See my post here:
[http://ubuntuforums.org/showthread.php?t=1317483](http://ubuntuforums.org/showthread.php?t=1317483)

Regarding Pulseaudio I have to say that although I am AFAIK not an idiot and working with Linux for over 14 years now I find at least the Ubuntu implementation terrible. You need at least three different applications to manage it (the sound manager that Karmic installs by default plus Gnome ALSA-mixer and Earcandy) and you cannot easily disable it or use pasuspender (it does not even work in Karmic).

I gave up fiddling with pulse after wasting hours on it and solved the problems by switching to KDE as desktop. Everything on ALSA and everything works excellent now!

---

### Post by alicemoon on 2009-11-10
> **VertexPusher said:**
> You are right about PA being crap, but why going OSS4?

All you needed to do is remove PA using Synaptic, then choose ALSA audio devices in Skype.

 after uprating skype would not recognise my usb phone so i removed PA as suggested and now it works fine - thanks

---

### Post by jml75 on 2009-11-10
Hi,

Read this!

[http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)

---

### Post by mooreted on 2009-11-10
> **jml75 said:**
> Hi,

Read this!

[http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)

Yeah, read that. It's not very helpful, actually.

I'm giving up on Skype. Just got a great deal on a VOIP phone from Charter. I'm basically getting a free phone for 2 years.

I'm not going to fight with software anymore. I don't have time. If it doesn't work on Linux properly, I'm not doing it. Make your software work on Linux and I'll use it. Until then, forget it.

---

### Post by VertexPusher on 2009-11-11
> **jml75 said:**
> Read this!

[http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)
This part is interesting:
> You might ask, why don't we support showing you normal ALSA devices alongside with pulseaudio server? Answer is simple: by default **pulseaudio opens hardware ALSA device exclusively, which means no other applications can access it and they either have to go through pulse or give up**. If we see pulse running - we don't even try to muck with it.Emphasis mine. The consequence of this is that Skype cannot use two separate sound devices for voice and ringing if PulseAudio is active, because Pulse will assign only one audio source/sink pair per application.

Awesome! A little more of this, and Linux audio will be back where it was in the 1990s. :lolflag:

---

### Post by mooreted on 2009-11-11
> **VertexPusher said:**
> This part is interesting:
Emphasis mine. The consequence of this is that Skype cannot use two separate sound devices for voice and ringing if PulseAudio is active, because Pulse will assign only one audio source/sink pair per application.

Awesome! A little more of this, and Linux audio will be back where it was in the 1990s. :lolflag:

You know, ALSA has been working fine for me for years. Why not just get some people together to fix ALSA instead of trying to reinvent the wheel?

I am not a developer so I don't know all the intricacies of the ALSA problem, but from a user's perspective, it just works.

---

### Post by VertexPusher on 2009-11-11
Please vote here to make PulseAudio optional:

[http://brainstorm.ubuntu.com/idea/21827/](http://brainstorm.ubuntu.com/idea/21827/)

---

### Post by mooreted on 2009-11-11
> **VertexPusher said:**
> Please vote here to make PulseAudio optional:

[http://brainstorm.ubuntu.com/idea/21827/](http://brainstorm.ubuntu.com/idea/21827/)

Voted

---

