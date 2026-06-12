---
title: "connected to wlan but firefox doesn't open webpages"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by jabadabuntu on 2009-06-28
hi all,

i installed ubuntu 9.04 hoping that those wlan problems have been fixed. and it seemed like this but still got some problems:
i can connect to my wlan router and the bar shows full sign strength but firefox doesn't open any webpages. if i connect to my router via cable it works but very slow.


some further infos:
wlan card:   RealTek 8187b
laptop:      Toshiba Satellite 300
ifconfig:
```
eth0      Link encap:Ethernet  Hardware Adresse 00:1e:33:42:6a:00   
          inet Adresse:10.0.0.3  Bcast:10.0.0.255  Maske:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:252 Basisadresse:0x2000  
 
lo        Link encap:Lokale Schleife   
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1 
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0  
          RX bytes:1342 (1.3 KB)  TX bytes:1342 (1.3 KB) 
 
wlan0     Link encap:Ethernet  Hardware Adresse 00:1b:9e:fc:18:4b   
          inet Adresse:10.0.0.3  Bcast:10.0.0.255  Maske:255.255.255.0 
          inet6-Adresse: fe80::21b:9eff:fefc:184b/64 Gültigkeitsbereich:Verbindung 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1 
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:1750 (1.7 KB)  TX bytes:4893 (4.8 KB) 
 
wmaster0  Link encap:UNSPEC  Hardware Adresse 00-1B-9E-FC-18-4B-38-34-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
iwconfig:
```
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:"IchBinNET"   
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:42:5C:9C    
          Bit Rate=1 Mb/s   Tx-Power=20 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
          Power Management:off 
          Link Quality=98/100  Signal level:-22 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions. 
```


somebody any idea

---

### Post by wojox on 2009-06-28
So what do you have?
Wireless router and cable modem?
Can you log into your router from firefox?
What type of router is it?

---

### Post by jabadabuntu on 2009-06-29
yes, i have a cable modem and a wireless router: netgear wgr614 v9
how can i connect into my router from firefox?

---

### Post by jabadabuntu on 2009-07-02
i'd like to ask one more time if there is anyone who knows what to do?

---

### Post by wojox on 2009-07-02
[http://192.168.1.0](http://192.168.1.0)

I think for netgear

---

### Post by superprash2003 on 2009-07-03
your eth0 and wlan0 has the same ip address , this ip conflict could be the root cause of your problem!!

---

### Post by jabadabuntu on 2009-07-19
hi,

how do i know what ip address it should be and how can i change it?

by the way: lately i connected into an unsecured wlan and i had no problems. it worked perfect without any kind of configuration. i hope this information is helpful.

---

### Post by Rurara on 2009-07-20
hi, yup i also have the same problem my firefox doesn't works at home but it works and open webpages in my office

---

### Post by moore.bryan on 2009-07-20
do you connect with your wireless using dhcp or a static address?

---

### Post by jabadabuntu on 2009-07-20
it is DHCP

---

### Post by martinbaselier on 2009-07-20
Dhcp will give you an ip automatically. 

Since you ip is in the 10.0.0.* range, your router probably has the ip 10.0.0.1 (or 10.0.0.2 with some of them)
so [http://10.0.0.1](http://10.0.0.1) will most probably be the address to reach your router in firefox. 

It's strange that your cabled and your wireless connection both have the same ip. If you open your network settings (right click on the network icon and choose setting or something equivalent), do you have an ip-address set there?

If so, choose dhcp instead.

Can you reach the router with it's ip address? If so, please post the correct ip address, for the next steps on determining where the problem lies.

---

### Post by moore.bryan on 2009-07-20
> **jabadabuntu said:**
> it is DHCP
are you using network-manager or wicd?

---

### Post by jabadabuntu on 2009-07-21
i use network-manager.

dhcp is already chosen. but i can not reach my router through firefox using the ip address 10.0.0.1.
i compared all settings of ubuntu in the informations about active networkconnections with the settings in windows and it is the same.

ip address 10.0.0.2
subnetmask: 255.255.255.0
default gateway: 10.0.0.1
DNS Server: 10.0.0.1

the routerlogin is 192.168.1.1 but i can not reach  my router using this address. 

> It's strange that your cabled and your wireless connection both have the same ip.

i installed ubuntu with the alternate cd and i had to make the network configurations manually. i followed the installation instructions but i couldn't find anything about eth0 or wlan0 so i took for both of them the same ip address hoping it would work.
guess this was wrong.

---

### Post by martinbaselier on 2009-07-21
I happen to have an rtl8187B USB adapter lying around here. It used to work, not great, but it worked. Now I don't seem to be able to get a connection with it either. I'll do some testing here and post my results.

---

### Post by martinbaselier on 2009-07-21
I got the rtl8187B up and runnning. 

How did I do it? 

I downloaded the latest kernel from karmic: 

[http://packages.ubuntu.com/karmic/any/linux-headers-2.6.31-3](http://packages.ubuntu.com/karmic/any/linux-headers-2.6.31-3)
[http://packages.ubuntu.com/karmic/any/linux-headers-2.6.31-3-generic](http://packages.ubuntu.com/karmic/any/linux-headers-2.6.31-3-generic)
[http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-3-generic](http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-3-generic)


Then I installed it. 
```

