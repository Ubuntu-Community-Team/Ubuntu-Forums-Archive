---
title: "Wifi problem, ASUS eee pc 100H"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by itsvan on 2013-04-20
HI i am currently on Ubuntu Ubuntu 10.04 LTS,i am using a ASUS eee pc 100H...Problem is my computer cannot connect to my wifi network.yet it reads all of the available networks in the area just fine..what could be the problem? i double checked my password and everything else in my house connects just fine to it except this laptop, its weird because this has never happened before...before this i had installed the latest ubuntu 12.0 i think it was and the wifi worked fine but it was to slow for my netbook so i uninstalled it. i dont know if it was a netbook edition of ubuntu but i did not like it i prefer the other one..please help :(

---

### Post by itsvan on 2013-04-20
itsvan@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:0b:ea:1b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:d9:78:11
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:f8000000-f800ffff

---

### Post by itsvan on 2013-04-22
itsvan@ubuntu:~$  lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
	Kernel driver in use: ata_piix
01:00.0 Network controller: RaLink RT2860
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
	Kernel driver in use: ATL1E
	Kernel modules: atl1e

---

### Post by itsvan on 2013-04-22
itsvan@ubuntu:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:"Itsvoogles Network"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1E:E5:5E:32:A7   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-35 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by marvselby on 2013-04-22
You didn't say if the machine could see your router but from the output of iwconfig I'm guessing it does.  I'm also guessing you use Network Manager to manage the connection.  Iwconfig is saying that the link quality is 100% so the problem seems to be in the configuration.  Are you using WPA/WPA2?  Use Network Manager to set up password etc. for the connection.

---

### Post by itsvan on 2013-04-25
Yes my computer does see my router and i try to connect to it and it fails each time, i do use WPA/WPA2 and as far as my knowledge goes its set up correctly with password and everything...ive been researching at it seems to be a problem with my rts860 driver or something but i have not been succesfull in installing it because i am not very good at it... but this isnt for certain what else could be going on?

---

### Post by mörgæs on 2013-04-25
10.04 is almost out of support. Have you thought of a clean install of Lubuntu 13.04?

---

### Post by itsvan on 2013-04-25
and well i stuck with ubuntu cus it was the first one, i later tried kubuntu but didnt appeal to me as much so i stuck with ubuntu ever since...im just a little unfamiliar with all the differences between them

---

### Post by itsvan on 2013-04-25
What worries me is just the specs and requirements of the new distros, 10.04 runs perfectly if there is any alternative with similar requirements to run i wont mind giving it a shot...

---

### Post by itsvan on 2013-04-25
as i mentioned in my first post, using the new version of ubuntu 12.04 or whatever it is my wifi worked instantly, but i cannot use that on this netbook because for some reason it is way to slow, lags and ends up crashing each time..so i have to stick with 10.04....NO i have never even heard of Lubuntu, i havent been using linux well over 2 years, what is the main difference?

---

### Post by marvselby on 2013-04-26
I don't think you have a driver problem since you can see other routers plus the output from ifconfig indicates the adapter is associated with the router.  Try looking at the configuration of one or all of the other machines which do connect to determine how they are configured.  if that doesn't give you any insight then you could try turning off all the security on the router and on this machine.  If you can connect that way, then it's a problem with the password or WA/WPA2.  At the risk of being insulting, I'm going to remind you that passwords are case-sensitive.  There's a checkbox in Network Manager's configuration to show the password which will help you determine if the password is indeed correct.

I am also running 10.04 and I am contemplating upgrading to 12.04.  So far I haven't because I don't like the desktop interface that comes with it.  I suspect that's what was causing your crashes and running slow.  There is a way to change the interface to the traditional Gnome but I haven't pursued that yet.

---

### Post by itsvan on 2013-04-26
> **marvselby said:**
> I don't think you have a driver problem since you can see other routers plus the output from ifconfig indicates the adapter is associated with the router.  Try looking at the configuration of one or all of the other machines which do connect to determine how they are configured.  if that doesn't give you any insight then you could try turning off all the security on the router and on this machine.  If you can connect that way, then it's a problem with the password or WA/WPA2.  At the risk of being insulting, I'm going to remind you that passwords are case-sensitive.  There's a checkbox in Network Manager's configuration to show the password which will help you determine if the password is indeed correct.

I am also running 10.04 and I am contemplating upgrading to 12.04.  So far I haven't because I don't like the desktop interface that comes with it.  I suspect that's what was causing your crashes and running slow.  There is a way to change the interface to the traditional Gnome but I haven't pursued that yet.

 i checked but the password is correct, what i ended up doing was installing xubuntu and to no surprise the Wifi connected perfectly.....i think theres an issue with ubuntu 10.04 and my type of wireless driver, ive researched this and many seem to have the same issue, also you are absoutlely right i do not like the new desktop for ubuntu and that is deffenetaly what is causing my crashes but i would consider changing if there is a way to change it back to the original, if you find out how let me know thank you very much:p for now il  be running xubuntu ;)

---

