---
title: "Nvidia GeForce 6800"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by wilberworld on 2006-06-05
Peeps,

My New Dell Dimension 9150 wont work with ubuntu because i cant get the graphics to work. As soon as i load the live CD so that i can install the screen just goes funny with a load of colours all over the place so i cant even install different drivers (because i cant get it to load properly in the 1st place)

It didnt work with Breezy either (same issue)

I have seen loads of posts saying there are major issues with NVIDIA cards but why is this? What am I supposed to do about it? If Ubuntu wont load i cant use it.

Does anyone know if this will be fixed by the next realease or if there is a good reason why NVIDIA will never work out of the box in ubuntu ?

Thanks,
Wilber

---

### Post by mdh on 2006-06-05
I have GeForce 6800 card and making the nvidia driver work was not difficult. This guide [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) enumerates a couple of methods and I followed the second method in the guide and it worked like a charm. Just be aware that in order to make method2 work, you would need to recompile the kernel module every time your upgrade your kernel. 

Hope this helps you to get started.

---

### Post by tseliot on 2006-06-05
[QUOTE=wilberworld]Peeps,

My New Dell Dimension 9150 wont work with ubuntu because i cant get the graphics to work. As soon as i load the live CD so that i can install the screen just goes funny with a load of colours all over the place so i cant even install different drivers (because i cant get it to load properly in the 1st place)

It didnt work with Breezy either (same issue)

I have seen loads of posts saying there are major issues with NVIDIA cards but why is this? What am I supposed to do about it? If Ubuntu wont load i cant use it.

Does anyone know if this will be fixed by the next realease or if there is a good reason why NVIDIA will never work out of the box in ubuntu ?

Thanks,
Wilber[/QUOTE]
Download the "alternate-install" version of Ubuntu so as to be able to install it on your computer.

Then you will need to install the Nvidia driver with my guide

---

### Post by echo $USER on 2006-06-05
I have a eVGA 6800GS CO.  I had to enable the safe VGA mode to get the stupid GUI on the live cd to work so I could install Dapper.  Once that finished, i loaded the drivers.

---

### Post by Torquemada28 on 2006-06-11
[QUOTE=tseliot]Download the "alternate-install" version of Ubuntu so as to be able to install it on your computer.

Then you will need to install the Nvidia driver with my guide[/QUOTE]
I have the same issue with my 6800 GS. After Kubuntu installs, the screen is a messed up collection of random colours when you boot it.
I downloaded the Kubuntu "alternate-install" and it makes no difference.
I originally installed from the normal Kubuntu DVD using the text mode and the alternate install apparently did the same thing. It looked like the same process to me but I'm a complete linux noob, so I could me mistaken. In any case, the result was the same using either installation source.

How would you propose I resolve this issue?
Remember, I'm a linux noob, so explain it like you're speaking to an idiot.

---

### Post by tseliot on 2006-06-11
[QUOTE=Torquemada28]I have the same issue with my 6800 GS. After Kubuntu installs, the screen is a messed up collection of random colours when you boot it.
I downloaded the Kubuntu "alternate-install" and it makes no difference.[/QUOTE]
What does "it makes no difference" mean?

Did you manage to install it? If so, the xserver would crash after the installation but this would be a problem easy to solve.

---

### Post by MrEricSir on 2006-06-13
[QUOTE=Torquemada28]I have the same issue with my 6800 GS. After Kubuntu installs, the screen is a messed up collection of random colours when you boot it.[/QUOTE]
This is exactly what happens to me.  The system boots fine, but X is garbled with streaks of random colors.  Both the nv and nvidia drivers that come with Kubuntu have this problem.

The vesa driver works fine.  I haven't tested the official Nvidia driver or anything else.

---

### Post by m3sm3r on 2006-08-25
I'm glad I'm not alone:

Specs: 

Computer Model: Dell XPS/Dimension 400/9150
OS: Ubuntu Dapper 6.06-1 LTS
Kernel: 2.6.15-26-386
lspci output for the 6800:
0000:01:00.0 VGA compatiable controller: nVidia Corporation NV41.1 [GeForce 6800]

Dell's info on my card from my service tag:

nVidia 256MB PCI Express x16 GeForce 6800

Dell also gives up the following in the original system configuration page:

CARD (CIRCUIT), GRAPHICS, 256, 6800, HMGA11B

With the live CD, I'm having the same out-of-range display artifacts. Had to install in safe mode, and the fresh install only works with the vesa driver. 

I've tried tseliots's method 1, 2, and his envy script to resolve the issue...nothing. 

I'm a linux n00b who is fresh out of ideas. If anyone can help, I'm in your debt.

---

### Post by tseliot on 2006-08-25
> **m3sm3r said:**
> I'm glad I'm not alone:

Specs: 

Computer Model: Dell XPS/Dimension 400/9150
OS: Ubuntu Dapper 6.06-1 LTS
Kernel: 2.6.15-26-386
lspci output for the 6800:
0000:01:00.0 VGA compatiable controller: nVidia Corporation NV41.1 [GeForce 6800]

Dell's info on my card from my service tag:

nVidia 256MB PCI Express x16 GeForce 6800

Dell also gives up the following in the original system configuration page:

