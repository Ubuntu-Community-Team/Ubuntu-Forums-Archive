---
title: "Installed WL driver, unable to conect with wep?"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by BigCityCat on 2009-08-12
I'm really new to this but I have manged to get the wireless to show up after restart. I just can't get it to connect. It keeps asking for wep key over and over and then fails. Here are my outputs.

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

pan0      no wireless extensions.

> *-network                                                                      
       description: Ethernet interface                                           
       product: MCP67 Ethernet                                                   
       vendor: nVidia Corporation                                                
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:da:b0:86
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:21:00:47:cb:c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:b4:3e:fd:58:4f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

> ii  linux-restricted-modules                   2.6.28.14.19                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.28-11-generic 2.6.28-11.15                             Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-2.6.28-14-generic 2.6.28-14.19                             Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common            2.6.28-14.19                             Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic           2.6.28.14.19                             Restricted Linux modules for generic kernels

---

### Post by superprash2003 on 2009-08-12
post output of **sudo iwlist scanning** , have you tried various authentication types liek 64bit, 128bit etc

---

### Post by BigCityCat on 2009-08-12
I recieved two different outputs. The first was while it was scanning and the second when it wasn't.

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1F:B3:73:0E:C1
                    ESSID:"2WIRE126"          
                    Mode:Managed              
                    Frequency=2.417 GHz (Channel 2)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-90 dBm
                    IE: WPA Version 1                                     
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0F:66:8F:65:A4
                    ESSID:"linksys"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1B:2F:5C:AD:96
                    ESSID:"Wireless"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-51 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s


---

### Post by BigCityCat on 2009-08-12
I only tried wep because that is what I have. It was given to me by the provider.

---

### Post by BigCityCat on 2009-08-12
Also I have tried the fb cutter firmware on both Kubuntu and Ubuntu on this same laptop. It worked in ubuntu and not kubuntu, but I want to make Kubuntu work.

---

### Post by BigCityCat on 2009-08-12
I'm having a conversation with myself. lol

Is there some other resource to fix all the wireless problems that Linux have or is it basically hit or miss?

I have already read through almost everything on this site. You guys who are helping do a service but the magnitude of problems is hard to deal with. I can see that, but all the animosity towards windows with all these problems Linux has seems a little crazy.

---

