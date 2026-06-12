---
title: "USB Sounds not working"
date: 2012-01-19
forum: Multimedia Software
---

### Post by chris1neji on 2012-01-19
I have small speakers left and right. That are USB power. I connected it to the USB port on my computer and a little light on the speaker goes on. There is no power cable required. I have tried increasing Volume control. One note however is that Volume control responds to Vol + and Vol - buttons that are on the speakers itself.

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)

I went over this post. I was able to follow up on some parts but its so much info it's very daunting. What would you like me to post or do ?

I feel like i need assistance. I am new to Lubunto. I can click around and type but that's about it. Don't understand half the commands or anything advance.

Sorry to bother you guys. I am off to sleep it's 2 AM now and i couldn't figured this out


EDIT:

I plug in my Senheissers Headphones, they use a mm jack and not USB. They work and sound amazing like always. Just wanted to include extra info. Please help someone :)

---

### Post by chris1neji on 2012-01-19
Any suggestions? Should i just buy new speakers?

---

### Post by amjjawad on 2012-01-20
Hello and Welcome to Ubuntu Forum :)

Thanks for choosing and using Lubuntu!

You are not bothering us at all but you need to include more details in your thread(s) so that we can help you and guide you to the right path. No worries, we shall do this step by step :)

I have no such hardware (USE Speaker) to test at my end but it's ok.

What release of Lubuntu are you using?

As long as the sound is working, it could be the speaker itself but that is just a guess, nothing for sure.

Do you have another machine we can try your speaker on? 
Have you tired to connect your speaker to another USB port?
Is this a PC or a Laptop?

---

### Post by chris1neji on 2012-01-21
my os info
> 
-Version-
Kernel		: Linux 3.0.0-14-generic (i686)
Compiled		: #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011
C Library		: Unknown
Default C Compiler		: Unknown
Distribution		: Ubuntu 11.10
-Current Session-
Computer Name		: Linux
User Name		: sosa (CSosa)
Home Directory		: /home/sosa
Desktop Environment		: LXDE (Lubuntu)
-Misc-
Uptime		: 27 minutes
Load Average		: 0.78, 0.63, 0.40


I tried the speakers on my windows xp and windows 7 machine they worked it loaded drivers and it worked.

I tried it in different USB ports front and back and it always turned on
(a little light turns on when its plug to usb)

I am on a desktop

---

### Post by zeeboos on 2012-01-21
I am new to Ubuntu also.  I am using Ubuntu 10.11 64 bit and I had sound problems also.  I resolved mine by doing these steps.  I hope your Ubuntu is similar enough that you can follow these steps.  I have learned most things in Ubuntu only take a single click to work so try this.  On the left side when you bring the mouse pointer to the edge of your screen a list of Icons should appear. Single click the system settings Icon. ( This icon looks like a cresent wrench with a gear behind it.) then single click sound.  You shoud then have a choice of tabs, choose hardware.  inside hardware try analog output.  There are also other tabs before you went to hardware and one of them is output. Try that you may have it set to headphones.  Notice in hardware and output there is an arrow bottom right that gives other options.  This is similar to sounds in the control panel in windows.  No need to use the terminal.  hope that helps you zeeboos

---

### Post by chris1neji on 2012-01-21
sadly the desktop user interface are not alike. What you just mention was not on my Lubunto version.

However i found that my speakers do work with Lubunto.

I did

> Step 1
If you are using Ubuntu 11.10 (Oneiric), then execute this command and reboot:


sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
source [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Then i opened up GNOME Mplayer
i didnt get sound and i was angry
I clicked on on Gnome Mplayer configuration.
AUDIO OUTPUT : i changed it to USB AUDIO (USB AUDIO) (ALSA)
PC MIXER was left alone PCM,0
AUDIO CHANNELS TO OUTPUT : it was on 5.1 surround and now stereo.

Basically i think the fault is Lubunto not being able to set my audio device properly. I wish there was a control panel i would have been able to do this without coming back here. Not that i dont like you guys but i myself offer windows seven support in other forums i cant always reply 24/7

New objective help me change my default sound device to USB AUDIO (USB AUDIO) (ALSA)

---

### Post by marinara on 2012-01-21
use alsamixer from the terminal or install gnome-alsamixer from synaptic.

I remember having a similar problem trying to turn off HDMI audio on my monitor.  Never did figure out how to do it, I ended up having to edit some config file deep in the bowels of linux or something just to disable the HDMI audio driver.  I blame pulseaudio.

---

### Post by chris1neji on 2012-01-21
i downloaded the gnome alsa mixe.

I see my options in there how do i set it to play by default to my USB MIXER?
i can get my music to play right by using GNOME Mplayer and going into preference and changing output. However i don't have that luxury option in sites like youtube. It's very important for me for this to work.

---

### Post by marinara on 2012-01-21
chris, I'm sorry i told you that alsamixer will do it.  It won't.

We need to make a small fix.

1.  post the output of this command aplay -L, then create a file called ~/.asoundrc with a slngle line like this:  > pcm.!default front:chris_usb_card_goes_here
I did this inside vmware from these instructions and it works well with my usb headphones
[http://alsa.opensrc.org/.asoundrc#Default_PCM_device](http://alsa.opensrc.org/.asoundrc#Default_PCM_device)

my aplay -L looks like this
> 
rich@rich-virtual-machine:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=AudioPCI
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Default Audio Device
front:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Front speakers
rear:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC1
    Rear speakers
surround40:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct sample mixing device
dmix:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct sample mixing device
dsnoop:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct sample snooping device
dsnoop:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct sample snooping device
hw:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct hardware device without any conversions
hw:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct hardware device without any conversions
plughw:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Hardware device with all software conversions
plughw:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Hardware device with all software conversions
default:CARD=Set
    C-Media USB Headphone Set, USB Audio
    Default Audio Device
front:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    Front speakers
surround40:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    Direct sample mixing device
dsnoop:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    Direct sample snooping device
hw:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    Hardware device with all software conversionsI look for these linesfront:CARD=Set,DEV=0
    C-Media USB Headphone Set, USB Audio
    Front speakers
will be different on your pc, depending on the name of your usb headphones.

then i create a new text file in my home directory called 
.asoundrc

you can do this from the terminal by typing
leafpad ~/.asoundrc

i type one line into leafpad and save it.  this line is:
> pcm.!default front:SetYou will need to replace the "front:Set" with whatever you found from the output of your aplay -L command
those lines we found from the output, you will be copy paste the "front" part and also copy paste the part after the 
"CARD="

if you restart applications, your headphones should start working.  

You are welcome to ask more questions, especially if I wasn't clear about the instructions.

---

### Post by chris1neji on 2012-01-22
Yeah im really new to linux... but i got this so far


sosa@Linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AUDIO [USB  AUDIO], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0



Please advice with detail on how to continue

---

### Post by davethewave83 on 2012-01-22
> **chris1neji said:**
> Yeah im really new to linux... but i got this so far


sosa@Linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AUDIO [USB  AUDIO], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0



Please advice with detail on how to continue

I've noticed Ubuntu doesn't have a very solid way of selecting a default sound device with ease, I'm not sure about Lubuntu as I have not yet tested it (will do that today) Kubuntu,however, has a very nice sound program for selecting the default sound device. In Kubuntu, it is extremely easy. Unfortunately I love Gnome too much.

I'm sure Lubuntu is detecting your device, but it's not selected as default and so, no sound is coming through it. 

In Ubuntu, I can click the speaker icon (volume) go to sound preferences, click hardware and then disable the built-in audio device, making the USB audio default. 

During boot up, the startup sound still plays through the internal sound card, but after logging in, the sound is then USB-audio.

I know you are in Lubuntu, but maybe this will help you.

---

### Post by marinara on 2012-01-22
looks like you didn't capitalize the l.
needs to be aplay -L
not aplay -l

please post the output again and we will continue :)

---

### Post by chris1neji on 2012-01-22
case sensitive interesting

> 
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Front speakers
surround40:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.0 Surround output to Front and Rear speakers
surround41:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Direct sample mixing device
dmix:CARD=I82801DBICH4,DEV=4
    Intel 82801DB-ICH4, Intel 82801DB-ICH4 - IEC958
    Direct sample mixing device
dsnoop:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Direct sample snooping device
dsnoop:CARD=I82801DBICH4,DEV=4
    Intel 82801DB-ICH4, Intel 82801DB-ICH4 - IEC958
    Direct sample snooping device
hw:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Direct hardware device without any conversions
hw:CARD=I82801DBICH4,DEV=4
    Intel 82801DB-ICH4, Intel 82801DB-ICH4 - IEC958
    Direct hardware device without any conversions
plughw:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Hardware device with all software conversions
plughw:CARD=I82801DBICH4,DEV=4
    Intel 82801DB-ICH4, Intel 82801DB-ICH4 - IEC958
    Hardware device with all software conversions
front:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    Front speakers
surround40:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    Direct sample mixing device
dsnoop:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    Direct sample snooping device
hw:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    Direct hardware device without any conversions
plughw:CARD=AUDIO,DEV=0
    USB  AUDIO, USB Audio
    Hardware device with all software conversions



@dave
nope no easy way of changing default selection

---

### Post by MoreOrLess on 2012-01-23
Install pavucontrol package if using pulseaudio.

If not, modify /etc/modprobe.d/alsa-base.conf file. You'll see something like this:
```
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```
Change the -2 to a 0 and reboot (or sudo alsa force-reload).

---

### Post by chris1neji on 2012-01-23
I complete all the steps you mention,
New problem arises when attempting to save.
>I do the modifications, 
>>click save, 
>>>new prompt asking to overwrite,
>>>>I cli ck yes
>>>>>error: can't open file to write

---

### Post by marinara on 2012-01-23
yeah chris. Check if you have pulseaudio installed.

at the terminal do
 >  pulseaudio --version


if you get an error, it's not installed.

sorry I should have had you check for pulseaudio first thing.

---

### Post by marinara on 2012-01-23
chris I think you may have pulseaudio.  so, you will not need to edit  /etc/modprobe.d/alsa-base.conf

---

### Post by chris1neji on 2012-01-23
sosa@Linux:~$ pulseaudio --version
pulseaudio 1.0
sosa@Linux:~$

---

### Post by chris1neji on 2012-01-23
i downloaded and install 
 pavucontrol

---

### Post by chris1neji on 2012-01-23
done :) 
fully working audio :)
Wow it's going to take me years to even get the basics on this OS...

Anyways where can i find my version of Add and Remove programs?

also how can i capture screen images there is something that is bugging me. Where volume control/internet connection/there is a gap about ------------ and then it shows the hour.

---

### Post by marinara on 2012-01-23
synaptic package manager is the equivalent of add/remove programs
to take screenshots, use synaptic to download a program called shutter.

---

### Post by MoreOrLess on 2012-01-23
> **chris1neji said:**
> I complete all the steps you mention,
New problem arises when attempting to save.
>I do the modifications, 
>>click save, 
>>>new prompt asking to overwrite,
>>>>I cli ck yes
>>>>>error: can't open file to write

You need root permissions (sudo before editor command).

---

### Post by Dennis N on 2012-01-23
> **chris1neji said:**
> 

...also how can i capture screen images there is something that is bugging me. 

Just to point out:

Lubuntu has a default screen capture program installed that takes a screenshot in the background when Print Screen is pressed. Results are time stamped and placed in your home folder without interrupting what you were doing with a save file dialog. Press Print Screen and try it out.

---

