---
title: "Can See APs But Can't Connect!"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by iwantwireless! on 2010-06-11
Hello all! I'm typing on my newly installed Ubuntu 10.04 Lucid Thingy-Magiggy on a cable!
Being a windows convert with no experience in DOS/Terminal and the like, I have no idea what I'm doing and have no clue what's up with my wireless connection!

Using Wicd Network Manager- I can see all the Access points in range, I tried to connect to my home access point to no avail.... "Bad Password"... (I was the one who set that password, I should know what it is!).

What's going on? I tried with wifi radar but that just crashed at the 'obtaining ip' bit so I guess that's the problem?

On a evesham laptop with 32bit desktop edition. Wireless = IntelPRO/wireless 2200BG (i think)

-ifconfig
eth0     [irrelevant]

eth1      Link encap:Ethernet  HWaddr 00:15:00:42:bf:de  
          inet6 addr: fe80::215:ff:fe42:bfde/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:1 dropped:1 overruns:0 frame:0
          TX packets:15 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:791 (791.0 B)  TX bytes:2837 (2.8 KB)
          Interrupt:22 Base address:0xc000 Memory:feafa000-feafafff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

nm-tool
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:15:00:42:BF:DE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    AP1: Infra, 00:24:17:E0:A4:91, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
  AP2:            Infra, 00:1C:DF:E3:AA:AD, Freq 2437 MHz, Rate 54 Mb/s, Strength 51 WPA
    AP3:      Infra, 06:21:04:9C:44:2A, Freq 2412 MHz, Rate 54 Mb/s, Strength 98
    AP4:           Infra, 0A:21:04:9C:44:2A, Freq 2412 MHz, Rate 54 Mb/s, Strength 98
    AP5:          Infra, 00:0F:B5:B4:FF:34, Freq 2432 MHz, Rate 54 Mb/s, Strength 46 WEP
    AP6: Infra, 00:21:04:9C:44:2A, Freq 2412 MHz, Rate 54 Mb/s, Strength 98 WPA WPA2


I've immediatedly spotted that the state is:disconnected... is this the problem?

GUIDANCE PLEASE! i even try to go on an unsecure network to no avail.

Thanks in advance
PS: I've had this problem with every distro i've experiemented with...

---

### Post by iwantwireless! on 2010-06-12
Shameless self-bump

---

### Post by iwantwireless! on 2010-06-12
Another bump... i've been searching all day, please can someone assist?!?

*-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:15:00:42:bf:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:22 memory:feafa000-feafafff

---

### Post by Trizzy on 2010-06-12
I just started having the same problem last night. I haven't found anything yet but I'm searching now. I'll keep you informed when I find a solution.


EDIT: I just found the solution that worked for me. Apparently having the original network-manager package installed conflicts with wicd working properly. Open a terminal and type in 
```
sudo apt-get remove network-manager
sudo /etc/init.d/wicd restart
```

This worked for me, as I'm connected wireless via wicd. The source I found was in this post [Link]("http://ubuntuforums.org/showthread.php?t=1498035&highlight=wicd+bad+password")

---

### Post by iwantwireless! on 2010-06-12
Thanks mate, please it worked for you but it didn't work for me :(

I tried to join a unsecured network and it just gets stuck at 'Obtaining IP...'

edit: trying to use ndiswrapper.. but can't download relevant driver from here:  [ftp://aiedownload.intel.com/df-support/7819/eng/wireless%208.1.1.0%20-%20generic%20tic%2088663.exe]("ftp://aiedownload.intel.com/df-support/7819/eng/wireless%208.1.1.0%20-%20generic%20tic%2088663.exe")

Link appears to be broken, FML

---

### Post by iwantwireless! on 2010-06-12
bump

---

### Post by iwantwireless! on 2010-06-13
Bump

---

### Post by Paddy Landau on 2010-06-14
I'm not an expert, but as no one else has been able to help you, let's see what we can do.

[LIST]
[*]First, why are you using wicd? Ubuntu already has a simple network manager built in. I would suggest that you forget about wicd and use Ubuntu's method.
[*]Second, as your computer can see the access points, that indicates that the drivers are working. You shouldn't have to fiddle around with ndiswrapper.
[/LIST]
So, I suggest that you:

[LIST=1]
[*]Uninstall wicd and ndiswrapper
[*]Reinstall network-manager and network-manager-gnome
[*]Reboot
[/LIST]
In other words, get Ubuntu back to where it started.

