---
title: "Enable wireless greyed out in Network Manager"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by leroybrownbpj on 2009-02-07
I've had Ubuntu installed on a laptop for the past couple weeks and have been attempting to get wireless working on it. Wired connection works fine. I was under the impression that Ubuntu was not recognizing the on board wireless (because the "enable wireless tab is greyed out on network manager) and so spent much energy trying to install Linux drivers or set up ndiswrapper to work with XP drivers but this seems to not be the problem after all.

I've just purchased a Belkin wireless "G" USB adapter model F5D7050 because it was listed as working "out of the box" and I am still having the same problem, but importantly it also made me notice something. If I double click on the network manager icon this is what I see:

-------------------------
**   Wired network**
O  auto eth0
**   Wireless Network (Belkin F5D7050 V4000)**
   wireless is disabled
**   Wireless Network (Intel PRO/Wireless 2200BG [Calexico2])**
   wireless is disabled
-------------------------

with all the above greyed out.

right clicking on the network manager icon shows the "enable networking" option checked and "enable wireless" below it unchecked but it is greyed out.

Can someone please tell me why this option is not checkable? It seems that ubuntu recognizes both the on board wireless and the belkin usb adapter. 

Please tell me what I'm missing.

Thanks.

---

### Post by leroybrownbpj on 2009-02-07
Is there more than one reason why this option would be non selectable?

---

### Post by mkvnmtr on 2009-02-07
After a fresh install I clicked on something to disable wireless because I use a wired connection. For the life of me I can't rember what it was. Then I wanted to play with some of the wireless networks in the area and I can't. On the other box I can. Wish I could remember or find it again it's what you are looking for. I know it wasn't enable driver or any thing like that. someone will tell us shortly, I bet.

---

### Post by leroybrownbpj on 2009-02-07
I'd like to hope so,
I asked around on this forum a week back for the same information before I became pretty sure that this was my problem and got no responses. I'm rather disapointed in the network manager app for not providing more information "cannot be enabled because xyz" as opposed to just greyed out.

---

### Post by TimDaniels on 2009-02-08
> **leroybrownbpj said:**
> .... I'm rather disapointed in the network manager app for not providing more information "cannot be enabled because xyz" as opposed to just greyed out.

I have the same complaint.  The Network Manager is non-intuitive and uninformative, and it still needs a lot of work.  I had been using Wi-Fi successfully for weeks, when I decided to disconnect before shutting down.  I'm not sure what I did, but now there is no option on the dropdown menu to check enable wireless.  Nothing I've been able to do in 5 days has brought that back or allowed me to connect wirelessly.  When I fire up the dual-booted Vista, Wi-Fi works like a champ, so I know it's not the laptop's hardware.  I continually get the feeling that Ubuntu is somebody's hobby project, not a commercially viable alternative to Windows.

*TimDaniels*

---

### Post by leroybrownbpj on 2009-02-08
Bump.

I don't like to hog forum space but there has to be someone who knows under what cirmcumstances Network Manager will grey out the option "enable wireless." This is absurd.

---

### Post by Sunspore on 2009-02-09
I experience the same problem too, but I use the laptop function key to disable the wireless accidently, now I am unable to enable it back.

anyone can help us?

---

### Post by Sunspore on 2009-02-09
guys I find the solution. 

on the wireless switch in ur laptop

open terminal

type : sudo ifconfig wlan0 up

and u will find that your wireless is working already

Hope that this will help

---

### Post by TimDaniels on 2009-02-09
> **Sunspore said:**
> guys I find the solution. 

on the wireless switch in ur laptop

open terminal

type : sudo ifconfig wlan0 up

and u will find that your wireless is working already

Hope that this will help

How does the wireless switch on the laptop figure into this?

I ran `ifconfig wlan0 up`, and I got the error msg:
wlan0: ERROR while getting interface flags: No such device

What was it supposed to do?

*TimDaniels*

---

