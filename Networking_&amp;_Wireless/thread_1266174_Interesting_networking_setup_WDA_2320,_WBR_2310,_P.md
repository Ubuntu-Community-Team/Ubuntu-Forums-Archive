---
title: "Interesting networking setup: WDA 2320, WBR 2310, PPPoE, Sympatico"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by edikkkk on 2009-09-14
Hey all,

I am completely new to ubuntu. been using gentoo on PPC hardware for about 2 years, tried it on my desktop, but the compiling of everything really took its toll on me. my friend recommended ubuntu because everything just works. well, he has a laptop thats supported out of the box and his wireless is a simple DHCP router with no security or anything. on top of this all, he's got an intel wireless card.....

my trip was different. i have the following setup (which worked in gentoo, mac os 10.4.11, windows xp, windows vista)

my router (RangeBooster G Router WBR-2310) is connected to my DSL modem (speedstream something, i doubt its important) on a LAN slot with an ethernet cable (there are 5 slots on the back of the router: WAN and 4 LANs. mine is hooked into one of the LAN slots). the router has an IP address 192.168.0.1, but everything is turned off, including DHCP. i have WEP shared passkey set up on the router (13 character ASCII). (not sure the difference between shared and open; i guess shared because i have to tell it to others if they want to connect to my network). i used to have ESSID turned off, but this router i have does not let me (firmware bug), so i broadcast my ESSID as usual.
from a computer (gentoo, for example), i set up networking manually. i force IP for my interface, wlan0, 192.168.0.101, broadcast is 192.168.0.255, subnet 255.255.255.0. then i use iwconfig to set ESSID and key.
(iwconfig wlan0 essid <name_of_network>
 iwconfid wlan0 key s:<my_key>)

then i create a new connection for PPPoE. it sits on the wlan0 interface, i just provide the regular username and password for my Bell Sympatico service, and off we go. we have internet.

[UBUNTU]

this is a tough one. i installed from the liveCD. my hardware seems to be recognized properly, but i cannot even connect to my wireless network. i didnt even try the PPPoE bit.

here is what i did.
first, i tried the GUI network manager (GUI for linux freaked me out). i tried manually setting the IP and leaving all the routing blank. selected 128 bit WEP ASCII passkey as i did with other OSes. no results. the green and blue dots appear and it looks like its trying to connect, but after a while it just asks me for my WEP info again. 

next, i went the manual way. i followed some guides on the wiki pages and here on the forums, tried editing my /etc/network/interfaces file to specify the IP, broadcast and subnet. used iwconfig as i did in gentoo to assign ESSID and my passkey. signal is at 0.

anyone has any ideas?
i know this is a strange setup. 

by the way, i am trying ubuntu 9.04. i have a P5K mobo, C2D processor, nvidia 9800 video. not sure what else is relevant.

i cannot post the outputs from my system since im at work and cannot ssh into my computer due to the lack of internet. if someone picks this up and decides to help a poor soul trying to get ubuntu working, i will post any output required. 

thank you

peace all!

---

### Post by edikkkk on 2009-09-14
by the way, i forgot to mention

i tried going into hardware setup and enabling madwifi through there. perhaps i didnt do enough testing, but when i enabled it, my wireless card did not even show up when i did iwconfig or ifconfig. i didnt play around with it, i went back and disabled the madwifi drivers.

---

### Post by edikkkk on 2009-09-14
ok, i got it working.
all that was needed was to go into synaptic and remove network-manager and network-manager-gnome. like i predicted, GUI in linux = evil. i mean, all those 3d virtual desktops are cool, but when it comes to setup, lets just stick to command line and config files.

peace all!
hope this helps someone.
pst me if you need additional info about my setup.

---

