---
title: "Vodafone 3g dongle not recognised"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by Rodemire on 2009-12-23
Hi,

I'm not sure if this is the same problem that other people that have submitted to the forums. I have a 3g vodafone K3565-Z usb dongle. I use Vodacom in South Africa.

The thing with me is sometimes when i log on the network manager picks up the dongle and when i click on the Network Manager applet, "Wired Network" and "Mobile Broadband" both appear and i can select my usb connection and it connects to the internet without a problem. But on other occasions, my connection type is just not there,(that is, when i click on the Network Manager applet, there is only "Wired Network... disconected") and no matter what i do i just can't connect. (In both cases, the dongle is connected when i boot)

Does anyone know why it behaves this way and is there a way i can get the network manager to always show my connection permanently? 

Thanks for all the help.

---

### Post by alexfish on 2009-12-23
> **Rodemire said:**
> Hi,

I'm not sure if this is the same problem that other people that have submitted to the forums. I have a 3g vodafone K3565-Z usb dongle. I use Vodacom in South Africa.

The thing with me is sometimes when i log on the network manager picks up the dongle and when i click on the Network Manager applet, "Wired Network" and "Mobile Broadband" both appear and i can select my usb connection and it connects to the internet without a problem. But on other occasions, my connection type is just not there,(that is, when i click on the Network Manager applet, there is only "Wired Network... disconected") and no matter what i do i just can't connect. (In both cases, the dongle is connected when i boot)

Does anyone know why it behaves this way and is there a way i can get the network manager to always show my connection permanently? 

Thanks for all the help.

hi

Unplug it then Plug it Back in After about 10 seconds  Its best To Plug it in after Booting up The Computer

Which Version Of  Ubuntu are you using

---

### Post by pdc on 2009-12-23
this is a ZTE device; (signified by the Z after the initial K3565)

I have one, as a trial; sometimes it is good; (meaning I quickly get a flashing blue light); sometimes it is stubborn; (meaning I get a flashing red light);

and I only find it to be good on Fedora 12; meaning it gives the blue flashing light;

as I plug it into Fedora 12, I can see it give a flashing red light, and then it switches to blue flashing; even though on "lsusb" it still has not been flipped

whereas with Ubuntu 9.10 it displays a flashing red light; (even though I can "flip" the modem with the "eject" command);

and continues to display red flashing;

---

### Post by Rodemire on 2009-12-23
> **alexfish said:**
> hi

Unplug it then Plug it Back in After about 10 seconds  Its best To Plug it in after Booting up The Computer

Which Version Of  Ubuntu are you using

I tried plugging in and unplugging  a couple of times but nothing changed, still no change in the Network Manager. I'm using 9.10 (sorry).

Plugging it after i have booted does not seem to work. All the times that I have been connected it was pluggen in when i booted. (like now for example, I am using Karmic, it just magically started to work, am afraid to shut down now) :-)

---

### Post by alexfish on 2009-12-23
> **Rodemire said:**
> I tried plugging in and unplugging  a couple of times but nothing changed, still no change in the Network Manager. I'm using 9.10 (sorry).

Plugging it after i have booted does not seem to work. All the times that I have been connected it was pluggen in when i booted. (like now for example, I am using Karmic, it just magically started to work, am afraid to shut down now) :-)
Try This  From the Terminal

Hi

can you post the last 8 lines of the log file viewer / messages

whilst you are connected

also try from the terminal

Code:

sudo gedit /etc/modprobe.conf

Add the line or or edit the value (0 to 10)  

[COLOR=Blue]options usb-storage delay_use= 1

[COLOR=Black]save file  then reboot

what pay plan are you on

[/COLOR][COLOR=Black]if you have sd card inserted try removing it

which part of South Africa do you live

Also check the Sim card is not loose , it is next to the usb port

You Can Try These Servers from this list ///  Set the Ipv4 settings  to  /  automatic(ppp ) address only  then ADD  address shown TO The DNS Servers  Box 

[http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)

Country                      IP_DNS            Q_RTT    timestamp

SOUTH AFRICA (ZA)       T  [COLOR=Navy]196.7.0.138 /  [/COLOR]   ,,,,,,,,,,,,0.4    2009-12-22 07:12:47
SOUTH AFRICA (ZA)       T [COLOR=Navy]196.7.147.235 /......... [/COLOR]    0.31    2009-12-23 14:27:11







[/COLOR][/COLOR]

---

### Post by garryknight on 2009-12-23
Betavine's Vodafone Mobile Connect should recognise it. Have a look [_here_]("http://www.betavine.net/bvportal/resources/datacards").

---

### Post by Rodemire on 2009-12-24
> **alexfish said:**
> Try This  From the Terminal

Hi

can you post the last 8 lines of the log file viewer / messages

