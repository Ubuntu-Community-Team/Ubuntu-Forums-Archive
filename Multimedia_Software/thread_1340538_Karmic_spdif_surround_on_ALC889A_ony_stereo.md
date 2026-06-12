---
title: "Karmic: spdif surround on ALC889A ony stereo"
date: 2009-11-28
forum: Multimedia Software
---

### Post by electrin on 2009-11-28
I upgraded to Karmic yesterday with the hope that Karmin would solve my issues with getting digital surround sound.

I had IEC958 out on Jaunty but no surround. Now when I've configured pulseaudio to the best of my understanding I can only get stereo sound from the IEC958. ( and its played on the rear speakers)

From what I understand, the IEC958 is detected as stereo only.

aplay -l give produces:
 ```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```aplay -L produces:
```
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

```
In pulseaudio configuration the IEC958 shows up as IEC958 stereo output and all I get when running ```
speaker-test -Dplug:pulse -c6 -l1 -twav

``` is stereo sound from the rear speakers. I've about to freak out and remove pulseaudio completely and just use alsa.

Anyone got any ideas what I't might be?
Oh, And yes 've changed daemon.pa to use 6 channels.

---

### Post by Corbelius on 2009-11-29
Same problem here. Digital output is only stereo.

```
@ubuntubox:~/Desktop$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
```

```
@ubuntubox:~/Desktop$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC889A Analog [ALC889A Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: ALC889A Digital [ALC889A Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```

---

### Post by udude on 2009-12-13
+1 here, with ALC888
After upgrade to karmic I was hoping to see "Digital Surround IEC958" in the pulseaudio volume control applet :)

$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

*Bump*

---

### Post by udude on 2009-12-13
btw, suppose I want to bypass pulse and force the 5.1 digital audio directly through ALSA. I wonder if there's some fancy mplayer (or other) commandline for that...

---

### Post by nicoloks on 2009-12-13
My full mplayer command line in Mythtv is;
> 
mplayer -vc ffvc1vdpau,ffwmvvdpau,ffh264vdpau,ffmpeg12vdpau -vo vdpau -ac hwdts,hwac3, -ao alsa:device=spdif -cache 8192 -fs -zoom -quiet %s

The bit that will be of interest to you is;

> -ac hwdts,hwac3, -ao alsa:device=spdif

---

### Post by lancerocke on 2010-05-08
anybody fix this for 'alc889A' yet?

---

### Post by lidex on 2010-05-08
> **lancerocke said:**
> anybody fix this for 'alc889A' yet?

Look here:
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")

---

### Post by lancerocke on 2010-05-08
> **lidex said:**
> Look here:
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")

thanks.
looking at [http://ubuntuforums.org/showthread.php?t=877811](http://ubuntuforums.org/showthread.php?t=877811), my asoundconf is blank

---

### Post by lidex on 2010-05-08
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by lancerocke on 2010-05-08
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.sure, thanks
```
danny@danny-desktop:~$ uname -a
Linux danny-desktop 2.6.32-22-server #33-Ubuntu SMP Wed Apr 28 14:34:48 UTC 2010 x86_64 GNU/Linux
danny@danny-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May  8 2010 for kernel 2.6.32-22-server (SMP).
danny@danny-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A

```

---

### Post by lidex on 2010-05-08
What is is the make/model of your PC/Laptop? And what is the configuration of audio jacks?

---

### Post by lancerocke on 2010-05-08
> **lidex said:**
> What is is the make/model of your PC/Laptop? And what is the configuration of audio jacks?

my computer is custom.
my mobo is gigabyte ga-ep45-ud3p.
7 speakers and a sub-woofer

---

### Post by lidex on 2010-05-08
So it has 8 audio jacks?

---

### Post by lancerocke on 2010-05-08
> **lidex said:**
> So it has 8 audio jacks?haha, im sorry. i do have 8 speakers going, but it's only because i use 2 on one jack on 2 of them. bought the splitter thing from radio shak. i have 6 jacks

---

### Post by lidex on 2010-05-08
> **lancerocke said:**
> haha, im sorry. i do have 8 speakers going, but it's only because i use 2 on one jack on 2 of them. bought the splitter thing from radio shak. i have 6 jacks

What about digital jacks? Output of this command:
```
aplay -l
```

---

### Post by lancerocke on 2010-05-08
> **lidex said:**
> What about digital jacks? Output of this command:
```
aplay -l
``````
danny@danny-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
danny@danny-desktop:~$ 


```

---

### Post by lidex on 2010-05-08
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by lancerocke on 2010-05-08
> **lidex said:**
> Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.ok, done. is this right?
[http://imgur.com/iD1RS.jpg](http://imgur.com/iD1RS.jpg)

---

### Post by lancerocke on 2010-05-08
wow, i thonk it worked! i set mpd to use pulseaudio, and i have sound!
you're the best bro. thank you so much!

---

