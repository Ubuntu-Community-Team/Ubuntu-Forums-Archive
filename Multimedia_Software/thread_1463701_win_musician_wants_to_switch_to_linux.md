---
title: "win musician wants to switch to linux"
date: 2010-04-27
forum: Multimedia Software
---

### Post by kokoshmusun on 2010-04-27
I have dual boot Win Vista and karmic.  I use Vista for recording music and Karmic for all my other work.  But Vista is unbearable (especially after discovering ubuntu).  I want to move my music to linux environment as well.  I have no idea how to, please help.

I have Phonic Firefly 302 USB audio interface, m-audio key rig 49 MIDI controller.

Should I try to set these up in ubuntu, or should I install a different distro on (eg., ubuntu studio or whatever). How do I get these recognized.  What software should I go for (I use Tracktion and Reason in Vista)? 

How to start?  I have no clues. Any pointers? 

Thanks...

---

### Post by cchhrriiss121212 on 2010-04-27
> How to start?  I have no clues. Any pointers? 
Firewire devices are only functional through jackd and the ffado driver. I googled around, and have seen that the card seems to be [supported]("http://www.ffado.org/?q=node/80"). From there you can try and get the card functional with jackd on your regular karmic install. [Here]("https://help.ubuntu.com/community/UbuntuStudioPreparation") is a great guide regarding firewire and everything else needed for audio production. The m-audio should be recognised with no configuring.

> What software should I go for (I use Tracktion and Reason in Vista)? 
One thing you should know before you start, is that linux audio programs do not work the same way as windows counterparts, so you are not going to get a like-for-like swap. What you have is a modular system with the jackd sound server acting as a central unit that connects every program to each other through a connection bay. This means you can connect any outputs to any inputs you like which gives you a very versitile platform. I wouldn't start thinking about software until you get the card running with jackd, but you will want to look at qtractor (DAW), phasex, zynsubfx and bristol (synths).

You can also search or post in the ubuntu studio forum for audio production help.

---

### Post by kokoshmusun on 2010-05-02
I am at a loss, any help is appreciated.

1) I added medibuntu repos:
> 
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

2) I installed the following packages:> 
sudo apt-get install hydrogen hydrogen-drumkits cmt caps swh-plugins tap-plugins alsa-firmware-loaders alsa-tools alsa-tools-gui alsa-firmware ardour audacious hydrogen jackd jack-rack qjackctl seq24 vkeybd zynaddsubfx patchage vlc kino pitivi acidrip ubuntustudio-menu gcdmaster blepvco mcp-plugins omins blop caps cmt fil-plugins rev-plugins swh-plugins tap-plugins dssi-host-jack dssi-example-plugins fluidsynth-dssi hexter xsynth-dssi

3) I try qjacktl and according to the error message, I do:

sudo gedit /etc/security/limits.conf

and add the following lines to this file:

  @audio          -       rtprio          100
  @audio          -       nice            -10




4) I open qjackctl and can see that the m-audio midi keyboard shows up.  But I all else seems to fail.  Here is the error message:
 p, li { white-space: pre-wrap; }  > 
