---
title: "Geforce GO 7900 GS (Dual)"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by Dejime on 2006-09-28
Just finished installing my Ubuntu setup (Had to use the alternate CD method, since I experienced a similar problem with the regular CD) and booted up. Everything loaded correctly, then I get a little blinking _ which eventually stops and I hear three short drum hits in a row. I wait patiently a while, then figure it's a problem with X starting and hit the power switch. I see the command line "DualDejime (The name of the box) login:" before it unmounts and shuts down. I can boot into "safe" ubuntu with a command line and all, but figure it's something about my GeForce GO 7900 GS card that's causing X not to work. I flipped around some other threads and everyone was like "Just install some beta drivers". 

First, I just want to make sure that my analysis is correct, and the problem is my video card drivers (I'm figuring the three drum hits mean something, but I just don't know what it is =D)

Second, I haven't installed beta drivers on ubuntu before...is it like other Linux setups? Details would be appreciated!

Thanks in advance

---

### Post by Dejime on 2006-09-29
*bump* thanks!

---

### Post by tseliot on 2006-09-29
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci -v
```

and

```
lspci -n | grep 300
```

---

### Post by Dejime on 2006-09-30
VGA driver-installed and had a problem, output error as follows:

VGA: C03 primer can't support depth 24

Screens found, none have usable config. That was by using what I knew about my card/screen and hitting enter whenever I didn't know the answer.

VESA drivers did nothing, same error.

lspci -v:

VGA compatible controller: NVIDIA corp: unknown device 0298 (reva)

lspci -n|grep 300:

0000:06:00.0 0300
10de:0298(reva1)

0000:07:00.0 0300
10de:0298(reva1)

---

### Post by tseliot on 2006-10-01
> **Dejime said:**
> VGA driver-installed and had a problem, output error as follows:

VGA: C03 primer can't support depth 24

Screens found, none have usable config. That was by using what I knew about my card/screen and hitting enter whenever I didn't know the answer.

VESA drivers did nothing, same error.

lspci -v:

VGA compatible controller: NVIDIA corp: unknown device 0298 (reva)

lspci -n|grep 300:

0000:06:00.0 0300
10de:0298(reva1)

0000:07:00.0 0300
10de:0298(reva1)
If you want to get the Xserver to work again, use "nv" instead of vesa.

If you want to solve the problem with the Nvidia driver you should set the driver to "nvidia" instead of vesa and try point 16 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by Dejime on 2006-10-01
I tried the "nv" driver and it didn't work. I couldn't find "nvidia" among the options...am I missing something? =D

---

### Post by tseliot on 2006-10-01
> **Dejime said:**
> I tried the "nv" driver and it didn't work. I couldn't find "nvidia" among the options...am I missing something? =D

You can scroll the list of drivers with your keyboard arrows

---

### Post by Dejime on 2006-10-01
I did. It's not there. Here is the list of the options
```

apm
ark
ati
chips
cirrus
cyrix
fbdeev (probably not, i just can't read my handwriting perfectly)
glint
i128
i810
mga
neomagic
nv
rendition
s3
s3virge
savage
siliconminion
sis
sisvgb
tdft
tga
trident
tseng
vega
vga
via
vmware
voodoo


```

No nvidia there? or am i looking for "nvidia" and i should be looking for another option?

---

### Post by tseliot on 2006-10-01
> **Dejime said:**
> I did. It's not there. Here is the list of the options
```

apm
ark
ati
chips
cirrus
cyrix
fbdeev (probably not, i just can't read my handwriting perfectly)
glint
i128
i810
mga
neomagic
nv
rendition
s3
s3virge
savage
siliconminion
sis
sisvgb
tdft
tga
trident
tseng
vega
vga
via
vmware
voodoo


```

No nvidia there? or am i looking for "nvidia" and i should be looking for another option?
ok, use this command then:
```
sudo nvidia-xconfig

```

---

### Post by Dejime on 2006-10-02
The command does not exist...very strange, no?

---

### Post by tseliot on 2006-10-02
> **Dejime said:**
> The command does not exist...very strange, no?

1) Which release of Ubuntu are you using (Hoary, Breezy, Dapper, Edgy)?
2) How did you install the driver?
3) Which driver did you install? the Legacy driver or the non-legacy one?

---

### Post by Dejime on 2006-10-02
Dapper...I haven't installed any driver yet, =P, which is probably part of the problem. Point me in the right direction? Just do your suggestion (the page that you already linked me to, trying to solve with problem 16?)

---

### Post by tseliot on 2006-10-02
> **Dejime said:**
> Dapper...I haven't installed any driver yet, =P, which is probably part of the problem. Point me in the right direction? Just do your suggestion (the page that you already linked me to, trying to solve with problem 16?)

Try Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Dejime on 2006-10-02
Yeah, I tried it and it worked, =P, sorry for wasting your time, =D

---

