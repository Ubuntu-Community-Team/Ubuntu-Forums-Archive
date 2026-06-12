---
title: "Ubuntu 10.10 can't find/connect to wireless network"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by 102jon on 2011-02-18
I recently installed the Maverick Meerkat distribution and am having problems getting it to find and connect to my wireless network. Additional info: I am using a Toshiba laptop and used the wubi installer to get Ubuntu.

---

### Post by Sean Moran on 2011-02-18
> **102jon said:**
> I recently installed the Maverick Meerkat distribution and am having problems getting it to find and connect to my wireless network. Additional info: I am using a Toshiba laptop and used the wubi installer to get Ubuntu.
A couple of terminal commands that might point in the right direction are: 

**ifconfig** 

and 

**rfkill list all**

The **ifconfig** command will list the inferfaces, and hopefully you should see **wlan0** somewhere in the list.  That's your wireless adaptor.  **rfkill list all** will hopefully produce a list like this:
```

user@trial-system:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``` 
which means that your physical ***hard*** wireless button is switched on, and the operating system agrees - the ***soft*** part.  If you get a '***yes***' rather than a '***no***' for either ***hard*** or ***soft***, that's where to look for the problem.

Is it possible to check these two listings?

---

### Post by 102jon on 2011-02-18
rfkill list all did not work, but i tried rfkill listall. here is the output for the two commands:


```
jonathan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:53:92:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

jonathan@ubuntu:~$ rfkill list all
jonathan@ubuntu:~$ rfkill listall
Usage:	rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
jonathan@ubuntu:~$ 
```

---

### Post by Sean Moran on 2011-02-18
I get the feeling that **rfkill list all** did work, and showed nothing because it doesn't see any wireless adaptors.  The output from **rfkill listall** looks like help information for unrecognised options, but that's not the main issue.

I'm pushing the limits of my understanding of wireless, particularly with Meerkat, as I did just reboot into my Meerkat installation and checked that wireless is working fine, although it didn't work when I first installed it, and I hardly use Meerkat except when I need to copy a 10.10 or 11.04 .iso to USB with the newer unetbootin 471 which works for distros that the Karmic version of unetbootin seems to have trouble with.  I forget what I did all those weeks ago to get Meerkat to work with my wifi.  Anyway ...

 The next terminal commands I know that might start your wifi adaptor, and list available access points are:
```

sudo ifconfig wlan0 up
sudo iwlist wlan0 scanning

```

On the GUI side, you might also look through System -> Preferences -> Network Connections, and check the Wireless tab to see what's there.

