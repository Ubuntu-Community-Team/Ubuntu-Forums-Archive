---
title: "Creative Sound Blaster X-Fi Xtreme Audio on MB"
date: 2010-05-03
forum: Multimedia Software
---

### Post by ehupp on 2010-05-03
I have a MSI P6N Diamond Motherboard with built in SB X-FI Xtreme Audio. 

[http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=1168](http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=1168)

 I am running 10.04 LTS 64-bit (but have tried both 64 and 32 bit via live disk)and I have been trying to get sound to work without having to add an extra sound card since version 8.04. I was hoping that I would be able to get sound natively with the release of 10.04.
 
Since release date I have spent hours and hours on google trying different versions of drivers, removing and upgrading ALSA, trying to install the driver that was posted on the Creative Beta Site etc etc to no avail.

In sound preferences it shows as SB X-FI Xtreme Audio CA0110-IBG.  When I click the options dropdown menu it presents a long list of options of which I have tried every possible variation. 

Has anyone been able to get this motherboard w soundchip working w Ubuntu 10.04 64 bit?

---

### Post by ehupp on 2010-05-04
<bump>
still looking for info on this if anyone has any?

---

### Post by age99 on 2010-05-05
I am in the same boat.  I am running a Windows 7 dual boot and the sound works great in Windows, but in 10.04, nothing at all.  It was the same situation in Jaunty.

Any ideas what can be done?

---

### Post by lidex on 2010-05-06
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

### Post by age99 on 2010-05-06
Here are the outputs:

```
uname -a
Linux mbuzi 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.
```

```
head -n 1 /proc/asound/card*/codec#*
Codec: Creative CA0110-IBG
```

I have a 64-bit Dell 9000, i7 processor, running windows 7 as well.  No problems in Windows.

---

### Post by age99 on 2010-05-06
Does anybody have any insight into this?  I've seen many posts, but no clear solutions.

---

### Post by lidex on 2010-05-06
The best i can do is recommend an alsa upgrade at the present. Go here:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")
Use the info there to edit the script that post links to for 1.0.23

---