[COLOR=#999999]18:34:53.466 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:34:53.756 Statistics reset.[/COLOR]
 [COLOR=#66CC99]18:34:53.787 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]18:34:54.105 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:35:11.572 Startup script...[/COLOR]
 [COLOR=#990099]18:35:11.573 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]18:35:11.976 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]18:35:11.976 JACK is starting...[/COLOR]
 [COLOR=#990099]18:35:11.977 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]18:35:11.981 JACK was started with PID=2301.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Your system has an audio group, but you are not a member of it.
 Please add yourself to the audio group by executing (as root):
   usermod -a -G audio (null)
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]18:35:11.990 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]18:35:11.991 Post-shutdown script...[/COLOR]
 [COLOR=#990099]18:35:11.992 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]18:35:12.403 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]18:35:14.142 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]



I also understand that there are different linux kernels for audio production (to reduce latency).  Should I try to replace my regular ubuntu kernel with one of those.  Or should I just keep my ubuntu working environment intact and install a separate distro for audio production in my laptop like MUSIX or UbuntuSTUDIO?

I have no idea what I'm doing, this is freaking me out a bit, complicated.  Help?  
Thanks in advance...

---

### Post by hxcobd on 2010-05-02
I'd recommend clicking the link in my signature and watching my tutorials on setting up Realtime audio and JACK in linux.

After following the steps in them, feel free to repost any questions and I (we) will do our best to help you.

To answer your question, though, no, you don't need a new distro for audio work. By adding those few simple lines in your limits.conf file, you're basically giving yourself the same performance that a "dedicated" audio distro would give you, more or less. They just pack in a boatload of audio programs, some of which may be useful to you, some which might not.

---

### Post by kokoshmusun on 2010-05-02
Those videos are awesome, I got further, but the main problem is I don't know how to get ubuntu to recognize my phonic firefly 302 usb audio interface.  When I start jack and go to setup, all I have are the following: plughw:0, (default), /dev/audio, hw:0, hw:0,0, /dev/dsp.

None of these seem to be the usb interface.  How do I get it recognized?

---

### Post by cchhrriiss121212 on 2010-05-02
Sorry about my earlier post, I thought the firefly was a firewire device so ignore that ffado stuff. Could you open a terminal and type "aplay -l" and post the output? This will show whether the device is recognised.

---

### Post by kokoshmusun on 2010-05-03
Yeah, it's a USB, not a firewire. Thanks for the help.

I plug in the USB audio interface and turn it on. I do aplay -l and this is what I get:

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


This is a laptop so what is listed must be the internal sound card. There is no evidence that the USB device is recognized, right?  What do I do?

---

### Post by kokoshmusun on 2010-05-13
bump?

---

### Post by JakobIndigoBlue on 2010-07-24
I just switched over to ubuntu, and I'm trying to figure out the best route to getting my audio production up and running. I am sick of the Windows nightmares and hassles and a good friend suggested ubuntu-problem is, he's not an audio guy. Obviously,I have a learning curve on my hands and that is fine, but just googling isn't helping a lot.What do you guys suggest?I downloaded a couple things, not realizing that I was downgrading my OS by installing them.Bear in mind I am a COMPLETE NOOB to this.Can someone help?

---

### Post by cchhrriiss121212 on 2010-07-24
> **JakobIndigoBlue said:**
> I just switched over to ubuntu, and I'm trying to figure out the best route to getting my audio production up and running. I am sick of the Windows nightmares and hassles and a good friend suggested ubuntu-problem is, he's not an audio guy. Obviously,I have a learning curve on my hands and that is fine, but just googling isn't helping a lot.What do you guys suggest?I downloaded a couple things, not realizing that I was downgrading my OS by installing them.Bear in mind I am a COMPLETE NOOB to this.Can someone help?
Things to consider before trying out ubuntu audio for music production:

[LIST]
[*]Is your hardware supported? Do you use an external or internal sound card for your work? If so check that it is in the [ALSA database]("http://www.alsa-project.org/main/index.php/Matrix:Main")
[*]Windows programs, DAWs, VSTs, plugins etc. are not natively supported. So ask whether you are happy swapping to FOSS and that it can handle what you want to do. You can get VSTs running but it is fiddly and invlolves either using WINE or using them in an environment they were not made for.
[*]It will take a few weeks of learning just to get comfortable and into a decent work flow (at least it did for me). So make sure you have the free time to get set up.
[/LIST]
If you think all that is fine then try installing the ubuntu-studio package from synaptic and explore. Try out Hydrogen first which is a top quality drum sequencer.
I'm not sure what you mean when you say "I downloaded a couple things, not realizing that I was downgrading my OS by installing them", anything you install will not downgrade your OS and can be removed just as easily.

> There is no evidence that the USB device is recognized, right?  What do I do? 	
To anyone else who finds this thread, this device is not supported on Linux.

---

### Post by kokoshmusun on 2010-11-21
I bought a new 64-bit PC for audio production but I'm stuck with Windows 7 because of my audio card (Phonic Firefly 302 USB) which is not supported in Linux as the last post said. 

A friend of mine is willing to get me a new interface around the same price range as mine, and trade it with me so I can use linux.

Which audio interface, if any, works out of the box in Linux?  I'm a little discouraged having wasted too much time trying to get my current interface working in Linux, so I need to find one that definitely works with minimal tweaking of the linux system (I'm thinking about using puredyne, btw).  

I'm thinking about the good old M-audio Mobilepre.  Anyone know this works for sure? 

If it doesn't look like this is going to happen, I will unfortunately have to stick with Win7.

---

### Post by cchhrriiss121212 on 2010-11-21
Hi again,
The mobilepre is a class compliant which means it will work fine out of the box. You could also look at the Edirol UA25EX or UA25. There are also plenty of PCI or firewire cards that work well, which are superior interfaces to USB IMO.

---

### Post by kokoshmusun on 2010-11-22
Thanks, I'd actually like to try a PCI card for once.  The alsa-project website is hard to parse.  When a card is listed, does it mean it works?  When I click on details, I get some code.  I don't know what it means.  

Would anyone recommend a specific PCI card?  Somebody in a different forum was happy with M-Audio Delta 1010LT.  Any ideas?

---

### Post by cchhrriiss121212 on 2010-11-22
The delta range is very well supported, and has good value for money. They do have a bug with pulse that will mean they won't work out of the box, but the solution takes literally 1 minute to apply. See here:
[http://newyork.ubuntuforums.org/showpost.php?p=9241410&postcount=10](http://newyork.ubuntuforums.org/showpost.php?p=9241410&postcount=10)

Regarding the ALSA project, anything listed there will work, but some devices have reduced functionality which will be noted in the notes column.

---

### Post by Sylos on 2010-11-22
+1 for the M-audio delta cards. I have one that I got working just by uninstalling PulseAudio (not necessarrily the solution I recomend but it works for me).

---

### Post by kokoshmusun on 2010-11-22
How about PCIe, which I just found out and seems to be a faster newer version of PCI.  There is the E-MU 0404 PCIe, and not many others that are as cheap.  The 0404 PCI is listed by Alsa project but not the PCIe.  And then I guess I have to get a preamp or a mixer for any PCI/e card.

---

### Post by cchhrriiss121212 on 2010-11-22
PCIe cards won't give you much advantage over regular PCI. You also need a spare slot on your motherboard as standard boards only have one which is used by the video card (if you have one installed).

A built-in pre-amp is a good benefit of a USB device, which I had not considered. Mixing can be handled by software nowadays, but some still prefer to have hardware mixing capabilities. 

It all depends on how many inputs and outputs you like to have, so consider what you need now and what you may need in the future, I don't need many so I went with a Delta 44.

---

### Post by kokoshmusun on 2010-11-23
Most of the time I record by myself, but sometimes I would like to record with another player, that is, 2 guitars at the same time.  I've never done that before with a computer yet.  Since the Audiophile 2496 is 4 x 4, I assume it can be done with that.  I've done some research and concluded that a preamp is better than a mixer for my purposes, and I've had an ART before that was great.  So, I'm thinking about getting the Audiophile 2496 + some ART preamp.  I'm going to trade in my Phonic USB for these, and hopefully it will give me the chance to discover music making in Linux as well.  

But then there's also the question, as I discovered on the web, of how to connect headphones/monitor to the Audiophile.  It's beginning to get a bit too complicated compared to an all-in-one USB card, and I'm wondering if it's worth the trouble now.  Maybe there is a PCI card that does all of this (preamp, headphone amp, etc.)?

I appreciate the replies, take care.

---

### Post by cchhrriiss121212 on 2010-11-23
It seems like the UA-25 can actually handle all that, and will be easier to set up. Take a look here:
[http://www.roland.com/products/en/UA-25/index.html](http://www.roland.com/products/en/UA-25/index.html)
[http://alsa.opensrc.org/index.php/Edirol_UA-25](http://alsa.opensrc.org/index.php/Edirol_UA-25)

---

### Post by Sylos on 2010-11-23
Hello again.

As far as preamps are concerned I use the M-audio OMNI breakout box (attaches to Delta 66 PCI card) that has two Preamps built into it that can be switched between Mic and Line level. It also has a host of monitoring and other input/output functions that Im ashamed to say I dont use or really know about - I am a one man band who just records guitar and then programmes drums etc.

[http://www.boomerangsounds.co.uk/product.php?xProd=57](http://www.boomerangsounds.co.uk/product.php?xProd=57)

---

### Post by kokoshmusun on 2010-11-23
Sylos, can you theoretically record two tracks at the same time (e.g., two guitar, or a guitar and vocals) with that system, or would you need something additional (e.g., a mixer)?

Chris1212, I know you've recommended the UA-25 before, and it totally is easier (all the cards I've owned before were USB or firewire) but if I'm getting a new card, since I have a desktop now, I really wanna try a PCI.  I found the Echo Gina 3G to be a good choice.  It's nicely priced, you can plug headphones into it, it's got 2 preamps, and phantom power as well I think.  Too bad it's not available in my country, but next time I fly out, I might get this.  

The following link has been really useful in comparing PCI cards: [http://www.tweakheadz.com/audio_interface_pci_comparison_chart.htm](http://www.tweakheadz.com/audio_interface_pci_comparison_chart.htm)

---

### Post by Sylos on 2010-11-23
> **kokoshmusun said:**
> Sylos, can you theoretically record two tracks at the same time (e.g., two guitar, or a guitar and vocals) with that system, or would you need something additional (e.g., a mixer)?



Yes you can. When you install the card you will need to install the Envy 24 controller for ICE1712 chipset cards (i think this comes automatically if you select to install all the studio packages - it certainly installs by default when you install the Ubuntu Studio distro). You just need to use the mixer controls on this to set the levels and then select the relevant inputs on your DAW (I use Ardour). I have just tested the above using a mic on channel 1 and my guitar DI into channel 2 and it worked flawlessly.

Check out the manual on M-audios site if you want a full breakdown of what you can do with it.

Good Luck

Also - +1 for Tweakheadz lab - spent many a good hour reading the tweakers reviews and guides.

---

### Post by kokoshmusun on 2010-11-23
Thanks a lot man, it's gonna be a while until I can get this gear and set it up but I appreciate the tips.

---

