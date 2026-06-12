---
title: "No sound in maverick"
date: 2010-11-01
forum: Multimedia Software
---

### Post by Skyline649 on 2010-11-01
Hello guys,
****
I'm having problems with my ubuntu 10.10 .That's the story.....

I've installed a fresh copy of 10.10 from the website of ubuntu, the desktop verison ,32bit , for my medion **WIM2160** .

So , i don't have any problems with media, wifi or web browsers , but the only problem is that i don't have sound from my internal speakers on my laptop, although i have sound with my headphones (logitech).I will upload the output info from my terminal :)

**lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by alexandari on 2010-11-01
U checked the mixer's settings?

---

### Post by Skyline649 on 2010-11-01
> **alexandari said:**
> U checked the mixer's settings?

Yep, i checked it , everything is set to max. i'll post a picture

[IMG][[IMG]http://img178.imageshack.us/img178/4792/screenshotqeb.png[/IMG]](http://img178.imageshack.us/i/screenshotqeb.png/)

Uploaded with [ImageShack.us](http://imageshack.us)[/IMG]

---

### Post by ivanovnegro on 2010-11-01
I have the same problem on the notebook of my girlfriend with Maverick, I have to check the Alsamixer there, to see if I can manipulate something.
At the moment its the same, Maverick works great on her older notebook except the internal sound, also HDA Intel.

---

### Post by Skyline649 on 2010-11-02
> **ivanovnegro said:**
> I have the same problem on the notebook of my girlfriend with Maverick, I have to check the Alsamixer there, to see if I can manipulate something.
At the moment its the same, Maverick works great on her older notebook except the internal sound, also HDA Intel.

Is your model the same az my sound ALC 883?

---

### Post by ivanovnegro on 2010-11-02
> **Skyline649 said:**
> Is your model the same az my sound ALC 883?

I did not check it yet and now I have not access to the notebook of my girlfriend, so I dont know if the chip is the same.
On my HP I have also HDA Intel but another model and I dont have sound issues.

Edit: It could take some time to use her notebook again, she is not here now, I will let you know asap if she does not change her mind with Linux because of this issue. She has a no name notebook, I have no idea what it is.
Can you tell me what type of notebook you have or what computer?
Its a pity but this issue makes some people to go back to Windows.

---

### Post by ivanovnegro on 2010-11-02
I can remember me of one thing, just for fun I put in her notebook the PCLinuxOS Live CD and the sound did not work neither, the same with Mint, I was looking for alternatives, so maybe its really a hardware problem with all Linux Distros, Im not sure.

---

### Post by Skyline649 on 2010-11-02
> **ivanovnegro said:**
> I can remember me of one thing, just for fun I put in her notebook the PCLinuxOS Live CD and the sound did not work neither, the same with Mint, I was looking for alternatives, so maybe its really a hardware problem with all Linux Distros, Im not sure.

Yes, I understand you... it's pity ,that because of this problems with linux they switch back to windows.By the way my laptop is MEDION ,it's a german brand ,not so good quality but i'm happy for the moment, it u want u can take a look from the website [http://www.medion.de/md96290/uk/noflash.html](http://www.medion.de/md96290/uk/noflash.html), it already 3 years old , the only thing that i changed it's one hard drive cause i broke it accidently ,and also the charger ( I step on it while it was on the ground at home :d ).

But still i want to fix the sound problem, if anyone can help us it will be good

---

### Post by ivanovnegro on 2010-11-02
> **Skyline649 said:**
> Yes, I understand you... it's pity ,that because of this problems with linux they switch back to windows.By the way my laptop is MEDION ,it's a german brand ,not so good quality but i'm happy for the moment, it u want u can take a look from the website [http://www.medion.de/md96290/uk/noflash.html](http://www.medion.de/md96290/uk/noflash.html), it already 3 years old , the only thing that i changed it's one hard drive cause i broke it accidently ,and also the charger ( I step on it while it was on the ground at home :d ).

But still i want to fix the sound problem, if anyone can help us it will be good

Thats really funny, its not exactly the same model, but its really similar like it looks and her notebook is also 3 years old and the more funny is that it broke one time too, the harddisk. Though its working fine and Ubuntu goes without problems and its really not so bad but she wants her sound back, I can understand it.
I still have to check the mixer.

---

### Post by alexandari on 2010-11-02
&#1057;&#1082;&#1080;&#1074;&#1072;&#1081; &#1090;&#1086;&#1074;&#1072; [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

&#1048; &#1089;&#1098;&#1097;&#1086; &#1090;&#1077; &#1089;&#1098;&#1074;&#1077;&#1090;&#1074;&#1072;&#1084; &#1076;&#1072; &#1087;&#1088;&#1077;&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1096; &#1072;&#1083;&#1089;&#1072;&#1090;&#1072;

```
 sudo apt-get purge linux-sound-base alsa-base alsa-utils 
```

```
 sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop 
```  

&#1074;&#1080;&#1078; &#1095;&#1077; &#1077; &#1076;&#1072;&#1076;&#1077;&#1085;&#1086; &#1079;&#1072; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1077; &#1080; gdm ubuntu-desktop &#1097;&#1086;&#1090;&#1086; &#1097;&#1077; &#1079;&#1077;&#1084;&#1077; &#1076;&#1072; &#1092;&#1088;&#1098;&#1082;&#1085;&#1077; &#1082;&#1072;&#1090;&#1086; &#1084;&#1072;&#1093;&#1085;&#1077;&#1096; &#1072;&#1083;&#1089;&#1072;&#1090;&#1072; &#1080; &#1103; &#1089;&#1083;&#1086;&#1078;&#1080;&#1096; &#1087;&#1072;&#1082; (&#1089;&#1083;&#1091;&#1095;&#1074;&#1072;&#1083;&#1086; &#1084;&#1080; &#1089;&#1077; &#1077; )

---

### Post by ivanovnegro on 2010-11-02
> **alexandari said:**
> &#1057;&#1082;&#1080;&#1074;&#1072;&#1081; &#1090;&#1086;&#1074;&#1072; [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

&#1048; &#1089;&#1098;&#1097;&#1086; &#1090;&#1077; &#1089;&#1098;&#1074;&#1077;&#1090;&#1074;&#1072;&#1084; &#1076;&#1072; &#1087;&#1088;&#1077;&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1096; &#1072;&#1083;&#1089;&#1072;&#1090;&#1072;

```
 sudo apt-get purge linux-sound-base alsa-base alsa-utils 
``````
 sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop 
```&#1074;&#1080;&#1078; &#1095;&#1077; &#1077; &#1076;&#1072;&#1076;&#1077;&#1085;&#1086; &#1079;&#1072; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1077; &#1080; gdm ubuntu-desktop &#1097;&#1086;&#1090;&#1086; &#1097;&#1077; &#1079;&#1077;&#1084;&#1077; &#1076;&#1072; &#1092;&#1088;&#1098;&#1082;&#1085;&#1077; &#1082;&#1072;&#1090;&#1086; &#1084;&#1072;&#1093;&#1085;&#1077;&#1096; &#1072;&#1083;&#1089;&#1072;&#1090;&#1072; &#1080; &#1103; &#1089;&#1083;&#1086;&#1078;&#1080;&#1096; &#1087;&#1072;&#1082; (&#1089;&#1083;&#1091;&#1095;&#1074;&#1072;&#1083;&#1086; &#1084;&#1080; &#1089;&#1077; &#1077; )

Ehm, what?
Im not really able to understand everything of Bulgarien if this is the case.
But what you want to say, that I have to preinstall the alsa stuff? I just go to look for the Link.

---

### Post by Skyline649 on 2010-11-02
> **ivanovnegro said:**
> Ehm, what?
Im not really able to understand everything of Bulgarien if this is the case.
But what you want to say, that I have to preinstall the alsa stuff? I just go to look for the Link.

yes, actually yes, but when i apply the code commands in the terminal,i got sound but after the restart i lost it again :)

---

### Post by ivanovnegro on 2010-11-02
> **Skyline649 said:**
> yes, actually yes, but when i apply the code commands in the terminal,i got sound but after the restart i lost it again :)