One more suggestion that comes to mind, considering you do appear to have some sort of connection to be here at all, (hoping it's linux ubuntu or debian), is:
```

sudo apt-get install wireless-tools

```
I'm fairly sure that Meerkat comes with **wireless-tools** on the Live-CD, but just in case.  

Sorry that I'm not an expert on wireless nor Meerkat.  I saw that you hadn't had a reply for almost an hour, so wanted to help out.  Maybe Graham Mechanical can improve on my rather amateurish advice.

---

### Post by 102jon on 2011-02-18
No I really appreciate all the help you're giving me, thanks so much. Here is the output of the commands you listed:


jonathan@ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for jonathan: 
SIOCSIFFLAGS: Operation not permitted
jonathan@ubuntu:~$ sudo iwlist wlan0 scanning
wlan0     No scan results

```
jonathan@ubuntu:~$ sudo apt-get install wireless-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wireless-tools is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jonathan@ubuntu:~$ 

```

---

### Post by gemma.laming on 2011-02-18
Hi Sean and Jon,
I am having some problems with my wireless connection.  I am visiting in Bangkok and am having problems with their wireless internet.  I hope that I am on the right thread, I have tried all the things you have suggested for Jon, but with no success.

I have a partial internet connection - by which I mean that I can get some websites and not others.  For example: I can open the website of Mozilla, but I cannot open the website addons.mozilla.org (or somesuch - it is the extra element before the dot that makes it inaccessible).  Another example is that I can access my yahoo email account (old) but not my new one (live.nl).  

Can you help?!  Gemma

---

### Post by amsterdamharu on 2011-02-18
To the op, it looks like no drivers might have been installed for wlan.
rfkill does not list anything as it does on my desktop without wireless. 
ifconfig does not list wlan adaptors (ifconfig -a might list it).

Some drivers do not support rfkill though so the driver might be there but just don't list in rfkill.

Could you check and post the output of the following commands?

```
ifconfig -a
```


Then try the following (don't post all of this please it's a lot of info)
```
lsusb
sudo lspci
```

I don't know if your wireless is usb or pci, if it's usb it should show somewhere in lsusb if it is pci it should show with lspci. If it shows with lspci could you try this command?
```
sudo lspci -vv
```

That should give even more info. If your scroll to where the pci wireless is listed (if it is pci) then it should show something like "Kernel driver" and or "Kernel modules", could you post that?

Maybe you just need to install the driver, could you press alt + F2, type jockey-gtk and click run. It should scan for a while and then end up with a list of available drivers you can install or with a message saying no drivers are available.

---

### Post by amsterdamharu on 2011-02-19
@Gemma:

Can you ping addons.mozilla.org? You can do so by executing the following command:

```
ping addons.mozilla.org
```

If you can't then it's probably no fault of yours but some dns problem. If you can then it's still probaly no problem with your wireless card but a browser setting.

---

### Post by Sean Moran on 2011-02-19
> **gemma.laming said:**
> Hi Sean and Jon,
I am having some problems with my wireless connection.  I am visiting in Bangkok and am having problems with their wireless internet.  I hope that I am on the right thread, I have tried all the things you have suggested for Jon, but with no success.

I have a partial internet connection - by which I mean that I can get some websites and not others.  For example: I can open the website of Mozilla, but I cannot open the website addons.mozilla.org (or somesuch - it is the extra element before the dot that makes it inaccessible).  Another example is that I can access my yahoo email account (old) but not my new one (live.nl).  

Can you help?!  Gemma
The good news is that you're able to access SOME websites.  I take it that you can RELOAD these websites to ensure that they're not just loading from your local cache, but you ARE indeed getting a real connection to Mozilla and Yahoo!, at times.

I can't think of why Thailand would have banned anything Mozilla or Live, and just tried [www.live.nl](www.live.nl) which came up very nicely from down here in Rayong, a couple of hundred kilometres south-east of Bangkok.  Sign in to Windows Live, it's telling me, but I won't hold that against you 9-).

[http://addons.mozilla.org](http://addons.mozilla.org) also came up very quicky from here, so neither of those websites are banned.  All I can think of, after so many different hotel wifi connections in LoS that only work every now and then, is, Welcome to Thailand.

Is it possible to try again, just to confirm that those two particular sites are not accessible?   Remember to prefix **addons.mozilla.org** with the **http://** because there's no www for Firefox to make sense of.

Also, it's just after midday here, and lots of Bangkok office people might have knocked off for the weekend and all on the way home to login to Facebook, so expect some heavy traffic until around 18:00 when everyone goes out to restaurants for the evening.

---

### Post by gemma.laming on 2011-02-19
[LEFT]Hi Sean and Amsterdam,
thanks for your replies!  I tried the ping - it did not work, sorry. I am getting the genuine article as I am also accessing other websites.  
 
I think it is a DNS problem because I can use the computers downstairs - but when it comes to my wireless on my laptop, it no longer works.  I have tried everything I can think of, which I guess isn' t much but at least I tried.  I don't think it is folk knocking off early, I tried yesterday evening and it happened then.  Which is why I wanted the addons.mozilla.org to get something to do something to the - I'm nolonger quite sure what I would be looking for now because I have spent so much time trying to figure out what to do :-(
 
I do love Thailand - I went to school here and there was no air conditioning: I forgot to bring my pullover to the lobby so I am now shivering in the cold!  
 
Thanks again, I will be back with a pullover to keep myself warm!! Gemma
 
PS I am running 9,04 because my computer did not like 9,10 and nobody would help me to sort it out.  I want now to back up my files online (also blocked) and move up to 10.something - but I might not on account of all the problems I see posted!  My computer is a Lenovo T60 something.  [/LEFT]

---

### Post by amsterdamharu on 2011-02-19
@gemma
I assume you have network-manager do your network settings and did not set it up manually. If you did it manually please make a backup of the resolv.conf before editing. If you have network manager (the little icon in the corner uses network manager) then there is no need.

If it is a dns problem you cold change your /etc/resolv.conf.
press alt + F2, type "gksu gedit /etc/resolv.conf" (no quotes) and click run.
Change the content to:
```
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Save it and then ping addons.mozilla.org again:
```
ping addons.mozilla.org
```


To revert to network-manager automatically set your dns settings do the following:
Open up the resolv.conf again and delete the contents then execute the following commands:
```
sudo service network-manager stop
sudo service network-manager start
```

The resolv.conf should be filled again.

---

### Post by gemma.laming on 2011-02-19
eth0      Link encap:Ethernet  HWaddr 00:1e:37:ce:a6:03  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:246468 (246.4 KB)  TX bytes:246468 (246.4 KB)

pan0      Link encap:Ethernet  HWaddr 06:05:c4:15:b5:a4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:28:9b:0d  
          inet addr:192.168.1.161  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe28:9b0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4676135 (4.6 MB)  TX bytes:1064528 (1.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-28-9B-0D-62-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


The command lsusb gave this result: 

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1199:6813 Sierra Wireless, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The sudo lspci gave this: 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

The other command gave about 400 lines and I simply have no idea what I am supposed to be looking for in it!  Sorry,  does this give you any idea as to what is going on?  Gem

---

### Post by gemma.laming on 2011-02-19
Hi Amsterdam Huru,
thankyou for your response which came as I was trying the commands you sent me; I am back on my computer now having been downstairs in the lobby.

Honestly, I have done so much and achieved so little that I cannot really remember what I did - or didn't.  I needed to get to the LAN connections to insert some URL (192.168.1.50) to start the whole thing, but quite how it was done is still a little mysterious to me.  

Messing around with code is not my idea of computing!!  I am one of those people who prefer clicking on icons and the like, I work with drawings and I still regard the code as having magical properties the like of which I should steer well clear of.  And if it actually works, it is like magic for me.  Sorry, that is how I am.  

As to know what I should save - or not save - I leave that in the hands of the gods.  

_When I tried your F2 command I had this response_: 

# Generated by NetworkManager
nameserver 192.168.1.251

I am now going to change it to the wording you gave me, and I have saved it ... I pinged addons.mozilla.org and got no response - but I did not get a (I can't remember precisely what it said) but it said that it was not possible to find the address.  

I am going to post this and try addons in the browser window ... wish me luck!!!! Gem

---

### Post by gemma.laming on 2011-02-19
I tried it in the browser window and got the "cannot find server" etc.  Oh, dear.  What should I try next?  I have been at this for hours, and have explored corners of my laptop that I never knew existed.  Gemma

---

### Post by gemma.laming on 2011-02-19
Just a thought: when I am asked for the user name and password, the system asks for it around twenty times again.  Is this my fault or the system?  I find that Linux does not always fit in with other systems found on the internet.  Gemma

---

### Post by amsterdamharu on 2011-02-19
@gemma

The lsusb, ifconfig -a and lspci were meant for the origional poster since he/she can't connect at all and have to figure out what hardware Ubuntu is having to use.

Your connection seems to work just fine that's why I asked you to change the dns server. DNS is a service that will translate google.com in a number like 64.233.183.106 and is needed to connect to web sites.

If you ping after changing the /etc/resolv.conf did you get a reply?

You could try both commands:[FONT=monospace]
[/FONT]```
ping addons.mozilla.org
cat /etc/resolv.conf
```

The nameserver (dns) you have now seems to be on the local network/in the hotel (192.168.?.?) this is very likely to cause your problem, make sure you are using the 8.8.8.8 and 8.8.4.4 as specified before.

---

### Post by gemma.laming on 2011-02-19
Hi there and thankyou for your response!

I tried it both ways, and did a re-start on each occasion just to make sure.  

I agree that it is probably the network I am doing battle with, but will follow your instructions and let you know the results in around ten minutes.  

I am enjoying Thai weather without air-conditioning, which is how I like it ;-)

Gemma

---

### Post by Sean Moran on 2011-02-19
> **gemma.laming said:**
> Just a thought: when I am asked for the user name and password, the system asks for it around twenty times again.  Is this my fault or the system?  I find that Linux does not always fit in with other systems found on the internet.  Gemma
Sorry I was away for a little while.  My fridge suddenly ran out of beer, and the nearby 108 store was closed to I had to walk all the way to the 711 to fix the problem.

This is a long shot, but I'm up here on the third-floor of this hotel, and that same problem where the access point keeps asking for the passkey over and over again happens to me all the time, from around 10m up and 20m west of the hotel's wifi router, through two floors of concrete mind you.  I have an external wireless modem on around 2 metres of USB cable that I hang out the window to the ledge of the balcony (when it's raining I pack it in a plastic cover), and that improves my reception to this hotel, although it also accesses the wifi of the dentist surgery across Sukhumvit Road, which is five times better than this hotel's wifi, and the password was a very easy guess if you can count to nine and add a zero.

Knowing that you're using a single wireless adaptor built into the system, are you able to test the signal at places close to a window or close to the most likely location of the router?  This goes for many of the Bangkok and Samut Prakan hotels where I've stayed, where you'll get it in the foyer, but in the room, the signal falls below 20%, and you'll get repeated dialog boxes asking you to enter your passphrase / key, because the signal you're sending most likely gets to the router as garbled nothing.

---

### Post by gemma.laming on 2011-02-19
_Results:_ 

ping:unknown host addons.mozilla.org
# Gemerated by NetworkManager
nameserver 8.8.8.8.
nameserver 8.8.4.4
gemma@gemmas-laptop:~$

and that is it.  I am sorry, I am totally baffled.  Gemma

PS the "quick reply" box does not work with firefox and my OS - should that happen on an Ubuntu forum?

---

### Post by Sean Moran on 2011-02-19
> **gemma.laming said:**
> _Results:_ 

ping:unknown host addons.mozilla.org
# Gemerated by NetworkManager
nameserver 8.8.8.8.
nameserver 8.8.4.4
gemma@gemmas-laptop:~$

and that is it.  I am sorry, I am totally baffled.  Gemma

PS the "quick reply" box does not work with firefox and my OS - should that happen on an Ubuntu forum?
Just to double check, if you try: **ping [www.yahoo.com](www.yahoo.com)** you have a fairly reliable control to tell you if it's just addons.mozilla.org or the whole Internet that's the problem.  My sixth sense tells me it's got to do with the signal between your room and the hotel's wifi router, because you keep getting asked for your passphrase, but my sixth sense is wrong 90% of the time.

---

### Post by gemma.laming on 2011-02-19
_I am getting this_:

ping: unknown host [www.yahoo.com](www.yahoo.com)

_for ping [www.google.com](www.google.com) I get the following_:

bash: [www.google.com:](www.google.com:) opdracht niet gevonden

Does this make any sense to you?

I do agree that it is probably the network not liking my operating system - there are a lot of websites (especially with boxes to fill in with addresses and suchlike) which do not like Ubuntu.  

Thanks again for your help.  I have a Thai engineer who is coming up to see me and he might be able to sort things from the network end, which as you say is probably the difficuty.  

Gemma

---

### Post by Sean Moran on 2011-02-19
No worries Gemma.  Chances are that your room is at the extremes of the hotel's wifi, but having someone there in person to double-check should see a resolution.  Also, that external USB ZyXEL G-202 wifi modem I picked up last year only set me back 890 baht, and it has come in very handy throughout all these different hotels where I find my laptop and I struggling with the promised hotel wifi amenities.  It's small and neat and very often proves to be a wonderful travel companion, even though it's not really an aircard:).

---

### Post by gemma.laming on 2011-02-19
Hello Amsterdam and Sean,
it transpires that I have been wasting my time - and worse, yours.  The hotel has blocked just about anything that it wants to.  Which includes access to my own website.  

I have a beautiful room, but if it is not possible to work here, then that all becomes irrelevant.  

I am very disappointed in their service, it is most un-Thai ;-(

Again, I am sorry to have wasted your time.  Gemma

---

### Post by Sean Moran on 2011-02-19
> **gemma.laming said:**
> Hello Amsterdam and Sean,
it transpires that I have been wasting my time - and worse, yours.  The hotel has blocked just about anything that it wants to.  Which includes access to my own website.  

I have a beautiful room, but if it is not possible to work here, then that all becomes irrelevant.  

I am very disappointed in their service, it is most un-Thai ;-(

Again, I am sorry to have wasted your time.  Gemma
Wasting my time is the primary reason that I come to Thailand for 90% of recent years.  Mai pen lai is essence of sanuk!  

Don't give up.  If you can find your computer a desl by the window, and if you can drop by any reasonable computer store, (I got mine from Hardware House International at Star Computer Rayong), you can buy a cheap little external wifi USB adaptor (NOT an aircard, but my aircard only cost me 1390 baht last November), and a nice long USB extension cable, and just hang that external USB modem out the window.  There are many wifi hotspots in Bangkok and most of the passwords are either the name of the hotel, 1234567890, or 1234554321.  There are variations to that, but mostly the easy ones are either the hotel name or something numeric and simple.  This is because hotels understand that most of their afluent farang guests are too stupid to memorise anything more complex.

You can also pickup a proper aircard at a good price, and even though the shop will tell you it won't work on Linux, they do, but sometimes you have to edit the /e/tc/modprobe.d/blacklist.conf file to add a line to temporarily switch off your onboard wifi adaptor (if there are conflicts).  If you can find a good cheap aircard, I'll be here for another six weeks to provide instructions, but the simple USB wifi adaptor on the end of a long cable out the window should pickup plenty of access-points outside your hotel, depending on which part of Bangkok you're in. Don't give up yet if you have good work to do.

---

### Post by TheBigH on 2011-02-19
Hi everyone,
I have followed this thread with great interest because I am having the same problems. I have just made the plunge- removing Micro$oft Window$ from my machine and installing Ubuntu 10.10, and now I can't get my USB wireless to work. Currently I am using a laptop I've borrowed to use this forum and download stuff that I then transfer to my problematic machine. I have successfully installed the wireless driver I was using before.

Below are the outputs of all the programs you've asked the other users in these thread to run. Please bear in mind that I am a rank linux newbie and have no idea what many of these commands do or what their output means.

```


**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:4f:b5:eb  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10872 (10.8 KB)  TX bytes:10872 (10.8 KB)


**sudo ifconfig wlan0 up**
[sudo] password for me: 
wlan0: ERROR while getting interface flags: No such device

**sudo iwlist wlan0 scanning**
wlan0     Interface doesn't support scanning.

**lsusb**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer
Bus 003 Device 003: ID 043d:007d Lexmark International, Inc. Photo 3150
Bus 003 Device 002: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 003: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Can anyone help me with this?
Cheers,
H.

---

### Post by amsterdamharu on 2011-02-19
You have Netgear, Inc WPN111 with missing firmware.
Here is an old post about installing ndiwrapper (Windows drivers wrapped)
[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

Can't find any packages for it:
googled for "site:packages.ubuntu.com netgear"

And looking on the forums the most recent is someone with the same predicament:
[http://ubuntuforums.org/showthread.php?t=1649667](http://ubuntuforums.org/showthread.php?t=1649667)

I guess you need ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

---

### Post by TheBigH on 2011-02-19
Yes! Got it working! Thank you.

---

