---
title: "Silent Soundblaster 24 live USB"
date: 2010-07-24
forum: Multimedia Software
---

### Post by OwenG on 2010-07-24
My sound card (Soundblaster 24 live! USB) stopped  working shortly after upgrading to 10.04. everything was fine until the upgrade as well a immediatly after, so I assume that an update was to blame.

If I boot the PC off a live CD, all is well and the sound card works fine.

I've tried running 
aplay -l 
but it assured me that I do not have a sound card on the system to setup !!!

Any Ideas as to how I find the broken config file or busted driver?

---

### Post by OwenG on 2010-07-25
After going through a few more threads of other peoples sound card problems I've used

[COLOR="Navy"]lsusb[/COLOR]

and got

[COLOR="Navy"]Bus 002 Device 002: ID 041e:3040 Creative Technology, Ltd Soundblaster Live! 24-bit External SB0490[/COLOR]

another output (I managed to loose the command) gave

[COLOR="Navy"]card1 : External [SB Live! 24bit external]
device0: usb audio [USB Audio]
subdevices 1/1
subdevice #0 : subdevice #0[/COLOR]

So the system kind of knows that they are there.

Does any one know any other command that will through any light on the situation?

---

### Post by lidex on 2010-07-26
Try re-installing alsa after removing old config files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by Graemej on 2010-07-31
I have a similar problem with my SB0490 where there is no capture working. The card is there and software using it can see the hw:1,0 input and update interrupts with no capture errors but no sound passes through the card. The play works just fine.

I have tried the purge and re-install of alsa and running it as 

portaudio:(hw:1,0) or 
hw:1,0

A friend with a 64 bit kernel has a card which works fine on that. I am using the rt kernel but have tried also on latest release kernel. I sure would like to get this fixed but think it is an alsa bug.

---

### Post by OwenG on 2010-07-31
Thanks for the excellent reply **lidex**, my Favourite OS is now making all the right noises thanks to your help. I no longer have to resort to the dual boot Vista 64 ultimate to hear stuff. The relief is palpable.

Thanks also to **Graemej**. I'm running the 64bit kernel and got into this pickle so I don't think it was the problem.

---

### Post by Graemej on 2010-07-31
Hi OwenG,

Great news about your sb live! I hope I don't need to upgrade to the 64 bit kernel but it is looking more and more like the solution in the short term. I am becoming more convinced that it is a bug in the alsa/32 bit kernel. Everything shows as I would expect on the 32 bit but just doesn't work. At least I am pleased for you

```

gvj@gvj-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 21
 1 [External       ]: USB-Audio - SB Live! 24-bit External
                      Creative Technology SB Live! 24-bit External at usb-0000:00:1d.0-1, full speed

```

Cheers, Graeme

---

### Post by OwenG on 2010-07-31
Hi Graemej,

Have you tried **Lidex**'s fix? It will update alsa to the newest verion as well as reset the config file.

Do you use the internal sound card? the SB 24 Live! runs rings around it sonically. Personally I'd disable it in the BIOS. It's one less thing to fault find.

I hook mine up to a Cambridge Audio Azur DacMagic 24/192 upsampler via a TOSlink. The combination sounds great.

Cheers, OwenG

---

### Post by Graemej on 2010-07-31
Hi OwenG,

I need both sound cards as I use them for a software defined radio. I use the SB0490 for the main channels to process the radio signals with fft's and other phase and filtering algorithms and access the card at the hardware level. The internal SigmaTel is used for the microphone and speaker amplifiers. The setup works fine in windows but of course I have no capture for the SB0490 in Linux. Apart from this problem there is no reason for me to boot in windows so I really want to fix this so I can get rid of the dual boot and recover the hard drive space.

Yes I have run Lidex's alsa install script and the Ubuntu synaptic install. I am not using the latest RT kernel and could try that but I think it is mostly aimed at getting UAC2 implemented but then again as it is a USB standard it may affect my external card. It is really frustrating and compounded by my not really knowing much about what I am doing. I have downloaded the Fedora Live iso last night and shortly will burn a CD and see if another distribution works.

Cheers, Graeme

---

### Post by Steve R. on 2010-08-08
> **lidex said:**
> Try re-installing alsa after removing old config files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

Also have a now silent SB 24 card.  The solution above did not work for me.  I have an Athlon64 dual core processor. 
Synaptic Package Manager lists a variety of possible choices, but I don't which would be potentially applicable.
Any other thoughts?

---

### Post by lidex on 2010-08-08
*Steve R:*
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by Steve R. on 2010-08-08
> **lidex said:**
> *Steve R:*
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

Thanks for responding. Problem SOLVED!  Evidently, the box "**IEC958**" in GNOME ASLA Mixer somehow became checked.  When I unchecked it, the sound worked.

Since the sound card was not working; I installed GNOME ASLA MIXER in hopes of having a better graphical representation.  I had been randomly changing the hardware settings under System -> Preferences -> Sound but nothing seemed to work. So I installed GNOME ASLA Mixer and started checking/un-checking the various options. Finally, when I unchecked the box "**IEC958**" the sound came back with a big loud bang.

I have no idea how that box became checked, but in case others have this this issue with their Sound Blaster; un-checking "**IEC958**" GNOME ASLA Mixer may work.  The Sound Blaster is also (harwdare) set to Analog Stereo Duplex. 

Again thank you very much for responding.

PS: I did a search (click) on "**[IEC958]("http://alsa.opensrc.org/DigitalOut")**".  Evidently it is a digital standard that is obviously incompatible with the Sound Blaster in analog mode.

---

### Post by ikonitas on 2010-10-15
[http://www.alsa-project.org/db/?f=952c3dbfff20d85c340a9c72f7f130365222cbfb](http://www.alsa-project.org/db/?f=952c3dbfff20d85c340a9c72f7f130365222cbfb)

I am still having a trouble with my external sound card :
Bus 001 Device 007: ID 041e:3040 Creative Technology, Ltd SoundBlaster Live! 24-bit External SB0490

Internal is working fine , but i want my external sound card make as a MAIN sound card 
```
alsaplayer -o alsa -d hw:1,0 /home/masteris/Music/mystical002.mp3
```its not playing any sound 

thanks

---

