---
title: "Wireless Network connection not working after 10.04 intalled"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by rewyllys on 2010-04-29
I just finished upgrading from 9.10 to 10.04 via the Update Manager.  My first noticeable problem is that my wireless connection with my home network no longer functions on my IBM Thinkpad T42 laptop.

The Network Manager applet shows that it detects my home network (and those of several of my neighbors), but I have not been able to get it to connect to this network.  I've been using WPA & WPA2 Personal settings for security, and the Network Manager applet had correctly picked up the password that I had been using under 9.10. 

I've searched the Ubuntu Forums for "wireless T42" and thought I'd found a solution in a posting that recommended using the "wcid" network manager, but I've been unable to find wcid either via the Synaptic Package Manager or the Ubuntu Software Center.

Possibly pertinent observations:  

1.  I've noticed that in Lucid Lynx the Network Manager applet's icon in the top panel is no longer the vertical bars symbol that it displayed in 
Karmic Koala; instead, the icon is a radiating fan display.  In the Network Manager's edit Network Connections window, this fan icon is shown on the Wireless Connection tab, while the vertical bars icon is shown on the Mobile Broadband tab.

2.  The Wireless Connection tab shows, on the line in which it shows awareness of my home wireless network (as "Auto 389690") that this connection was "Last Used" "1 month ago".  It should be saying something like "today".

FWIW, the Network Manager detected my wired "eth0" connection with no difficulty.

Both Jaunty and Karmic picked up my home wireless connection without any problems.  Now I have no idea what to try next.

Thanks in advance for any and all help.

---

### Post by rewyllys on 2010-04-29
In this Forum I just came across another post in response to a question similar to mine above.  One responder suggested posting the output from the terminal command "lspci".  Here it is for my laptop:
[INDENT]ron@ron-laptop-Ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
ron@ron-laptop-Ubuntu:~$ 
[/INDENT]I hope this helps someone suggest an answer to my problem.  Again, thanks in advance.

---

### Post by hihowareyou on 2010-04-29
Same problem, except with the previous version too.

