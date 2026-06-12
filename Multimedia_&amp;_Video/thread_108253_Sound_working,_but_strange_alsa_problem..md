---
title: "Sound working, but strange alsa problem."
date: 2005-12-25
forum: Multimedia &amp; Video
---

### Post by Chman on 2005-12-25
Hi there,

I've searched on this forum and google, but I can't find a solution to my problem. I've bought & installed an Hercule Fortissimo 4 sound card. This card use an ENVY24 HT chipset (according to alsamixer - ice1724). I can play sounds perfectly but there's a problem with alsa. Look at this screenshot :

[img]http://img500.imageshack.us/img500/9526/captureterminal3ab.png[/img]

And I can't change the volume. I've tried to reinstall alsa-base but it doesn't change anything. My onboard AC97 is disabled (in bios). Here are some informations, ask me if you need more :

```
chman@a11w:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm running Xfce... Thanks in advance for you help :)

Chman

---

### Post by Chman on 2005-12-27
No one to help me ?
It's a bit annoying to have to switch on windows to watch a movie correctly... :(

---

### Post by qbxk on 2006-01-17
For the record - I'm using a M-Audio Revolution 5.1 and i have the exact same problem, and further, aplay -l gives me identical to the above.

This machine is destined to become a stream encoder for our radio station and I have not installed X on it, so being able to solve this problem with command-line only tools would be preferred.

How can I get this to look and act like a normal card?  `cat /dev/dsp` only sits and hangs, this is what I believe I need to read from to accomplish my goal.

---

### Post by mpvano on 2006-01-18
The first thing you should do is go back into the alsamixer and figure out how to change the display to show ALL the card registers. The default display you are looking it does NOT show all the controls and switches. The default is to display ONLY the ones the alsa team THINKS are for playback. In the case of VERY complicated cards like the envy based ones, they often guess wrong.

Try hitting F5 once you open the alsamixer and the line that says playback should move the highlight to "all" - you should now see all the controls alsa thinks are available. (There are a LOT).  Alsa presets them all to zero - This is not usually useful - it's a safety precaution to keep people from blowing up speakers and other hardware connected to their systems. You'll have to figure out how to set them correctly for your use.

The second problem you should be aware of is that "cat /dev/dsp" reads from the "oss emulation" driver of alsa, not from the driver connected to the mixer you are looking at. It's possible for the card to be working fine under ALSA, but for the oss emulation to not be loaded, or to be incorrectly configured or confusing to use.

I currently use several delta 44 cards which use a similar chipset (ice1712) under a variety of linux operating systems for purposes similar to yours.

Because the chip sets these cards use is pretty complicated to understand and operate, I can't give you any more detailed advice, but I can tell you that I do have it working just fine after a basic "server install" under both oss and alsa at the moment on a Dell 1750 server I'm configureing, so the ubuntu "server install" seems to put everything there that's needed.

My "playback" mixer display looks just like yours, so I think that's not your problem, and I suspect you have everything you need installed.

The envy chip sets are very complicate to understand, and several of the switch settings will cause them to appear to lock up if you don't understand their function - in particular it has very confusing options to control its internal clocking. Some of them disable the internal clocking - it sounds like that's what you may be experiencing. Try reading up on the purpose and use of these switches.

It also has a completely separate digital mixer built in that does NOT do what you probably think it does. It doesn't route capture audio.

Also be aware that the chip set has many more registers than are probably used by your card, and the fact that they appear in the mixers can be very confusing.

You can learn a lot more about what's going on in your alsa installtion by examining the entries in /proc/asound.

I also suggest downloading the alsa source package and unpacking it (but don't try to install it!). It contains some documentation files scattered through the package that have very useful information.

Of course, you should have already read the documentation files in /usr/share/doc /alsa-base and .../alsa-utils.

One thing that often helps is to run some audio into the inputs and listen to the outputs while playing with the alsa mixer settings. That way you can at least tell if you have the "hardware" input and output controls set properly and can figure out how the routing works. Once you get the digital mixer configured, you're about half way there....

I also find it useful to install just enough xlib support in servers to allow remote xservers to use x windows programs via ssh. The "envy24control" graphical mixer for this family of chips may work with your card, and it's a powerful tool that's easier to understand.

I don't think it's part of the ubuntu alsa packages, so you may have to download and install it from sources - I believe it's currently part of the alsa-tools source package. I've been working without it under ubuntu, but I think I'm going to figure out where it is and install it myself because it's pretty handy...

To use this family of cards, you also probably need to have a correctly configured "asound.conf" file to map the card into useful devices.

hope this points you in the right direction, but you're going to have to do some homework. Fortunately there's a lot of information around the net about using cards based on these chips....

Mario

---

### Post by evayroberto on 2007-08-20
Anybody has solved this issue? I have a Fortissimo IV card, with envy24ht chip, and I have the same problem described. I want to use Ubuntu, no XP, but if I cant hear my 5.1 speakers, I will back to XP:(:(:(:(

---

### Post by evayroberto on 2007-08-20
No one can help me, please?
I have tested other distro's, and same issue, it seems alsa problem (tested with Mandriva 2007, Comfusion, PCLinux, Ubuntu, and Knoppix).
If I push f5 to see what alsa can show, it only shows one more channel, the right channel, but the other channels are not showed.
Could I solve it using oss instead of alsa? How can i do it?
Thanks

Roberto

---

### Post by Saoshyant on 2007-08-20
Installing OSS may do the trick, but the process is complex and you have to keep an eye on the OSS forum in case something goes bad.

Go to //opensound.com and download the .deb version of OSS.  Try to follow any instructions you find.  Oh, and dpkg uses a lower case -i not -I.

This process would be much easier if Ubuntu would be changed to use OSS or allow easy installation of OSS, but that's not the case currently.

---

### Post by evayroberto on 2007-08-21
Thanks for your help.
I have downloaded oss dev package, but I cant install it, I suppose its a permission issue. I will test it and I will report here. Thanks again.

---

### Post by evayroberto on 2007-08-22
OSS installed and problem continues. I have checked several .asoundrc configurations and no solution yet. Please, I am desperate. I need that 5.1 sound in my ubuntu.:confused:

---

### Post by Saoshyant on 2007-08-25
> **evayroberto said:**
>  I need that 5.1 sound in my ubuntu.:confused:

Hmm, I guess at this point you really need to ask help at the experts.  Look into the [OSS forum](http://www.4front-tech.com/forum/index.php) and good luck.

---

