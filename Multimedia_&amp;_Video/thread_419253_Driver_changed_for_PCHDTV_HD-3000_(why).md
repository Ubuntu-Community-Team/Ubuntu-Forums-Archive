---
title: "Driver changed for PCHDTV HD-3000 (why?)"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by dara on 2007-04-22
My PCHDTV HD-3000 card worked under 6.10 and MythTV fairly well, though under 7.04 I can no longer add it under the DVB choice in the setup screen.  I believe this is because the driver automatically selected for this card has changed from 6.10 to 7.04.  After a 6.10 install, sudo lshw showed cx8800/cx88-dvb as the drivers, but now they are cx8800/cx88-mpeg.  Is anyone else with this card having problems after upgrading to 7.04?  Is it worth trying to change drivers or should I try to get MythTV to work with this card with the new drivers?

Dara



PS Output from lshw:

Ubuntu 6.10:

           *-multimedia:0
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant
                physical id: 2
                bus info: pci@02:02.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx8800
                resources: iomemory:fc000000-fcffffff irq:169
           *-multimedia:1
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                vendor: Conexant
                physical id: 2.2
                bus info: pci@02:02.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx88-dvb
                resources: iomemory:fd000000-fdffffff irq:169

Ubuntu 7.04:

   *-multimedia:0
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant
                physical id: 2
                bus info: pci@02:02.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
                resources: iomemory:fc000000-fcffffff irq:18
           *-multimedia:1
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                vendor: Conexant
                physical id: 2.2
                bus info: pci@02:02.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx88-mpeg driver manager latency=32 maxlatency=88 mingnt=6
                resources: iomemory:fd000000-fdffffff irq:18

---

### Post by electronikjunkie on 2007-04-23
The loading of cx88-dvb in 2.6.20 is not automatic anymore. You have to add it to /etc/modules. Before you do, try this:

```
sudo modprobe -rv cx88-dvb
sudo modprobe -rv cx8800
sudo modprobe -rv cx88-blackbird
sudo modprobe -v cx88-dvb
sudo modprobe -v cx8800
ls -l /dev/dvb/adapter0
ls -l /dev|grep video
dmesg
```

You should see some dvb and video devices and dmesg should show the card added. Also you may want to blacklist cx88-blackbird as you shouldn't need it. MythTV should see the card now.

---

### Post by dara on 2007-06-10
I typed those lines into the terminal before running MythTV Backend Setup and it does result in the DVB setting seeing the card.  However, when I select Finish, the card does not show up as listed.  I tried to create a source anyway (HDTV) and that doesn't show up as listed either.  So of course the Input Connections screen isn't going to work.

I also tried the procedure on [https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list) which didn't work either (I completely reinstalled after trying this to try out MythDora so there was no remnant of this procedure when trying your procedure.)

I must be missing something obvious - I can't believe it worked so easily in Edgy and now I can't get it to work - frustrating.  I'm tempted to ditch this card (which I've never been that happy with anyway and get an HDHomeRun which has its own help page.

Dara

---

### Post by dara on 2007-06-10
One last thing - assuming I can get this to work using the commands given above, do I need to do this just once or put these commands in particular files that get executed on boot (figure that I know absolutely nothing about blacklisting, etc. just tell me the files and what goes in them - this has worked great for me w.r.t. wireless and sound, both of which require editing text files for my setup).

Thanks, Dara

---