sudo dpkg -i linux-headers-2.6.31-3_2.6.31-3.19_all.deb
sudo dpkg -i linux-headers-2.6.31-3-generic_2.6.31-3.19_i386.deb 
sudo dpkg -i linux-image-2.6.31-3-generic_2.6.31-3.19_i386.deb

```

You only need to add the headers if you have dkms installed (virtualbox uses it for example.and I believe the ATI proprietary driver does too.)

Do not do this if you use the proprietary drivers from ATI, because they are not yet ready for this kernel as far as I know. It might be the same for Nvidea. If you use open source drivers (the drivers ubuntu installs standardly) it should work fine. 

Also do not attempt this with OSSv4 installed. 

Now reboot and it will automatically pick the new kernel. If your system does not start with the new kernel for some strange reason, reboot, press esc to enter the grub boot menu and choose 2.6.28-13. After that you would need to edit /boot/grub/menu.lst and change the default. 

Then change the speed:
```

sudo iwconfig wlan0 rate 11M

```
Apparently it has problems to work on 54Mb/s. After that change it works just fine. 

I also noticed it works for a short period of time when setting it to 11Mbps in 2.6.28-13, the current kernel in jaunty. The signal strength is much higher with the newer kernel though (63/70 and the router is standing downstairs.) and with the old kernel it stopped working after a couple of minutes. (signal strength 0; though my built in wireless showed the same strength as before)

Updating the kernel might lead to some problems, but it will probably just work fine.

---

### Post by cariboo on 2009-07-21
> **jabadabuntu said:**
> i use network-manager.

dhcp is already chosen. but i can not reach my router through firefox using the ip address 10.0.0.1.
i compared all settings of ubuntu in the informations about active networkconnections with the settings in windows and it is the same.

ip address 10.0.0.2
subnetmask: 255.255.255.0
default gateway: 10.0.0.1
DNS Server: 10.0.0.1

the routerlogin is 192.168.1.1 but i can not reach  my router using this address. 



i installed ubuntu with the alternate cd and i had to make the network configurations manually. i followed the installation instructions but i couldn't find anything about eth0 or wlan0 so i took for both of them the same ip address hoping it would work.
guess this was wrong.

Where is 10.0.0.2 coming from? If your routers internal ip address is 192.168.1.1 then the dhcp range should be from 192.168.2 - 192.168.1.254. 

Right click on the network mnager icon in the top panel and select Edit Connection, highlight your device and click Edit. Enter your user password, then click the IPv4 tab click the Method drop down and set it to manual, then in the text box below enter your ip address - 192.168.1.100, netmask - 255.255.255.0, gateway - 192.168.1.1. In the dns server text box enter 208.67.222.222, this is the Opendns  dns address, this should get you going. Finally click apply.

You should now be able to access your router and surf the interwebz.

---

### Post by moore.bryan on 2009-07-21
Do you have WEP or WPA? If WPA, TKIP or AES?

---

### Post by martinbaselier on 2009-07-21
The realtek 8187B driver has only recently been added to the kernel. It is still considered experimental by the kernel developers.

---

### Post by jabadabuntu on 2009-07-22
woow, thanks a lot for your advices. i'll try all of them and will get back to you

> 
The realtek 8187B driver has only recently been added to the kernel. It is still considered experimental by the kernel developers.

i know there were some problems with the realtek 8187B driver, but since i got connencted to the wlan i thought the driver problems has been fixed and my problem would be caused by something else. well, if all other attempts will fail i'll try to install the latest kernel

apart from this:

> if i connect to my router via cable it works but very slow.

since the cable connection doesn't use the realtek wlan modem there has to be some additional problem except of the realtek  driver problem. or is my thought wrong? however, i'll post this weekend

---

### Post by martinbaselier on 2009-07-22
There have been other reports of people having problems with both wired and wireless cards, because both were not properly supported yet. I tried connecting on the current kernel with my rtl8187B, using the same settings as on the internal wireless card. It did not work.

It showed I was connected, but I could not even reach the router. It worked for a few minutes when I switched to 11mbps, but after that it showed there was no signal. (according to my internal driver it was still at the same level as always.)

I've also tried to compile the new module for use with the current kernel, but apparently there have been some changes in the API, so it would not compile. I also tried to compile a module which I found on aircrack, this did not help either.

For the wired lan you could experiment with **ethtool**. It might help if you change speeds. Before you make any changes, I'd advice you to create a file with the current settings first. **sudo ethtool eth0 > nic.txt** will create a file called nic.txt. **cat nic.txt** will show you what's in it. use **man ethtool** for more info. Also if you know which kernel module it uses, you can see if there are any options you could set with modinfo. You can most of the time find the kernel module in use with **sudo lspci -v | less** and search for your card.

By the way did you try to turn of ip v6. Apparently it could give trouble om some hardware. I don't know by hard how to do it. It should be easy to find on google though.

---

### Post by jabadabuntu on 2009-07-29
hi all,

i decided to reinstall ubuntu. in the installation i didn't have to configure the network manually this time. dont know the reason. after the installation the wired connection with router worked perfect. so i downloaded all available updates. then i added a wireless connection manually. i chose WPA2 & WPA2 Personal. it works perfect...

well... perhaps it is not a satisfactory solution since we still dont know what was the problem, but... well... it works now :biggrin:

strange...

thanks a lot for your interest

---

