---
title: "Setting up an Ubuntu Studio computer"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by Hanj on 2006-11-28
Me and my brother are planning to convert an old Windows XP box to an Ubuntu studio computer (running apps such as Ardour, Hydrogen and Rosegarden). None of us knows a great deal about studio equipment and such, so I would love to get some tips from people with some experience on using Ubuntu as a studio.

I was planning to put Xubuntu Edgy on the box. Xubuntu because the machine is a bit old (only 256 MB of RAM for instance). Edgy because my experience is that sound works better in Edgy than in Dapper, so getting Alsa, Jack etc set up properly should be easier. Does this sound like a wise choice?

We are also going to replace the crappy old soundcard with something better, and I could really use some tips on equipment that plays nicely with Ubuntu. Basically, we want to be able to plug in a microphone, a guitar, a bass and a keyboard somehow. It'd be nice to be able to record on at least two channels simultaneously.
As I understand it we could a) buy a mixer and connect all the instruments to this, or b) replace the current soundcard with an audio interface and skip the mixer. What are the pros and cons? If we go with the mixer, does that mean we can use a cheaper soundcard and still get the same sound quality? Our budget isn't big, so tips on cheap equiment that works good on Linux will be greatly appreciated!

As you might have guessed, I'm a complete noob when it comes to these things, so any general tips would be great. Good articles on things such as Jack would also be nice (I know about the ubuntu studio wiki already).

---

### Post by k1001001 on 2006-11-28
Sorry that I don't have any other advice to offer, but if you want a really inexpensive and simple way to record simultaneous tracks, you might want to check out an [Alesis USB mixer]("http://www.musiciansfriend.com/product/Alesis-MultiMix-8USB-Mixer-with-USB-and-DSP?sku=630166"). There's other versions with more channels, and also a Firewire version available as well. The USB version only sends L/R mains to the computer, but the Firewire version will send separate tracks to the computer. It's definitely a good way to get multi-track recording easily going for a low price, however I don't know if latency will be an issue or not. I don't own one of these, however it's been on my wish list for quite a while.

256 MB of RAM may not be enough either. I don't really know how much RAM Ubuntu uses compared to XP (I would assume considerably less), but recording and editing music requires a lot of computer power. It could be enough though. I guess you won't really know until you try it.

---

### Post by doobit on 2006-11-28
You need a lot of RAM to run smoothly. 512MB is minimum IMHO.
I don't know if the firewire audio boxes have linux drivers for them yet. I use an M-Audio FW410 professionally, but I can't use it in Linux, that I am aware of. I wish I could. I have a SBlive at home that works good, but it's noisy compared to the FW410, and doesn't have XLR inputs.

---

### Post by Hanj on 2006-11-28
Thanks for your replies. I figured 256 MB of RAM might be too little - if it turns out things run too slowly I'll just buy some more.

@k1001001: Thanks a lot for the advice. That mixer seems to do what I want, and it's pretty affordable. Do you know anything about how it works under Linux?

