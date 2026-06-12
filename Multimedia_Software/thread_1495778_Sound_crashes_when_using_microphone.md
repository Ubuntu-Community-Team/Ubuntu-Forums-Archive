---
title: "Sound crashes when using microphone"
date: 2010-05-28
forum: Multimedia Software
---

### Post by calinut1 on 2010-05-28
Hello,

Maybe this problem was already solved in a thread somewhere around here but I couldn't find it if it was.

I use Ubuntu 10.04 but I had this problem in 9.10 too.

I have a problem regarding my sound preferences. I have a microphone and I want to use it to make calls. The problem is that when I speak into the microphone when a program like Skype is used, my sound suddenly crashes(The microphone won't take any input nor will I hear any sound from the speakers if I play a video or music. This gets fixed if I restart the computer).
This also happens if I go to Sound preferences &#8594;  Input or Output and edit something there.

If I don't make any of the above, the sound works just fine as I can listen to music and play videos.

I don't know much about computer hardware but here is some info about my sound card:

```
VIA Technologies, Inc. VT1708/A[Azalia HDAC] (VIA High Definifion Audio Controller) (rev 10)

Subsystem: Biostar Microtech Int'l Corp Device 820f
```


If someone has the time and patience to try and help me, I would be really thankful!

Also, if possible, please try make the answer as clear as possible, as for a beginner!

I AM REALLY SORRY IF THIS WAS POSTED ANYWHERE AND I DIDN'T FOUND IT!

Thank you in advance for your time and effort!

---

### Post by calinut1 on 2010-05-30
Bump! Can nobody help me?

---

### Post by lidex on 2010-05-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by calinut1 on 2010-05-30
Here is the output of the commands:

**uname -a**

```
Linux calin-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```

**aplay -l**

```
List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**cat /proc/asound/version**

```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

**head -n 1 /proc/asound/card*/codec#***

```
Codec: Realtek ALC662 rev1

```

My computer is not of a certain brand. It is made out of different hardware pieces.
This is how I bought it.

Thanks for trying to help me.

---

### Post by lidex on 2010-05-30
Is it a brand name computer? HP, ASUS, Acer, Dell, etc?
First do this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by calinut1 on 2010-05-30
No, it's not a brand. It was made from different pieces of hardware. This is how I bought it.

Oh and when I execute both commands you gave me I get:

```
rm: cannot remove `/home/calin/.asound*': No such file or directory

```

```
rm: cannot remove `/etc/asound.conf': No such file or directory

```

---

### Post by lidex on 2010-05-30
Any difference?

---

### Post by calinut1 on 2010-05-30
> **lidex said:**
> Any difference?

well... that's interesting. I hear the sound when I log out, but now it seems like the sound doesn't work when I log in.

It's that sound icon and "---" after it. I also can't go to sound preferences. Nothing happens when I click the sound icon.

EDIT: I can hear sound but I just can't access the preferences. Should I try and use the microphone now?
EDIT2: I restarted the computer and now I can access the sound preferences too. Nothing has happened.

---

### Post by lidex on 2010-05-30
> EDIT2: I restarted the computer and now I can access the sound preferences too. Nothing has happened
But does it crash?

---

### Post by calinut1 on 2010-05-30
> **lidex said:**
> But does it crash?

Well, even if I don't have the microphone connected, it crashes when I go to output/input and try to edit something. the crash is only for a second though and afterwards sound works like usual.

---

### Post by lidex on 2010-05-30
OK. Try this.
**First**
```
sudo apt-get purge pulseaudio libasound2 libpulse0 pulseaudio-utils libasound2-plugins pulseaudio-module-udev pulseaudio-module-hal
```
**Second**
```
sudo apt-get install pulseaudio pulseaudio-module-x11 pavumeter paman pavucontrol
```

---

### Post by calinut1 on 2010-05-30
well... those commands deleted the majority of my programs. A lot from accesories, internet, sound and video etc. was deleted. :(

Is there any way to recover all those things?(Even firefox was deleted.)

Anyways, I'll check if the sound problem was fixed.

EDIT: It gets even worse... It seems like gnome desktop was uninstalled. When I log in I have no visual interface. I only get a console-like screen. I am currently writing this post from a lubuntu live cd. It's almoust like everything was uninstalled.

---

### Post by lidex on 2010-05-30
Don't know why pulse would be tied to all those packages. Do this from a console:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by calinut1 on 2010-05-30
> **lidex said:**
> Don't know why pulse would be tied to all those packages. Do this from a console:
```
sudo apt-get install ubuntu-desktop
```

Done. I have the desktop back. I tested if the sound crashes and yeah it does the same way as before. That might be because I installed Ubuntu-desktop. I assume pulseaudio was installed toghether  with it.

---

### Post by lidex on 2010-05-30
> **calinut1 said:**
> Done. I have the desktop back. I tested if the sound crashes and yeah it does the same way as before. That might be because I installed Ubuntu-desktop. I assume pulseaudio was installed toghether  with it.
Yeah, pulse comes with. Try this - I promise no collateral damage. 
Using a Terminal="Applications->Accessories->Terminal"

```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
Reboot.

---

### Post by calinut1 on 2010-05-30
> **lidex said:**
> Yeah, pulse comes with. Try this - I promise no collateral damage. 
Using a Terminal="Applications->Accessories->Terminal"

Reboot.

Done. Although when I work around at sound preferences it doesn't crash that often(it still crashes but rarely), when I use  a program like Skype or GTK_RocordMyDesktop it crashes.

---

### Post by lidex on 2010-05-30
Now this:
```
sudo apt-get install --reinstall gnome-media gnome-media-common
```
Logout/in

---

### Post by calinut1 on 2010-05-30
Done. It still crashes.

---

### Post by lidex on 2010-05-30
OK. Next try upgrading alsa via the alsa-upgrade link in my sig.

---

### Post by calinut1 on 2010-05-30
I am currently doing this. I have a question: If I install ALSA, shouldn't I remove pulseaudio?

EDIT:

It worked. I called somebody with Skype and he heard me but he said he heard me in an echo-like way. He heard me saying something multiple times. I don't know if this is because of the microphone or because of ALSA.
I would be very happy if you could help me in that way too, thanks!

Anyways, thank you a lot for your help and for your patience!

---

