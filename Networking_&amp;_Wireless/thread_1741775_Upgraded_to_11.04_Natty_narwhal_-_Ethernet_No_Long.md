---
title: "Upgraded to 11.04 Natty narwhal - Ethernet No Longer Connects..."
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by werners on 2011-04-28
I can't seem to get a network connection anymore after the upgrade to 11.04...  the configuration for eth0 is correct, and I can see my active connection to the router, but I simply can't get anything to come active no matter what I do (even a manual config won't connect).

Am I missing something????

In the network icon drop-down, I do see "WIRED NETWORK, and "DEVICE NOT MANAGED", dimmed-out.

---

### Post by nfgrachanin3 on 2011-04-29
I had to reinstall Natty and got the Ethernet to work but I do not have wireless available. The network manager does not show any wireless connections available. The additional drivers put in the Broadcom STA driver. Never had a problem ever with the previous versions.

---

### Post by timothyrshell on 2011-04-29
I'm having the same problem.  I have a good notebook with a lot of memory, so I have two partitions and two installations of Ubuntu, because with upgrades there always seems to be a bug or two to work out.  If one version is upgraded and I can't go online with it, I can always use the other one.  I have Ubuntu 10.04 on both and upgraded to 11.11 just a few hours ago, and as the computer was cleaning up it dropped the internet connection.  Then when I rebooted it I can't get it to connect.  I went back to the other 10.04 system on the other partition and booted up and every thing works fine, just like usual.  Soooo.... I think I have a bug to work out.  This computer is AMD Turion64x2.  I've been working with Linux for more than 6 years now, and am able to do some work in terminal.  I'm usually able to copy and paste fixes from forums like this into terminal to fix my bugs.  But, this upgrade is just hours out of the box so to speak, so I'm not finding fixes yet.  

Please advise.  

Tim Shell

---

### Post by timothyrshell on 2011-04-29
correction: I meant upgraded to version 11.04

TIm

---

### Post by senshisteph on 2011-04-29
I'm having a similar issue. I clicked on a wireless network (actually before Natty I wasn't even aware I had a wireless card, so there's something!) and when I disconnected from the wireless network, I found I'd lost my ethernet connection. Rebooting, and even a cold restart didn't help.
Then I tried deleting all the wireless connections in 'edit connections' - and on a restart my ethernet was fine. It seems like it can switch from wired to wireless, but can't switch back, and when I was rebooting after first trying a wireless connection, I was being automatically connected wirelessly, so it couldn't switch to a wired connection (if that makes any kind of sense).
This isn't much of an issue for me, as I only use ethernet (having never realised I had wireless networking before, I hopped on a neighbours connection out of curiosity), but it must be a real PITA for anyone who needs to switch between the 2 regularly.

---

### Post by Neil Stoker on 2011-04-29
I have the same issue with Network Manager showing "Device Not Managed" for both the wired and wireless (I'm fine about not using wireless at the moment, and I had unresolved problems with it in Ubuntu 10.10).

I don't think this is a contributory factor, but my upgrade from 10.10 to 11.04 was proceeding fine - it went and grabbed the various files to download and I had to leave it overnight - when I came back to check it, somehow it had got stuck such that I couldn't access it, it wasn't clear if a screensaver was on or something else was blocking it, but I had to reboot.  Post-reboot I found that various 11.04 things had installed, but I ran the Update Manager just in case and a few things needed to be finished.  I restarted and it all seems fine, barring the Network Manager.

Just to be completely clear, my computer DOES have network access (I am using it now to browse to this page and everything coming from ifconfig in the terminal looks okay, I can ping sites etc etc)  Not sure if this makes any difference but my PC is an (old-ish) Dell D610 laptop.

Any other details I should post that would be useful to help diagnose this?  Any constructive advice gratefully received!

Neil

---

### Post by MauiKaren on 2011-04-29
Upgraded today and absolutely can't connect to wireless. Wired is ok.  But laptop is unusable unless someone can fix this.

---

### Post by zanginator on 2011-04-29
I am also having the same problem, but i have 2 NIC's and the one works but the other does not 

:S kinda of a bummer theres no fix yet.

---

### Post by zanginator on 2011-04-29
I've solved my problem, so i'll try help now,

Open Terminal and type

[PHP]sudo gedit /etc/NetworkManager/NetworkManager.conf[/PHP]instead of Gedit you can use what ever editor you like

Find a section with the title [ifupdown]
and there should straight under it be a line saying 

managed=false

Just change false to true, save, restart and hopefully it should be working


[ifupdown] maybe renamed something else on your system (i don't know) but its the last part of the document.

I hope this helps :D

EDIT:
Manually overriding for Static IP seems to be unavaliable at the moment, but this will get the connections up and running for now.

---

### Post by matt90 on 2011-04-29
WOW...it was seriously that easy!  Thank you so much!  It makes you wonder why they would ever assume you *wouldn't* want a connection managed....

---

### Post by timothyrshell on 2011-05-02
Okay, I tried this fix which was listed, and the window opened to the Network Manager, I changed the value from false to true, saved it and checked to see that it was saved correctly, restarted the computer, but still no connection.  

Any other possible options? 

Timothy

---

### Post by lz1dsb on 2011-05-02
So let's wrap it up. 
You don't see your wired Ethernet interface?
What do you see from the output of "ifconfig"?
Are you able to access the local addresses in your IP subnet?
Are you able to ping your own IP address?

---

### Post by nroussi on 2011-05-02
Thank you. I had the same problem on a Dell 1720. At first install, the wired was working but the wireless was not. The restricted driver for broadcom BCM4311- was activated. Then after some googling I downloaded bcmwl5.inf and installed it using ndiswrapper. Then I deactivated the restricted driver and used your solution. Now both cards work.

---

### Post by afrodeity on 2011-05-04
> **nroussi said:**
> Thank you. I had the same problem on a Dell 1720. At first install, the wired was working but the wireless was not. The restricted driver for broadcom BCM4311- was activated. Then after some googling I downloaded bcmwl5.inf and installed it using ndiswrapper. Then I deactivated the restricted driver and used your solution. Now both cards work.

I installed the recommended kernel from kernel.org via kernelcheck to see if it would cure the slowness I am experiencing with natty. Now the network is unreachable. I can't even ping the router after dropping back to the default natty kernel. It is not a hardware problem because I can reach the network via booting a CD live session, so something must be wrong with the modules. Is there a networking module I have to load? 

I will try changing network manager setting as suggest after a reboot.

---

### Post by lz1dsb on 2011-05-04
There shouldn't be any networking module you need to load. It should be in the kernel as far as I know. That's one of the main differences with Windows. In the Linux kernel you should have all the initial modules and drivers....

---

### Post by afrodeity on 2011-05-06
I have to start network manually with pon-dsl-provider.

I checked sysv and there could be a problem with the runlevel, have now set to recommended default of 2 through 5.

UPDATE: No go, changing the run-levels does nothing. I've filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/777184")

---

### Post by vanlindholm on 2011-05-07
I had a similar problem. It would connect to ethernet if connected directly to the router but not via ethernet to mains (powerline adapters - [http://www.belkin.com/uk/IWCatProductPage.process?Product_Id=496178](http://www.belkin.com/uk/IWCatProductPage.process?Product_Id=496178)) which worked without any problems on 10.10. 

Restarting the networking fixed the problem..
sudo /etc/init.d/networking restart 


Cheers,

---

### Post by vanlindholm on 2011-05-07
btw: I also recommend if applicable to your environment that you set  managed=true in /etc/NetworkManager/NetworkManager.conf and restart nm (/etc/init.d/network-manager restart) as mentioned earlier in this thread. This allows the NetworkManager to handle interfaces that are enabled in /etc/network/interfaces. See [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

---

### Post by afrodeity on 2011-05-07
> **vanlindholm said:**
> btw: I also recommend if applicable to your environment that you set  managed=true in /etc/NetworkManager/NetworkManager.conf and restart nm (/etc/init.d/network-manager restart) as mentioned earlier in this thread. This allows the NetworkManager to handle interfaces that are enabled in /etc/network/interfaces. See [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

Neither fix works for me, I'm afraid. Setting managed=true and restarting the networking fail to solve the problem. I fear this has something to do with the ethernet module. I think I am going to try unloading and reloading the module to test it.

---

### Post by dkc.com on 2011-05-08
Hi friends,

Did a fresh install of Ubuntu 11.04 on my Dell Inspiron 1520. [Broadcom Card/model: BCM4401 PCI.ID: 14e4:170c] Neither ethernet nor wifi. STA driver can not be installed due to an error. Installed b43 driver but to no use.

Also tried the following unsuccessfully: 

> **zanginator said:**
> 
[PHP]sudo gedit /etc/NetworkManager/NetworkManager.conf[/PHP]instead of Gedit you can use what ever editor you like

Find a section with the title [ifupdown]
and there should straight under it be a line saying 

managed=false

Just change false to true, save, restart and hopefully it should be working


[ifupdown] maybe renamed something else on your system (i don't know) but its the last part of the document.

Interestingly, every time when I try to activate STA drivers from 'Additional Drivers' a message appears that 'eth0' has been disconnected. It will connect to 'eth0' afterwards. But the shut-down button in system tray would go red to inform 'restart to complete update'.

Any idea guys? What's happening?

Thanks for reading thus far.

---

### Post by afrodeity on 2011-05-08
I removed network-manager after previously doing a reinstall, and it not working.

ie
```

apt-get install --reinstall network-manager

```

This is what happened when I just removed the damn thing. It removed network-manager and network-manager-gnome. Then when I reinstalled after cleaning the cache, it installed network-manager and network-manager-gnome{a}

```


apt-get remove network-manager

apt-get install network-manager

```

After rebooting my network manager is working flawlessly. Hooray.

---

### Post by lz1dsb on 2011-05-08
You need internet connectivity in order to activate the STA broadcom driver. The system must download it and than install it...


Cheers, 
Boyan

---

### Post by comperocean on 2011-05-12
> **zanginator said:**
> I've solved my problem, so i'll try help now,

Open Terminal and type

[PHP]sudo gedit /etc/NetworkManager/NetworkManager.conf[/PHP]instead of Gedit you can use what ever editor you like

Find a section with the title [ifupdown]
and there should straight under it be a line saying 

managed=false

Just change false to true, save, restart and hopefully it should be working


[ifupdown] maybe renamed something else on your system (i don't know) but its the last part of the document.

I hope this helps :D

EDIT:
Manually overriding for Static IP seems to be unavaliable at the moment, but this will get the connections up and running for now.
thanks so much,
i try it, and resolve this issue.

in /etc/networkmanagement/networkmanagement.conf

modify the ifupdown=false to ifupdown=true

restart the OS. ( I cannot only restart the network service to reload the configure file to network service. )

the net is OK.

---

### Post by timothyrshell on 2011-05-13
This is Timothy again.  I'm still not getting any connection, though I did uninstall network manager, now I need the internet to reinstall, but don't have it.  I can't get any connection in terminal either.  

I also just downloaded the ubuntu 11.04 I386. iso for 32 bit system, and burned a copy on CD.  I put the copy into my friends notebook computer and it can't connect to the internet from his computer either.  Ubuntu 10.04 and 10.10 both work fine, the problem is I've already upgraded my primary partition to 11.04 and really need an internet connection.  I'm having to reload all my programs on the 10.04 secondary partition and switch back and forth all the time.  

This has been my constant experience with Ubuntu, I love it, and will never go back to Windows, but, there are always a few bugs that have to be worked out every time there is an upgrade or new install.  I have spent quite a lot of time online searching and resolving this type of issue.  Usually, there's something on a forum somewhere that will give me "the fix", but I still haven't found it this time.  I'm quite sure that there is a change made at the end of the install process for upgrading to 11.04 that changes some file in the directory, possibly when it is removing unneeded files in the clean up process that eliminates or changes a file needed to connect to the internet, because I had a connection when I did the online up grade up to the very last minute of the install, then the connection dropped and couldn't be restarted.  

Still looking for solutions, 

Timothy

---

### Post by lz1dsb on 2011-05-13
What do you see from the output of "ifconfig'?

---

### Post by afrodeity on 2011-05-13
First test to see if you have connectivity by booting with a live CD. If you can't connect that way, then you have a problem with your hardware. I would then try running:

```

sudo pppoeconf

```

which will search for ethernet connections using the old-school method. Enter your details Try eliminating infrastructure issues before you tackle network-manager.

---

### Post by timothyrshell on 2011-05-13
Here's the output of ifconfig from terminal: 

  	 	 	 	 	 	  

 eth0      Link encap:Ethernet  HWaddr 00:1f:c6:e5:cc:ca   
           inet6 addr: fe80::21f:c6ff:fee5:ccca/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:286 errors:1 dropped:0 overruns:0 frame:1  
           TX packets:16 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:33780 (33.7 KB)  TX bytes:3761 (3.7 KB)  
           Interrupt:43 Base address:0x2000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:16 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:16 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by timothyrshell on 2011-05-13
Here is the output of running sudo pppoeconf in terminal

                                 tshell@ubuntutshell:~$ sudo pppoeconf
 [sudo] password for tshell:  
 Plugin rp-pppoe.so loaded.
 tshell@ubuntutshell:~$ plog
 May 13 21:26:30 ubuntutshell pppd[2155]: Connected to 00:14:78:54:5d:10 via interface eth0
 May 13 21:26:30 ubuntutshell pppd[2155]: Using interface ppp0
 May 13 21:26:30 ubuntutshell pppd[2155]: Connect: ppp0 <--> eth0
 May 13 21:26:30 ubuntutshell pppd[2155]: CHAP authentication failed: bad username or password
 May 13 21:26:30 ubuntutshell pppd[2155]: CHAP authentication failed
 May 13 21:26:30 ubuntutshell pppd[2155]: Connection terminated.
 tshell@ubuntutshell:~$ ifconfig ppp0
 ppp0: error fetching interface information: Device not found
 tshell@ubuntutshell:~$ sudo apt-get install network manager
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 E: Unable to locate package network
 E: Unable to locate package manager
 tshell@ubuntutshell:~$  

I know my network manager was uninstalled.  I'll try to install it again, but I'll have to download and burn a good boot cd first.  I'll report back again soon.  I'll also try these options on the other notebook.

Thanks for these pointers
 

Timothy

---

### Post by timothyrshell on 2011-05-13
I also tried running Ubuntu from the CD in the Gateway 32bit notebook,  Ubuntu 11.04 runs like normal, but no internet connection at all.  Same  commands in terminal result in similar output as listed above for my  Asus 64bit notebook.  Again, Ubuntu 10.04 is running fine in the Asus on  a separate partition, and connects like normal, no troubles at all.  

What is the deal about the "CHAP authentication failed"?  I'm entering  the correct information.  My connection is listed and set up under "Edit  Connections" as a DSL connection with user name, service, and  password.  It normally connects automatically and I never have to worry  about anything with it.  

When I run "ifconfig" in terminal with Ubuntu 10.04 and live connection to the internet it yields the following: 

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:e5:cc:ca  
          inet6 addr: fe80::21f:c6ff:fee5:ccca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8087 errors:1 dropped:0 overruns:0 frame:1
          TX packets:1615 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2086742 (2.0 MB)  TX bytes:366527 (366.5 KB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45352 (45.3 KB)  TX bytes:45352 (45.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.16.10.178  P-t-P:172.16.10.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9188 (9.1 KB)  TX bytes:1629 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:98:35:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
Any advice would be greatly appreciated, 

Thanks, 

Timothy

---

### Post by afrodeity on 2011-05-14
I'm assuming that you have to run ppoeconf because network-manager is not installed or not working. It should bring up an ncurses interface. First screen will search for devices and give you a list. Then it will ask you if all you interfaces have been found. Press yes. When it asks you for username and password, enter details. That should bring up your ethernet, otherwise try 
```

pon dsl-provider

```

If they not found, then you may have hardware issues. Check to see if your hardware is connecting using a live CD.

---

### Post by snyderxc on 2011-05-17
> **zanginator said:**
> I've solved my problem, so i'll try help now,

Open Terminal and type

[PHP]sudo gedit /etc/NetworkManager/NetworkManager.conf[/PHP]instead of Gedit you can use what ever editor you like

Find a section with the title [ifupdown]
and there should straight under it be a line saying 

managed=false

Just change false to true, save, restart and hopefully it should be working


[ifupdown] maybe renamed something else on your system (i don't know) but its the last part of the document.

I hope this helps :D

EDIT:
Manually overriding for Static IP seems to be unavaliable at the moment, but this will get the connections up and running for now.

Thanks so much! This worked for me too.

---

### Post by rayne127 on 2011-05-19
I am also having problems connecting to Wifi after upgrading to 11.04. I tried setting managed=true and restarted with no luck. I am able to connect to my router via ethernet. My wifi is showing up as an option but it's not able to scan for any networks (and I know there's a lot here as I live in an apartment). Even adding my wifi manually and trying to connect that way is a no go. It keeps acting like it's trying to connect then asks me again and again for the passcode. 

Here's is my ifconfig output:
> eth0      Link encap:Ethernet  HWaddr 00:16:d4:14:1d:cf  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe14:1dcf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1356772 (1.3 MB)  TX bytes:235112 (235.1 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:42:e7:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
I'm not sure if it's a driver issue or an OS issue? I never had any problems with 10.04 or 10.10 connecting through wifi.

I'm on an Acer Aspire 5100 laptop.

---

### Post by Simon Bateman on 2011-05-19
> **snyderxc said:**
> Thanks so much! This worked for me too.

Sorry -- I tried this fix, still NO Wired connection.   Wireless is OK though.

Using: Lenovo 3000 G530 laptop, originally Windows 7 then dual boot with openSUSE 11.4 now just Natty!

Life is about choices, today I choose to be Grumpy!

---

### Post by boy007 on 2011-05-28
> **rayne127 said:**
> I am also having problems connecting to Wifi 

I'm on an Acer Aspire 5100 laptop.

Hi,

 upgrade kernel to 2.6.39.0

It's just bug at kernel code,..., can be related WIFI on/OFF switch
or somthing other,... I got by upgrade my 5110 work. To update
I needed to have AUTO ETHERNET ON and connect ethernet cable to
activate wireless!!! and then whit instructions,...

Instructions are here:

[http://www.wmlcloud.com/linux/how-to-update-ubuntu-11-04-default-kernel-to-resolve-unity-issues/](http://www.wmlcloud.com/linux/how-to-update-ubuntu-11-04-default-kernel-to-resolve-unity-issues/)

---

### Post by WML Cloud on 2011-05-28
The new update is meant to resolve unity issues.

---

### Post by boy007 on 2011-05-28
> **boy007 said:**
> Hi,

 upgrade kernel to 2.6.39.0

It's just bug at kernel code,..., can be related WIFI on/OFF switch
or somthing other,... I got by upgrade my 5110 work. To update
I needed to have AUTO ETHERNET ON and connect ethernet cable to
activate wireless!!! and then whit instructions,...

Instructions are here:

[http://www.wmlcloud.com/linux/how-to-update-ubuntu-11-04-default-kernel-to-resolve-unity-issues/](http://www.wmlcloud.com/linux/how-to-update-ubuntu-11-04-default-kernel-to-resolve-unity-issues/)

Ok, and it dose not work, again,...
strange,... I get list of rouiters if I connet ethernet cabel,...
it activates AUTOETHERNET and then AUTOWIRELESS,....
but after reboot it dose not show anything ,, and againg needs ethernet
cabel connection for some seconds,..

---

### Post by daoki82 on 2011-05-28
Since this seems to be happening to everyone that upgrades to 11.04, is it safe to say falling back to the 10.04 version will fix this problem? I've read in various threads this enables the wireless, because I've now honestly seen like 12 different ways of trying to fix 11.04, but each seems individual to its own case. 

As great as it is to be up to date with things, in the case of ubuntu I really feel like I could have saved myself the headache by *not* upgrading... 10.04 here I come. (again)

---

### Post by Smack937 on 2011-06-13
Thanks for the assist. I will try this after work. I had stumbled across some more time intensive trial and error approaches, but hopefully this will work!

---

### Post by afrodeity on 2011-06-14
Deleting configuration file for Network-Manager works [http://ubuntuforums.org/showpost.php...09&postcount=2](http://ubuntuforums.org/showpost.php...09&postcount=2)

---

