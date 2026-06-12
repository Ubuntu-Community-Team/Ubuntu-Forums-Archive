---
title: "Mythbuntu Shuts Down Networking"
date: 2010-05-20
forum: Mythbuntu
---

### Post by zuixro on 2010-05-20
So I have several Mythbuntu 10.04 computers on the same network. I've been slowly upgrading them all to Gigabit NIC's, and so far I haven't had any problems. The most recent one I did, though, didn't seem to like it. It seems to be disconnecting from the network if it's not sending anything. The lights on my switch turn on when something is connected. With this computer, the lights turn on steady for a second, flash (indicating that there is activity on the line), turn steady again, then turn off. When I first boot up the computer I can't SSH in. I have to go to the computer and disconnect and reconnect from/to the computer a couple of times. (which is inconvenient, because it doesn't usually have a keyboard or mouse attached to it, gotta get a KVM switch) Eventually I can get it to where it stays steady, but then the lights on the switch say that it's 10/100 not gigabit. I've used this model of NIC before on other computers, and it's never given me any trouble. 


Does anyone know what could cause Ubuntu to shut off the network card?

---

### Post by matt06 on 2010-05-20
What is your network card?  Are you using the same card is the other machines?  You should be able to find out with 'lspci'.  Here is mine:

```
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

---

### Post by ian dobson on 2010-05-20
Hi,

Go to a ternimal prompt and do a dmesg and have look for errors comming from your network card.

It could be hardware conflict or maybe the same IP address on several PC's on your network, also try a different network cable. 

When I updated my network to gbit one of my boxes showed similar problems, it would sometimes connect and work for a short time before loosing the connection. After I replaced all the wiring/wall plugs everything worked without a single problem.

Regards
Ian Dobson

---

### Post by zuixro on 2010-05-30
Sorry for the delayed response... Been a little busy. Networking is kind of working... I did have 5 commercial flagging jobs fail with error code "254", which I couldn't find any documentation about.

Anyway, lspci gives me this:
```
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```I have use this same network card (same type, different physical card) in my main backend, with no problems. 
edit: I just realized that it's the same card that you are using matt06 haha.

dmesg gives me tons of lines of:
```
[462868.891729] r8169: eth0: link down
[462871.245388] r8169: eth0: link up
[462873.389426] r8169: eth0: link down
[462875.890275] r8169: eth0: link up
[462878.238385] r8169: eth0: link down
[462880.545725] r8169: eth0: link up
[462882.366517] r8169: eth0: link down
[462884.006474] r8169: eth0: link up
```This computer (and all my computers) are set up for a static IP with a host name in the router (which I rebooted). Switching it off of a static IP made the networking somewhat stable, but, as you can see above, it still drops out. All of my static IP's are in the 192.168.1.150 range, well above the 192.168.1.100-116 that my router uses for DHCP.

I just realized that I didn't switch out the network cable, but it was working just before I changed the network card. I did try another port on my switch. I will see if I can get another cable and try that.

---

### Post by matt06 on 2010-05-31
Hi zuixro.  I'm not sure what is causing your connection to continuously drop and reconnect like that.  Someone with more expertise will have to chime in here.  This is what my dmesg looks like WRT my NIC.

```
[    1.706354] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.706390] r8169 0000:02:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.706436] r8169 0000:02:07.0: no PCI Express capability
[    1.707104] eth0: RTL8169sb/8110sb at 0xdf87e000, xx:xx:xx:xx:xx:xx, XID 1000
[   18.844459] udev: renamed network interface eth0 to eth1
[   18.857308] r8169: eth1: link up
```

I don't know why eth0 becomes eth1, but it's been like that since I installed the card I believe.

---

### Post by ian dobson on 2010-05-31
Hi,

Linux or better udev is renaming your new network card to eth1 as udev has "seen" a different network card that way eth0.

Your network up/down/up problem sounds alot like a switch/network cable problem. Are you using home made cables or pre purchased? At what speed is the network running at? I had a problem with my frontend that worked without any problems at 100MBit, after changing over to a giga switch the network would go up and down like a yoyo. In the end I replaced all the wiring and since then I`ve not had any more problems.

You can try using the mii tool to force the network card to 100MBit to see if that helps.

Regards
Ian Dobson

---

### Post by zuixro on 2010-05-31
matt06: Those lines were what was there after a few days of uptime. It's off right now, I'm gonna boot it up soon and see what it says then.

ian dobson: It is a high quality Cat6 cable made by Belkin I believe. (might even be shielded). Like I said, I'm gonna have to round up a new one to try.  I've changed switch ports and that hasn't helped. 

Now I'm thinking it might have something to do with the hardware. It's a P3 system, and a little below the requirements on the Mythbuntu website. I've never had any problems though. 

I recently reinstalled Mythbuntu on this system, and that didn't help...

---

### Post by matt06 on 2010-05-31
> **ian dobson said:**
> Linux or better udev is renaming your new network card to eth1 as udev has "seen" a different network card that way eth0.

Hi Ian.  Thanks for the info  That udev line was mine and I'd like to find out a bit more about why it does this, but I haven't been motivated enough to check it out since it 'works' as is.

---

### Post by matt06 on 2010-05-31
> **zuixro said:**
> Now I'm thinking it might have something to do with the hardware. It's a P3 system, and a little below the requirements on the Mythbuntu website. I've never had any problems though. 

I recently reinstalled Mythbuntu on this system, and that didn't help...

You might be onto something.  Have you tried physically moving the card to a different slot?  The cables/switch/router/whatever else is in the mix is a good place to look as well.

I forgot to say also that I am running Mythbuntu 9.10 as a master backend on this machine.  Anyway, maybe this will help you zuixro.

```
matt@mythtv:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

OT..Ok, I was intrigued enough by Ian's info to run 'ethtool eth0' to see if it showed anything, but just got this:

```
matt@mythtv:~$ sudo ethtool eth0
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available
```

I have no problem with just leaving mine as eth1.

[Using ethtool]("http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html")

---

### Post by zuixro on 2010-06-02
Ok, ethtool gives me this:

```
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes


```

Right now it looks like it's connected steadily. (I'm pinging it from my main computer, and it hasn't dropped a packet in 5 minutes)

Checking Mythweb, It's running a commercial flagging job. It started one when I first turned it on, but it "Failed with exit status 254".

NFS mounts look fine, looks like this might be one of those "one out of ten" times that it gets a good connection.  The switch says it's a 100Mbit connection, but I'm kinda ok with that. If it gives me much more trouble, I'll switch back to the old card.

---

### Post by matt06 on 2010-06-03
> **zuixro said:**
> Ok, ethtool gives me this:

```

    Speed: 1000Mb/s


```

The switch says it's a 100Mbit connection, but I'm kinda ok with that. If it gives me much more trouble, I'll switch back to the old card.

Is "Speed: 1000Mb/s" a problem when using a 100Mbit switch?  Perhaps you can force the card to 100Mbit to see if it helps?

---

