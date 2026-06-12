---
title: "I cannot listen my music smoothly."
date: 2011-01-03
forum: Multimedia Software
---

### Post by jorgeaz on 2011-01-03
p { margin-bottom: 0.08in; }  When I play my music using any application or I use anything that get out from the speakers I can't listen it smoothly. It is like a jump (silence) that occurred randomly.
 I have read the sticky (Comprehensive Sound Problems Solution Guide) where I learn that I have more than one on-board sound cards after:
     aplay -l             I got this:
 **** List of PLAYBACK Hardware Devices **** 
 card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog] 
   Subdevices: 0/1 
   Subdevice #0: subdevice #0 
 card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI] 
   Subdevices: 0/1 
   Subdevice #0: subdevice #0 
 

 So, I am suspecting that Ubuntu is switching sound cards when I play music. If I follow the same Sticky there is another part ([SIZE=3]_**Configuring default sound-cards / stopping multiple sound-cards from switching) **_[/SIZE][SIZE=3]so I typed:[/SIZE]
 [SIZE=3]    [/SIZE][SIZE=3]cat /proc/asound/modules          then I got this:[/SIZE]
  [SIZE=3]0 snd_hda_intel [/SIZE]
  [SIZE=3]1 snd_hda_intel [/SIZE]
 

 [SIZE=3]when I follow next step I type:[/SIZE]
 [SIZE=3]    sudo nano /etc/modprobe.d/alsa-base[/SIZE]
 [SIZE=3]so get into an editor. From this point on, I get confuse. Please help.[/SIZE]
 [SIZE=3]I don't want to listen music in itunes (windows), I just love Ubuntu.[/SIZE]

---

### Post by lidex on 2011-01-04
Can you give more info please? 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by jorgeaz on 2011-01-09
thanks you!!! very much for your answer. 
I am new in ubuntu so I am going to copy exactly what I did following your instructions:
I opened the terminal and ...


jorge@jorge-desktop:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2011-01-09 18:45:40--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org]("http://www.alsa-project.org")... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80]("http://www.alsa-project.org%7C77.48.224.243%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-01-09 18:45:41--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80]("http://www.alsa-project.org:80").
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,025      23.9K/s   in 1.1s    

2011-01-09 18:45:43 (23.9 KB/s) - `alsa-info.sh' saved [27025]

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base line 1: ignoring bad line starting with '1'
WARNING: /etc/modprobe.d/alsa-base.save line 1: ignoring bad line starting with 'gonza33'
WARNING: /etc/modprobe.d/alsa-base.save line 3: ignoring bad line starting with '1'
WARNING: /etc/modprobe.d/alsa-base.save.1 line 1: ignoring bad line starting with '0'
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base line 1: ignoring bad line starting with '1'
WARNING: /etc/modprobe.d/alsa-base.save line 1: ignoring bad line starting with 'gonza33'
WARNING: /etc/modprobe.d/alsa-base.save line 3: ignoring bad line starting with '1'
WARNING: /etc/modprobe.d/alsa-base.save.1 line 1: ignoring bad line starting with '0'
Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : y
Uploading information to [www.alsa-project.org]("http://www.alsa-project.org") ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=deb872d81b5f8a00ac79d6600dfd8fe43e6a8c08](http://www.alsa-project.org/db/?f=deb872d81b5f8a00ac79d6600dfd8fe43e6a8c08)

Please inform the person helping you.


That is exactly what happen in my terminal...
I am going to try to send you as attach a  copy of recording of music plaid in order you have an idea of what's going on... if I can zip the mp3 file 
Thank you again!!!
thank again

---

### Post by lidex on 2011-01-09
First you should remove those files you created:
```
sudo rm /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.save /etc/modprobe.d/alsa-base.save.1
```
I'll show you a better way to edit if you actually need it and there is a file there already, by default - alsa-base.conf

Next try updating your alsa driver using this method:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by jorgeaz on 2011-01-10
Well, You didn't give me time to zip a piece of file of my music, Why?.... I don't have to anymore..
Thanks to you, I'm just listening it, very smoothly right now, no faults, no jumps, no problems..
Thank you very much!! for helping me and for using your time to help others...
Jorge

---

### Post by lidex on 2011-01-11
And you are welcome! Enjoy. Please mark the thread solved using 'Thread Tools' up top.

---