CARD (CIRCUIT), GRAPHICS, 256, 6800, HMGA11B

With the live CD, I'm having the same out-of-range display artifacts. Had to install in safe mode, and the fresh install only works with the vesa driver. 

I've tried tseliots's method 1, 2, and his envy script to resolve the issue...nothing. 

I'm a linux n00b who is fresh out of ideas. If anyone can help, I'm in your debt.
Try point 4 of the Problems Section of my guide (you don't need to use NVAGP 0)

---

### Post by m3sm3r on 2006-08-25
tseliot: Thank you for responding, and for your work on improving the ubuntu experience...

Unfortunately, solution 4 did not help. As X starts, the monitor goes to inactive.

To confirm settings, below is the device section of my xorg.conf.

Section "Device"
    Identifier     "NVIDIA Corporation NV41.1 [GeForce 6800]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "RenderAccel" "Off"
    Option         "IgnoreDisplayDevices" "DFP,TV"
    Option         "NoRenderExtension" "Off"
    Option         "AllowGLXWithComposite" "Off"
    Option         "Accel" "Off"
EndSection

I will post an excerpt of my Xorg.0.log file momentarily.

---

### Post by m3sm3r on 2006-08-25
Ok...looking through the Xorg.0.log, I come across several identical errors at the end.

(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory. 

Otherwise, I see no errors. I also have no pen/tablet inputs connected to my desktop. 

Thank you in advance for your response...

---

### Post by tseliot on 2006-08-25
It's not a real error. It's in your xorg.conf only for compatibility reasons (with tablets) but it doesn't cause any problem

---

### Post by m3sm3r on 2006-08-28
Doh. This whole thing was a matter of PEBKAC.

The machine had two monitors hooked into the 6800. I never noticed the other monitor's output since I used the second input for another machine. 

tseliot...thank you for all your help.

---

### Post by plugitin on 2006-08-29
I have an nVidia 6800 GS from eVGA, and when I try going into the ubuntu OS all I get is messed up white screen, and whenever I press enter a few times I hear a little drum-beat thingy. 

This is my first time using Linux and it's really late at night right now, and I can't exactly think that great (or really type). So if you have any questions I can reply to them later, but if anyone has any suggestions or solutions I would *greatly* appreciate it. I *really, really* want to get my ubuntu up and running!

thanks in advance
mark

---

### Post by tseliot on 2006-08-29
> **plugitin said:**
> I have an nVidia 6800 GS from eVGA, and when I try going into the ubuntu OS all I get is messed up white screen, and whenever I press enter a few times I hear a little drum-beat thingy. 

This is my first time using Linux and it's really late at night right now, and I can't exactly think that great (or really type). So if you have any questions I can reply to them later, but if anyone has any suggestions or solutions I would *greatly* appreciate it. I *really, really* want to get my ubuntu up and running!

thanks in advance
mark

boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

---

### Post by plugitin on 2006-08-29
Wow! Thanks a lot! I really apprectiate it. 

I am going to go and try it right now.

---

### Post by plugitin on 2006-08-29
Went through everything and loaded the Vesa drivers, but to no avail. It looked even worse than when the nVidia drivers were loaded. At least with the nVidia I could use and see the mouse and kinda see a grayish text-box, with the Vesa drivers it is just all artifacts.

Any other suggestions?

---

### Post by wilberworld on 2007-02-07
Ok,

i posted this question origionally and still havent got this sorted - i admit im a noob and dont really know what im doing but i was kinda hoping the feisty version would work since i hear the ati and nvidia drivers are turned on by default. However, i downloaded the latest feisty beta and this also has the same issue as pervious versions and still brings up a load of colourfull rubbish on my screen after the ubuntu loading logo....

Any more suggesions that are EASY to do?

Thanks,
Will:lolflag:

---

### Post by klein de usa on 2007-02-27
hi
i'm no expert but i have crashed ubuntu a few times lol sorry
i have a dimension 4700 with a nvidia 6800 vid card, if your's is like mine it has a intel video card on the mother board that is disabled, the nvidia card is pci, maybe you can disable the nvidia card or take it out and use the intel, the vidio cards are hit or miss it looks to me yours doesn't work mine dose, the next guys doesn't.
mine won't do dir , it was just a thought .

---

### Post by tdiguy on 2007-10-08
I have a gforce 6800 PCIE card on my desktop. So far i have loved ubuntu on my laptop. I have a problem with my desktop where i did not have any issues installing the newest ubuntu but it is in very low resolution and if i go to the restricted driver management and enable the card it never starts correctly with graphics problems. I have downloaded some packages that i thought would correct this but i cant tell that they did anything and my resolution is still low and it only allows me to choose 640x480 and 800xsomething

---

### Post by tdiguy on 2007-10-10
No information at all?

---

### Post by bij33 on 2007-10-10
I had a similar problem. I disabled the Nvidia driver usage completely and renamed xorg.conf to something else (any name). I think when Ubuntu does not find the xorg.conf file during the system start-up it uses the default driver automatically.  The screen resolution (1280X1024) and refresh rate of (75 Hz) that was not obtainable with Nvidia before are now both set correctly on my Dell. For now, I am not using Nvidia driver till there is a fix out.

---

