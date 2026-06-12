---
title: "PulseAudio line-in volume setting not sticking"
date: 2017-07-31
forum: Multimedia Software
---

### Post by &amp;KyT$0P# on 2017-07-31
I like the volume of my line-in input to be set at 96% (-1.00 dB).  A few seconds after waking from suspend, and on most reboots, it sets itself to a much lower value, usually 66% (-11.00 dB).

Why is PulseAudio playing tug-of-war with me?  How to stop it?

Thanks

---

### Post by &amp;KyT$0P# on 2017-08-26
bump

---

### Post by &amp;KyT$0P# on 2017-08-31
bump

---

### Post by &amp;KyT$0P# on 2017-09-07
bump

---

### Post by &amp;KyT$0P# on 2017-09-14
bump

---

### Post by &amp;KyT$0P# on 2017-09-22
bump

---

### Post by &amp;KyT$0P# on 2017-09-29
bump

---

### Post by &amp;KyT$0P# on 2017-10-06
bump

---

### Post by &amp;KyT$0P# on 2017-10-13
bump

---

### Post by &amp;KyT$0P# on 2017-10-20
bump

---

### Post by &amp;KyT$0P# on 2017-10-31
bump

---

### Post by &amp;KyT$0P# on 2017-11-08
bump

---

### Post by &amp;KyT$0P# on 2017-11-17
bump

---

### Post by &amp;KyT$0P# on 2017-12-02
bump

---

### Post by &amp;KyT$0P# on 2018-02-09
bump

---

### Post by &amp;KyT$0P# on 2018-03-06
bump

---

### Post by &amp;KyT$0P# on 2018-04-15
I now use 18.04, and the line-in volume is still not sticking where I set it.  But instead of being dragged down, it gets reset to 100%.

* Turns out that's not always the case.  Sometimes it goes up to 100%, and sometimes it gets dragged down same as before.

---

### Post by &amp;KyT$0P# on 2018-04-27
bump

---

### Post by &amp;KyT$0P# on 2018-05-29
bump

---

### Post by #&amp;thj^% on 2018-05-29
I had this same behaviour, I fixed mine, and for what it's worth my audio specs are:
```
pinxi -A
Audio:
  Card-1: Intel Sunrise Point-H HD Audio driver: snd_hda_intel 
  Card-2: NVIDIA GF114 HDMI Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k4.15.0-21-generic
```
My fix was to edit this file: "/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common"
```
sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```
Search for the text &#8220;Element PCM&#8221;. You should see the following text:

```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all 
override-map.2 = all-left,all-right
```
change the section of text to look like the following:
```
[Element PCM]
switch = mute
volume = ignore
volume-limit = 0.01
override-map.1 = all 
override-map.2 = all-left,all-right
```
Note: that the value 0.01 can be adjusted as needed to change how quiet and loud the volume is. Making the number smaller reduces the max volume while making the number larger increases the max volume.
I ended up with a value of 0.0075 (0.005 was too quiet) which I felt gave a good maximum volume and resulted in better overall control over the volume range.
Note:  run "pulseaudio -k"  each time you change the number.

Even if you include &#8220;volume = ignore&#8221;, you ABSOLUTELY MUST include &#8220;volume-limit = <your value here>&#8221;.
Otherwise, PulseAudio will still merge the volume controls, even though you explicitly told it not to!
I also noticed that when I "first" changed the above, the linein was changed to my "HDMI Audio" so check that if you hear no sound on first try.
Good Luck!:)

---

### Post by &amp;KyT$0P# on 2018-06-02
Thanks 1fallen, I am going to try that after my next system backup.

Is there a way to make this change from inside my home directory or somewhere inside /etc?  I'm concerned that an update to the [FONT=Courier New]pulseaudio[/FONT] package could wipe out changes to [FONT=Courier New]/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common[/FONT] .

---

### Post by #&amp;thj^% on 2018-06-03
> **halogen2 said:**
> 
Is there a way to make this change from inside my home directory or somewhere inside /etc?  I'm concerned that an update to the [FONT=Courier New]pulseaudio[/FONT] package could wipe out changes to [FONT=Courier New]/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common[/FONT] .
Sorry not that I have found. :( Darn it. :)
I have used for only a few months now so we will have to wait to see if this sticks or even gets fixed some time down the line.
Best Regards
EDIT: On Arch Today 6/4/2018 took an update to "pcmciautils-018-8 & pulseaudio-alsa-2-4"  and it did not change any values that I had made>> dose not mean though that a complete Pulse version change won't though. "FWIW"

---

### Post by &amp;KyT$0P# on 2018-06-07
Unfortunately it didn't work.  After a reboot my line-in volume is back to 100%. :(

---

### Post by #&amp;thj^% on 2018-06-07
Seriously?  :confused: It's working here on both Xubuntu 18.04 and Arch
It might have something to do with your specs, is this your Mac laptop?

---

### Post by &amp;KyT$0P# on 2018-06-07
> **1fallen said:**
>  is this your Mac laptop?
Yes

Edit: inxi output -
```
$ inxi -Axxz
Audio:     Card Intel 7 Series/C216 Family High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:1e20
           Sound: Advanced Linux Sound Architecture v: k4.15.0-22-generic

```

---

### Post by #&amp;thj^% on 2018-06-07
Well my friend I'm clueless then, I also have this working on a Lenovo T430 with the I3 Cpu which is at my home ATM, All are using XFCE DE's 
I'm not sure how to advise now, Oh I'm using the PulseAudio Plugin for the Volume Control but that is all I can think of for now.
```
inxi -Axxz
Audio:
  Card-1: Intel 7 Series/C216 Family High Definition Audio 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 chip ID: 8086:1e20 
  Sound Server: ALSA v: k4.16.13-2-ARCH 

```
And
```
pulseaudio --version
pulseaudio 11.1

```

---

### Post by #&amp;thj^% on 2018-06-21
To confirm>> _Yes_ an upgrade in pulseaudio will wipe the changes we/I made in **"/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common"**
back to:
```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all 
override-map.2 = all-left,all-right

```
However the upgrade to pulseaudio version **pulseaudio 12.0** has solved the volume tug-a-war for my system at least on my "Arch install". NOTE: The settings for "qpaeq" remained intact.   
```
pulseaudio --version
pulseaudio 12.0

```
And:
```
qt5-multimedia 5.11.1-1
```

---

### Post by &amp;KyT$0P# on 2019-01-07
Would [this solution]("https://ubuntuforums.org/showthread.php?t=2409720") help here?

If the only way to know is for me to "just try it", how do I revert that in case it doesn't work out?

---

