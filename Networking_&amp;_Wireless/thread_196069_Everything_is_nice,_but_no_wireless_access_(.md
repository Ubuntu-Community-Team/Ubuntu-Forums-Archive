---
title: "Everything is nice, but no wireless access :("
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by Imre Mehesz on 2006-06-13
hello ya'll,

it looks like i've been posting everywhere, BUT here.. now here it is:

- finally i could install the new ubuntu (6.06) on my PIII compaq armada M700 laptop. it has a PCI WP54G v2 wireless card in it which is recognized by the system with texas chipset ... i even got the power led on, i can see it with iwconfig:[I]
lo no wireless extensions

wlan0 IEEE 802.11b+/g+ ESSID:"linksys" nickname:"acx v0.3.21"
[etcetcetc]

sit0 no wireless extensions (<- i don't know what this is though!?)[/I]

in the /etc/networks/interfaces i have:

[I]iface wlan0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1 (<- this is my router's IP )
wireless-mode managed (<- somebody recommended to put this here)
wireless-essid linksys (<- this is my ESSID)

auto wlan0
[/I]

sudo iwlist wlan0 scan gives me:
*wlan0 No scan results*

on the GUI side:
i have an "!" sign on my two little monitor screens on the top-right corner if i click on it, the status value says:
*disconnected*

if I go to the configuration i have everything activated ...

i even installed a little tool called **network-manager-gnome** or something like this but it says:
*"No network connection"*

i cannot even ping 192.168.1.1 - there is absolutely no connection between the router and my card :(

i hope you guys can help me!

thank you,

eMzMiM

---

### Post by noname101 on 2006-06-13
To get your card to work you'll have to use ndiswrapper:
```

sudo modprobe -r acx_pci
sudo rm -fr /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/acx
sudo apt-get install ndiswrapper-utils
```
Now you need to download a windows driver for your card or use the cd it came with.  
I would recommend the [HWP54G drivers]("http://www.hawkingtech.com//support/details.php?CatID=19&FamID=33&ProdID=149&Rev=T2") it doesn't matter what drivers you use. As long as it is the same chipset. Asuming its Texas Instruments ACX 111 as you only said Texas Instruments. It could be ACX 100. In that case you'll have to use a different driver then the above. Ok so now extract the file you download or if its on the cd copy the files from your cd to your home folder.

Just double click t2wpg2k4_7.0.1.33.zip on your desktop and right click the Driver folder and choose extract and then for the folder choose your home folder.
Now do this:

```
sudo ndiswrapper -i Driver/TNET1130.INF
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

For some reason doing ndiswrapper -m doesn't do enough for it to load the module at boot so do the following too:

```
sudo gedit /etc/modules
```

Add at the bottom ndiswrapper.

Then set it up using System | Administration | Networking or just do ifdown wlan0 then ifup wlan0. If its already setup.

---

### Post by Imre Mehesz on 2006-06-13
with this answer ubuntu definitely won another user for this linux OS :)

thank you very much. i had to reboot though (maybe just a */etc/init.d/networking rebstart* would do the trick too, but i just wanted to make sure ;) )

and one more thing:
i had to put my ISP's IP addresses as domains.... for some reason without them i couldn't go to the internet (just on the local network!)

but it works 100% for now, big THANK YOU!


--
eMzMiM

---

### Post by blackjack6.21.91 on 2006-06-14
Congrats on joining the community!

---

