---
title: "Automatically switch between &quot;Analog headphones&quot; and &quot;Analog output&quot;"
date: 2010-03-22
forum: Multimedia Software
---

### Post by uccie on 2010-03-22
Hey, 

every time I want to listen music from my headphones I have to do like: 

1. Main menu >> System >> Preferences >> Sound >>> Output >>>> Connector >>>>> Analog Headphones 

and vice versa. 

I have no experience in bash scripting and I have no idea how to find automatic solution to my problem. 

The problem in pseudo-code:

Begin
if 
  headset plugged in front jack
  then Connector := Analog Headphones
else 
       Connector := Analog Output
End

I'll be very grateful for your help.
uccie

---

### Post by missilesilo on 2010-03-25
Bump. I would also like to figure out how to automate this. Windows does it, why can't Ubuntu?

---

### Post by Brandel Valico on 2010-03-25
Not sure why, but this is working on certain devices. My Laptop and Desktop does this automatically in Jaunty - Lucid. Wifes Laptop works but her Desktop doesn't. Have been trying to figure out why. Used to get around the issue by setting the sound indicator to control only the pc speakers. Then mute them when using headphones. Sadly the new indicators don't seem to allow you to select what it controls as specifically as you used to be able to do.

Laptop has an > ATI Technologies INC IXP SB400 AC'97 Audio Controller (Rev. 02) 
For it's soundcard

---

### Post by peyu on 2010-05-16
Same problem here, but at the beginning, just after installing Lucid Lynx, it was working.. After doing a trick to be able to select the microphone device (which didn't work), it stopped to switch automatically. 
I reverted the changes I made in alsa-base.conf file, but it still doesn't work since then...

Any idea?

My soundcard is 
```
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```

---

### Post by peyu on 2010-05-17
Now it works !
I put at the end of /etc/modprobe.d/alsa-base.conf this line:
```
options snd-hda-intel model=auto
```

I got it looking at Ubuntu Documentation ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto))
and this thread, which gives a lot of configuration options according to computer models:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by renatkh on 2011-05-17
> **peyu said:**
> 
```
options snd-hda-intel model=auto
```
Did not work for me :(. Did it work for anyone else?

---

### Post by peyu on 2011-05-18
Hi renatkh,
At the end, it's not working so good... I mean, with the new ubuntu 11.04, in the alsa-base.conf, no option was specified, the mic was not working and neither the auto-switch.
I found this post [http://ubuntuforums.org/showthread.php?t=1075643](http://ubuntuforums.org/showthread.php?t=1075643), and choose the option according to my model (ALC268). So now with "auto", sometimes it works, sometimes it doesn't work, but I have no idea why...

---

### Post by peyu on 2011-05-18
my model is ALC268

---

### Post by Corsus on 2011-08-18
sudo gedit /etc/modprobe.d/alsa-base.conf
Added this to the end "options snd-hda-intel model=auto"

Adding this did it for me on 11.04 Classic.

Sorry if this seemed an unnecessary bump.

---

### Post by peyu on 2011-08-19
Thanks Corsus,
I've tried also this option and sometimes it works, sometimes not... I don't understand why.
I've also tried other alsa options found on internet, and I still haven't found the best one... It seems also to be relationated with the microphone, because generally if the autoswitch works, the microphone also, and vice versa...

---

### Post by jelun4 on 2012-02-17
Hi,


 You must open alsamixer in terminal and disabled Auto-Mute Mode.


 Now when you plugged your headphones it doesn't switch to Analog Headphones in the sound settings.

---

### Post by prosp4300 on 2012-04-09
jelun4's answer works for me.
1. run alsamixer from konsole, 
2. press F6 to select card "HDA Intel"
3. press F3, then you can see the Auto Mute column
4. press Right to highlist Auto Mute
5. press Up to turn it on, then headphone plugin/out will disable/enable speaker

Really Thank You

---

### Post by prosp4300 on 2012-04-09
Attached alsamixer screenshot that run from konsole

---

