---
title: "How to isolate problem with video?"
date: 2014-01-25
forum: Multimedia Software
---

### Post by robertzito on 2014-01-25
I have been having an odd issue since upgrading to 13.10. At least 3 or 4 times a day I will lose video on my laptop. The one thing that is consistent is that ever time it happens I hear the fan of the laptop speed up. The screen gets all covered lines through it sometimes I will get a white screen. But every time all I have to do is force a hard shut down and it comes right back and maybe good for day or hours.

What can I do to begin trouble shooting and isolating the issue so that I can finally fix it?

---

### Post by QIII on 2014-01-25
Hi!

Could you give us the specs on your machine?  What is the video setup?

---

### Post by robertzito on 2014-01-25
I am not using any outputs, just the display on the laptop itself.

It is a Dell [COLOR=#444444][FONT=Trebuchet MS]Inspiron 17R 5720 

Memory: [/FONT][/COLOR]7.7 GiB
Processor: Intel® Core™ i7-3612QM CPU @ 2.10GHz × 8 
Graphics: Intel® Ivybridge Mobile
OS Type: 64-bit

---

### Post by Yellow Pasque on 2014-01-26
It sounds a bit like GPU overheating. It may be an Optimus (hybrid GPU) machine, and you'll have to install Bumblebee to turn off the nvidia card when it's not being used so it doesn't heat up the interior and suck your battery. Show output of lspci:

```
sudo update-pciids
lspci
```

---

### Post by robertzito on 2014-01-26
Thank you, I will give it a try & followup to the post in hopes it may assist others.

---

### Post by robertzito on 2014-01-26
Here is the output
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by robertzito on 2014-01-26
Just so I am clear; in reading about Bumblebee it says [COLOR=#333333][FONT=Ubuntu Beta] "provide support for [/FONT][/COLOR][NVIDIA Optimus]("http://www.nvidia.com/object/optimus_technology.html")[COLOR=#333333][FONT=Ubuntu Beta] laptops" but I know my graphics card is Intel, should I still give it a try?[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2014-01-26
No, it's not an Optimus machine (from quick Googling, I saw that some Inspiron 17R 5720's were).

I'm not really sure what to tell you to do next. If it was me, I'd run a LiveUSB of 13.10 and see if I could reproduce the behavior there.

---

### Post by Bucky Ball on 2014-01-26
*Thread moved to** Multimedia & Video**.*

---

### Post by robertzito on 2014-01-26
Thanks I will give it a try, I dont think it is an over heat issue because somtimes the laptop can be off overnight and the first boot of the day can see the issue.

---

### Post by robertzito on 2014-02-13
Just in case it helps I have been using sudo tlp start and I have noticed it has gotten better, I don't want to "spit in the wind" but so far so good!

---

