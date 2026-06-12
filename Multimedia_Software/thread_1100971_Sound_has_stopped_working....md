---
title: "Sound has stopped working..."
date: 2009-03-19
forum: Multimedia Software
---

### Post by MadnessRed on 2009-03-19
Hi, fo rsome reason sound has stopped working on Ubuntu for me. It used to work fine but now it has jsut stopped, I have install Skype and put the PC in a new case and added a DVD drive since I last remember it working.

If anyone has any ideas to the cause / a fix I would be very greatful.

I have searched Google but nothing I found looks like my roblem however I will keep searching as well.

Here is the info I think that will be useful, if you need any more info please jsut ask.

> $ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xff5ec000 irq 22
 1 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC655 at 0xee00, irq 23

Sound cards, I have 2,
ATI HD3850 HDMI ouput includes sound.
Realtek AC97 on Abit IP-95 (my default sound card)

When I go to sound and press Test is runs fine but with no noise, no errors either. I have turned up all my volumes and there is nothing muted.

---

### Post by MadnessRed on 2009-03-25
*bump*

---

### Post by markbuntu on 2009-03-26
It appears that the ati hdmi is being detected first and so is the default so all your sound is directed to it instead of the on-board AC97. You can go here about fixing that.

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

If you are having problems after that go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by MadnessRed on 2009-03-27
Those topics don't seem to be working, ill go through what I did.

> madnessred@anthony-desktop:~$ sudo gedit /etc/modprode.d/alsa-base
[sudo] password for madnessred: 
This opens up a blank file.

> madnessred@anthony-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_via82xx

> sudo apt-get install asoundconf-gtk
I install asoundconfig-gtk

> madnessred@anthony-desktop:~$ asoundconfig-gtk 
bash: asoundconfig-gtk: command not found
Doesn't seem to want to run though.

If I go to 
System > Preferences > Default Sound Card,
no difference when I change it.

> madnessred@anthony-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_via82xx

Another check on card order.

So I figured maybe I had to write the file form scratch. So ehre is what I think the file should be
```
options snd_hda_intel index=0
options snd_via82xx index=1
```
> madnessred@anthony-desktop:~$ sudo gedit /etc/modprode.d/alsa-base
So I open the file and add in the text, however when I save ti says file not found.

So I tried to do a save as an create the file but it appears the modprobe.d directory doesn't exist. To check I tried to cd to that directory.
> madnessred@anthony-desktop:~$ cd /etc/modprode.d/
bash: cd: /etc/modprode.d/: No such file or directory

Anyway I decided to take a look at my etc folder and see what I could fiddle with, 
> sudo nautilus
And then I went to etc and there was a directory modprobe.d, so I went into the directory to see what was there and there were several files including alsa-base.

Anyway I opened up that file and amended it to this...
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

