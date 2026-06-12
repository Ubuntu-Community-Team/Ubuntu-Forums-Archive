---
title: "Flash video sound"
date: 2008-04-26
forum: Multimedia Software
---

### Post by LordSaladin on 2008-04-26
I upgraded to Hardy Heron on Thursday, and subsequent to doing so, I have realised that, when I try to play Flash videos on YouTube and other sites, despite getting video perfectly fine, I am unable to hear any sound.

All other applications are making sound perfectly, and when trying to re-configure my ALSA-mixer, nothing works at all.

Any ideas on what could be wrong, and how to fix it?

((Note: I am using FireFox 3b5 for my web browser))

---

### Post by carlz0r on 2008-04-26
I couldn't make 2 sources of audio work at the same time when I installed Hardy, (ex. youtube and rythmbox, or youtube and totem.) until I went in to system>preferences>sound, and changed everything back to ALSA.  those new Pulseaudio options just did not work for me at all.

Hope this helps, sorry if it doesn't.

---

### Post by mtron on 2008-04-26
look [here]("https://wiki.ubuntu.com/PulseAudio") guys.

The wiki page gives good instructions. To work around the flash problem, you need to install a package:

```
cd ~
wget http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb
rm libflashsupport_1.0~2219-1_i386.deb
```

and flash will work ;)

---

### Post by ElVirolo on 2008-04-26
Hi everyone.

I have a similar problem : sound doesn't work with youtube but it does with all the other flash animations. The strange thing is that, since I use Kubuntu, pulseaudio is not installed...

---

### Post by ElVirolo on 2008-04-26
Up

---

### Post by Dr. Faustus on 2008-04-26
> **carlz0r said:**
> I couldn't make 2 sources of audio work at the same time when I installed Hardy, (ex. youtube and rythmbox, or youtube and totem.) until I went in to system>preferences>sound, and changed everything back to ALSA.  those new Pulseaudio options just did not work for me at all.

Hope this helps, sorry if it doesn't.

I had the exact same problem.  It seems PulseAudio doesn't like running Flash audio and media player audio at the same time.   I reverted back to ALSA and everything worked fine again.   PulseAudio doesn't seem to work for me either.

---

### Post by jhnphm on 2008-04-27
No need to kill pulseaudio, just install libflashsupport

---

### Post by ElVirolo on 2008-04-27
Thanks for your help, but libflashsupport is installed and youtube still doesn't work.

---

### Post by portach king on 2008-04-27
> **mtron said:**
> look [here]("https://wiki.ubuntu.com/PulseAudio") guys.

The wiki page gives good instructions. To work around the flash problem, you need to install a package:

```
cd ~
wget http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb
rm libflashsupport_1.0~2219-1_i386.deb
```

and flash will work ;)

Hey thanks. That fixed it for me.
Is this a common problem? It's was pretty annoying when I wasn't able to play online media while another multimedia app was open. I can imagine some new users would have no idea what the problem is and possibly not even consult the forums. :neutral:

---

### Post by ElVirolo on 2008-04-27
What I still don't understand is why it doesn't work even if pulseaudio is not installed.

---

### Post by ElVirolo on 2008-04-27
Up (again)

---

### Post by ElVirolo on 2008-04-28
Up (sorry...)

---

### Post by dexterchief on 2008-05-02
This is what worked for me:

```
sudo apt-get install libflashsupport
```

---

### Post by BCtom on 2008-05-03
> **mtron said:**
> look [here]("https://wiki.ubuntu.com/PulseAudio") guys.

The wiki page gives good instructions. To work around the flash problem, you need to install a package:

```
cd ~
wget http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb
rm libflashsupport_1.0~2219-1_i386.deb
```and flash will work ;)


WOW, Worked like a charm! 

I wonder if this bit of news should be put into the "How-tos," or "Upgrades problem" part of the forum. I'm seeing a lot of threads of people having this same issue with flash.

Anyway, thanks for posting the quick fix here. It solved the problem at least for me.

---

