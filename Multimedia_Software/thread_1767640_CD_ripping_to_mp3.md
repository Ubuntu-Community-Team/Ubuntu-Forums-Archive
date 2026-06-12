---
title: "CD ripping to mp3"
date: 2011-05-25
forum: Multimedia Software
---

### Post by b1lancer on 2011-05-25
I've been doing some searching on the internet about how to rip my cd's to mp3 within ubuntu. I seem to find that LAME isn't a good way to convert the files. I saw the sticky within the forums and RubbyRipper is recommended, but the installation seemed a bit confusing to me. Everything else I found through my search was considerably old. I'm using Karmic Koala. Any suggestions? (This is also a sticking point for people I try to convince to switch over to ubuntu, btw.)

---

### Post by wolfen69 on 2011-05-26
I think CDex is the best, and I've used it for years. It's a windows app that's open source, but works perfect in wine. [http://prdownloads.sourceforge.net/cdexos/cdex_151.exe?download](http://prdownloads.sourceforge.net/cdexos/cdex_151.exe?download)

RipperX is a good app available natively in ubuntu. 

Why is it a sticking point? There are plenty of good apps for ubuntu/linux. You just need to find them.

---

### Post by b1lancer on 2011-05-26
That's the thing: most people I talk to don't want to spend too long searching for things and encountering possibly "complicated" instructions.

---

### Post by tommcd on 2011-05-26
I use **asunder** for ripping CDs. You do need lame for mp3 support. Asunder is fast and light and works well in my experience.
Asunder is in the Ubuntu repos.

---

### Post by andrew.46 on 2011-05-26
Might be a good time to pimp one of my own guides :). Perhaps try this one:

HOWTO: Convert music CDs to MP3 using the Command Line.
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

---

### Post by nothingspecial on 2011-05-26
> **andrew.46 said:**
> Might be a good time to pimp one of my own guides :). Perhaps try this one:

HOWTO: Convert music CDs to MP3 using the Command Line.
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)


Or for the full guide

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---

### Post by coffeecat on 2011-05-26
> **tommcd said:**
> I use **asunder** for ripping CDs.

+1. There's also sound-juicer - also in the Ubuntu repos - but I prefer asunder. They're both GUI apps and hardly "complicated". 

> **andrew.46 said:**
> Might be a good time to pimp one of my own guides :). Perhaps try this one:

HOWTO: Convert music CDs to MP3 using the Command Line.
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

+10. Although command line, couldn't be easier.

**EDIT**: Just noticed this:

> **b1lancer said:**
>  I'm using Karmic Koala. Any suggestions? (This is also  a sticking point for people I try to convince to switch over to ubuntu,  btw.)

Karmic is past end-of-life and no longer supported. That would certainly be a sticking point for trying to convince people to switch to Ubuntu if they see an update fail! Time to upgrade to a supported version.

---

### Post by b1lancer on 2011-05-26
Thanks for the replies.

i was just concerned about using LAME since I saw this on a Ubuntu guide:

> **WARNING:** the gstreamer LAME plugin, used in the instructions below, is broken and will produce substandard quality MP3s. You can track the bug [here]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483"). If you want to create MP3s, it is recommended not to use Sound Juicer; use a program that doesn't interface with LAME through gstreamer instead. Good examples are [RubyRipper]("https://help.ubuntu.com/community/CDRipping#RubyRipper") and [ABCDE]("https://help.ubuntu.com/community/CDRipping#ABCDE").   [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)


And I will be updating soon...

---

### Post by oldfred on 2011-05-26
If I am going to spend the time ripping the CDs I want the better quality. So I configure AudioCD Extrator (Sound Juicer) to extract to FLAC in preferences. 

I find when using Sound Converter to write mp3s to my MP3 player that it converts and writes faster than just copying the mp3 to my flash player. Not sure why it that still applies as I have not done it recently.

---

### Post by wolfen69 on 2011-05-26
> **oldfred said:**
> If I am going to spend the time ripping the CDs I want the better quality. So I configure AudioCD Extrator (Sound Juicer) to extract to FLAC in preferences. 

I find when using Sound Converter to write mp3s to my MP3 player that it converts and writes faster than just copying the mp3 to my flash player. Not sure why it that still applies as I have not done it recently.

But are you able to get 320kb mp3's with sound juicer? In the past I havn't been able to get anything but 128kb. I don't do much ripping anymore, but when I do, I just use CDex.

---

### Post by oldfred on 2011-05-26
With flac on my hard drive I do not care about mp3 bit rates. My little mp3 player cannot use anything over smaller files anyway.

I just checked an I use high which is 192kbps. It does have an insanely high setting of 320.

---