#Lets add this stuff from the ubuntu forums
options snd_hda_intel index=0
options snd_via82xx index=1
```

So I saved it and ran the System > Preferences > Sound program and still nothing. I am gonna keep fiddling and see if I can persuade it to like it now.

---

### Post by markbuntu on 2009-03-27
You can find asounconf-gtk in the System/Preferences menu as Default Sound Card.

---

### Post by MadnessRed on 2009-03-27
yh i have the Default Sound Card installed, I though I mentioned it, when I open it, what should be displayed on the <select>? atm its balnk when I first open it, I choose my card then press quit

---

### Post by markbuntu on 2009-03-27
Well, I was hoping to avoid this but you have to go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by MadnessRed on 2009-03-27
> **markbuntu said:**
> Well, I was hoping to avoid this but you have to go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

hm it doesn't seem to be working still. When I play music I can see the volume meter bars changing but there is not sound. It really weird coz it always used to work.

---

### Post by markbuntu on 2009-03-27
If the volume bars are moving then the driver etc is all working. You just need to direct it to the proper device and make sure the volume is turned up. If that is the pulsuaudio volume meter then open the pulseaudio volume control and right click on the stream in the Playback tab. See where that gets you

---

### Post by MadnessRed on 2009-03-27
> **markbuntu said:**
> If the volume bars are moving then the driver etc is all working. You just need to direct it to the proper device and make sure the volume is turned up. If that is the pulsuaudio volume meter then open the pulseaudio volume control and right click on the stream in the Playback tab. See where that gets you

its going to
> ALSA PCM on front:1 (VIA8237) via DMA

---

### Post by markbuntu on 2009-03-27
Ok, that's progress of some sort. It is trying to play to the front speakers on your sound card. In the Output Device section see if the bars are moving for that device. If they are not, see if you can push up the sliders. Also make sure the little shield icon is not greyed out. click on the little speaker mute icon and you can tell.

If the bars are moving check your speaker connections.

---

### Post by MadnessRed on 2009-03-28
I have front audio on my motherboard but nothing plugged into it.

I am currently booted into windows and sound is working fine, gonna check all the channels.

...

ah, we may have a problem...

my front speakers (output) doesn't work,
my centre / sub works and my rear work.

By switching wires. All my cables work, and all the individual speakers work, it just seems that the front l/r audio out does not work. hm, perhaps a motherboard with sound 5mm away from the pcix slot is not a good idea :)

well I have been looking for a new mobo for a while to go crossfire but until then is there a way I can set my audio to surround sound in ubuntu so I cam at least get read and center outputs?

---

### Post by markbuntu on 2009-03-29
You can remap the outputs.

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

---

### Post by MadnessRed on 2009-03-30
Hi, thanks, I found a USB sound card though, which I have plugged in but your post was useful in configuring it to work in 5.1

---

### Post by markbuntu on 2009-03-30
Well, usb can be a cheap and easy solution. There are so many problems with hda sound chips because of OEM tweaks that it is very difficult for the alsa people to keep up.

---

### Post by MadnessRed on 2009-03-30
hda?

and yh, usb sound card is not a permanent solution as its not mine and I need to return it some point.

also are there any sound cards to avoid with ubuntu. ones which dont work that well.

---

### Post by markbuntu on 2009-03-31
Definitely do not even consider anything by creative, especially the X-fi line. Creative has been extremely non-helpful to linux users since day one so all the drivers had to be painstakingly reverse engineered and the ones they did eventually come out with are crap. They do not deserve your money.

I remember back around 1994 that creative was actively trying to stop people from writing linux drivers for the SB16 card.

If you want a good card for short money, there are a lot of c-media based cards that work OOB.

---

### Post by MadnessRed on 2009-03-31
> **markbuntu said:**
> Definitely do not even consider anything by creative, especially the X-fi line. Creative has been extremely non-helpful to linux users since day one so all the drivers had to be painstakingly reverse engineered and the ones they did eventually come out with are crap. They do not deserve your money.

I remember back around 1994 that creative was actively trying to stop people from writing linux drivers for the SB16 card.

If you want a good card for short money, there are a lot of c-media based cards that work OOB.

Wow, ok, the USB sound card was a Creative SoundBlaster Live! which worked straight way, all I did was change the default sound card and didn't even need drivers. Guess I was lucky. :)

But that info on the XiFi range was very useful as I was considering getting one. Many thanks for the info.

I what kind of quality of the c-media sound cards? A search on ebay seems to only give me cards going for 99p buy it now being sold from hong kong.

---

### Post by markbuntu on 2009-04-01
Diamond and SIIG sell cards with c-media 8768 chipsets. I have a SIIG Soundwave 7.1 PCI that was around $40 and it is as good if not better than similar price Creative cards. They are very good for the price range.

There are specs at newegg and probably better prices. It will work great for your windows. It also has digital in and out which not many cards have and the alsa driver has pcm capture which is handy.

---

### Post by MadnessRed on 2009-04-01
> **markbuntu said:**
> Diamond and SIIG sell cards with c-media 8768 chipsets. I have a SIIG Soundwave 7.1 PCI that was around $40 and it is as good if not better than similar price Creative cards. They are very good for the price range.

There are specs at newegg and probably better prices. It will work great for your windows. It also has digital in and out which not many cards have and the alsa driver has pcm capture which is handy.

OK thanks, I'll keep an eye out for them. Many thanks for all your help :) A bit off topic but have the Ubuntu forums gone a strange colour for you? Maybe Aprils fools or something.

---

