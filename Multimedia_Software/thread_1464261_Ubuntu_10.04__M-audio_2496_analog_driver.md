---
title: "Ubuntu 10.04  M-audio 2496 analog driver"
date: 2010-04-28
forum: Multimedia Software
---

### Post by svkndv on 2010-04-28
Ubuntu 10.04 & M-Audio 2496

I connect my card out to amplifier through analog connection as my amp support only analog out, 

Unfortunately Preference>> sounds shows only digital output. I tried various solutions suggested in this forum, in some cases I am getting right channel but not stereo.

aplay-l proves system recognized the card as m-audio 24/96, 

I am not sure why there is no out of box solution available for a famous card which is in the market for last 8-9 years.

Do you recommend me to install OSS which is supported by M-Audio?

---

### Post by ianc on 2010-04-29
This - unfortunately - is a very long-standing issue.

You can find workarounds here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442), but it seems it won't be fixed in Pulseaudio until changes are made first in ALSA.

---

### Post by cchhrriiss121212 on 2010-04-29
> I am not sure why there is no out of box solution available for a famous card which is in the market for last 8-9 years.
The solution for most users has been to uninstall pulse which is what I have done with my ice1712 card. You can then use straight alsa for output and set levels and bitrate with envy24control or alsamixer.

---

### Post by lidex on 2010-04-29
In essence:
> Alternate channel mappings needed for ICE1712

Cards such as Audiophile 2496, Delta 1010LT and others using the ICE1712 chip, there is a bug with the channel mapping.

Diagnosis

Open a terminal, then enter this command:

cat /proc/asound/cards | grep ICE1712

If you get a line specifying the name of your soundcard, you're probably affected.

Fix / workaround

See bug #178442. 

---

### Post by svkndv on 2010-04-30
> **ianc said:**
> This - unfortunately - is a very long-standing issue.

You can find workarounds here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442), but it seems it won't be fixed in Pulseaudio until changes are made first in ALSA.

#63 resolved the issue with M-Audio 2496. At-least I can listen music. But it disabled all digital channel. Anyway that doesn't matter for me unless I upgrade my amplifier.

Thanks for the help

---

### Post by scottstoked on 2010-05-02
I'm an average Windows user who has been dabbling in Ubuntu off and on, but I have NEVER been able to get my Delta 1010LT to work. I'm sure an average experienced Linux user could figure it out, but I've spent hours trying to learn how to do it and I'm giving up. The community is full of great people who try their best to help, but seem to only know how to give instructions as if you are already well versed with terminal commands.

I'm eager to try Ubuntu again as soon as installing a driver for my card becomes simple.

---

### Post by cchhrriiss121212 on 2010-05-02
> **scottstoked said:**
> I'm an average Windows user who has been dabbling in Ubuntu off and on, but I have NEVER been able to get my Delta 1010LT to work. I'm sure an average experienced Linux user could figure it out, but I've spent hours trying to learn how to do it and I'm giving up. The community is full of great people who try their best to help, but seem to only know how to give instructions as if you are already well versed with terminal commands.

I'm eager to try Ubuntu again as soon as installing a driver for my card becomes simple.
Did you try posting a request for help? I would be happy to explain any commands/instructions you are having trouble understanding. As mentioned earlier the delta series is fully supported, just not with pulse audio which is the default sound server in Ubuntu. Here are some things you can try:
Disable onboard sound in your BIOS setup (press f2 to access BIOS when your PC first boots)
Go to synaptic package manager and remove pulse audio packages, then install envy24control from a package called alsa-tools
Use envy24 to set the analogue volume levels
Check you are in the audio group by looking in System>Users & Groups
Reboot

---

### Post by lidex on 2010-05-02
> **scottstoked said:**
> I'm an average Windows user who has been dabbling in Ubuntu off and on, but I have NEVER been able to get my Delta 1010LT to work. I'm sure an average experienced Linux user could figure it out, but I've spent hours trying to learn how to do it and I'm giving up. The community is full of great people who try their best to help, but seem to only know how to give instructions as if you are already well versed with terminal commands.
I'm eager to try Ubuntu again as soon as installing a driver for my card becomes simple.
We'll be glad to have you. Terminal commands are really not that difficult when you understand that all you need to do is copy and paste. It is actually more difficult to walk someone through all the steps with a gui - open this, navigate to that, scroll down to this, double-click on that....etc. How to find a terminal: Terminal="Applications->Accessories->Terminal". I do understand your frustration. We all want things to "just work".

Have you ever started a thread for help with this issue? I'm sure we could walk you through the necessary steps.

---

### Post by scottstoked on 2010-05-02
Thank you for the replies and I'm very sorry for hijacking the thread. I will start a new thread and try to get this up and running one more time. Thanks again!

---

### Post by LxP on 2010-05-03
> **ianc said:**
> This - unfortunately - is a very long-standing issue.

You can find workarounds here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442), but it seems it won't be fixed in Pulseaudio until changes are made first in ALSA.

Thanks, ianc.  As it did for svkndv, the workaround in comment #63 of the bug report you mentioned enabled analogue output on my Audiophile 2496 through PulseAudio.

---

### Post by yosoyeleze on 2010-05-05
Hello 4 all:

Please. Help me! I have a Audiophile 2496 soundcard, and pulseaudio on ubuntu 10.04 show only the digital output. I try uninstall pulseaudio.
I used Ubuntu hardy for advance professional audio production, and this distribution work fine.

solutions?

---

### Post by lidex on 2010-05-05
> **yosoyeleze said:**
> Hello 4 all:

Please. Help me! I have a Audiophile 2496 soundcard, and pulseaudio on ubuntu 10.04 show only the digital output. I try uninstall pulseaudio.
I used Ubuntu hardy for advance professional audio production, and this distribution work fine.
solutions?

See post #63 here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442")
And next time start your own thread.

---

### Post by mirosol on 2010-06-06
I just moved from gnome to KDE after 10.04 release. With KDE's Phonon, i got my audiophile 2496 to work straight out of the box. This is the first time after pulse's release that this has happened. Seems that Phonon and alsa do work quite nicely with ICE1712 chips. You still need packages "alsa-tools" and "alsa-tools-gui", but you don't need to configure anything.

Other problemchip, "azalia" with 5.1 spdif seems to work with out of the box with Phonon. (At least that's what my friend said.. He's been battling with pulse and that chip for about two years now..)

Pulseaudio is beatiful on paper, but it just doesn't work on all essential chips. At least not yet.
+m

---

### Post by Breambutt on 2010-06-06
> **mirosol said:**
> Pulseaudio is beatiful on paper, but it just doesn't work on all essential chips. At least not yet.
Yet? It's been the default brainfart in Ubuntu since what, Hardy or Intrepid? :|

Even with the PulseAudio "fixed" for ice1712 cards, PA has serious issues with MIDI in general and it doesn't work with Timidity at all. Sure I could run VSTis or the default soundbank in TuxGuitar, but the first option is a little hardcore and the latter just sounds like a bunch of turds. I'm sure there's another partial fix for that too, but when is this temporary band aid chain going to end if you take that path?

I say dump PulseAudio while you still can, and I actually gave it a try this time. There's no downside to getting rid of it, I also stopped getting mysterious playback hicups as soon as I removed it.

---

### Post by jmaasing on 2010-07-10
> **Breambutt said:**
> Yet? It's been the default brainfart in Ubuntu since what, Hardy or Intrepid? :|


Removing pulseaudio and setting up ALSA works for me (M-Audio 2496).

But ever since pulseaudio was introduced it has been a struggle. It has been several years now and still the same crap every time. Next upgrade will not be Ubuntu for me.

---