Now let's get onto the next stage... 
[LIST]
[*]On your task bar you should see something that looks like a radar symbol. It's the Network Manager applet.
[*]Click once on it, and you'll see a list of available wireless networks.
[*]Click on your network, and after a few seconds it should prompt you for the password.
[*]Enter your password.
[/LIST]
Let me know what results you get.

---

### Post by iwantwireless! on 2010-06-14
Thanks for your time, Paddy.
I've done what you've said, Once I've typed in the password (WPA & WPA2 Personal), The radar symbols light up for ages, then the password screen comes back up again.

Then 'wireless network disconnected' flashes up in the top right hand corner.

Thanks

---

### Post by Paddy Landau on 2010-06-14
> **iwantwireless! said:**
> Once I've typed in the password (WPA & WPA2 Personal), The radar symbols light up for ages, then the password screen comes back up again.
That's a sign that the router is rejecting your password.

Can you access your router in another way? For example, via an Ethernet cable or from Windows (if you have a connected Windows). Then you can:

[LIST]
[*]Check whether you have any security restrictions, e.g. MAC or IP addresses?
[*]Double-check your password. Be sure not to use fancy characters that may differ between Windows and Linux, e.g. accented characters.
[/LIST]

---

### Post by iwantwireless! on 2010-06-14
Hey,

Just checked: My router has no security restrictions, and my password isn't that fancy. I could log in easily the other day when I had windows on this laptop.

edit: Also, as I have BT, it comes with unsecured BTFON, which is an unsecured network, that also I cannot log in to.

Thanks

---

### Post by GoldenAxe on 2010-06-14
Same problem.

I'm installing a Wifi PCI card, and Edimax 7727ln . It is supposed to work out the box.

With it installed the radar shows all the wifi signals loud and clear. But  it won't connect. I get prompts every two minutes to connect, followed by the radar swirling as it tries to connect.

Here's the curiosity. When I remove the PCI card and insert a USB dongle it works fine. Same passwords, same machine. 

Any ideas?!?!

---

### Post by Paddy Landau on 2010-06-14
I'm sorry, as I said earlier, I'm no expert. Let's hope that someone else can help you with this issue.

The only two other things that I can think of are:

[LIST]
[*]Can you connect from the Live CD?
[*]Try Google.
[/LIST]
Sorry I can't help any further.

---

### Post by iwantwireless! on 2010-06-14
No worries Paddy, I couldn't connect from a live disc either.

I will try out a usb wireless adapter and see if that works. If anyone can suggest anything else please feel free to advise!

EDIT: just tried USB wireless adapter... doesn't work..

Honestly, in my experience, Linux is just more trouble than what it's worth (which is nothing lol as its free). Haven't been able to connect to the internet without sticking in a cable since I installed this. A lot easier and more simple sticking to windows. GRRRR

---

### Post by Paddy Landau on 2010-06-14
I've just remembered three more things for you to try. They have solved different people's problems at some stage.

1)

Have you connected your laptop with an Ethernet cable and run all updates? Sometimes, the updates download extra drivers just for your hardware. Reboot after running the updates and try again.

2)

Your computer's BOIS may need updating. Check your manufacturer's website to find out whether this is true of your laptop. If there is an update, be sure to follow the instructions precisely.

3)

Apparently, the wireless can store a surcharge of static electricity (or something -- I don't understand the technical aspect). To solve:

[LIST]
[*]Turn off your computer.
[*]Unplug your power lead.
[*]Remove the battery from your laptop.
[*]Press and hold your power button for 60 seconds.
[*]Release the power button.
[*]Reinsert your battery, re-attach your power lead, and try again.
[/LIST]
I hope one of these solves your problem!

---

### Post by bazzal1941 on 2010-06-14
Don't know if this helps but it worked for me. There appears to be  a problem with RT chips in 10.04 when trying to access WPA.

Have a look at

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by fidolip on 2010-06-16
> **Paddy Landau said:**
> 
2)

Your computer's BOIS may need updating. Check your manufacturer's website to find out whether this is true of your laptop. If there is an update, be sure to follow the instructions precisely.



Since wireless works fine while under windows my guess would be that he doesn't have to do anything with bios.

I'm having very similar problem, but, what's weirdest imo, I CAN connect to secured networks (at least the one at my parents) but I CANNOT connect to unsecured ones (e.g. hotspots)! very confusing.. In a search for an answer, will let you know if I solve my problem.

EDIT:
wtf? just restarted my laptop (I usually standby it on and off for days without restarting) and right now I'm writing via unsecured network.. well, at least I know one possible solution to my problem. I wonder if it'd be enough to restart my wireless card..

---