### Post by Sunspore on 2009-02-09
you have to on the wireless function on your laptop. Normally the manufacturer will come with a button for you to on it or a slider. 

If your wireless button is off, there is no current going to your wireless card, the system will display no such device.

---

### Post by ppatrick on 2009-03-19
This is amazing... I cannot understand how Ubuntu launches a version with this bug....

I tested 8.10 desktop on a Tecra M5 with an internal Intel wireless card and a more powerful PCMCIA Proxim/Orinoco 8470-WD.

If the laptop wireless enabler switch is not ON both cards are discovered but the wireless function cannot be activated (grayed). I've also added an USB Dlink DWL-G122 with the same results...

When I turned the internal intel card on using the laptop switch Ubuntu enables all the wireless devices...

botom line, 
if your laptop switch is not on you won't get wireless services no matter what... if your button is ON you'll get wireless but no way to switch off the generally very weak internal wireless card...

after that and SEVERAL tries I've got connected on my internal Intel card, the Proxim couldn't connect...
I've been just using the drivers the installation process sets.

UBUNTU please solve this nightmare....

---

### Post by JoshAF1986 on 2009-05-03
I have the same problem. I right-clicked on the network icon on the panel (ACER Aspire One 110 with Ubuntu 9.04 Netbook Remix) and disabled the wireless. Now it is all greyed out and nothing I do will change that.
 
I've tried blacklisting acer_wmi and loadin ath5k, I've tried using the madwifi driver, and on typing "sudo ifconfig wlan0 up" in the terminal I get the response "SIOCSIFFLAGS: Resource temporarily unavailable".
I must admit that I haven't a clue what it was I was attempting, I just read on forums people's solutions and tried them out...
 
My wifi did work out-of-the-box, untill I manually disabled it. How can I re-enable it?My greyed out area says:
 
**[COLOR=gray]Wired Network[/COLOR]**
[COLOR=gray]disconnected[/COLOR]
**[COLOR=gray]Wireless Networks[/COLOR]**
[COLOR=gray]device not ready[/COLOR]
___________________
VPN Connections     >

---

### Post by timClicks on 2009-05-03
really need to reiterate that this has been a problem for me also. When I accidently flick the wireless switch to off, flicking it to on doesn't help. Network manager wont allow me to enable wireless (I assume this is because you need to be root.) Could the devs please change network manager so that you can enter your root password through the GUI.

On a brighter note, ifconfig did work. Phew!

---

### Post by JoshAF1986 on 2009-05-03
don' ask me why, but after multiple reboots and hair-pulling, ifconfig worked for me too...

I'm not gonna go looking for answers, lets just say there is a God and he enjoys frustrating us!

:P

---

### Post by Yondergod22 on 2009-05-03
> **TimDaniels said:**
> How does the wireless switch on the laptop figure into this?

I ran `ifconfig wlan0 up`, and I got the error msg:
wlan0: ERROR while getting interface flags: No such device

What was it supposed to do?

*TimDaniels*
I don't know much, but I *might* be able to help

what's the output of
ifconfig and iwconfig

---

### Post by Egi_Power on 2009-05-11
Hi!

I had some trouble with my wireless also, but it's now sorted out, big thanks goes to **chili555**: [ipw2200 problems in Hardy, Acer Aspire 1690]("http://ubuntuforums.org/showthread.php?t=1154721")
I was lucky, because it took just a couple of days.

On the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") page there are 2 sticky threads (at the time of writing).
One of them is [Supported wireless cards list and procedure to get help.]("http://ubuntuforums.org/showthread.php?t=370108") -> There is a link [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681") by gnusci.
I would recommend that you attach the outputs of those commands in the terminal in your post, as I did it in my thread.

***EDIT:***
These are the commands I meant:
1 ) Machine Brand and Model (PC/Laptop):
```
Get it from your product information.
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
$ lspci
$ lsusb
```

(hint) use grep to get only information about the Wireless
```
$ lspci -nn | grep 'Wireless Brand'
```