I tried to install a DELL driver (dell inspiron e1405) .exe file and extract the .inf file. No good, nothing happened. All I have is a wired connection which I wont have for much longer (moving) and I need wireless ASAP. Help me too :( Please?

---

### Post by Tony-steam on 2010-04-30
I just finished upgrading from 9.10 to 10.04 via the Update Manager.  My first problem is that I too cannot now achieve a wireless connection

Network Manager  detects my home network (and several others), but I have not been able to get it to connect to this network.
I too have  been using WPA & WPA2 Personal settings for security, and the Network Manager applet had correctly picked up the password that I had been using under 9.10. The key is of 10 characters in length.
Help!

---

### Post by Neosano on 2010-05-01
Upgraded to 10.04 from 9.10.
Now I regret.
My wireless can't connect to the router. (WEP)
Interesting thing I've found in my kern.log

```
May  1 12:32:55 Anna kernel: [ 1420.404067] wlan0: authenticate with 00:1c:f0:df:06:2f (try 1)
May  1 12:32:55 Anna kernel: [ 1420.405675] wlan0: authenticated
May  1 12:32:55 Anna kernel: [ 1420.413050] wlan0: associate with 00:1c:f0:df:06:2f (try 1)
May  1 12:32:55 Anna kernel: [ 1420.420919] wlan0: RX AssocResp from 00:1c:f0:df:06:2f (capab=0x431 status=0 aid=1)
May  1 12:32:55 Anna kernel: [ 1420.420923] wlan0: associated
May  1 12:32:55 Anna kernel: [ 1420.436543] wlan0: deauthenticating from 00:1c:f0:df:06:2f by local choice (reason=3)
May  1 12:32:55 Anna kernel: [ 1420.640168] wlan0: deauthenticating from 00:1c:f0:df:06:2f by local choice (reason=3)
May  1 12:32:55 Anna kernel: [ 1420.839068] wlan0: authenticate with 00:1c:f0:df:06:2f (try 1)
May  1 12:32:55 Anna kernel: [ 1420.844061] wlan0: authenticated
May  1 12:32:55 Anna kernel: [ 1420.844082] wlan0: associate with 00:1c:f0:df:06:2f (try 1)
May  1 12:32:55 Anna kernel: [ 1420.849103] wlan0: RX AssocResp from 00:1c:f0:df:06:2f (capab=0x431 status=0 aid=1)
May  1 12:32:55 Anna kernel: [ 1420.849106] wlan0: associated
May  1 12:32:55 Anna kernel: [ 1420.877057] wlan0: deauthenticating from 00:1c:f0:df:06:2f by local choice (reason=3)
May  1 12:32:55 Anna kernel: [ 1421.076188] wlan0: deauthenticating from 00:1c:f0:df:06:2f by local choice (reason=3)
May  1 12:32:56 Anna kernel: [ 1421.270893] wlan0: authenticate with 00:1c:f0:df:06:2f (try 1)
May  1 12:32:56 Anna kernel: [ 1421.273137] wlan0: authenticated
May  1 12:32:56 Anna kernel: [ 1421.280877] wlan0: associate with 00:1c:f0:df:06:2f (try 1)
May  1 12:32:56 Anna kernel: [ 1421.288892] wlan0: RX AssocResp from 00:1c:f0:df:06:2f (capab=0x431 status=0 aid=1)
May  1 12:32:56 Anna kernel: [ 1421.288896] wlan0: associated
May  1 12:32:56 Anna kernel: [ 1421.300546] wlan0: deauthenticating from 00:1c:f0:df:06:2f by local choice (reason=3)
May  1 12:32:56 Anna kernel: [ 1421.504767] wlan0: deauthenticating from 00:1c:f0:df:06:2f by local choice (reason=3)
```and so on spamming my log.
Before the upgrade there were no such messages. Help, please!

---

### Post by yrhen on 2010-05-01
same here.
A month ago I got wireless working using WICD under Karmic, last night upgraded to Lucid and neither WICD nor network manager will connect - or NM connects and keeps reconnecting/reconfiguring.
Not a clue what is going on - don't even know which output to dump here to show the problem

---

### Post by Neosano on 2010-05-01
Oh, Fixed it!
Use knetworkmanager instead of Wicd.
:-(

---

### Post by chlorinekid on 2010-05-01
im not much help, but i got the same problem too. it finds the wireless signal but after entering the password it thinks about it for a minute and then just requests the password again.

10.04 netbook remix works fine with my acer aspire one. just the desktop im having problems with..

---

### Post by Dearhell on 2010-05-01
Same problem here: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

> So after upgrade from 9.10 to 10.04 the wireless network stopped working.

When I click right on the network manager, the "activate wifi network" option it's grey and unselected and cannot be activated.

Though the device seems properly recognized, appears the right name and model when I left click on the network manager. 


---

### Post by yrhen on 2010-05-01
it's creepy. I'm on air, but I don't have a clue why. It seems killing wicd helped, but if I want to check Networkmanager it immediately disconnects. so as long as i don't try to find out how, it actually works. Did Heisenberg join the lucid team :P?

---

### Post by nyarnon on 2010-05-01
Worsed release yet. Iphone support? I have two out of three wireless USB sticks not working (wpa2 OR driver). These are sitecom wl-302 v1.001 and tp-link wn721n. The sitecom is a regression I read and the tp-link is still in experimental mode. This release should have been called a CR = commercial release instead of a LTS They tried to hard to make the charts with this thing and didn't bother to listen to the reports or fix the problem during alfa and beta. Well now they will be listening I guess and this is just why they have to call for betatesters (like in the X memoryleak). Nobody wants to participate in the process any more, the interested testers rather wait till all the noobs flamed away and then upgrade when things are fixed. There not listened to anyway.

---

### Post by udippel on 2010-05-04
> **Neosano said:**
> Upgraded to 10.04 from 9.10.
Now I regret.
My wireless can't connect to the router. (WEP)
Interesting thing I've found in my kern.log

Before the upgrade there were no such messages. Help, please!

I'd love to do the latter, but the solution must come from Ubuntu. Because you're not alone here. Welcome to the party! (e.g. [http://ubuntuforums.org/showthread.php?p=9232313#post9232313](http://ubuntuforums.org/showthread.php?p=9232313#post9232313))

Uwe

---

### Post by Neosano on 2010-05-10
> **udippel said:**
> I'd love to do the latter, but the solution must come from Ubuntu. Because you're not alone here. Welcome to the party! (e.g. [http://ubuntuforums.org/showthread.php?p=9232313#post9232313](http://ubuntuforums.org/showthread.php?p=9232313#post9232313))

Uwe
Well, looks like wicd was broken after upgrading.
Removed it completely and installed again - now it works :-]

---

### Post by rewyllys on 2010-05-14
The problem for which I opened this thread has been solved.  Apparently the problem arose through a mistake--a mistake that I must have made.  Here is the story:

In the toolbar, you can click on System > Preferences > Network Connection.  This brings up a window labeled "Network Connections", in which you can click on the Wireless tab.  This brings up a listing of the wireless networks detected by the wireless card, in the form of a list of items of reading "Auto <network name 1", "Auto <network name 2", and so on.  When you highlight one of these items and click on Edit, you will be asked to enter a password and click on Authenticate, and then you will see a window labeled "Editing Auto <name of network chosen>".

This window has a tab labeled "IPv4 Settings", under which there is a box named Routes.  Clicking on Routes opens a window named "Editing IPv4 routes for Auto <network name>".  

In this window there is an option named "Use this connection only for resources on its network".  Somehow the box corresponding to this option had been checked, presumably by me when I was floundering around.  The unintended choosing of this option resulted in what its name implies: viz., that that particular wireless network could be used only to access the computers in my house.  

Unchecking this box solved the problem, and I can now use my home wireless network to connect through my home router to the Internet.

---

