---
title: "my own wireless troubles"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by solx on 2006-02-27
My wireless is on a pcimcia card. The card shows up properly under lshw. Here is the relevant section:

        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:10000000-10000fff irq:9
           *-network
                description: Wireless Notebook Adapter MN-520
                vendor: Microsoft
                physical id: 0
                version: 1.0.3
                slot: Socket 0

It appears that no driver is attaching to the card. It does not show up at all under ifconfig or iwconfig. I have installed linux-wlan-ng, and my card is on the list of those that should be supported by this. What am I missing?

Thanks for the help.

---

### Post by jamesr on 2006-02-27
What is seen in dmesg 

dmesg
 gives full file and you will have to look manually for references

dmesg |grep eth0

will look for references to eth0 etc

---

### Post by solx on 2006-02-27
I dont see anything under dmesg that seems to relate directly to the wireless card. The closest matches are:

[ 1799.801856] tulip0:  MII transceiver #1 config 1000 status 782d advertising 01e1.
[ 1799.805986] tulip0:  MII transceiver #0 config 1000 status 782d advertising 01e1.
[ 1799.806105] eth0: Conexant LANfinity rev 8 at 00011400, 00:90:96:19:8B:02, IRQ 9.
...
[ 1823.584945] Yenta: CardBus bridge found at 0000:00:08.0 [0e11:b103]
[ 1823.584991] Yenta: Enabling burst memory read transactions
[ 1823.584999] Yenta: Using CSCINT to route CSC interrupts to PCI
[ 1823.585005] Yenta: Routing CardBus interrupts to PCI
[ 1823.585015] Yenta TI: socket 0000:00:08.0, mfunc 0x01001002, devctl 0x64
[ 1823.585059] ts: Compaq touchscreen protocol output
[ 1823.862237] Yenta: ISA IRQ mask 0x0818, PCI irq 9

---

### Post by solx on 2006-02-27
Further info. This is from the gnome device manager. The card is listed as Unknown Device, nested under the Cardbus controller.

info.bus                    'pcmcia'
info.parent                '/org/freedesktop/Hal/devices/pci_104c_ac50'
info.udi                     '/org/freedesktop/Hal/devices/pcmcia__1__1'
linux.hotplug_ type     1  
linux.subsystem          'pcmcia'
linux.sysfs_path              '/sys/devices/pci0000:00/0000:00:08.0/0.0'
linux.sysfs_path_device    '/sys/devices/pci0000:00/0000:00:08.0/0.0'
pcmcia.socket_number     0

---

### Post by Lambert on 2006-02-27
Do you get any output from this command?

cardctl ident

---

### Post by solx on 2006-02-27
solomon@solomon:~$ cardctl ident
Socket 0:
  product info: "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
  manfid: 0x02d2, 0x0001
  function: 6 (network)

---

### Post by jamesr on 2006-02-27
The first 3 lines were the lines of interest> [ 1799.801856] tulip0: MII transceiver #1 config 1000 status 782d advertising 01e1.
[ 1799.805986] tulip0: MII transceiver #0 config 1000 status 782d advertising 01e1.
[ 1799.806105] eth0: Conexant LANfinity rev 8 at 00011400, 00:90:96:19:8B:02, IRQ 9.

Also a later line confirmed the PCI @00:08.00.
post the output of 
sudo ifconfig -a

---

### Post by solx on 2006-02-27
solomon@solomon:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:90:96:19:8B:02
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:28606 dropped:0 overruns:0 carrier:62919
          collisions:0 txqueuelen:1000
          RX bytes:30308463 (28.9 MiB)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1472 (1.4 KiB)  TX bytes:1472 (1.4 KiB)

---

### Post by Lambert on 2006-02-28
Open up this file with text editor

```
sudo gedit /etc/pcmcia/config.opt
``` 
and add this to the bottom of the file

```

card "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
  manfid 0x02d2, 0x0001
  function 6 (network)
bind "linux-wlan-ng"

```

after saving the file and closing editor, run this command

```

sudo kill -HUP `cat /var/run/cardmgr.pid`

```

now run iwconfig to see if you have an interface. You may also consider rebooting to let all the services restart.

---

### Post by jamesr on 2006-02-28
Hi,

