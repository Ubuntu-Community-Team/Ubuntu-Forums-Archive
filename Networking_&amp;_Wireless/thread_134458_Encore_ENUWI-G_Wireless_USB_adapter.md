---
title: "Encore ENUWI-G Wireless USB adapter"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by Floppyjoe on 2006-02-21
I just bought this Encore ENUWI-G USB 54 Mbps Dongle
[IMG]http://images10.newegg.com/NeweggImage/ProductImageCompressAll125/33-180-017-06.jpg[/IMG]
which works fine in Windows. I can't seem to get it to work in Ubuntu. I've tried Ndiswrapper on it which creates a driver for it but when i do a modprobe on it the light doesn't come on. I tried to scan for routers but that did not work either. Has anyone been able to get one of these to work? Anyone have any suggestions?

UPDATE:I did get it to work if you just follow the thread. See Post#10

---

### Post by ebcoelho on 2006-07-03
Did u found the solution???? Thanks!

[]'s

Eduardo

---

### Post by marcosaccioly on 2006-11-27
Anyone has the answer for that *in the world*?? :)  Cuz I've browsed all possible threads around the web and *no one* knows how to do it... 

If anyone finds anything, plz help... 

Cheers

---

### Post by Floppyjoe on 2006-12-19
I have as yet not figured out how to use this device in Ubuntu. Mind you I have not tried very hard either. It was a cheap Wi-fi gadget though and probably not very popular also.

---

### Post by marcosaccioly on 2006-12-20
Yeah... Well, I haven't given it a hard try either and I'm no Linux expert for trying. It actually was the cheapest device I could find which supported 108Mb so I gave it a shot. Not an accurate shot, though ;)

Thanks for the reply and please keep me updated if u make any advances. I'll keep in touch if I make that thing work. 

Cheers,

Vini

---

