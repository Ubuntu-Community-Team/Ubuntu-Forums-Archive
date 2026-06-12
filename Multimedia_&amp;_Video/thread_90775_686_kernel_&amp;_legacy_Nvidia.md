---
title: "686 kernel &amp; legacy Nvidia"
date: 2005-11-15
forum: Multimedia &amp; Video
---

### Post by tjotser on 2005-11-15
Before i had Hoary and  had no problems with my PCI TNT2 M64 and the 686 kernel. Switching to nvidia-glx-legacy for Breezy-386 worked untill  switching to the 686-kernel. I have researched a bit but find myself stuck / frustrated. I am a newb to linux and need your help please:KS 

Maybe I should go back to Hoary?? Or can i freely experiment this kind of trouble on the liveCD ?

Thanks in advance;)

T.j.o.T.s.e.R

---

### Post by az on 2005-11-15
Did you install the linux-restricted-modules--2.6.12-9-686-nvidia-legacy package too?  The drivers are there.

You also need the nvidia-glx-legacy package.

---

### Post by tjotser on 2005-11-16
I'll give it a try later today and let you know
sounds promising :)

---

### Post by tjotser on 2005-11-16
I don't know what i exactly did last night but now it works!, i think i followed some tutorial. removed  "dri" and "glcore". Also did the restricted stuff which you kindly pointed out. This should help me the next time , to know the answers lie in these forums.My PIII-666 is a lot better now
:KS 
THANKS AGAIN

---

### Post by godvalve on 2005-12-18
> **azz]Did you install the linux-restricted-modules-2.6.12-9-686-nvidia-legacy package too?  The drivers are there.

You also need the nvidia-glx-legacy package.[/QUOTE]

*Geeeeeeeeeez!*  Finally some good advice on legacy drivers. I just spent an hour crawling google and the forums looking for a simple answer on how to install legacy nvidia drivers (Ubuntu style). The "wonderful" [HOWTO: Latest NVIDIA drivers]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=glx") doesn't make the installation of legacy drivers very clear (although, thanks to that guide I realized that I needed legacy drivers).

For others in this predicament, the restricted modules you want to download are based on the kernel you are using. Thus, you must use the command **uname -r** to ascertain which kernel you are running. Take the output and Insert it in place of the command in tseliot's example:
[QUOTE=tseliot]

sudo apt-get install linux-restricted-modules- **uname -r** -nvidia-legacy
[/QUOTE]

In short:
```

sudo apt-get linux-restricted-modules-2.6.12-9-686-nvidia-legacy
sudo apt-get nvidia-glx-legacy
```
Don't forget that the /etc/X11/xorg.conf file needs to be altered as per tseliot's HowTO:
[quote=tseliot]

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf
scroll the file down until you find the line with &#8220 said:**
> #[/COLOR][COLOR="Green"]Load "dri"[/COLOR]
[COLOR="red"]#[/COLOR][COLOR="Green"]Load &#8220;GLcore&#8221;[/COLOR]
Load "extmod"
Load "freetype"
[COLOR="Green"]Load "glx"[/COLOR]
Load "int10"
Load "record"
Load "type1"
Load "vbe"
```

Then find the section Device and make sure the word I put in red is &#8220;nvidia&#8221;:

```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Green"]nvidia[/COLOR]"
BusID "PCI:1:0:0"
```


CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit


I might add that this was done on a virgin install of Ubuntu 5.10. The NVidia splash screen showed immediately on my next boot. \\:D/

A few keywords for the forum search function:  geforce2 legacy drivers tnt nvidia

---