The card is being seen by ifconfig and has an address. Your router address is 192.168.0.xxx is that correct. Post the output of 

cat /etc/resolv.conf

---

### Post by Lambert on 2006-02-28
I'm going to bow out and let jamesr continue so not to confuse you. We're both going in different areas.

But some clarification is needed as I don't believe eth0 is your wireless card. I'm guessing it's your wired nic.

This is why.
1. Your first post of lshw shows no physical id.
2.  In first post if eth0 was attached to the device it should show logical name there but I don't see it.
3.  eth0: Conexant LANfinity - this doesn't match the lshw output of microsoft mn-520 from cardctl ident and lshw
4.  CardBus bridge found at 0000:00:08.0 is the card bus location in the pci -bus, the actual card would fall into a location of :00:08.1 or something similar
showing it's position after the cardbus bridge.

Eth0 does denote some wireless devices but there are other factors. Usually if a wired nic is found and the wireless device falls into the ethx naming scheme, the wired gets name eth0 and the wireless nic gets eth1

I will claim I might be missing something and am no networking guru so corrections are welcome.

But please clarify what eth0 is to make sure we're not looking at the wrong area.

---

### Post by jamesr on 2006-02-28
Hi Lambert,

I was hoping that you carry on with pcmcia side which you obviously a lot more experience than me, so I would be stuck on that side.

Re the networking side your questions were in the back of mind and I was hopeing that some be answered some of your pcmcia side questions.

Please do not feel that I am overiding anything that you are saying. Is there any that we could contact each other, but I am not sure how to go this.

---

### Post by solx on 2006-02-28
I want to thank you both for working on this with me.
Lambert is right: eth0 is my wired ethernet connection, and it is working just fine. I wasnt sure if jamesr was barking up the wrong tree of if he was following some nuance I wasnt aware of.

Lambert: /etc/pcmcia/config.opt is not a file. There is a config.opts and a plain "config". Looking at the contents of these files, I would guess that those lines belong in "config"
I have tried putting those lines in both files, but Im still not getting anything. However when I tried to:
sudo kill -HUP 'cat /var/run/cardmgr.pdi'
I got:
ERROR: garbage process ID "cat /var/run/cardmgr.pdi".

---

### Post by solx on 2006-02-28
I have also restarted.

---

### Post by solx on 2006-02-28
Lambert was definitely heading in the right direction with editing
/etc/pcmcia/config
I noticed that "linux-wlan-ng" (or any variant on that) was not defined among the devices at the top of /etc/pcmcia/config so I told my card to bind to "orinoco_cs" which is defined and also supports my card's chipset. I restarted and iwconfig showed an "eth1" which was my wireless card.
I would still like to get the card working with wlan-ng. My card does have an entry in the file "/etc/pcmcia/wlan-ng.conf"  Why is this not enough?

---

### Post by Lambert on 2006-02-28
[quote=jamesr]

Please do not feel that I am overiding anything that you are saying. [/quote] 
Nothing to do with that, just sometimes two people helping can cause more confusion then help. 

A little busy currently to give this due attention as I need to read over this again and do a little research. I'll come back shortly to revisit this and post if I can offer anything more.

Make sure I have the correct driver name though as it might not be bind "linux-wlan-ng"

---

### Post by jamesr on 2006-02-28
Solx,

My apologies but I think, I was barking up the wrong tree but we all make mistakes and that is my excuse.

---

### Post by Lambert on 2006-02-28
/etc/pcmcia/config is the static file that is maintained by the project maintainers of the pcmciautils program. You can add to that file but they recommend to add to the config.opts file at the bottom. both files are read for that information.

I'm not that familiar with this driver so not sure where wlan-ng.conf file comes in. I did notice your device is listed there showing to bind to prism2_cs. I'd try copying that over if you haven't to the config.opts file and reboot to see if it binds the driver to the device.

A few minutes of searching point most people at using the orinoco_cs driver instead for this device. My quick understanding is that driver is the newer version which combines feature from 3 various drivers. Not sure what features you're looking at that you require linux-wlan-ng. I don't think I can offer any more as the few tricks I know are listed here. all I can offer now is to keep searching. or maybe someone later will see this and be able to offer what the rest of us are missing.

---