### Post by rickrose on 2006-12-20
](*,)  Has anyone tried looking in /var/log/messages and/or /var/log/syslog and posting a screenshot so someone could possibly help you.  I need more to go on than you tried this and that. I believe I tried this same adapter a while ago with ubuntu dapper drake and there were some funky errors during ndiswrapper configure.  Not sure though.  If you could post some logging information, lspci or lsmod output, or something/anything then I might be inclined to help. :) Otherwise [-(

---

### Post by Floppyjoe on 2006-12-21
I tried to get this Enuwi-g Usb adapter to work again in Ubuntu 6.06 by using ndiswrapper to install the driver.
This time the light comes on when i modprobe ndiswrapper.  I can do Sudo iwlist wlan0 scan and see my router with the device. I can't connect with it though using sudo dhclient wlan0. There must be some setting I'm not properly setting on my router or Ubuntu but I think the device works though. The following is a dump from /var/log/messages.

> Dec 20 22:05:17 localhost kernel: [17181370.196000] usb 5-8: new high speed USB device using ehci_hcd and address 3
Dec 20 22:15:52 localhost -- MARK --
Dec 20 22:20:51 localhost kernel: [17182304.396000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
Dec 20 22:20:51 localhost kernel: [17182304.412000] ndiswrapper: driver sis163u (OEM,11/29/2004,5.1.1039.1020) loaded
Dec 20 22:20:53 localhost kernel: [17182305.620000] wlan0: vendor: 'Wireless Driver'
Dec 20 22:20:53 localhost kernel: [17182305.620000] wlan0: ndiswrapper ethernet device 00:40:f4:da:b7:ae using driver sis163u, 0457:0163.F.conf
Dec 20 22:20:53 localhost kernel: [17182305.620000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Dec 20 22:20:53 localhost kernel: [17182305.624000] usbcore: registered new driver ndiswrapper

I copied the files SiS163u.INF and SiS163u.sys from the Windows Xp section of the drivers folder on the driver disk that came with the Enuwi-G Usb adapter to Ubuntu in my home folder under the folder Enuwi-g. Then I Changed to that directory in the terminal.
> $ cd \Enuwi-g
Then I installed the driver using the ndiswrapper utility(You need to make sure Ndiswrapper-utils is installed first.
> $ sudo ndiswrapper -i SiS163u.INF
Then I listed the driver.
> $ ndiswrapper -l
I got this message.
> Installed ndis drivers:
sis163u         driver present, hardware present
I then loaded the module ndiswrapper.
> $ sudo modprobe ndiswrapper
The light came on on the usb adapter.
I did iwconfig next.
> $ iwconfig
With this result.
> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          RTS thr:2312 B   Fragment thr:2312 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Then i scanned for my router.
> $ iwlist wlan0 scan

And got this result.
> wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:30:CB:DB
                    ESSID:"WarGames"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:0/100  Signal level:-30 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s; 6 Mb/s; 5.5 Mb/s
                              2 Mb/s; 1 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000

At this point I turned the encryption on my router off and tried to connect to the router.
> g$ sudo dhclient wlan0
With this result.
> Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:40:f4:da:b7:ae
Sending on   LPF/wlan0/00:40:f4:da:b7:ae
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Does anyone have any Ideas how to get it to connect to the router? What settings am I missing?

---

### Post by Floppyjoe on 2006-12-21
Today i added a few commands and did get this Enuwi-G adapter to work and connect to my router. These commands from the terminal were.
> $ sudo iwconfig wlan0 mode managed
$ sudo iwconfig wlan0 channel 7
$ sudo iwconfig wlan0 essid WarGames


there is probably some way to automate some of this so it happens automatically at bootup howerver I am not quite sure how yet. I hope this helps someone out there.

---

### Post by xlr8n4d on 2006-12-24
I am also VERY new to Ubunto, just downloaded Edgy and have it installed onto a machine last night.  I have this same wireless adapter, and have come up with the fact it is connecting on what I know to be Eth1.  I have found the windows driver on the internet for downloading also.  I have done the sudo ifconfig eth1 up and it asked for my password, having entered that and then checking with ifconfig it shows details about the Eth1, after sudo ifconfig eth1 down that information disappears when doing an ifconfig

Sorry for sounding so ignorant, I have looked on this forum but I just don't seem to be able to put together the different threads and their instructions ](*,) to solve my current dilema.

Could someone please help me by writing line for line, exactly what I need to get this harware working?

I think a description of sudo would be the first to help, I understand some things require admin privledges, and some things don't.  

A busy forum will likely help a lot, thanks in advance for all your consideration as I learn and join your community.

---

### Post by Floppyjoe on 2006-12-25
Well this Enuwi-G Wireless usb adapter works with Ndiswrapper for me on an Ubuntu Edgy 6.10 install.  First off you'll need to make sure Ndiswrapper-utils 1.8 is installed on you computer. I used a hardwired network cable to install this onto the computer using the synaptic package manager in System/Administration/Synaptic Package Manager. 

If you don't have any connection to the internet you can install Ndiswrapper-utils 1.8 from the Ubuntu installation Disk. Goto System/Administration/Synaptic Package Manager. Then Click on Edit/Add CD-Rom. Next click on Reload. 

Do a search for Ndiswrapper and download Ndiswrapper-utils 1.8 to your system. Next I copied my windows xp drivers that came with the adapter from the windows xp section of the driver folder on the CD. These drivers were called SiS163u.INF and SiS163u.sys. With other versions of this adapter there may be a .bin file that also needs to be present in the folder you are installing the driver from. I put these into my home folder into a folder called Enuwi-g. 

Next I opened a terminal screen by clicking on Applications/Accessories/Terminal.

I then changed to the directory where the driver files were located.
```
cd \Enuwi-g 
```

Next I installed the driver using the Ndiswrapper utility by entering the following commands into the terminal.
```
sudo ndiswrapper -i SiS163u.INF
```

The sudo part means Super User Do. Ubuntu doesn't like anyone but root level accounts installing things and doing other important tasks on the computer. This is a safety measure. You may be prompted to enter your password after this command. Remember that the letters in the driver name are case sensitive.

I then listed the Ndiswrapper driver using the following commands in the terminal.
```
ndiswrapper -l
```

I got the following results:
> Installed ndis drivers:
sis163u driver present, hardware present 

Note if you got a listing of an invalid driver you probably typed the name of the the driver wrong. Once again remember it is case sensitive. You can delete the invalid driver by entering the following commands:
```
sudo ndiswrapper -e drivername
```
Where the drivername is the name of the invalid driver listed. Then list the ndiswrapper drivers again with the ndiswrapper -l command to see if it deleted properly.

I then loaded the ndiswrapper driver using:
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```

The light on the usb adapter should turn on now.
I did an iwconfig next by typing iwconfig into the terminal with the following result.
> lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

wlan0 IEEE 802.11FH ESSIDff/any
Mode:Managed Frequency:2.432 GHz Access Point: Not-Associated
Bit Rate:11 Mb/s Tx-Power:18 dBm Sensitivity=0/3
RTS thr:2312 B Fragment thr:2312 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I now know that my interface is wlan0 Yours may have a different name. We need to make sure the ndiswrapper driver is loaded at boot-up. Also now would be a good time to activate the interface using System/Administration/Networking and selecting the wireless interface and slecting properties and entering the Essid of your router and selecting DHCP. Check on the activate check box. Make sure you deactivate your wired lan card too. A thing will pop up saying activating device or something like that. Just let that finish. It may take a while.

Now to make sure your computer loads the ndiswrapper driver automatically at boot-up you would enter this:
```
sudo ndiswrapper -m
```
```
sudo gedit /etc/modules
```
And edit/add the word ndiswrapper to the end of the file. Save the file and exit.

Next you want to add some code into the /etc/network/interfaces file to make sure your computer knows what settings the router is using. Look for entries called wlan0 or the name your computer calls your interface. It may be different.
Enter :
```
sudo gedit /etc/network/interfaces
```
If you see this:
> auto wlan0
iface wlan0 inet dhcp

Then enter the following code below it:
```
wireless-essid   YourNetworkName
wireless-channel 11
wireless-mode    managed
```
Where YourNetworkName is your routers Essid and you enter the channel that your router is using instead of 11.

You should see something like this:
> auto wlan0
iface wlan0 inet dhcp
wireless-essid   YourNetworkName
wireless-channel 11
wireless-mode    managed

Then save this file and close it.

Now I'm assuming your router is open and not using encryption here and that Mac address screening is off too.Now i would restart your computer and when it boots up you should have internet access. You may need to reboot twice.

I hope this works for you. It did for me. Tell me how it goes.

---

### Post by xlr8n4d on 2006-12-25
Thanks, I will get on that as soon as I can tomorrow when family calms down some

---

### Post by xlr8n4d on 2006-12-25
> couldn't copy SiS163u.INF at /usr/sbin/ndiswrapper-1.8 line 144.


That is what it gave me after the first command of 
> xlr8n4d@Linux:~/Desktop/Enuwi$ sudo ndiswrapper -i SiS163u.INF
and asking for my password.

I do not have connection to a hard wire to download the Ndiswrapper, I found [HERE]("http://rpmseek.com/rpm-dl/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.html?hl=com&cx=824:N:0:3249137:0:0:0") that I have got in the same folder as the SiS163u.INF file, though currently I have them on my desktop, do you think that could be the problem and where else would you suggest?

I do not know or understand much about basic Linux file systems, but I am learning.  How can I get to that line 144 and look at it to see what it says?

---

### Post by Floppyjoe on 2006-12-25
Hmmm.... Maybe try deleting the invalid driver again if it lists as invalid now. Then try re-installing the driver again using:
```
sudo ndiswrapper -i drivername.inf
```

There should be only one version of an .inf file in the folder your are installing it from.

The same thing happened to me before with the line 144 error but I kept banging away at it until i figured it out. I think in that instance I just reverted to the commands above, but when I entered ndiswrapper -l it showed the driver and the hardware present.  There may be a problem with your USB port or something because it is not seeing the device. I should add that my Encore Enuwi-G USB Adapter is a 54Mbps model.
[IMG]http://images10.newegg.com/NeweggImage/ProductImageCompressAll125/33-180-017-06.jpg[/IMG] 
If you have the 108 Mbps model The Encore Enuwi-SG USB Adapter it may use a different driver.
[IMG]http://images10.newegg.com/NeweggImage/ProductImageCompressAll125/33-180-020-02.jpg[/IMG]

---

### Post by xlr8n4d on 2006-12-26
I am chatting on MSN with someone trying to fix this right now, if you would please like to join, my MSN ID is [email]xlr8n4d@hotmail.com[/email] I tried to write you there and it said you were not logged in.

so far we have removed the one driver with sudo ndiswrapper -e filename, you say that command will work if I only have one INF file in the folder the SiS163u.INF file is in?  

I have not tried it yet, but it IS the only INF file there, few .dll files and a .sys file

---

### Post by xlr8n4d on 2006-12-26
I bought my adapter maybe 2 years ago, it is silver, but not like the picture you included.  It is more square.  When I bought mine it came in a white box, with an unlabeled CD full of drivers, but does have the Encore name on the top of the hardware, though does NOT have the logo.

---

### Post by xlr8n4d on 2006-12-26
That was it, used the drivers that were supplied with my antique dongle and not the ones from the website that were not intended to use with this adapter and we had results that gave me connectivity.

The power and activity lights do light up during the splash screen of the boot up, but do not function with the desktop open.


Thanks to the community here on the ubuntu forums for your patient support

---

### Post by bone2006 on 2007-01-02
I have the newer one and it seems encore even went out of business.  Anyway the CD that came with it only has a setup file to run, so the individual inf and sys file aren't on the CD.  I tried searching online, but came up with no luck.

Mine is the 108Mbps USB G adapter model.  If I'm not mistaken it's model ENUWI-G

I went to my computer in windows, click on the device and I can see it has this file under the drivers folder in windows ar5523.sys but can't find any inf file

Any suggestions or help?

---

### Post by bone2006 on 2007-01-02
I found this web site [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

It listed by exact model and told me to get these files from windows

Driver: Need to get the drivers from window$ instalation (athfmwdl.inf/.sys, net5523.inf,ar5523.bin/.sys)

---

### Post by bone2006 on 2007-01-04
I finally got my wifi up and running and thought I'd post incase anybody else has this card.

Mine is actually the new ENUWI-SG, which the install CD only has a setup.exe, so you can't grab the drivers from the CD and the company seems to be out of business, so downloading the drivers from their website wasn't possible.
While in windows XP, I had to grab these files



athfmwdl.inf
athfmwdl.sys
net5523.inf
ar5523.bin
,ar5523.sys

A lot of instructions I found said to use the load_fw_ar5523 command, but I believe that was only for Ndiswrapper 1.6, which the command was removed it seems for 1.8.

After coping the files over I had to actually install two drivers.  

ndiswrapper -i athfmwdl.inf
modprobe ndiswrapper
modprobe -r ndiswrapper
ndiswrapper -i net5523.inf
modprobe ndiswrapper

After this I had to reboot and I did a scan.  After doing a scan I still couldn't connect to my router.  I had to edit the interface file and set a static IP and needless to say I'm online now. 

Hopefully this helps somebody else who might have the same one I have

---

### Post by Ark_74 on 2007-02-07
Hi to every one here, as many of you i have an Encore ENUWI-G Wireless device (54 Mbps) and i did it run twice and i thought "ohh i'm a genius" because of the Ndiswrapper thing and all that, after  i turn off my computer when on it just stop working, i made an "sudo modprobe ndiswrapper" and it turns the link light on (again) and ask me for the wlan key. One more time i turn off and when i turn on, the same thing but this time the "sudo modprobe ndiswrapper" didn't help, the link light was on but no connection. I have the Network-manager but don't recognize my wlan so i cant connect, but the network-monitor says i have a 100% signal level.

and i tried to configure the way you do and :(  it didn't work either.
Here what i got with some codes:

```
**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3  
          RTS thr:2312 B   Fragment thr:2312 B   
          Power Management:off
          Link Quality:100/100  Signal level:-79 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8006   Missed beacon:0

sit0      no wireless extensions.
```

```
**$ sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:e7:00:61:cb
Sending on   LPF/wlan0/00:18:e7:00:61:cb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


```
**$ sudo nano /etc/modules**
  GNU nano 1.3.12           Fichero: /etc/modules                               

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

ndiswrapper


```


```
**$ sudo gedit /etc/network/interfaces**
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


auto wlan0
iface wlan0 inet dhcp
wireless-essid INFINITUM9412
wireless-channel 6
wireless-key s:[here's my key]
wireless-mode managed
```



And that's how i tried to configure but nothing happens so far.
---

Here's the way i made it work the first time.
First i made a clean first installation Ubuntu Edgy from my Live CD
Then i carried my whole PC near the ADSL hub so i could have a wire connection and download all the upgrades it took me like an hour (depending the download speed), download the Ndiswrapper from [here]("https://launchpad.net/distros/ubuntu/edgy/i386/ndiswrapper-utils-1.8/1.18-1ubuntu2")
(I add an attachment if you want)  then install it.

Then i copied the drivers to my Pc, i heard that the ones that are for win2000 works better than those for winxp, so i copied those (win2000) to the folder "dvr2000"

```
$ cd \dvr2000
```

$ sudo ndiswrapper -i driver.inf (that in my case is SiS163u.INF)
so ti goes like this
```
$ sudo ndiswrapper -i SiS163u.INF
Password:
```
then its says that the driver (sis163u) is installed or close if not then the headers or the kernel or something is not upgraded (i presume :p )
next
```
$ ndiswrapper -l
```

if you get this then you're in the way
```

driver installed, hardware present
```

```
$ sudo ndiswrapper -m
```
and finally

```
$ modprobe ndiswrapper
```

to tell you the truth here i got and error
FATAL ERROR  "#$#$&&$%()  (sorry i didn't copy the error)
so i did this

```
$ sudo modprobe ndiswrapper
```     (hehehe sounds crazy i know)

and the link light turns on

and i installed the network-manager and network-manager-gnome with synaptic (internet connection required) it's easy
and 
```
$ sudo reboot
```

here's something funny after this procedure my ubuntu was kind of slow, when it load is like if there were some kind of error, but then it loaded complete and i could use my wireless connection.
It worked like a week before it falls and now i'm with no internet  :cry: 

I'm new with Ubuntu, i'm new on linux, and i hope i explain myself 'coz my english its not quite perfect.

---

### Post by Ark_74 on 2007-02-07
Can you help me to config this damn thing?](*,) 
:guitar: 
I hope you have some kind of magic trick that could work in my case.
Thank you all
I use an 1.1 USB Port (coz i don't have 2.0 :cry:)

---

### Post by Floppyjoe on 2007-02-08
What is the name of your USB adapter and what version of Ubuntu are you using? This works for my Encore Enuwi-G Wireless USB adapter in Ubuntu Edgy 6.10. My adapter is a 54Mbps unit. On the package it says the device works with USB Rev 2.0, 1.1, and 1.0 so I think it should work with 1.1.

---

### Post by Ark_74 on 2007-02-08
I have Ubuntu Edgy 6.10, and a device 54 Mbps Encore ENUWI-G just like the one on the picture on the first pages (the grey one).
The Kernel i'm not sure but it's upgraded and as i said it worked but then it stop working, and tried to configure this way and nothing.
Could you tell me how did you configure so i can do it too, it seems that we both have the same hardware.
Thnx!:-k

---

### Post by Floppyjoe on 2007-02-08
Ok, did the unit work until after you did an upgrade?

---

### Post by Ark_74 on 2007-02-08
Yes, i upgrade my ubuntu and after all the installation i install the ndiswrapper the one i put on my last post, and follow some instructions, and it work like a week, then it just stop working. And know i configure it i can read the signal from my router but there is no connection so i cant get into internet :(

---

### Post by Floppyjoe on 2007-02-08
There are a few things that can make your wifi stop working. Sometimes it is an update that will break it. Sometimes it is broken because you installed a network connection program that changes your configuration files. Sometimes playing around with System/Administration/Networking can overwrite your configuration files. Sometimes it is because of messing around with router settings in the router. Sometimes it is faulty hardware. I'm sure there are more reasons why it could stop working. If your hardware is not faulty then you probably should be able to get it to work again. If all else fails maybe re-installation of Ubuntu is required. 

So can you tell me how you connect to the internet. Do you use a program to connect or do you just have it configured to connect automatically at boot-up. Are you using a laptop or are you using a desktop. Are you using encryption and if so is it Wep or Wpa?

What is the output of:
```
iwconfig
```
and
the contents of the file /etc/network/interfaces:
```
sudo gedit /etc/network/interfaces
```

Edit: Ark's problem was a network-manager configuration issue which was solved by disabling all the network interfaces in System/Administration/Networking and commenting out all the interfaces except for lo in the file /etc/network/interfaces and then rebooting the system.

---

### Post by Ark_74 on 2007-02-11
Hey Floppyjoe, thanks.
For all the support you gave me and, great to talk to you.  I'll try to make (based on my short experience) a tutorial, for trying not to die in the first configuration of the Ndiswrapper and this device ENUWI-G.

Thanks to all guys, and we'll see us around.
:lolflag:

---

### Post by Eckman on 2007-02-12
Feb 12 21:45:48 Dark-Recesses kernel: [ 3297.732706] usb 4-6: new high speed USB device using ehci_hcd and address 8
Feb 12 21:45:48 Dark-Recesses kernel: [ 3297.841032] usb 4-6: configuration #1 chosen from 1 choice
Feb 12 21:45:48 Dark-Recesses kernel: [ 3297.935489] usb 4-6: reset high speed USB device using ehci_hcd and address 8
Feb 12 21:45:48 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver sis163u 
Feb 12 21:45:48 Dark-Recesses kernel: [ 3298.046001] ndiswrapper: probe of 4-6:1.0 failed with error -22

 I followed all the instructions and still kept coming up with this. It kept ignoring the dll files. Any ideas on whats going on?

Feb 12 22:58:00 Dark-Recesses kernel: [ 6841.699147] usb 4-6: new high speed USB device using ehci_hcd and address 9
Feb 12 22:58:00 Dark-Recesses kernel: [ 6841.807445] usb 4-6: configuration #1 chosen from 1 choice
Feb 12 22:58:00 Dark-Recesses kernel: [ 6841.901923] usb 4-6: reset high speed USB device using ehci_hcd and address 9
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(324): file siswinst.dll is ignored 
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(324): file siswpars.dll is ignored 
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(324): file siswbase.dll is ignored 
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver sis163u 
Feb 12 22:58:00 Dark-Recesses kernel: [ 6842.012667] ndiswrapper: probe of 4-6:1.0 failed with error -22

This is with the dll files in the directory. Im still pretty new to this, the forums have provided an invaluable tool for me ot learn all this. thanks for all the help.

---

### Post by Floppyjoe on 2007-02-15
> **Eckman said:**
> Feb 12 21:45:48 Dark-Recesses kernel: [ 3297.732706] usb 4-6: new high speed USB device using ehci_hcd and address 8
Feb 12 21:45:48 Dark-Recesses kernel: [ 3297.841032] usb 4-6: configuration #1 chosen from 1 choice
Feb 12 21:45:48 Dark-Recesses kernel: [ 3297.935489] usb 4-6: reset high speed USB device using ehci_hcd and address 8
Feb 12 21:45:48 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver sis163u 
Feb 12 21:45:48 Dark-Recesses kernel: [ 3298.046001] ndiswrapper: probe of 4-6:1.0 failed with error -22

 I followed all the instructions and still kept coming up with this. It kept ignoring the dll files. Any ideas on whats going on?

Feb 12 22:58:00 Dark-Recesses kernel: [ 6841.699147] usb 4-6: new high speed USB device using ehci_hcd and address 9
Feb 12 22:58:00 Dark-Recesses kernel: [ 6841.807445] usb 4-6: configuration #1 chosen from 1 choice
Feb 12 22:58:00 Dark-Recesses kernel: [ 6841.901923] usb 4-6: reset high speed USB device using ehci_hcd and address 9
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(324): file siswinst.dll is ignored 
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(324): file siswpars.dll is ignored 
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(324): file siswbase.dll is ignored 
Feb 12 22:58:00 Dark-Recesses loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver sis163u 
Feb 12 22:58:00 Dark-Recesses kernel: [ 6842.012667] ndiswrapper: probe of 4-6:1.0 failed with error -22

This is with the dll files in the directory. Im still pretty new to this, the forums have provided an invaluable tool for me ot learn all this. thanks for all the help.

Ndiswrapper from the repositories does not work with custom kernels. You would need to install a new version of ndiswrapper from sourceforge.net. I have a walkthrough here:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)

You will need an internet connection to load the essential programs for compiling programs.

---

### Post by Eckman on 2007-02-18
Yeah I tried that, still the same error. I tried it on a friends XP laptop, works great. Got another ideas, cause im lost.

---

### Post by Floppyjoe on 2007-02-19
Where did you get those dll files from and what are they for? To use ndiswrapper you only need the .inf .sys and .bin files.

---

### Post by Eckman on 2007-02-19
Off the cd that came with it. I didnt see any bin files however.

---