3 ) check interface:
```
$ ifconfig
$ iwconfig

```
(hint) if the Wireless interface name is wlan0 you can also use
```
$ iwconfig wlan0
```

4 ) Check for modules:
```
$ lsmod
```

(hint) search for the Wireless module
```
$ lsmod | grep "wlan_module_name"
```

5 ) Kernel boot messages
```
$ dmesg
```

(hint) the same as in (4)

6 ) Network configuration
```
$ sudo lshw -C network

```
7 ) Scan for networks:
```
$ iwlist scan
```

(hint) the same as in (3)
```
$ iwlist scan wlan0
```

8 ) Ubuntu Version:
```
$ lsb_release -d
```

9 ) Kernel/architecture (including 32 vs. 64 bit):
```
$ uname -mr
```

10 ) Restarting the network:
```
$ sudo /etc/init.d/networking restart
```

***END OF EDIT***

It would help others to see what's wrong exactly.
Don't forget to describe your issue also.

Good luck fixing your problems.

Best regards,

Egi_Power

---

### Post by samspectre on 2009-05-11
I have been having a similar problem (in 9.04) as those described above. I'm using a Dell Studio 17 laptop. The wireless was working fine until a few days ago, and then all I got was the grayed-out "Wireless Disabled". In this thread I learned about the WiFi switch (d'oh!)... and... now it appears to be working. Thanks everyone! *slinks away*

---

