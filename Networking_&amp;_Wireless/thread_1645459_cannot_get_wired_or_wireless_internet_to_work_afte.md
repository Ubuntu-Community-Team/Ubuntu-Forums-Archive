---
title: "cannot get wired or wireless internet to work after upgrade to 10.10"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by hypnotysd on 2010-12-14
today i installed ubuntu 10.10 on my hp mini 210 netbook. previously i had ubuntu netbook remix running and had no problem accessing the internet both wired and wireless; however, since installing 10.10 i have been searching for a solution for the last six hours but have been unable to get either to work. 

as far as hardware is concerned i have a broadband bcm4313 802.11 network controller and am running through a linksys router which i know to be working because i have 4 other computers connected to it all with internet access.

i checked ifconfig and a lo conection was listed but no eth0. i also tried downloading a broadband tar.gz driver but dont have any packages to build it and cant get any since the computer has no internet.

i assume wired is easiest to setup so lets start there even though i use wireless 90% of the time. im new to linux so please dont expect me to know any terminal commands. thanks in advance

---

### Post by grahammechanical on 2010-12-14
I cannot stay with you for long. Can you please confirm that you see a network icon on the top panel to the right. As you say that networking is not working then the icon will look like a wedge of curved lines expanding upwards and it will have a red exclamation mark set against it. This appears when ever networking is disabled whether you are using a wired or wireless connection.

If there is no network icon then go to System>Preferences>Startup Applications. Look for Network Manager in the list of programs. Is there a tick mark against it? If not click in the Network Manager line and reboot.

If you do have a Network Manger icon then right click it and see if there is a tick mark against Enable Networking and Enable Wireless. If there is not then click both of them to enable these features.

By the way, do you need to switch the wireless adapter on through a FN+function key combination? Has that been done? Was the wireless hardware switched on during the installation process? I am just asking. We need to eliminate the silly things.

Regards.

---

### Post by hypnotysd on 2010-12-14
thank you for getting back to me so quickly. the network icon on the task bar is there with the red exclamation mark through it. when i right click it there are four options. Enable Networking and Enable Notifications both have check marks next to them, Connection Information is blacked out, and when I click the Edit Connections option a window pops up where i can manually add a network but ive never had to manually set up any of my other computers. In the past ive just selected it from available networks that automatically load on the list. also wireless is enabled on my keyboard. is there any way to check if i have a network controller driver installed or if it got deleted somehow when i installed 10.10 over my previous data?

---

### Post by Cahan on 2010-12-14
Howdy and I am having somewhat the same problem here but for me I have wireless and cell phone with no problem but no wired it is not even listed and I am running 10.04 LTS but I did use the 10.10 live cd and did have wired there my system is a Toshiba C655 and I am using the 64bit old system was a dell C640 but was having bluetooth problems with 10.10 that is why I went with 10.04

---

### Post by hypnotysd on 2010-12-17
hey can anyone help me out here im dead in the water. from what ive read i cant get internet without creating an eth0 connection with an ip address so can anyone tell me how to do that?

---

### Post by fedu on 2010-12-17
Hi, I'm having similar issues, but I have no network icon and network manager is not listed in System>Preferences>Startup Applications. I just installed Ubuntu Studio 10.04 on my laptop. I had straight 10.04 as a second OS on it before and had network issues as well. I fixed those issues and felt like an idiot afterwards. Try making a new network connection and name it whatever the router's SSID is. I was trying to name my network as "Home" so I could identify it, but it wasn't being recognized. 

I don't know if that helps at all, but I figured I'd try.

Good Luck!


PS - If anyone reads this and knows how to add the network manager to System>Preferences>Startup Applications, let me know. Thanks!

---

### Post by matt-fender on 2010-12-17
punch this into a terminal, can you see anything that looks remotely like a network adaptor?

```
lspci
```

---

### Post by matt-fender on 2010-12-17
> **fedu said:**
> Hi, I'm having similar issues, but I have no network icon and network manager is not listed in System>Preferences>Startup Applications. I just installed Ubuntu Studio 10.04 on my laptop. I had straight 10.04 as a second OS on it before and had network issues as well. I fixed those issues and felt like an idiot afterwards. Try making a new network connection and name it whatever the router's SSID is. I was trying to name my network as "Home" so I could identify it, but it wasn't being recognized. 

I don't know if that helps at all, but I figured I'd try.

Good Luck!


PS - If anyone reads this and knows how to add the network manager to System>Preferences>Startup Applications, let me know. Thanks!


System>Preferences>Startup Applications>Add

Command is ```
nm-applet --sm-disable
```

Name is ```
Network Manager
```

Comment is ```
Control your network connections
```

---

### Post by hypnotysd on 2010-12-17
@fedu
i added my router SSID to my list of network connections but the network still isnt found

@matt-fender
i typed in lspci and my network controller was listed at the bottom as  broadcom BCM4313 802.11, does that mean the driver is installed or is it  just recognizing the hardware?

---

### Post by matt-fender on 2010-12-17
> **hypnotysd said:**
> @fedu
i added my router SSID to my list of network connections but the network still isnt found

@matt-fender
i typed in lspci and my network controller was listed at the bottom as  broadcom BCM4313 802.11, does that mean the driver is installed or is it  just recognizing the hardware?


Thats a good start, 

punch this into a terminal

sudo lshw -C network

paste output please

---

### Post by hypnotysd on 2010-12-18
> **matt-fender said:**
> Thats a good start, 

punch this into a terminal

sudo lshw -C network

paste output please
PCI (sysfs)

*-network UNCLAIMED
description: Network controller
product: BCM4313 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:53000000-53003fff

---

### Post by matt-fender on 2010-12-18
Hiya, if you read back through your output from the teminal you can see

```
UNCLAIMED
```