whilst you are connected

also try from the terminal

Code:

sudo gedit /etc/modprobe.conf

Add the line or or edit the value (0 to 10)  

[COLOR=Blue]options usb-storage delay_use= 1

[COLOR=Black]save file  then reboot

what pay plan are you on

[/COLOR][COLOR=Black]if you have sd card inserted try removing it

which part of South Africa do you live

Also check the Sim card is not loose , it is next to the usb port

You Can Try These Servers from this list ///  Set the Ipv4 settings  to  /  automatic(ppp ) address only  then ADD  address shown TO The DNS Servers  Box 

[http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)

Country                      IP_DNS            Q_RTT    timestamp

SOUTH AFRICA (ZA)       T  [COLOR=Navy]196.7.0.138 /  [/COLOR]   ,,,,,,,,,,,,0.4    2009-12-22 07:12:47
SOUTH AFRICA (ZA)       T [COLOR=Navy]196.7.147.235 /......... [/COLOR]    0.31    2009-12-23 14:27:11







[/COLOR][/COLOR]
Hi Alexfish,

I'm not sure which log file you mean, i just took the last couple of lines of syslog (/var/log), I hope its what you asked for, the following are the lines:

---------------------------------------------------------------------------------------------------------------------
Dec 24 10:16:34 rodemire pppd[2473]: Could not determine remote IP address: defaulting to 10.64.64.64
Dec 24 10:16:34 rodemire pppd[2473]: Cannot determine ethernet address for proxy ARP
Dec 24 10:16:34 rodemire pppd[2473]: local  IP address 41.27.119.183
Dec 24 10:16:34 rodemire pppd[2473]: remote IP address 10.64.64.64
Dec 24 10:16:34 rodemire pppd[2473]: primary   DNS address 196.207.32.83
Dec 24 10:16:34 rodemire pppd[2473]: secondary DNS address 196.207.32.69
Dec 24 10:16:34 rodemire NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Dec 24 10:16:34 rodemire NetworkManager: <info>  Activation (ttyUSB3) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 24 10:16:34 rodemire NetworkManager: <info>  Activation (ttyUSB3) Stage 4 of 5 (IP4 Configure Get) started...
Dec 24 10:16:34 rodemire NetworkManager: <info>  Activation (ttyUSB3) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 24 10:16:34 rodemire NetworkManager: <info>  Activation (ttyUSB3) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 24 10:16:34 rodemire NetworkManager: <info>  Activation (ttyUSB3) Stage 5 of 5 (IP Configure Commit) started...
Dec 24 10:16:35 rodemire NetworkManager: <info>  (ttyUSB3): device state change: 7 -> 8 (reason 0)
Dec 24 10:16:35 rodemire NetworkManager: <info>  Policy set 'Vodacom' (ppp0) as default for routing and DNS.
Dec 24 10:16:35 rodemire NetworkManager: <info>  Activation (ttyUSB3) successful, device activated.
Dec 24 10:16:35 rodemire NetworkManager: <info>  Activation (ttyUSB3) Stage 5 of 5 (IP Configure Commit) complete.
Dec 24 10:16:35 rodemire NetworkManager: Tried to set deprecated property gsm/band
Dec 24 10:16:35 rodemire NetworkManager: Tried to set deprecated property gsm/band
Dec 24 10:16:35 rodemire nm-dispatcher.action: Tried to set deprecated property gsm/band
Dec 24 10:16:38 rodemire ntpdate[2546]: adjust time server 91.189.94.4 offset -0.033312 sec
Dec 24 10:17:01 rodemire CRON[2589]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 24 10:18:09 rodemire anacron[1767]: Job `cron.daily' started
Dec 24 10:18:09 rodemire anacron[2707]: Updated timestamp for job `cron.daily' to 2009-12-24
Dec 24 10:18:42 rodemire NetworkManager: Tried to set deprecated property gsm/band

----------------------------------------------------------------------------------------------------------------------

I am in Johannesburg. The sim card I am using is a prepaid line i buy data bundles in advance. The sim card is correctly inserted. The funny thing is that if i go to XP and use Vodafone's software (Vodafone Connect) it connects to the internet, and if i reboot to Ubuntu, the network manager then recognises the usb dongle. If i shut down and boot first into Ubuntu it doesnt recognise it.

/etc/modprobe.conf is empty. I added the line and will reboot now. I hope something works to get this permanent.

Thanks for your help.

---

### Post by Rodemire on 2009-12-28
Hi,

My network issue seems solved. I did a couple of things and I think it was the usb_modesitch which worked for me. 

