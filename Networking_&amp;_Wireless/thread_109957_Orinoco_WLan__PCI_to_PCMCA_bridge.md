---
title: "Orinoco WLan / PCI to PCMCA bridge"
date: 2005-12-29
forum: Networking &amp; Wireless
---

### Post by M_berglund on 2005-12-29
Hi, I just got my hands on a WLan for PCI, its a orinoco silver card, now im wondering how go get it up and running.. 

ifconfig just finds loopback and eth0 witch is the onboard lan... 

the lspci shows:
0000:00:14.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)

lshw:
```
server
    description: Computer
    product: VT8623-8235
    vendor: VIA Tech............
 ...........
     *-pci
          physical id: d0000000
          bus info: pci@00:00.0
          version: 00
          clock: 66MHz
        *-pci
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display UNCLAIMED
                physical id: 0
                bus info: pci@01:00.0
                version: 03
                size: 64MB
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: irq=11
 .................
        *-network
             physical id: 12
             bus info: pci@00:12.0
             version: 74
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=via-rhine irq=11
        *-pcmcia
             physical id: 14
             bus info: pci@00:14.0
             version: 01
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus irq=10
  *-network:0
       description: Ethernet controller
       physical id: 1
       logical name: eth0
       serial: 00:40:63:d8:b0:46
       capabilities: mii autonegotiation 100bt-fd 100bt 10bt-fd 10bt ethernet
       configuration: autonegociated=100bt broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=192.168.1.33 link=yes multicast=yes
  *-network:1 DISABLED
       description: controller
       physical id: 2
       logical name: sit0
```

tried modprobe orinoco, modprobe orinoco_cs, modprobe hermes, but nothing happens what i can se...

---

### Post by Lambert on 2005-12-29
That lscpi output is not a wireless device, it's a controler on your motherboard for that pci bus.

lshw doesn't show your card either 

post the output of this command

```
sudo lshw -businfo
```

and all the output of lspci

---

### Post by M_berglund on 2005-12-30
alright,,,, here it comes:

lspci:
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:00:14.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)
```

root@server:/home/phrozen # lshw -businfo
Harware Lister (lshw) - A.01.03
usage: lshw [-options ...]
        -version      print program version
        -html         output hardware tree as HTML
        -xml          output hardware tree as XML
        -short        output hardware paths

seems like it cant find the option businfo........ 
lets try the short command instead? :D

root@server:/home/phrozen # lshw -short
```
H/W path          Device  Class      Description
================================================
                          system     Computer
/0                        bus        Motherboard
/0/0                      memory     BIOS
/0/4                      processor  CPU
/0/4/7                    memory     L1 cache
/0/4/8                    memory     L1 cache
/0/14                     memory     System Memory
/0/14/0                   memory     DIMM
/0/d0000000               bridge
/0/d0000000/1             bridge
/0/d0000000/1/0           display
/0/d0000000/d             bus
/0/d0000000/10            bus
/0/d0000000/10.1          bus
/0/d0000000/10.2          bus
/0/d0000000/10.3          bus
/0/d0000000/11            bridge
/0/d0000000/11.1          storage
/0/d0000000/12            network
/0/d0000000/14            bridge
/1                eth0    network    Ethernet controller
/2                sit0    network    controller
```


I didnt think that the TI device was a wireless device, i beleved that it was the bridge between my pci port and the pcmcia orinoco card....

---

### Post by Lambert on 2005-12-30
I'm going of memory while writing this.

there were two different kinds of orinico silver cards. isa and pcmcia. With our output I'm leaning that your card is an isa which isn't plugnplay. There are extra steps needed to add the card into the bus system.

If it is a pcmcia card then its also not plug n play as it's not showing up.

Looks like you are going to have to manually configure the card. I am not one who knows how to do this.

One other command you can run to check is

```
sudo cardctl ident
``` 

this should give information about the card if it's able to read the device memory. If no information then the card is not in the system and needs to be manually added.

---

### Post by M_berglund on 2005-12-30
There is allso an PCI orinoco. or to say, they sell it as a orinico pci but in hardware specific terms its an PCI to PCMCIA bridge and then its just a regular PCMCIA orinco card installed on the brigde, The ISA version was the same thing.. just a bridge to the PCMCIA card....

And i noticed another thing, there is a Texas Instrument chipset on the bridge... with the marking PCIBUS and the TI symbol.. hm..

Edit: Found this: [http://www.seattlewireless.net/index.cgi/TexasInstrument1410](http://www.seattlewireless.net/index.cgi/TexasInstrument1410)

Now only to figure out what to do with it.. :P

---

### Post by Lambert on 2005-12-30
Not that knowledgeable here with this card but I have a question then.

You say the card bus bridge / controller is on the pci card it's self and not on the motherboard. Running the lspci command the system is identifying the bridge. If it can recognize the bridge on the card, then shouldn't it also be able to recognize the pcmica chipset also at location 0000:00:14:1

and if not then why would it only be able to read the controller on the card and not the following chipset after the controller?

Knowing this card is a little dated, is this how they used to handle the bridges controllers? Put them on the devices and not on the mother boards?

---

### Post by M_berglund on 2005-12-30
Hmm..

A picture of the device:
[IMG]http://phrozen-industries.com/3.jpg[/IMG]

The CardBus bridge dissapers when i remove this device from the pci slot, so its clear that they are atleast connected, and i dont beleve the controller is on the mobo sens there is a TI logo on the PCI device and there isnt one on the mobo...  But why i am not seeing the orinoco card aswell i dont know... tryed to use the command cardctl but only got the "command not found" answer, .... 

sens i know this card works in winXP is there any emulated enviroment so i could use the win drivers maybe? I also tried the PCI port by plugging in a ethernet network card, and it worked without problems....

If im not going to get this to work then ill try brezy, i have hoary at the moment so, maybe thats an solution? 

And by the way, thanks for taking the time..... :D

---

### Post by Lambert on 2005-12-31
See this link if it helps at all.

[http://www.linux.ie/newusers/beginners-linux-guide/plug-and-play.php](http://www.linux.ie/newusers/beginners-linux-guide/plug-and-play.php)

---

