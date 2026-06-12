---
title: "No sound from Headphone Jack Ubuntu 9.10 64 bit version"
date: 2010-01-17
forum: Multimedia Software
---

### Post by Brain_of_J on 2010-01-17
I'm dual booting Windows 7 and Ubuntu 9.10 64bit on a new HP laptop.
In Ubuntu, I'm not getting any sound from the headphone jack. I've tried a couple of different solutions but haven't had much luck. Sound works through the internal speakers in both Windows and Ubuntu. Sound through the headphone jack works only in Windows.
The sound card is a IDT 92HD75B3X5.
This is a fresh 9.10 install, save for the changes mentioned below.
I've attempted to use the gnome-alsa fix that's mentioned in a few threads, but I don't have a "Headphone" tab to "un-mute".
I've attempted to recompile the driver as mentioned in this thread
[http://ubuntuforums.org/archive/index.php/t-1255723.html](http://ubuntuforums.org/archive/index.php/t-1255723.html)
but that didn't work either.

Any suggestions would be appreciated.

---

### Post by sports.car.guy on 2010-01-17
Have you opened up a sound mixing / volume control to see if the volume is turned up and the jack for it is not muted?

---

### Post by Brain_of_J on 2010-01-17
Ok. This is truly bizarre.
After the above steps I re-booted into Windows to watch a little Hulu...
Then I re-booted back in to Ubuntu and everything seems to be working as it should. 
The strange part  is that I had re-booted in to Ubuntu several times after applying the changes mentioned above...
I'll monitor and see what happens.

---

### Post by sports.car.guy on 2010-01-17
> **Brain_of_J said:**
> Yes, i've checked there. However, I don't have an option to mute/ un-mute a headphone jack. In fact, a headphone jack is not listed there at all


If you go into the mixer app and choose settings, does it give the option to add the channel to the mixer for it?

Also what is your out put for aplay -L

It will list your hardware devices.

Here is my output for example:

my@example:~$ aplay -L                 
default:CARD=XFi                                
    Creative X-Fi, Front/WaveIn                 
    Default Audio Device                        
front:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Front speakers
rear:CARD=XFi,DEV=0
    Creative X-Fi, Surround
    Rear speakers
center_lfe:CARD=XFi,DEV=0
    Creative X-Fi, Center/LFE
    Center and Subwoofer speakers
side:CARD=XFi,DEV=0
    Creative X-Fi, Side
    Side speakers
surround40:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.0 Surround output to Front and Rear speakers
surround41:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=XFi,DEV=0
    Creative X-Fi, IEC958 Non-audio
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

---

### Post by Brain_of_J on 2010-01-17
My output is

brain@brain-Ubuntu:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
brain@brain-Ubuntu:~$

---

### Post by sports.car.guy on 2010-01-17
It appears the card is coming up properly. It is a 7.1 laptop? Unless that is incorrect it should work. What variant of Ubuntu are you using.

I am using Kubuntu myself and not subject to some of pulseaudio's little quirks. This could be one of those.

---

### Post by Brain_of_J on 2010-01-17
Well...it seems to be working now...we'll see how long that lasts.

---

### Post by sports.car.guy on 2010-01-17
That is good to hear.

---

### Post by vishyc88 on 2010-01-18
guys i too have the same problem, no output from the front audio jack. ill paste the aplay-L output here. its a dektop that im using.
jujixz@ubuntu:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
please help. thnx

---

### Post by 110686 on 2010-03-03
Hello,

I've a similar problem. I am running on a HP DV6 Laptop (dual boot, Ubuntu 9.10)and I do have sound, but when I plug in my headphones the laptop produces sound from the internal speakers, and from the headphones.
On Windows 7 my soundcard is called IDT and on Ubuntu 9.10 it is called Intel HDA. Neither do I have a option to un-mute the sound on the headphones

---

### Post by wilsontp on 2010-03-28
> **110686 said:**
> Hello,
 
I've a similar problem. I am running on a HP DV6 Laptop (dual boot, Ubuntu 9.10)and I do have sound, but when I plug in my headphones the laptop produces sound from the internal speakers, and from the headphones.
On Windows 7 my soundcard is called IDT and on Ubuntu 9.10 it is called Intel HDA. Neither do I have a option to un-mute the sound on the headphones
 
I am having the same issue on my HP tx2525nr laptop

---

### Post by spooled_u on 2010-03-28
I'm having some issues as well... here is my output...

kronusthebonus@linux1:~$ aplay -L
aplay: relocation error: aplay: symbol snd_device_name_hint, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
kronusthebonus@linux1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kronusthebonus@linux1:~$ 


Strange, no ?

---

