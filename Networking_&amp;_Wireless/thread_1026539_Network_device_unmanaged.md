---
title: "Network device unmanaged???"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by linuxishard on 2008-12-31
hi, i have an odd issue that only occured after my system crashed just last night, 

my wifi adapter is working,imusing it right now, but i cannot scan for new networks and so on, since the built in network manager says that that device is unmanaged.

truthfully my laptop is in a bad state, its taken sum what of a beating over time, but a few major beatings left it for want of a better word DEAD.

as it happens,
intrepid saved its life,the point is, some of the hardware had to be removed due to fault, including my built in wifi card, 
so im forced to use a usb wifi adapter, its a netgear WG111v3,
ive used it alot, its works just fine first time with ndiswrapper,(thanx ubuntu forums for that gem of info) 

But i can only connect to my default network. since the network manager just says that the device is unmanaged. any ideas how to make it managed?

i realise that i canuse other network, or specifically Wifi network tools, to do just the same job. but it is a pain to have to.

its odd i thought since it only did this after a system crash,
which i also could use a hand working out why it does that too, 
it crashes randomly, but i think it may be my motherboard having a big nasty crack all through it, which causes it to have issues turning on without external power, it runs fine of the battery, it powers up but never even reaches bios, it just hangs on a blank screen.... im used to it buy this point but it sucks. 

any ideas, like i sed its not really urgent, but i could use a hand workin it out. 

thanks in advance :D

---

### Post by jobano on 2009-03-27
as seen on [https://answers.launchpad.net/ubuntu/+question/58626](https://answers.launchpad.net/ubuntu/+question/58626)
change managed=true in /etc/NetworkManager/nm-system-settings.conf

worked for me :)

---

