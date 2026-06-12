---
title: "Dlink DWL-G520+ B1 working on Ubuntu 8.10"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by Racha Cuca on 2009-03-11
Hello Folks,
After spending some days looking, around this excelent forum, for a soluction that would bring my old DWL-G520+ Version:B1 back to life, I finally made it. This is my first post in this forum so, forgive me if it should no be here.

OBS: This card uses the ACX111 firmware. To identify your card you can do as Craig teached in his tutorial.

**sudo lspci -n**

look for one of those numbers:
    * 104c:8400 (acx100 CardBus)
    * 104c:8401 (acx100 PCI)
    * 104c:9066 (acx111 Cardbus/PCI)

Enough talk, lets go put the stuff to work. Here is what I did:

1- First, remove your card from the PC to avoid the annoying blinking caps lock freeze bug.

2- Login again and do the following:

**sudo apt-get install linux-backports-modules-intrepid**

That will kill the blinking caps lock bug

3- You may boot your pc and attach your wireless card again
 
4- Remove the network manager to keep you free from the always DHCP bug.

**sudo apt-get remove --purge network-manager**

5- Download the firmware with WEP support that the Craig talked about in his page: [http://www.houseofcraig.net/acx_firmware.tar.bz2http://www.houseofcraig.net/acx_firmware.tar.bz2]("http://www.houseofcraig.net/acx_firmware.tar.bz2http://www.houseofcraig.net/acx_firmware.tar.bz2")

Thanks Craig for the great tutorial!

6- Extract the firmware files to some place (i.e. your home directory)

7- Copy all firmware files (just the files) to /lib/firmware

8- Enter the following command:
**sudo modprobe acx**

9- Edit the network interfaces file

**sudo vi /etc/network/interfaces**

10- Add your wireless configuration there (mine goes that way):

[B]auto wlan0
 iface wlan0 inet static
     address 192.168.0.51
     netmask 255.255.255.0
     network 192.168.0.0
     broadcast 192.168.0.255
     gateway 192.168.0.1
     wireless-mode managed
     wireless-channel auto
     wireless-rate auto
     wireless-essid <put your essid here>
     wireless-key <put your WEP key here>

[/B]

11- Done, you are (with some luck) connected to your wireless network.

---

