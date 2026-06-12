---
title: "TerraTec Cinergy T Pcie Dual"
date: 2012-04-06
forum: Mythbuntu
---

### Post by Sctmon on 2012-04-06
I have had my Myth system running happily for a few years now with a NovaT-500 tuner card but I am currently building a new system to replace it.
I decided to use a TerraTec Cinergy T Pcie Dual for this one because a quick glance here  [http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_PCIe_dual](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_PCIe_dual) mentioned that the drivers are supported from kernel 3.3.

Unfortunately I neglected to check the current kernel verion and it is no surprise that I cannot get it to work. I have now installed 12.04 beta 2 and also kernel 3.3.0-030300 but the card is still not being recognised. It is appearing in the list of attached pci devies 
lspci
Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
lspci -vnn
06:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder [14f1:8852] (rev 04)
    Subsystem: TERRATEC Electronic GmbH Device [153b:117e]
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at fd200000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885
    Kernel modules: cx23885


But I cannot get mythtv to see it. I am assuming that the drivers are not loaded for it. Can anyone offer any help or suggestions on where to start trouble shooting?

My Linux knowledge is fairly limited to solving various mythtv issues over the years so there are plenty of gaps.

---

### Post by nickrout on 2012-04-06
look at the output of dmesg and also see if there are any entries in /dev/dvb.

---

### Post by Sctmon on 2012-04-07
Thanks for replying,

I have 11.10, kernel 3.0.0.17 installed and the dmesg output for that is attached. I have also installed 12.04 on another partition and upgraded to kernel 3.3 and the dmesg output is also attached. The complete files were too large to attach so I may well have edited out something important!

Neither make a lot of sense to me unfortunately and neither system has a /dev/dvb folder

12.04 with 3.3 kernel does not seem to work particularly well as the back end will not start and a few other errors pop up after it boots so in an ideal world I would like to find a way to get the card to work with 11.10.

Excuse my ignorance but would the latest build of LinuxTV drivers be included with each updated kernel and if so should 3.0.0.17 not have them? If not would I be able to build them myself in 11.10? Would that help?

---

### Post by Sctmon on 2012-04-07
I followed this very helpful guide [here]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#If_the_Modules_did_not_load_correctly_or_the_device_is_still_not_configured_correctly_for_use:") and it all seems to work!, the backend now finds the card.

Only down side is that it had caused a few minor problems with the desktop ie the panel at the top of the screen is now blank and missing the clock and other notifications and the whole system has frozen a couple of times so far but I can live with that for the moment.

Can you suggest a way of only installing the driver I need for this card as opposed to the complete set of dvb drivers, it is obviously causing some kind of issue with my system.

---

### Post by rrofes on 2012-04-14
hello sctmon,
I am planning to use this cinergy card with mythtv also. did you solve the problem? can I use "Cinergy T PCIe dual" with mythtv?
best regards,

---

### Post by Sctmon on 2012-04-14
I think I did. I reinstalled mythbuntu 11.10 on a new drive, installed all updates, added gnome desktop and then built the linuxTV drivers, rebooted, but that time the drivers didn't load. I re formatted the drive and tried again and on the 3rd attempt doing exactly the same thing the dvb folder appeared in /dev and the card is working. This was just a test as I am waiting until 12.04 is out (12 days to go) to build my new backend.

Seems like a good card. I only bought it because I have 1 pci slot and 5 pci-e slots. Once my new backend is working and ready to go I will take the novaT500 out of my old system to fill the pci slot. If you can wait a couple of weeks I will post an update but I think it will be fine.

---

### Post by rrofes on 2012-04-14
many thanks for your fast answer. did you use the two tuners at the same time from mythtv? for example, recording one channel while watching another?

---

### Post by Sctmon on 2012-04-14
I haven't tried that yet. All I did was check the drivers loaded and mythtv recognised both tuners. I also successfully scanned for channels using both tuners.
I have left the drive I installed it on at work so I won't be able to try recording until I get it back during the week.

---

### Post by rrofes on 2012-05-03
Hello again Sctmon. I have a problem with my Cinergy T PCIe Dual. Got working only one of the two tuners. See my post:

[http://ubuntuforums.org/showthread.php?p=11900855#post11900855](http://ubuntuforums.org/showthread.php?p=11900855#post11900855)

Any help would be very welcome!

---