### Post by marvselby on 2013-04-26
I think you're right.  There have been some problems with 10.04 and Ralink wifi.  I think it has to do with the drivers supplied with 10.04.  I know I fought like crazy with my USB dongle before I broke down and compiled the driver from Ralink's website.  When I switched to a PCI card, I built the driver before I even tried an install and it worked perfectly.  I seem to remember someone saying the 10.04 drivers were reverse-engineered or something like that.

If you are consumed by curiosity, you could try building the driver and trying it.  Yeah!  Right!  Glad to hear Xubuntu is working.

In wandering around this morning, I  found something really terrific.  It's a script that examines the wireless configuration and outputs a text file.
Here's how to do it:  copy and paste this code into the prompt: wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
That will download the script, run it and output the information in your home directory.  How cool is that?

One thing I happened to notice was that iwconfig called your wifi wlan0.  That's what makes me think it's a reverse-engineered driver.  The Ralink drivers are usually called ra0.  Just a thought.

I'm preparing to upgrade my laptop to 12.04, probably over the weekend.  I copied my data from my Ubuntu partition to my Windows 7 partition tonight.  I'm going looking for the way to get rid of Unity and install classic Gnome.  I'll pop back soon to let you know how it went.

---

### Post by itsvan on 2013-04-27
> **marvselby said:**
> I think you're right.  There have been some problems with 10.04 and Ralink wifi.  I think it has to do with the drivers supplied with 10.04.  I know I fought like crazy with my USB dongle before I broke down and compiled the driver from Ralink's website.  When I switched to a PCI card, I built the driver before I even tried an install and it worked perfectly.  I seem to remember someone saying the 10.04 drivers were reverse-engineered or something like that.

If you are consumed by curiosity, you could try building the driver and trying it.  Yeah!  Right!  Glad to hear Xubuntu is working.

In wandering around this morning, I  found something really terrific.  It's a script that examines the wireless configuration and outputs a text file.
Here's how to do it:  copy and paste this code into the prompt: wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
That will download the script, run it and output the information in your home directory.  How cool is that?

One thing I happened to notice was that iwconfig called your wifi wlan0.  That's what makes me think it's a reverse-engineered driver.  The Ralink drivers are usually called ra0.  Just a thought.

I'm preparing to upgrade my laptop to 12.04, probably over the weekend.  I copied my data from my Ubuntu partition to my Windows 7 partition tonight.  I'm going looking for the way to get rid of Unity and install classic Gnome.  I'll pop back soon to let you know how it went.

Cool thanks for the script il keep it just in case, although i obliterated ubuntu into xubuntu and all is working fine..and ta that ralink driver like you said seems to be be the issue i came across but i just coudnt figure out how to fix it..im not to good with installig anything without using the command terminal...yah keep me updated with how your ubuntu goes im curious to see how it turns out

---

### Post by nachwaal3ab on 2013-04-28
[COLOR=#000000]You didn't say if the machine could see your router but from the output of iwconfig I'm guessing it does. I'm also guessing you use Network Manager to manage the connection. Iwconfig is saying that the link quality is 100% so the problem seems to be in the configuration. Are you using WPA/WPA2? Use Network Manager to set up password etc. for the connection.[/COLOR]

---

### Post by marvselby on 2013-04-28
Well, I am now a very happy camper.  I have a system on my laptop that looks very much like it did before only now I am running 12.04!

You are halfway to the solution.  I installed Xubuntu 12.04 over my original installation of Maverick, mainly because I didn't want to install and then uninstall Unity.  I like the Xubuntu installer because it detected my Maverick installation and offered to upgrade it.  Well, somewhere along the way it kinda choked so I restarted the installation and ended up with Xubuntu 12.04.  The Xfce interface was close to what I wanted, but just not quite.  After a bunch of reading, I used Synaptic to install Gnome.  There's a package called gnome.  I'm not sure if it installs gnome-session-fallback but you could check to make sure.  (That's what gives the classic Gnome.)

I was disappointed when I restarted the machine and got the Xfce interface.  i had originally set up Xubuntu to not require a login so I double checked the setup under USERS.  It said a password was required.  I logged off and much to my surprise I got a screen where I could choose the interface.  It has a number of choices - Gnome, Gnome Classic, Gnome classic without effects, Xfce, Xubuntu and maybe one or two more.  I chose Gnome classic, input my password, and there was my Gnome classic interface.  The only thing I had to do was move the bar from the top of the screen to the bottom.  It took a couple of tries before I figured out that if you hold down the Windows button plus the ALT key and right-click the bar it pops down a menu where I could choose "properties".  The popup remains as long as you hold the keys.  I changed the position of the bar from the properties screen and made it a bit wider.  Some of the settings and stuff are in slightly different place on the menu, but it's for all practical purposes the same.

I'm not sure if it's configured to not require a login, but now when I power down and restart, it loads what I was running when I did a shutdown.  That is good.  

This whole exercise got me to thinking about the differences between Windows and Linux.  We may grumble a lot about changes and all the choices we have, but by gosh we have choices.  I feel sorry for the poor people who are stuck with Windows 8.  They have no choices of interfaces.

Hope this helps you get the classic Gnome.

---

