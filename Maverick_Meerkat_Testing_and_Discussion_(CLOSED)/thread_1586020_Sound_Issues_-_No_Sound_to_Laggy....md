---
title: "Sound Issues - No Sound to Laggy..."
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Vakman on 2010-10-01
Hello, so I have come back to Ubuntu again since I don't game much anymore and I don't really play anything that is not a Platinum rating in Wine, play less, blah blah...

So. Sound problems are anything from in something like Teeworlds, the sound lags a few seconds behind. In Warsow the sound is distorted and just is nothing close to what it should be. Since last reboot I no longer have any options for sound either, when opening the Sound preferences it tells me that it is waiting for sound system to respond. Now, my sound it working in things like music and Youtube videos but I have no controls for any of it and I experience the problems in other applications that I stated above. It is integrated Realtek sound.
I tried to fix the User Privileges to allow for sound devices but that was not it either.

---

### Post by lidex on 2010-10-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Vakman on 2010-10-04
```
lawrence@Vakman-PC1:~$ uname -a
Linux Vakman-PC1 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
lawrence@Vakman-PC1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lawrence@Vakman-PC1:~$ dpkg -l | grep "alsa"
ii  alsa-base                                                1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-utils                                               1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  bluez-alsa                                               4.69-0ubuntu2                                   Bluetooth audio support
ii  gstreamer0.10-alsa                                       0.10.30-2                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                          14.3.1-1build1                                  SoX alsa format I/O library
lawrence@Vakman-PC1:~$ uname -a\
> 
Linux Vakman-PC1 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
lawrence@Vakman-PC1:~$ uname -a\
> 
Linux Vakman-PC1 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
lawrence@Vakman-PC1:~$ uname -a
Linux Vakman-PC1 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
lawrence@Vakman-PC1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lawrence@Vakman-PC1:~$ dpkg -l | grep "alsa"
ii  alsa-base                                                1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-utils                                               1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  bluez-alsa                                               4.69-0ubuntu2                                   Bluetooth audio support
ii  gstreamer0.10-alsa                                       0.10.30-2                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                          14.3.1-1build1                                  SoX alsa format I/O library
lawrence@Vakman-PC1:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```
That was the perfect way to ask for all that by the way.
Moving along:
Motherboard: ASUS P6T
CPU: Intel Core i7 920
GPU: ATi Radeon 4850
RAM: 6GB Corsair DDR3 Tri-Channel 1333MHz
Can't think of anything else you would need there. There are no other PCI or PCIe sound cards or any other cards aside from a PCIe Wireless card which works out of the box anyhow.
Also, when I was trying to fix this I have messed up the new/cool sound applet that comes in 10.10. I am back to what used to be there.
Thanks for the help in advance.

---

### Post by lidex on 2010-10-05
Make sure this package is installed:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```
For your panel applet try removing the sound/indicator applet from panel. 
Next:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session indicator-sound
```
Now reset your panels:
```
gconftool-2 --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Next right-click on your panel and select 'Add to panel' and add back items that are missing. Indicator applet I believe should have volume control, but you may need to play around as there are three indicator entries in my add list. You may want to search synaptic for 'applet' to find any that are not in the list as they have to be installed to appear there.

---

### Post by Vakman on 2010-10-06
```
lawrence@Vakman-PC1:~$ sudo apt-get install libsdl1.2debian-pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2debian-pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 84 not upgraded.
```
So what you said about the applet did restore the applet, thank you. But I still have the other sound applet, how would I remove it and just keep the one?

---

### Post by ktp on 2010-10-06
if you want to remove the old gnome volume control applet, then see if you have "gnome-volume-control-applet" running.  If so kill it.  It might also be started when you login so check "System -> Preferences -> Startup Application" and remove it if there.

---

### Post by lidex on 2010-10-07
Ah, 'Waiting for sound system to respond'. May need to reset your audio config. Try this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

---

### Post by Vakman on 2010-10-07
@ktp That isn't there but it went away after I restarted so not to sure on that.
@lidex ```
lawrence@Vakman-PC1:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: cannot remove `/home/lawrence/.asound*': No such file or directory
lawrence@Vakman-PC1:~$ sudo rm /etc/asound.conf
[sudo] password for lawrence: 
rm: cannot remove `/etc/asound.conf': No such file or directory
lawrence@Vakman-PC1:~$ 

```
But I don't get that Waiting for it to respond since the last thing you told me to do before this or the one before that.
But it still lags behind. If I am listening to music and then I pause the sound is still going. It is really bad if I watch a video as well and even worse in games in the sense that the sound just completely distorts itself.
Either way it says there is no such file there as you can see above.
EDIT: Also note, I never had sound problems on previous versions of Ubuntu. But I like this 10.10.

---

### Post by lidex on 2010-10-07
> **Thisislaw said:**
> @ktp That isn't there but it went away after I restarted so not to sure on that.
@lidex ```
lawrence@Vakman-PC1:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: cannot remove `/home/lawrence/.asound*': No such file or directory
lawrence@Vakman-PC1:~$ sudo rm /etc/asound.conf
[sudo] password for lawrence: 
rm: cannot remove `/etc/asound.conf': No such file or directory
lawrence@Vakman-PC1:~$ 

```
But I don't get that Waiting for it to respond since the last thing you told me to do before this or the one before that.
But it still lags behind. If I am listening to music and then I pause the sound is still going. It is really bad if I watch a video as well and even worse in games in the sense that the sound just completely distorts itself.
Either way it says there is no such file there as you can see above.
EDIT: Also note, I never had sound problems on previous versions of Ubuntu. But I like this 10.10.
Those are user-added conf files, so only there if you put them.

---