Maybe you have to add your user to the sound, thats what I did in Arch, it seems to be similar, take a look in the forums about this as at the moment Im busy or maybe our bulgarian friend could help us again.

(&#1061;&#1074;&#1072;&#1083;&#1072; &#1090;&#1080; &#1079;&#1072; &#1086;&#1074;&#1086;.)

---

### Post by Skyline649 on 2010-11-02
> **ivanovnegro said:**
> Maybe you have to add your user to the sound, thats what I did in Arch, it seems to be similar, take a look in the forums about this as at the moment Im busy or maybe our bulgarian friend could help us again.

(&#1061;&#1074;&#1072;&#1083;&#1072; &#1090;&#1080; &#1079;&#1072; &#1086;&#1074;&#1086;.)

aham, i see , i'm gonna try to add my username to the command line in the conf. file

---

### Post by ivanovnegro on 2010-11-04
Ok, the sound chip is the same.
And I manipulated the alsamixer without success like you.
Now I will try the same with that command to see if I can change it.
At the end, you have now internal sound fixed?

Regards

---

### Post by Skyline649 on 2010-11-04
> **ivanovnegro said:**
> Ok, the sound chip is the same.
And I manipulated the alsamixer without success like you.
Now I will try the same with that command to see if I can change it.
At the end, you have now internal sound fixed?

Regards

i still don't have anything,actually it's now getting worst, i don't have the indicator icon on the top panel , but still i get sound from my USB headphones

---

### Post by fatwilly6 on 2010-11-05
> **ivanovnegro said:**
> Maverick works great on her older notebook except the internal sound, also HDA Intel.
Hi all - there are a number of issues with different Intel HDA chips and the fact that various manufacturers butcher & hack the chips & drivers. There are several posts within this forum about it and alterations you may need to make to config files to get things to work properly. I seem to recall it's all about output pins & logic control!!  Just search the forum for Intel HDA Sound and you will find . . fortunately I have an emu10k1 chip in my pc!

---

### Post by ivanovnegro on 2010-11-05
> **fatwilly6 said:**
> Hi all - there are a number of issues with different Intel HDA chips and the fact that various manufacturers butcher & hack the chips & drivers. There are several posts within this forum about it and alterations you may need to make to config files to get things to work properly. I seem to recall it's all about output pins & logic control!!  Just search the forum for Intel HDA Sound and you will find . . fortunately I have an emu10k1 chip in my pc!

Thank you for your suggestions, will check the forum entries asap.

---

### Post by Skyline649 on 2010-11-08
> **ivanovnegro said:**
> Thank you for your suggestions, will check the forum entries asap.

I fixed it :) ,i just add something to the last line of **sudo nano /etc/modprobe.d/alsa-base.conf**

This is the line: options **snd-hda-intel model=auto**

and then save with Ctrl+X when it ask for save click on Y and then restart the laptop , and u gonna hear the log in sound of ubuntu :)

---

### Post by ivanovnegro on 2010-11-08
> **Skyline649 said:**
> I fixed it :) ,i just add something to the last line of **sudo nano /etc/modprobe.d/alsa-base.conf**

This is the line: options **snd-hda-intel model=auto**

and then save with Ctrl+X when it ask for save click on Y and then restart the laptop , and u gonna hear the log in sound of ubuntu :)

Thats great news. I played a while with the notebook but my girlfriend wanted to work with it, so I did not have many time to explore everything and I even wanted to download the driver for this Realtek as I found something in the net.
But your workaround sounds great, will try this, thank you.

---

### Post by ivanovnegro on 2010-11-11
No, it does not matter what I do with this notebook, the sound does not work. I tried all the options and in the conf also but nothing. I have only external output when I plug in boxes or headphones. Maybe I did something wrong. The only option I have now would to freak out or to search in the Ubuntu documentation about this specific Intel chip.

---

### Post by lidex on 2010-11-11
> **ivanovnegro said:**
> No, it does not matter what I do with this notebook, the sound does not work. I tried all the options and in the conf also but nothing. I have only external output when I plug in boxes or headphones. Maybe I did something wrong. The only option I have now would to freak out or to search in the Ubuntu documentation about this specific Intel chip.

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

