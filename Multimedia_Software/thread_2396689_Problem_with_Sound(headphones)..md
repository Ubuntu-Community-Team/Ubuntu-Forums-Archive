---
title: "Problem with Sound(headphones)."
date: 2018-07-19
forum: Multimedia Software
---

### Post by sangamswadik on 2018-07-19
Hello,I'm new to Ubuntu.

I noticed after yesterday's update,headphones are not getting detected,But I'm able to hear from the speaker.
I'm using the headphones through "pulseAudio volume control" but the sound is not clear there is some kind of noise.
What should I do to resolve this I tried the solution posted at the FOSS website.It did not help me.


Thanks.

---

### Post by sangamswadik on 2018-07-19
I browsed through this
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
But I was unable to understand this.

---

### Post by beyondlimitgld on 2018-07-19
Where do you plug the headphones port?Front panel or back panel?
If back panel is working,you need to go into your BIOS to change the audio driver.

---

### Post by slickymaster on 2018-07-19
*Thread moved to **Multimedia Software**.*

---

### Post by ajgreeny on 2018-07-19
Probably also worth checking that the microphone, if you have one, is not picking up ambient noise or the spinning disk hum and passing it to the speakers or headphones.

---

### Post by sangamswadik on 2018-07-20
> **beyondlimitgld said:**
> Where do you plug the headphones port?Front panel or back panel?
If back panel is working,you need to go into your BIOS to change the audio driver.

Headphone is connected to the front panel.
I typed in ```
alsamixer
```.The Headphones were muted.I reconfigured them,they worked  and I saved the configuration using  ```
sudo alsactl store
```.
But I have to redo the same thing  every time I reboot.
The headphone is not only muted,it does not even appear in the "output" in settings->sound .

---

### Post by leunam12 on 2018-07-21
I have the same problem, no auto-switch when the headphones are plugged in. Bluetooth headphones do work the way they are supposed to,
but the wired ones don't.

---

### Post by leunam12 on 2018-07-21
Regarding the noise; whenever I hear noise coming from the speakers or headphones
I kill speech dispatcher and it solves the problem. There seems to be a bug with 
speech dispatcher that causes the sound to be distorted.
```
ps -eo pid,cmd | grep speech
```
will give you the processes using speech dispatcher.

---

### Post by leunam12 on 2018-07-21
Example ```

rivasdom@RivasPC-2:~$ ps -eo pid,cmd | grep speech
 3154 /usr/lib/speech-dispatcher-  3154 /usr/lib/speech-dispatcher-modules/sd_generic /etc/speech-dispatcher/modules/generic.conf
 3157 /usr/lib/speech-dispatcher-  3157 /usr/lib/speech-dispatcher-modules/sd_espeak-ng /etc/speech-dispatcher/modules/espeak-ng.conf
 3163 /usr/lib/speech-dispatcher-  3163 /usr/lib/speech-dispatcher-modules/sd_dummy /etc/speech-dispatcher/modules/dummy.conf
 3166 /usr/bin/speech-dispatcher   3166 /usr/bin/speech-dispatcher --spawn --communication-method unix_socket --socket-path /run/user/1000/speech-dispatcher/speechd.sock
 3203 grep --color=auto speech     3203 grep --color=auto speech

```

Then ```
kill 3154 3157 3163 3166
```

---

### Post by kazakore on 2018-07-21
I've actually had similar happen to my system in the last weeks or so, but as I use quite a non-standard audio setup (and 18.04 was the first time it ever worked even briefly) I've not fussed that much about it.

Until some recent update connecting or disconnecting from the headphone socket would cause the speaker output to be muted within Qasmixer (so Alsa) which is good as there is something strange where if the speaker isn't muted in Alsa I lose all the bass frequencies at the actual output. Enabling Auto-Mute Mode kills the speaker when plugging in headphones but doesn't mute the Alsa channel so I get the lack of bass now if I trust it to this method alone and have to manually mute and unmute.

I think in my case I have stopped PA doing something even though I've always generally tried to not having it doing anything with the system as much as possible as I do unload some modules when I load up the Jack sever so might not be update related in my instance....

Sorry to not actually be of any help :(

---

### Post by beyondlimitgld on 2018-07-21
Yes,so you can try the back panel,if it's working,the problem is the BIOS setting,when you boot up the pc press the F(*) according your motherboard,after enter the Menu try to find the setting(mine are at the Chipset setting)that can change the audio driver,i give you a link so you can more easily to understand
[https://youtu.be/2As1oO36BOY](https://youtu.be/2As1oO36BOY)
This video just enable the front panel,every motherboard have different setting,mine are having the options to change the audio driver.

---

### Post by mIk3_08 on 2018-07-22
to force reload alsa
use the following command in terminal
```
sudo alsa force-reload
```
```
sudo apt-get remove --purge alsa-base pulseaudio
```
```
sudo apt-get install alsa-base pulseaudio
```
And force reload alsa again:
```
sudo alsa force-reload
```
in terminal and edit speech-dispatcher file by using the following command
```
sudo -H gedit /etc/default/speech-dispatcher
```
In here, change run=yes to run=no
Reboot and enjoy the sound

---

### Post by mIk3_08 on 2018-07-22
> **sangamswadik said:**
> I browsed through this
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
But I was unable to understand this.

Name:dkms
Description: Dynamic Kernel Module Support Framework
Latest version:	2.3-3ubuntu9.2
Release: bionic (18.04)


go to terminal; ctrl + alt + t
then type;
```
[COLOR=#333333]sudo apt-get install dkms[/COLOR]
```

---

### Post by sangamswadik on 2018-07-24
> **mIk3_08 said:**
> to force reload alsa
use the following command in terminal
```
sudo alsa force-reload
```
```
sudo apt-get remove --purge alsa-base pulseaudio
```
```
sudo apt-get install alsa-base pulseaudio
```
And force reload alsa again:
```
sudo alsa force-reload
```
in terminal and edit speech-dispatcher file by using the following command
```
sudo -H gedit /etc/default/speech-dispatcher
```
In here, change run=yes to run=no
Reboot and enjoy the sound

Hi.I got this when I ran the last one.

```
No protocol specified
Unable to init server: Could not connect: Connection refused

(gedit:12099): Gtk-WARNING **: 08:38:55.384: cannot open display: :0


```

---

### Post by sangamswadik on 2018-07-24
> **mIk3_08 said:**
> Name:dkms
Description: Dynamic Kernel Module Support Framework
Latest version:    2.3-3ubuntu9.2
Release: bionic (18.04)


go to terminal; ctrl + alt + t
then type;
```
[COLOR=#333333]sudo apt-get install dkms[/COLOR]
```

And I got this.Its clearly not 9.2 but 9.1.
```
sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