I did the modeswitch as per this thread below from the advice of a guy called Johan-Steyn:
[http://ubuntuforums.org/showthread.php?t=1305931&highlight=vodafone&page=5](http://ubuntuforums.org/showthread.php?t=1305931&highlight=vodafone&page=5)

I hope it also helps others out there.

Thanks for your help guys.

---

### Post by st0nes on 2010-02-25
> **alexfish said:**
> Try This  From the Terminal

<snip>
You Can Try These Servers from this list ///  Set the Ipv4 settings  to  /  automatic(ppp ) address only  then ADD  address shown TO The DNS Servers  Box 

[http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)

Country                      IP_DNS            Q_RTT    timestamp

SOUTH AFRICA (ZA)       T  [COLOR=Navy]196.7.0.138 /  [/COLOR]   ,,,,,,,,,,,,0.4    2009-12-22 07:12:47
SOUTH AFRICA (ZA)       T [COLOR=Navy]196.7.147.235 /......... 



Hi Alexfish,

I don't understand where to put these things.  I've got a box that is greyed out for Addresses and a smaller box for DNS servers.  How do I put these in? Just the IP or the whole line with the ,,,, etc? And how are they delimited?  Do I separate them with commas, or what?

My dongle isn't recognised at all: no desktop icon and nothing in network manager.  The output of lsusb indicates that it is actually there and some part of the OS is aware of it:
```
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.P.A.
```
I only gave you one line because I'm at work where they won't let me plug my laptop into the corporate network and Ubuntu HAS NOT MOUNTED my flashdrive.  I only installed this 10.04 yesterday and already I'm appalled at how bad it is.  I've been happily using 8.04 for the last couple of years, but I had a hardware failure, so I decided to upgrade both hardware and software at the same time.  I have found a myriad of other problems which I cannot hope to fix until I can connect to the internet.

Is there some way of taking out the "SOLVED" label on this thread? I've followed the instructions in the thread and my problem is not solved.

---

### Post by alexfish on 2010-02-26
Hi stOnes

Looks like you have a ZTE device, not a vodafone K3565-Z as in the OP

however your device may configure in Ubuntu 10.04 . "I have  just test a ZTE with same ID's with live CD "

when you boot up 10.04, insert the device, does anything show on the desktop, if so point at the icon with the mouse then right click and eject the device, you should now be able to configure the device from the network manager { look at the top right panel } and click make new connection , follow the wizard , "you may leave the device in upon boot"

also after you have ejected the device please post the listing again from the lsusb command

if you have installed Usb Modeswitch Please un install , some ZTE devices work without it

thanks in advance

alexfish

Ps screen shot of your request , my addresses may be different to yours

---

### Post by st0nes on 2010-02-27
Thanks Alexfish, I gave you incorrect information--I have 9.10, not 10.04.

I cannot install vodaphone-mobile-connect because I keep getting the error "Error: Dependency is not satisfiable: ozerocdoff".  I have installed ozerocdoff, but I still get the error message.  Is there a way around this?

---

### Post by pdc on 2010-02-28
the guys who maintain the VMC software got rather depressed with ubuntu last year, and said they could not offer support; 

when you plug the modem in, does it flash a red or a blue light?

---

### Post by alexfish on 2010-02-28
> **st0nes said:**
> Thanks Alexfish, I gave you incorrect information--I have 9.10, not 10.04.

I cannot install vodaphone-mobile-connect because I keep getting the error "Error: Dependency is not satisfiable: ozerocdoff".  I have installed ozerocdoff, but I still get the error message.  Is there a way around this?

Hi


  	 	 	 	 	 	  The vmc installation details are at[ ]("https://forge.betavine.net/projects/vodafonemobile")[http://www.betavine.net/bvportal/resources/datacards/os/ubuntu](http://www.betavine.net/bvportal/resources/datacards/os/ubuntu) and there are also a series of support forums.   
 

 when it asks for users who have permission to run the device one should include root and then the permissions problem should disappear . Also try the same code if trying to reinstall VMC due  to  dependencies errors.
 

 Code :
 

 sudo /opt/vmc/usr/bin/uninstall-vodafone-mobile-connect
 

 Please note if you have a ZTE device or others then the usb_modeswitch  may not be required , if it is not detected remove the usb_modeswitch: check this with the “ lsusb “ command from the terminal.Same may apply to the ozerocdoff , but can't confirm this ; also  can't confirm if removing these  will impact on the VMC .
 
Further to this software I have looked through the scripts  and it uses The PPP and its supporting scripts , almost like for like . if you want to monitor the connection try to install " pppstatus" , if this is installed check out the etc/ pppstatus files , for configs etc.
run pppstatus from the terminal Code : pppstatus

Regards

alexfish

---

### Post by st0nes on 2010-03-06
> **pdc said:**
> 
when you plug the modem in, does it flash a red or a blue light?
Blue.

I've just about had enough of this now.  Time to find another OS.

---