Also (forgive my stupidity, I'm really new to this) if I plug in a mixer in the USB port, does that mean the sound card is only used for output?

---

### Post by k1001001 on 2006-11-28
Sorry, but no I have no idea how it works under Linux. I do have a USB microphone though, and I got it to work by playing around with JACK. I imagine the mixer would work in a similar manner.

And my guess would be that you could still use the microphone (pink) or line-in (blue) inputs on your sound card in addition to the USB mixer. The mixer wouldn't turn off the sound card. If you wanted to play back sound while recording though, it would be best to go out of the soundcard so there is the least amount of latency possible.

---

### Post by doobit on 2006-11-29
The application should have choices in the preferences as to what is used for input and what is used for output. I have used a USB sound card for mic input and the onboard sound card for output to the headphones and it works no problem with Audacity. There is less latency with firewire, so I wish someone would develope linux drivers for the M-Audio and Presonis firewire boxes.

---

### Post by Hanj on 2006-11-29
I read somewhere that the [M-Audio Delta 44]("http://www.m-audio.com/products/en_us/Delta44-main.html") is one of the best supported audio interfaces for Linux (though not by the manufacturer it seems). Can anyone confirm this?

---

### Post by akselvonpaksel on 2006-11-29
Even though alsa is supposed to support all tandards compliant usb-devices:
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

it seems the Alesis mixer is not the best idea: 

[http://ubuntuforums.org/archive/index.php/t-205290.html](http://ubuntuforums.org/archive/index.php/t-205290.html)

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Alesis#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Alesis#matrix)

But further googling may give newer info than the ubuntuarchive...

---

### Post by asmok on 2006-11-30
M-Audio Delta 44, 66 and 1010 are great cards for Linux/Ubuntu.

This is one amazing project:

[http://dto.freeshell.org/notebook/KarmaPod.html](http://dto.freeshell.org/notebook/KarmaPod.html)

About Delta-serie:

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix)

Keyword is "Envy24":

[http://www.nue.tu-berlin.de/wer/batke/Download/delta66howto.pdf](http://www.nue.tu-berlin.de/wer/batke/Download/delta66howto.pdf)

Best Regards Asmo Koskinen.

---

### Post by Hanj on 2006-11-30
I guess I will look into the Delta cards then. Thanks for those links, asmok, they look really useful!

---

### Post by rune_kg on 2006-12-13
Hey

Just to clarify. A mixer will mostly have better preamps than a normal soundblaster type soundcard. So it will be an improvement over plugging straigth into the soundblaster type soundcard. But the sound will still suck as the general soundquality, signal to noise ratio and AD converters sucks.

So forget the mixer. Buy a decent pro/semipro soundcard with good linuxsupport (verifyed from several sources) and plug you mics and line inputs directly into it. 

Connect directly from your soundcard to your amp/stero/speakers

Take Care

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by asmok on 2006-12-14
I like to share some sreenshots/information about M-Audio Delta-66 soundcard.

It is great card, go for it.

I got this kind of hardware now, I upgrade PC later.

1. Ubuntu Dapper - 800Mhz Duron/256M.

2. 6 G IDE/XFS.

2. M-Audio Delta-66.

3. Alto S-8 -mixer.

4. AKG-microphone.


Pic 1

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Jack-ReZound_01.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Jack-ReZound_01.png)

I did use ReZound as a recorder with Jack.

Working with stuff was something like this: AKG-microphone -> Alto S-8 -mixer -> Break Out Box INS-1 -> M-Audio-Delta-66 -> Alsa/Jack -> ReZound.

Pic 2

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Jack-ReZound_02.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Jack-ReZound_02.png)

Jack with M-Audio-Delta-66

Pic 3

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Jack-ReZound_03.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Jack-ReZound_03.png)

I got one wire (mono) from mixer to Break Out Box (INS-1), so I double that in Jack: Capture_1 to Input_1 and Input_2 in ReZound.

Pic 4

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Alsa-Envy24Control_04.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Alsa-Envy24Control_04.png)

Of course you can use Delta-66 without Jack, with Alsa. Then you need Envy24Control - you can found as package on Dapper.

Pic 5

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Alsa-Envy24Control_05.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Alsa-Envy24Control_05.png)

DAC0 = Break Out Box OUTS-1
DAC1 = Break Out Box OUTS-2
DAC2 = Break Out Box OUTS-3
DAC3 = Break Out Box OUTS-4

Now you can control volume if you just listen Delta-66.

I will not use Egdy, but when Feisty is out I think everything is even better than now with Dapper.

Best Regards Asmo Koskinen.

---

### Post by asmok on 2006-12-15
> **asmok said:**
> I like to share some sreenshots/information about M-Audio Delta-66 soundcard.


I found out how to use it direct with ReZound without Jack.

Pic 1

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-ReZound_06.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-ReZound_06.png)

Recording to INS-2.

Pic 2

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-ReZound_07.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-ReZound_07.png)

Recording to INS-1, then pausing and switching to INS-2 and recordding to INS-2.

Great card, indeed.

Best Regards Asmo Koskinen.

---

### Post by asmok on 2006-12-16
> **asmok said:**
> I found out how to use it direct with ReZound without Jack.

Yet Another Screenshot:

[http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Audacity.png](http://www.arkki.info/howto/M-Audio-Delta-66/M-Audio-Delta-66-Audacity.png)

Now I got Audacity working with M-Audio Delta 66.

I will write howto (in Finnish) for that soundcard (Dapper, Audacity, ReZound and Jack) in a couple weeks; maybe I'll translate that in english, too.

Best regards Asmo Koskinen.

---

### Post by CadetD on 2006-12-19
I would also recommend that you take a look at m-audio Delta sound cards. 
They provide multi in/out and SPDIF, built-in mixer and have excellent support under linux. 
I personally use the Delta-44 and have had not problems. 

[http://midiman.com/index.php?do=products.list&ID=pciinterfaces](http://midiman.com/index.php?do=products.list&ID=pciinterfaces)

---

