---
title: "ARGH! It worked, now it doesn't work! WG311v3 w/ ndiswrapper"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by skelooth on 2006-06-12
So, I install ubuntu...

sudo apt-get install ndiswrapper-utl
sudo ndiswrapper -i win98driver.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

*poof* wlan0 shows up in network-admin, great!

sudo apt-get install network-manager

Wait a minute, something funny, network manager icon says no hardware detected? hmmmm

*restart*

Full bars in connection applet, flawless connection to the internet.... but network-manager still says no devices found... So i ignore it and download ~400mb of updates etc via synaptic. Everything works fine....

I restart for whatever reason...

Now I get 1 bar but it says 0% connectivity if I click on it.... network-manager still says no devices. I have an IP address and it says i've sent and recieved ~9packets, so SOMETHING worked for a split moment.

No matter what I do i can't seem to get this bizznatch to work again. I toyed around with deactiving and reactivating the wlan0, etc etc... but nothing. I tried restarting. I tried blanking out the wireless network name, i tried disabling networking. I tried disabling networking and the card then starting both back up. I tried restarting under a variety of conditions.... nothing.

I had a similar problem on my lap top (running 3 computers with ubuntu in total) and the lap top's wireless is buggish as well, where after it originally finds a network, the wireless card somehow gets turned off, and I gotta reboot before the hardware comes back online. I'm clueless though on what's going on with this one. It's a netgear WG311v3... any ideas why it would work perfect, then stop? Any reason my network-manager is not seeing it?

---

### Post by skelooth on 2006-06-13
bump

---

### Post by skelooth on 2006-06-13
arg!!!!

sudo iwconfig wlan0 essid networkname
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0

works!!!!

I have to write a bash script to make the wireless card usable? This computer is for my mom, and I'd rather not confuse her to death... not sure why this happens.

I uninstalled network manager and commented everything out but lo and wlan0 in /etc/network/interfaces

when I try to activate it in network-admin i get full signal for about 3 seconds then it drops.

---

### Post by skelooth on 2006-06-13
am I recieving no help because no one knows? Or is there a sticky or something I should have found? I've scoured these boards....

---

### Post by noname101 on 2006-06-13
Try using System | Administration | Networking to configure it. If its a Texas Instruments ACX 111 card, then you'll have to delete the acx driver.
```
sudo modprobe -r acx_pci
sudo rm -fr /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/acx
```
You may also need to modprobe ndiswrapper:
```
sudo modprobe ndiswrapper
```
For me ndiswrapper -m didn't do enough to make it load the module at boot. So I had to edit /etc/modules and add at the bottom ndiswrapper.

---

### Post by Agent86 on 2006-06-14
[QUOTE=noname101]Try using System | Administration | Networking to configure it. If its a Texas Instruments ACX 111 card, then you'll have to delete the acx driver.[/QUOTE]

I believe the WG311v3 uses a Marvell chipset. It's the WG311v2 that uses the ACX111 chip.

The way to make sure would be to do an

> lspci


command in the terminal followed by a

> lshw -C network


and let us see the results.

[QUOTE=noname101]For me ndiswrapper -m didn't do enough to make it load the module at boot. So I had to edit /etc/modules and add at the bottom ndiswrapper.
[/QUOTE]

Yes, editing /etc/modules will get ndiswrapper to load at boot time for sure.

Also, if you're NOT using Network Manager, your /etc/network/interfaces file should have some lines resembling these at the end

> iface wlan0 inet dhcp
wireless_mode managed
wireless_essid networkname


These lines would take the place of your 

[QUOTE=skelooth]
sudo iwconfig wlan0 essid networkname
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0
[/QUOTE]

and enable your interface at boot time.

---