### Post by chili555 on 2009-08-13
As long as you have a connection with wired ethernet, which you do, Network Manager and its cousin knetworkmanager will not allow a wireless connection. Please see: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7). Especially:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.In order to test your connection, you must detach the wire and ideally, issue a command:```
sudo ifdown eth0
```May I assume you are trying to connect to:> Cell 03 - Address: 00:1B:2F:5C:AD:96
ESSID:"Wireless"
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:5/5 Signal level:-51 dBm Noise level:-90 dBm
Encryption key:onThat's the only access point I see that is using WEP. Have you double-checked your key? Is it 10 or 26 characters? Are you plugging it in to 'WEP 40/128 bit key?' Have you tried both upper and lower case for any letters in your key, viz:```
096C7F280E
```and, also:```
096c7f280e
```Sorry for the delay in replying.

---

### Post by BigCityCat on 2009-08-13
Chili I can't test this right now cause I was giving Ndiswrapper another shot. I didn't use the ubuntu community instructions the last time and I wanted to try a few drivers. Mostly the one that came directly off the windows partition. Here is the out put from that install. Bear in mind I have blacklisted a few drivers. I realize these are two seperate tasks we are dealing with.

After isntalling driver in ndiswrapper and running

ndiswrapper -l

> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
        device (14E4:4328) present (alternate driver: ssb)

here is my blacklist.conf

[QUOTE]# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist ssl
blacklist rmmod wl ssl
blacklist b43[/QUO

---

### Post by chili555 on 2009-08-13
I believe the last part needs to be as follows:```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist ss[COLOR="Red"]b[/COLOR]
blacklist wl 
blacklist b43
```Also, I notice that, in addtion to a blacklist.conf, you have a separate file, blacklist. Please copy and paste it for me. Thanks.

---

### Post by BigCityCat on 2009-08-13
I have tried several different drivers with ndiswrapper with no success.

It seems either way I try it doesn't work. With the ndiswrapper I can't find a driver that works and when we set it up your way I can see my network but cant connect. I think it has something to do with wep but that key was assigned by my provider and I don't know how to fix or change that security. I heard something about maybe resetting the router and trying to connect during the reset. I don;'t know. Another problem I was having, is when me and you set it up your way my pc won't shut down completely and I was having to pull the plug. I know if it has something to do with what was being blacklisted cause when I removed those additions it shut down properly, but then the wireless would'nt restart.

I have learned a great deal during this process but I am begining to think I am out in the cold with this driver until the developers come up with a solution.

Is it possible to buy a different internal wireless adapter maybe by intel for this pc and make that work? I was looking at the prices and they were like maybe 20 to $40 dollars. What do you think?

---

### Post by BigCityCat on 2009-08-13
> **chili555 said:**
> I believe the last part needs to be as follows:```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist ss[COLOR="Red"]b[/COLOR]
blacklist wl 
blacklist b43
```Also, I notice that, in addtion to a blacklist.conf, you have a separate file, blacklist. Please copy and paste it for me. Thanks.

 what is the command exactly?

---

### Post by BigCityCat on 2009-08-13
> **BigCityCat said:**
> what is the command exactly?

never mind



blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

---

### Post by BigCityCat on 2009-08-13
ok I  fixed the blacklist.conf

I can't understand how we had it working the last time but can't get it this time. It's making me crazy.

---

### Post by chili555 on 2009-08-13
So this is the *blacklist* file?```
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```And the long file you quoted above is the *blacklist.conf* file? If that is the case, you can safely remove the blacklist file entirely:```
sudo rm /etc/modprobe.d/blacklist
```You don't need to worry about bcm43xx, since it no longer exists as a module in Jaunty aka 9.04. To be entirely safe, I'd probably add the b43legacy bit to blacklist.conf.

Now run iwconfig. Do you have an interface, wlan0 perhaps? Do you see networks? Can you connect?

Since we had an interface with the wl driver and could see your network, I am skeptical that ndiswrapper will help. However, stranger thaings have happened and I have been wrong before! So let's keep trying.

---

### Post by BigCityCat on 2009-08-13
I called hp and found the intel card and part number that goes with this laptop. The question is is it supported. I pre ordered win 7 for 50 dollars. If this card works I can get it between 20 and 60 dollars. I can cancel my win7 pre order to pay for it. If the crad will work.

intel 802.11 a/b/g/n wlan circuit

part number 480985-001

---

### Post by BigCityCat on 2009-08-13
> **chili555 said:**
> So this is the *blacklist* file?```
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```And the long file you quoted above is the *blacklist.conf* file? If that is the case, you can safely remove the blacklist file entirely:```
sudo rm /etc/modprobe.d/blacklist
```You don't need to worry about bcm43xx, since it no longer exists as a module in Jaunty aka 9.04. To be entirely safe, I'd probably add the b43legacy bit to blacklist.conf.

Now run iwconfig. Do you have an interface, wlan0 perhaps? Do you see networks? Can you connect?

Since we had an interface with the wl driver and could see your network, I am skeptical that ndiswrapper will help. However, stranger thaings have happened and I have been wrong before! So let's keep trying.

Just to let you know. Some of this has changed because I have been screwing around with ndiswrapper. Also some things on that blacklist.conf I put there. It's not exactly how me and you set it up. Right now I can the wireless up by doing

sudo rmmod ssb wl
and 
sudo modprobe wl

---

### Post by BigCityCat on 2009-08-13
I do not have wlan0

I have

> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated


---

### Post by BigCityCat on 2009-08-13
also I am not at home so I do not have acess to my network right now, but there are other networks here at work recognized. I just don't have the password.

---

### Post by chili555 on 2009-08-13
If you can get the card to work with wl, the native driver, then ndiswrapper is not working for you. It does create an eth1 interface and it scans, but when it is taken over by knetworkmanager, it just won't connect. 

When you scan at work:```
sudo iwlist eth1 scan
```Do you see any networks with "key:off?" Can you connect to one of those? If so, that means your whole issue is encryption; that is, the WEP key.

Please do:```
cat /etc/rc.local
```and copy and paste the result here.

---

### Post by BigCityCat on 2009-08-13
> **chili555 said:**
> If you can get the card to work with wl, the native driver, then ndiswrapper is not working for you. It does create an eth1 interface and it scans, but when it is taken over by knetworkmanager, it just won't connect. 

When you scan at work:```
sudo iwlist eth1 scan
```Do you see any networks with "key:off?" Can you connect to one of those? If so, that means your whole issue is encryption; that is, the WEP key.

Please do:```
cat /etc/rc.local
```and copy and paste the result here.

no all the keys are on. I tried connecting to what I thought was unsecure but there is no way to tell if they are just weak signals.

Here is the output you asked for.

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

---

### Post by chili555 on 2009-08-13
> **BigCityCat said:**
> I called hp and found the intel card and part number that goes with this laptop. The question is is it supported. I pre ordered win 7 for 50 dollars. If this card works I can get it between 20 and 60 dollars. I can cancel my win7 pre order to pay for it. If the crad will work.

intel 802.11 a/b/g/n wlan circuit

part number 480985-001I believe this is the Intel 5100 agn chipset. If you search this forum for '5100,' you will see that there are quite a few problems with it. If it were my money, I would not spend it to trade one monster for a new monster.

---

### Post by BigCityCat on 2009-08-13
also I found this page about the intel card would work for me. I think the one at the bottom of that list corresponds with the part that HP gave me. Can you tell me if they are one and the same?

[http://linux-wless.passys.nl/query_chipset.php?chipset=Intel](http://linux-wless.passys.nl/query_chipset.php?chipset=Intel)

what hp told me

intel 802.11 a/b/g/n wlan circuit

---

### Post by BigCityCat on 2009-08-13
> **chili555 said:**
> I believe this is the Intel 5100 agn chipset. If you search this forum for '5100,' you will see that there are quite a few problems with it. If it were my money, I would not spend it to trade one monster for a new monster.

right, that is what I am trying to decide

---

### Post by BigCityCat on 2009-08-13
Do I need to go in and blacklist ndiswrapper now or remove it?

---

### Post by chili555 on 2009-08-13
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing. I hope that's not all there is to it! Please try again and see if there isn't one more line:```
exit 0
```Please *sudo kate /etc/rc.local* and make it look like this:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing. 
rmmod wl ssb
sleep 3
modprobe wl

exit 0
```Proofread, save and close. Restart the machine and run *iwconfig*. Do you have an eth1 interface? Good! Now we are ready to connect when you get home.