this means your wireless card is recognised but has no driver installed for it, or ubuntu is not using it. I'll have a dig around and get back to you

---

### Post by matt-fender on 2010-12-18
Try searching the synaptic package manager for 

broadcom-sta-tools i think?

i used to run the same card on 9.10

ummm might be worth checking to see if there is any hardware drivers available for your net card

This is under Administration, there may be a Broadcam hardware Driver for you to install and try.

Hope this helps, looking forward to hearing back.

---

### Post by hypnotysd on 2010-12-18
the only software i found in the synaptic package manager relating to broadcom just provides a list of pci id's which make it possible to detect the model of wireless card and its installed. i couldnt find any additional drivers. i havent been able to update anything since i installed 10.10 since ive never been online. 

im very confused why that last readout says my wireless card is 64bit since i ordered a 32bit pc and have 32bit 10.10 installed. how can i check this?

i did download a 32bit broadcom driver for my wireless card but its a tar.gz file and i couldnt figure out how to install it. should i use this?

---

### Post by matt-fender on 2010-12-18
> **hypnotysd said:**
> the only software i found in the synaptic package manager relating to broadcom just provides a list of pci id's which make it possible to detect the model of wireless card and its installed. i couldnt find any additional drivers. i havent been able to update anything since i installed 10.10 since ive never been online. 

im very confused why that last readout says my wireless card is 64bit since i ordered a 32bit pc and have 32bit 10.10 installed. how can i check this?

i did download a 32bit broadcom driver for my wireless card but its a tar.gz file and i couldnt figure out how to install it. should i use this?


Extract that tar file, there should be a readme file, you may have to adjust the makefile if you use WPA encryption

---

### Post by hypnotysd on 2010-12-18
i tried installing the tarball before but i dont have the headers and tools to build the file. ill look for them and get back with you. im new to this ive never had to install anything without using apt-get

---

### Post by matt-fender on 2010-12-19
Do you have installation disc for the Broadcam for Windows?

If you do, i can guide you through installing an app called ndiswrapper which should allow you to a windows inf driver file, to connect.

---

### Post by hypnotysd on 2010-12-19
i have a soft copy for windows 7 install..

---

### Post by hypnotysd on 2010-12-19
i tried searching for ndiswrapper-utils-1.8 in the synaptic package manager but i its not listed so i just downloaded ndiswrapper and thats a tarball as well. could it be listed as something else in the manager?

---

### Post by matt-fender on 2010-12-19
To install ndiswrapper without an internet connection.

Insert your ubuntu cd

System>Administration>Synaptic  Package Manager


Open Package Manager

Settings > Repositories


ensure that the "Installable from CD-ROM/DVD is ticked"

save/close

go back to synaptic package manager and search "ndis"

Mark ndisgtk for installation and the other needed dependencies should install with it.

---

### Post by hypnotysd on 2010-12-21
i added the cd to the repository but when i tried to reload the synaptic  package manager to download the package information an error occurred after  downloading 9 packages.

"W: Failed to fetch [http://us](http://us).archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg Could not resolve  'us.archive.ubuntu.com' "

other links were listed in the error but they  were all along those lines. all i did was add the cd to the directory. 

then i decided to search for the ndis files and they were all listed so i marked them for install and  ndiswrapper-common files installed correctly but ndisgtk and  ndiswrapper-utils-1.9 data could not be found

---

### Post by irockonguitar on 2010-12-22
> **hypnotysd said:**
> i added the cd to the repository but when i tried to reload the synaptic  package manager to download the package information an error occurred after  downloading 9 packages.

"W: Failed to fetch [http://us](http://us).archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg Could not resolve  'us.archive.ubuntu.com' "

other links were listed in the error but they  were all along those lines. all i did was add the cd to the directory. 

then i decided to search for the ndis files and they were all listed so i marked them for install and  ndiswrapper-common files installed correctly but ndisgtk and  ndiswrapper-utils-1.9 data could not be found


I tried doing this too, but my error was:

"W: Failed to fetch cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_amd64.deb File not found"

Is it normal that it is looking for AMD files when my processor is an Intel i5?

EDIT: I suppose it's looking for AMD because the iso is for amd64. Will it still work on Intel? I don't see an option on the Ubuntu homepage to download an intel version of 10.10.

---

### Post by hypnotysd on 2011-01-01
i reinstalled ubuntu 10.10 from the cd making sure my ethernet cable was connected during install. upon restart my computer was online with a wired connection.

i then went to system->administration->additional drivers and my broadcom driver was listed for install.

after installing the broadcom driver went to system->preferences->network connections and manually added my wireless network to the list. after selecting this network a wireless link was established.

---

### Post by matt-fender on 2011-01-18
> **hypnotysd said:**
> i reinstalled ubuntu 10.10 from the cd making sure my ethernet cable was connected during install. upon restart my computer was online with a wired connection.

i then went to system->administration->additional drivers and my broadcom driver was listed for install.

after installing the broadcom driver went to system->preferences->network connections and manually added my wireless network to the list. after selecting this network a wireless link was established.


Glad you got it sorted!, I forgot to mention, after adding the CD-ROM as a reposit, you may need to close down anything related to synaptic ( sometimes a reboot will help )  before it registers the CD as a reposit. Glad you're sorted though.

---

### Post by kumar@india on 2011-09-05
I have installed ubuntu 10.10 32bit as a guest s/w on virtual box.My main OS is windows xp 32 bit. Initially after installation the internet was working fine. But suddenly the internet stops working . I have a wired connection. I also verified from network manager that the OS recognizes
my wired connection with message "eth0 active". Even I am able to ping my internet server. But through
Firefox INTERNET IS NOT ACCESSABLE.
Any help is appriciated. Also let me know if any more information is required.

---