### Post by andrealani on 2009-06-09
I have had the same problem: wireless perfectly working with 9.04 and then permanently greyed out after I had disabled it on purpose. Afterwards, it was impossible to activate it again ... At the end, the problem was that I had accidentally set the wireless switch to OFF  :-( The simplest possible solution ... 

thx a lot for the hint :p

---

### Post by bobdavis on 2009-10-10
> **leroybrownbpj said:**
> I've had Ubuntu installed on a laptop for the past couple weeks and have been attempting to get wireless working on it. Wired connection works fine. I was under the impression that Ubuntu was not recognizing the on board wireless (because the "enable wireless tab is greyed out on network manager) and so spent much energy trying to install Linux drivers or set up ndiswrapper to work with XP drivers but this seems to not be the problem after all.

I've just purchased a Belkin wireless "G" USB adapter model F5D7050 because it was listed as working "out of the box" and I am still having the same problem, but importantly it also made me notice something. If I double click on the network manager icon this is what I see:

-------------------------
**   Wired network**
O  auto eth0
**   Wireless Network (Belkin F5D7050 V4000)**
   wireless is disabled
**   Wireless Network (Intel PRO/Wireless 2200BG [Calexico2])**
   wireless is disabled
-------------------------

with all the above greyed out.

right clicking on the network manager icon shows the "enable networking" option checked and "enable wireless" below it unchecked but it is greyed out.

Can someone please tell me why this option is not checkable? It seems that ubuntu recognizes both the on board wireless and the belkin usb adapter. 

Please tell me what I'm missing.

Thanks.
I have a Dell Vostro 1500 Notebook.  The Wireless switch on the left side did the trick.  Grey-out disappeared and it immediately logged on to the wireless network.

---

### Post by cris007 on 2009-11-19
HERE MAY BE THE SOLUTION. I had the same problem with the grayed out Enable Wireless. I tried lots of things I found on different forums with no results. After hours of work it turned out I disabled the wireless from Windows (I have both Windows XP and Linux Mint on my laptop). The wireless button would have no effect in Linux if the wireless was disabled in Windows. After enabling the wireless in Windows and restarting in linux the wireless worked perfect. Also the wireless button worked after that: it would enable/disable my wireless in Linux. Don't know how to explain this, I suppose it must be hardware specific and somehow when disabling the wireless in Windows it really did something with the wireless hardware (turn off). If anyone can explain it would be nice. Hope it helps some of you.

---

### Post by rogerw05465 on 2009-12-02
Guys, see here:
[http://ubuntuforums.org/archive/index.php/t-279212.html](http://ubuntuforums.org/archive/index.php/t-279212.html)

I edited the etc/network/interfaces file per motrennoc's link, rebooted, and the wireless was there and hopping.

Hope that helps

Roger

---

### Post by almufadado on 2009-12-04
I am "at war" with this too.... because gathering knoledge about this is plain and simply, not easy nor accessible to all.

From the knowledge i gather about ipw2200 (and other similar hardware, all related to laptops designed to windows X (x=not for you guys! Sign:  Bill)  

I went from many solutions there are out there, but focused in acerhr as the eth is integrated in a laptop system.

It's seems after all this is related to a simple udev something keycode !!!!

There is a  hardware disable/enable button !
Works in windows with proper drivers from the manufacturer of the laptop, not from those from intel !
Ubuntu, by default, do not recognize this set of special keycodes, that I understand are specific to this make and model, although many people has the same problem, results in multiple variants of the same problem.

I also understand there must be a function associated with that keycode (the hardware kill switch) that in missing in the kernel 

Also I find that what is truthfully lacking in linux (all distros alike) is a UNIVERSAL HARDWARE REPOSITORY, and a chinese philosopher would  says "to get ashore, do not swim against the flow but use it's power to take you there "   

The problem (as in life) is always the "elseif"'s not the "if"s and not the "else"'s 

And yes, I was not being very helpful ! Same as my greyed out wireless  with a windows kill switch ! and it seems to do the job !

---

### Post by khbkhb on 2009-12-23
I too have this issue, and removing and reinstalling the driver hasn't helped. 

System: Dell 830
Ubuntu: 9.10
lshw: 
BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:07:fd:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f1ffc000-f1ffffff
cat /etc/motd
2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64

Unclear what caused the original disablement (whether it was the last set of updates, or if I disabled it via the network manager for some reason) as I got days at a time without using the wireless (and then use it intensively for days ;< ... I was just getting into that mode).

Memory (mine) is falliable, but says that the device was wl0 or wlan0 (like my eeePC) but currently disagrees

khb@khb-jj64b:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:83:f2:27  
          inet addr:10.20.9.41  Bcast:10.20.15.255  Mask:255.255.248.0
          inet6 addr: fe80::221:70ff:fe83:f227/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:453521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:441384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74776925 (74.7 MB)  TX bytes:54845463 (54.8 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:07:fd:a4  
          inet6 addr: fe80::223:4eff:fe07:fda4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5342 (5.3 KB)  TX bytes:5342 (5.3 KB)

pan0      Link encap:Ethernet  HWaddr 8a:81:cf:7c:b7:c7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and lshw is pretty clear about it being eth1
The hardware indicator light says that wifi is active, and my eeePC is able to find several accesspoints.

I've worked through a couple of the troubleshooting guides, but they seem to be focused on the "never worked" side of things ... and I haven't made any progress.

Is this enough clues? If not, and folks want to send me information directly I'll summarize for the forum

---

### Post by vlotoshnikov on 2009-12-26
Hey guys,

I had the same problem and found a SOLUTION that could work for some other configurations. I have Dell Inspiron 13 and faced the issue right after upgrading Ubuntu 9.04->9.10.

SOLUTION: I had "enable wireless" check box grayed out while the hardware "wireless switch" on the laptop was ON (and the `bcmwl-kernel-source' driver was correctly installed). But I noticed that the check box was becoming not grayed out and switched ON once I'd switch the hardware wireless switch OFF (weird enough). Obviously, Network Manager was confusing the wireless switch positions.

SO WHAT I DID WAS that 
1. I switched wireless OFF with the hardware wireless switch and restarted the box.
2. After logging in (and checking that "enable wireless" check box was grayed out - this time for a good reason) I changed the hardware switch to the ON state and now the "enable wireless" check box was not grayed out and switched ON; everything was working again.

Hope this helps. Good luck!
Seva

---

### Post by margazhang on 2009-12-27
Install WICD in to replace Network Manager - WICD is definitely better if you have problem with the latter.

---

### Post by jackies on 2009-12-27
My enable wireless switch is checked. But OS is not seeing router (no signal in NM)? I was thinking of hard wire first and then going wireless later (same fix as always with Windows). Maybe it would work with Ubuntu also?

---

### Post by obiwantoby on 2010-01-04
> **vlotoshnikov said:**
> Hey guys,

I had the same problem and found a SOLUTION that could work for some other configurations. I have Dell Inspiron 13 and faced the issue right after upgrading Ubuntu 9.04->9.10.

SOLUTION: I had "enable wireless" check box grayed out while the hardware "wireless switch" on the laptop was ON (and the `bcmwl-kernel-source' driver was correctly installed). But I noticed that the check box was becoming not grayed out and switched ON once I'd switch the hardware wireless switch OFF (weird enough). Obviously, Network Manager was confusing the wireless switch positions.

SO WHAT I DID WAS that 
1. I switched wireless OFF with the hardware wireless switch and restarted the box.
2. After logging in (and checking that "enable wireless" check box was grayed out - this time for a good reason) I changed the hardware switch to the ON state and now the "enable wireless" check box was not grayed out and switched ON; everything was working again.

Hope this helps. Good luck!
Seva

I can confirm that this solution worked. I am on a Dell Inspiron 1520 with the Intel 4965agn adapter. And of course, Dell has implemented a wireless switch.

It is important to note that I know I did **not** toggle the switch, this issue occurred spontaneously. I ran updates from the update manager, installed an Nvidia driver and all of the sudden wireless was disabled. So I did exactly  what was noted above. Switch the switch to off, reboot, then set the switch to on. 

Kind of bad experience to start using Ubuntu...but I am glad at least to have a known solution here in the forums.

---

### Post by obiwantoby on 2010-01-07
I would now like to add that this issue is reoccurring. Even after disabling the Wireless switch in the bios, I will have to reboot enable the switch, turn it off and boot into Ubuntu so I can flip the switch on for my wireless to work.

What is going on here?

---

### Post by adempewolff on 2010-01-09
same problem with Latitude D630, upgrading from 8.10 -> 9.04.  I have a clean install of 9.04 I've been running on another partition since the beta which doesn't not have this problem.

Network manager confuses the switch positions.  It thinks whatever position the laptop booted with is the "off" position.  Only way to make wireless work is to always remember to boot with switch actually in off position.

If someone can point me towards which config files NetworkManager might use to interact with the network switch I can compare the files between my two partitions to find the problem.

Thansk.


edit:  although I should note that I'm nearly certain the problem reported towards the end of this thread by dell users has nothing to do with the one this thread was created for.  I created a thread earlier today in the dell forum for my problem if people want to list their experiences there: [http://ubuntuforums.org/showthread.php?t=1376732](http://ubuntuforums.org/showthread.php?t=1376732)

---

### Post by maraja on 2010-01-23
> **vlotoshnikov said:**
> 
1. I switched wireless OFF with the hardware wireless switch and restarted the box.
2. After logging in (and checking that "enable wireless" check box was grayed out - this time for a good reason) I changed the hardware switch to the ON state and now the "enable wireless" check box was not grayed out and switched ON; everything was working again.


I can also confirm this works on a Dell XPS1330,Ubuntu 9.10 Karmic **64bit** and backports enabled ( sudo apt-get install linux-backports-modules-karmic ).

For your info I haven't faced this problem on the same system with Ubuntu 7.10, 8.04, 8.10, 9.04 and 9.10 -- **ALL 32bit** versions.

Since I have installed the Karmic 64bit version (to get some extra speed from my XPS ;)) I started having this issue so I hope some developers sees this topic and fix the bug.

Thank you so much **vlotoshnikov** you made my day :popcorn:

---

### Post by Apetrunk on 2010-02-10
Sorry to bring back this thread. It seems like it must not be too old.

When I was running the "demo" of Ubuntu, this is what the Network Manager thing showed:
Wired Network
Disconnect
VPN Connections

And that was it. But then there was something else in the notification area saying something about some bad drivers or something. (If I saw the word for what the drivers were, I would know it, and I know it wasn't something good.) If I remember right, it ran a hardware update or something and then I could see wireless networks and all went well.

I just installed Ubuntu recently and don't have that icon for the drivers, and I don't even see "wireless networks" in Network manager anymore. I've turned on and off the wireless switch and turned it off and rebooted and nothing.

When I boot back into Windows, the wireless works just fine, so it's not a hardware problem. Any ideas?

---

### Post by Apetrunk on 2010-02-10
Nevermind. I did step two on [this site]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html") because I couldn't do the rest, but that had made the OS recognize that the wireless drivers weren't activated and let me activate them so yay.

---

### Post by ahagele on 2010-08-30
Hi,
this thread is a bit dated but maybe someone is still looking for answers here.

I have the same issue with wireless dropping off for no reason.

And I found the reason and a solution for it.

When installing the proprietary driver for my Broadcom B43legacy (ndiswrapper) then things go wrong. The board does mostly not work but worse, once the 'enable wireless' is ticked off it can't be turned on again (greyed out).
So I got another Wireless card which does not need the proprietary driver, and all is fine.
I needed to disable the Broadcom driver, reboot and it's all back to normal.

Of course it would be nice to find out what's causing NetworkManager to trip up on a card running under ndiswrapper. But I've wasted enough time on this already and it will remain a mystery.

Cheers
Andreas

---

### Post by luffy_chan_19 on 2010-08-30
i have attempted to turn on the wireless using the keyboard shortcut but every time i do the ilist scan is says wlan0 is dissabled, is there a way to turn on your card sing the terminal?

---

### Post by graeme.whelan on 2011-01-24
Same problem with Dell Inspiron1525 with Dell 1395 (Broadcom) integrated wireless.
I've been reading forums and trying fixes for two weeks now.  After finally finding a working driver, the wireless was always disabled in network manager without any way to enable it.

However the preceding posts made me take another look at the hardware switch...

I could either have wireless enabled by turning off power to the device with the hardware switch, or turn power on for the wireless card and have Ubuntu disable wireless for me.

SOLUTION:
1. Turn the hardware wireless switch OFF (on my laptop, right-hand edge next to DVD drive)
2. Restart Ubuntu
3. Turn switch ON
4. Look for and connect to your preferred wireless network.

It seems that if a hardware switch is present, that Ubuntu sees it as a toggle switch rather than on/off. As soon as I started Ubuntu as above, it connected within seconds and now working flawlessly!  :p

THANKS TO ALL THOSE WHO HAVE POSTED DETAILED STEPS AND RESULTS, even if it didn't work out for them, it prompted me to arrive at a solution that worked for my machine.

---

### Post by HeyAZ on 2011-02-11
Same problem, new hp laptop with intel 6250 wireless built in.  10.10 installed on entire disk, but "wireless is disabled" shows as greyed out; no access to get it working.  So, I posted on Intel's forums, letting them know many people have this problem with latest drivers.
Today (2 weeks later), I completely re-installed 10.10 from scratch: & the wireless now magically works!  I was connected to the internet during the install, and checked those two boxes for updates and 3rd party software.  Perhaps the latest downloads include some fix from Intel.  Or, maybe it was just the wine. But in any event, all works perfectly.  
So I would say start over from scratch, clean install, hopefully all is good.

Thanks Ubuntu ~ 64-bit 10.10 rocks!

---

### Post by superduperlinuxperson on 2011-06-11
Try this:
 
sudo NetworkManager
 
find out the pid, then
 
sudo kill (pid)
sudo NetworkManager
 
that should start it in root, then you can check the little box
 
hope this helps!!

---