---

### Post by chili555 on 2009-08-13
> **BigCityCat said:**
> Do I need to go in and blacklist ndiswrapper now or remove it?Not quite yet. Let's see what happens after you restart. We can clean this all up tonight. You seem to have a very tolerant employer, yes?

---

### Post by BigCityCat on 2009-08-13
Ok I changed it to what you wanted, and yes the exit 0 was there.

---

### Post by chili555 on 2009-08-13
And after a restart, is eth1 there?

---

### Post by BigCityCat on 2009-08-13
I did what you said. It didn't come up, but I changed some things from what me and you did the last time. When I get home I will put it back the way it was and hopefully those last few changes will take effect. I'm going there now. Should be back in about 30 minutes.

---

### Post by BigCityCat on 2009-08-13
It's own like popcone. lol

It's working. It has to be the last thing you did. I put it back the way we did initially and then the only changes were what we just changed. I am going to put a full run down of the process in this thread if it's ok with you. With the disclaimer that this process may not work for everyone and that I am not the expert. You are, but this works for this set up. It should help a lot of people.

---

### Post by BigCityCat on 2009-08-13
oh yeh I still have to restart.

---

### Post by BigCityCat on 2009-08-13
good after the restart. Thanks a lot Chili you are the man. Nobody anywhere else had any solutions. I read tons of material.

---

### Post by chili555 on 2009-08-13
Kopete when you get home?

---

### Post by BigCityCat on 2009-08-13
> **chili555 said:**
> Kopete when you get home?

I'm home now and Kopete is online.

---

### Post by BigCityCat on 2009-08-13
i put the whole process here

[http://ubuntuforums.org/showthread.php?p=7781802&posted=1#post7781802](http://ubuntuforums.org/showthread.php?p=7781802&posted=1#post7781802)

---

