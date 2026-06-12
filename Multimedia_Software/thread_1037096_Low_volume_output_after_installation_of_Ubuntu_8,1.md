---
title: "Low volume output after installation of Ubuntu 8,10"
date: 2009-01-11
forum: Multimedia Software
---

### Post by stefros68 on 2009-01-11
I have installed Ubuntu 8.10 on an Amilo M 7400.

The soundcard is a Cirrus Logic CS4299 rev 4. After installation I can listen to the sound, but its very weak. I have to pump up the volume very hard.

I added a line in alsa-base: options snd-hda-intel model=generic and
restarted alsa, no success at all.

My settings of Master & PCM seems okay, also there is no muted setting.

Can anybody help me, please ?

Thanks in advance

Stefan

---

### Post by John Jason Jordan on 2009-01-14
> **stefros68 said:**
> I have installed Ubuntu 8.10 on an Amilo M 7400.

The soundcard is a Cirrus Logic CS4299 rev 4. After installation I can listen to the sound, but its very weak. I have to pump up the volume very hard.
I added a line in alsa-base: options snd-hda-intel model=generic and
restarted alsa, no success at all.
My settings of Master & PCM seems okay, also there is no muted setting.

I have the same problem, but I'm sure the causes are different. I upgraded Hardy x86_64 to Intrepid and the volume worked fine as before. However, there is a problem with bluetooth on Intrepid and as a result it killed my bluetooth audiophile headphones. In an effort to get them working I installed all of the pulseaudio modules (not all of them had been installed for some reason). Afterwards the bluetooth DR-BT50 headphones still don't work and now my volume level is less than half what it is supposed to be, Even at maximum volume it is not loud enough.

It's possible that your problem is related to mine, but unless you are using pulseaudio I doubt it. On the other hand, both your problem and mine might be caused by something deeper. In that case the source of the problem may be the same for both of us.

Edit Jan 15 2009: I solved it by using alsamixer. But instead of just using the command "alsamixer" I had to append "-D hw.0." Only then did alsamixer show all the sliders. Once they were all visible I could see that some were turned down halfway. Moving them all up to max (except the mic) restored my sound to what it was with Hardy and before installing pulseaudio.

---

### Post by stefros68 on 2009-01-18
Hi,

I tried Alsamixer with option to see all sliders. Every slider was at max. peak!

I used a script to install a new version of Alsa. Now I have no soundcard detected by Ubuntu and have no clue what to do!

Can you help me, please ::eek:

---

### Post by John Jason Jordan on 2009-01-18
> **stefros68 said:**
> Hi,

I tried Alsamixer with option to see all sliders. Every slider was at max. peak!

I used a script to install a new version of Alsa. Now I have no soundcard detected by Ubuntu and have no clue what to do!

Can you help me, please ::eek:

Sorry, your problem exceeds my proficiency level. :(

Hopefully someone smarter than me can offer more suggestions.

Wait ... have you installed pulseaudio? It is supposed to be installed by default starting with Hardy. But I discovered that some of the modules were not installed on my Intrepid computer. Search the forums for "pulseaudio" and you should turn up more information about it.

---

### Post by stefros68 on 2009-01-26
Is it possible that there are some problems concerning 2.6.27.11-generic kernel and AC97 soundcard?

If its really exist, can I install an older version of Ubuntu Kernel?

---

### Post by John Jason Jordan on 2009-01-26
> **stefros68 said:**
> Is it possible that there are some problems concerning 2.6.27.11-generic kernel and AC97 soundcard?

If its really exist, can I install an older version of Ubuntu Kernel?

For the first question, check Google and Launchpad. Launchpad is the place where most Linux bugs get reported and discussed. Anyone can read Launchpad, but you have to register (free) to post.

As for installing an older kernel, yes you probably can. I say that because I have heard of it being done. I have never done it myself. However, sometimes installing an older kernel breaks some feature of the current operating system or of some program. If your Intrepid is an upgrade you should see an option to boot to a previous kernel in the Grub boot menu. (Hit esc right after the BIOS message flashes by and just before the Ubuntu splash screen starts.) You can also look at the menu list with:

gedit /boot/grub/menu.lst

If you want to make changes to it, add "sudo" in front because you can read it as a user, but to edit it requires root privileges.

---

