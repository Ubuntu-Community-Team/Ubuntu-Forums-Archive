---
title: "cant install es1869 sound driver"
date: 2006-02-06
forum: Multimedia &amp; Video
---

### Post by NoJock on 2006-02-06
Brand new user of linux and forums.

Have looked at several threds and have tryed them from the console ctrl+alt+f1 is the right way to the console? All the differant things i have tryed report does not exist or not directory, also hard drive is not loaded when Ubuntu is started up. Running os from CD. Audio is not a card it is built on board. Any direction would be apreciated. Ok have done some more digging there is no /etc/dev/dsp does not exist. Where to now???

Sticky: tried all the tricks in your post and none of them worked, thanks ill keep looking. How tos and trouble shooting!!

---

### Post by FarEast on 2006-02-07
> Have looked at several threds and have tryed them from the console 
> ctrl+alt+f1 is the right way to the console?

You can open the shell window(console) by clicking menu items:
Application > System > Console

There is no information of 'es1869' on the web of ALSA.
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix)

EDIT: Sorry, it will be driven by 'snd-es18xx'.

I would like to know which sound chip is on your mother board.
Execute 'lspci -v | grep audio' and paste the output, please.

EDIT: Then read this:
[http://ubuntuforums.org/showpost.php?p=640288&postcount=2](http://ubuntuforums.org/showpost.php?p=640288&postcount=2)

---

### Post by NoJock on 2006-02-08
[QUOTE=FarEast]> Have looked at several threds and have tryed them from the console 
> ctrl+alt+f1 is the right way to the console?

You can open the shell window(console) by clicking menu items:
Application > System > Console

There is no information of 'es1869' on the web of ALSA.
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix)

EDIT: Sorry, it will be driven by 'snd-es18xx'.

I would like to know which sound chip is on your mother board.
Execute 'lspci -v | grep audio' and paste the output, please.

[COLOR="Magenta"]Thanks, for your response. when i enter the above exec i get no reponce just takes me back to the command line.[/COLOR]

EDIT: Then read this:
[http://ubuntuforums.org/showpost.php?p=640288&postcount=2](http://ubuntuforums.org/showpost.php?p=640288&postcount=2)[/QUOTE]

see next

---

### Post by NoJock on 2006-02-08
FarEast:

[COLOR="Magenta"]Thanks, for your response. when i enter the above exec i get no reponce just takes me back to the command line.[/COLOR]

How ever did tryed this link and no luck either. When looking in /ect/modeprobe.d/sound
There is no sound info for the ess es 18xx of any kind.
Have tryed the ***[COLOR="Magenta"]sudo apt-get install isapnptools[/COLOR]*** response cant find package 
 
System >Administration >Device Manager and there is info there indicating that the OS did see but did not install.

Have know idea of how to cut and past this info to post it. 
Under Applications >System Tools. There is no console just a New Login that look like a terminal. 
This all may be and issue that im running for the CD to try and understand a different OS befor i go and install it with WinXP
which works on this box with no problems..

Thanks for your patiants.

---

### Post by FarEast on 2006-02-08
> Thanks, for your response. when i enter the above exec i get no reponce
> just takes me back to the command line.

Sorry!  For the sound chip is on ISA bus, it cannot be detected by 'lspci'.

> System >Administration >Device Manager and there is info
> indicating what the OS see but ...
> Have no idea of how to cut and past this info to post it. 

I think the information is the same as the output of 'lspci -v'.

You are using so-called 'Live-CD', don't you?
First, reserve IRQ5,11 for ISA-pnp devices.  You can do it with BIOS setting.
After booting the system, try to load the module by the command below.

```
$ sudo modprobe snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0
```

Good luck!

---

### Post by NoJock on 2006-02-08
Thanks,but did not work response FATAL: ERROR running install comand for snd_es18xx
The bios is set to 220-22f, 388-38b, 330=331, irq 5, dma1, dma0

Allas may have a kernal problem?? First line when trying to exec the above didnt see (blind) befor.
ERROR inserting snd_es18xx (/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-es18xx.ko): no such device

---

### Post by FarEast on 2006-02-08
[COLOR="Red"]----- Ignore this; I was mistaken. -----[/COLOR]

OK...

Try OSS(Open Sound System) driver instead of ALSA(Advanced Linux Sound
Architecture) driver.

```
$ sudo modprobe es18xx
```

---

### Post by NoJock on 2006-02-09
[QUOTE=FarEast]OK...

Try OSS(Open Sound System) driver instead of ALSA(Advanced Linux Sound
Architecture) driver.

```
$ sudo modprobe es18xx
```[/QUOTE]

[COLOR="Magenta"]**FATAL: Module es18xx not found **[/COLOR]

---

### Post by NoJock on 2006-02-09
[QUOTE=FarEast]OK...

Try OSS(Open Sound System) driver instead of ALSA(Advanced Linux Sound
Architecture) driver.

```
$ sudo modprobe es18xx
```[/QUOTE]

FATAL: Module es18xx not found

---

### Post by FarEast on 2006-02-09
Ah... Sorry, NoJock#-o 
There is no OSS driver 'es18xx'.

Now I am at a loss what to suggest so that you can
solve the problem on Ubuntu booted with the Live-CD.

Well... If you are satisfied with Ubuntu in other respects,
install it on your hard drive.  And join the thread below.
(If you cannot solve the problem on Ubuntu, it will be
not available on other distros, either.)

[http://ubuntuforums.org/showthread.php?t=12525](http://ubuntuforums.org/showthread.php?t=12525)

---

### Post by leLune on 2007-02-18
Found if you type:

```

sudo modprobe es18xx
sudo modprobe snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=5

```

it pops right up

edit:
I'm sorry! It's sudo modprobe snd-es18xx **NOT** sudo modprobe es18xx

eidt #2:
I do...
```

sudo modprobe es18xx
sudo modprobe snd-es18xx
sudo modprobe snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=0 dma2=1

```
**don't worry about error-msgs**

dma1=0 dma2=1 are my settings, but dma1=1 dma2=5 has worked before

---

### Post by qb4ever on 2007-02-19
Since its a ISA card you could try the **snd-es1688** driver. Thats what I had to use to get my ESS 1869 working on my old Compaq armada

---

### Post by NoJock on 2008-07-21
Thanks to all problem resolved installed pci audio card and all works well.

---

