---
title: "ubuntu windows dhcp"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by thane on 2006-06-12
I have dual Ubuntu windows xp dual boot box and one ethernet card built into the motherboard.

I can connect to the Internet and update via synaptic fine if I boot into Linux. But if I let my son boot into windows, and then I boot back into Ubuntu, I can't connect to anything for at least a couple of hours maybe more.

I connect with DHCP for both operating systems, and my ISP absolutely refuses to give me static IP for Linux. I know of at least one person who fixed this or a similiar problem with a static IP for Linux. (I assume that windows steals the dhcp and won't relinquish it for a certain period of time?).

Is there any way to make windows give up the connection it stold and keeps for a while even when it isn't running, i.e., allow me boot back into Ubuntu and access the Internet?

---

### Post by jvictor on 2006-06-12
I stand corrected if proved wrong here, "windows doesnt steal the IP" , 

to begin with

1) how do u connect to the net ? is there a router at ur place ?

2) or is it that a cable comes into ur aptmt/home and u plug it into ur machine ?

Maybe as a temp fix u can 

```
ipconfig /release 
``` in windows before shutting down

To be honest it looks like to me more of a DHCP problem of linux and your ISPs router, bcoz some routers are 'tweaked ' to support Windows 

Or this is a recurring pattern and the developers need to look into the DHCP implementation of Linux.

plz give us info on how u connect to the net ..its v crucial in this case

---

### Post by thane on 2006-06-12
I am connecting to the Internet via Sweden's Telia broadband service with a Prestige 660H Triple Play (ADSL) modem.

I have one ethernet cable going from the modem to my inbuilt network card. The telephone line goes from the modem to a outer plug on the wall that alows me to both connect the modem and a telephone. So there is no router other than the external Telia (DHCP) server. 

I believe my network card is a VIA Technologies, Inc VT6102 [Rhine-II].

Does that help? And thank you for the ipconfig /release. I'll try it next time.

Thanks for the help. :)

---

### Post by jvictor on 2006-06-12
Hi
This typically looks like a ADSL configuration where ur data and telephone lines are split using a adsl splitter.

U dont need a static IP from your ISP for this, u can manually configure it within your 'network'

Ur router will have a public ip that ur ISP sees and a private one that ur computer sees. we need to be bothered only about the private one

First you need to be sure of the LAN / private IP add of this router , mostly they use 192.168.1.1 , or go to windows and just check the default gateway settings 



Now get bac into Linux and 
System > Administration > networking 

Select ethernet >properties

Configuration :: Static IP

IP address :: 192.168.1.2 ( use an ip address that falls under the class of ur default gateway 
(ie, if router is  192.168.0.1 ur ip must 192.168.0.2 )

and Gateway :: 192.168.1.1 or whatever

Go to the DNS tab and add ur ISPs DNS server as the **first one **

Click OK.

With that we have set up a static IP


and hopefully after a reboot it must work.

Another thing that I want to know is does ur son 'hibernate' windows or shuts down..

Theres a setting in windows device manager that allows to turn off ur network card as a part of power mgmt , I used to have problems if I didnt disable it bcoz the ethernet portion of my router never 'woke up' if i hibernated from windows and booted into linux... It worked only if i came bac to windows or shutdown windows, and completely powered off the router

Plz try this and get bac.

HTH

---

### Post by thane on 2006-06-13
He shuts windows down; he doesn't use hibernate.

/Thane

---

### Post by jvictor on 2006-06-13
Any success with the Static IP ?

---

### Post by Jimmy_r on 2006-07-29
Any luck, thane? I have exactly the same problem(or had rather, since i do not dual-boot anymore.)

Anyways, I also have Telia ADSL.

If i start ubuntu when the computer has been off for a while, it has no problem connecting.
But if I have started windows before, i have to wait 15-30 mins before ubuntu can connect.
If i do a sudo dhclient, it says: no working leases, sleeping.
Suse have not got this problem when dual-booting with windows, so it is not _only_ telias fault.

---

### Post by thane on 2006-12-04
I'm coming back to this thread now after a little more time and exposure to using Kubuntu/Ubuntu for a while.

Waiting about 15 to 30 minutes sounds about right to be able to use the Internet again after having been logged in on Windows. 

Unfortunately or fortunately, as the case may be, I have neither the time or the patience to wait that long. So what I have found is that if I open up a terminal in windows and write the command "ipconfig /release", I can then reboot into Ubuntu and be able to once again get access to the Internet.

The point about Suse is also good. It has been a few months since I used it, but I could get back onto the Internet more quickly with Suse, and if I found that my son had secretly just used windows, I could open a termnial and type, I believe, #ifconfig /release". I did not have to wait nor log back into windows to get it to release my network connection.

So what is it that Suse is doing, and can or should it be done in Ubuntu? 

This windows hogging my network card or modem is really annoying. It is, of course, more of a problem with windows than it is with Linux, I can boot back and forth between different versions without any trouble. But what can be done to stop windows from screwing my Internet connection, or quickly and easily get the connection back without having to wait, or boot back into windows to stop it? ](*,)

---

### Post by haiku99 on 2006-12-29
I've been fighting a similar problem and so far it looks like the ISP DHCP server locks to the MAC address, and that somehow the machine name/MAC address combo looks different when Ubuntu boots so an IP address is not supplied (don't uderstand this since the MAC should not change since the ethernet card is the same, but from what I've read this can happen).  A possible solution I plan to try is to install a router so that the ISP always sees the same MAC address...  Also from what I've read Windows should release the IP automatically when it shuts down, but does not.....and Linux does.   Anyway, hope this helps, I'll post again if I learn more/fix the problem...

---

### Post by Soarer on 2006-12-29
I think this is a feature of your modem. Many ISPs try to lock down broadband access to 1 PC at a time, generally by MAC address. Some (NTL here I believe) charge more if you want multiple PCs to access, or insist you buy their router.

In this case, the modem will only give out one IP address at a time. Windows doesn't release this when it shuts downs, as it quite reasonably expects to use it again when it reboots. So Ubuntu asks for an IP address, but the modem has already given out its one & only address, and refuses.

The solution is to do, in a DOS window when Windows is running, 'ipconfig'. This will tell you the IP address the router has given out. You should then be able to put this into Ubuntu (using the instructions for static IP above). Then, when you boot Ubuntu, the modem will think it is the same machine connecting (which it is of course) and carry on as normal.

A warning: networking is a bit of a black art still, as implementations of DHCP differ significantly between OSs. Let us know if this works, please.

---

### Post by adamonline on 2006-12-29
I've had the same problem when changing the MAC address (or rather, the hardware) the modem's connected to.  In my case, I was unplugging my modem's output to the router and plugging it into my Ubuntu machine.  I found that unplugging the power to the modem for a minute would reset it (something good ol' Comcast taught me years ago).  Plug it back in, wait for it to start back up, and you're good to go.  

Sure, it's not as fast as the dhconfig release thing, but it'll come in handy next time you shut down windows without releasing the connection.  It'll only take about 2 minutes instead of 15-30 ;)

-ADAM

---

### Post by handy on 2006-12-30
It is also possible to ugrade the firmware, as in make it ***standard*** if your ISP has supplied you with a modem/router that they have put custom firmware in.

If you google for your specific hardware & you get a listing from [http://whirlpool.net.au](http://whirlpool.net.au) have a look there, they give great info'...

Or, of course go to the manufacturers site, if your modem/router's firmware is upgradeable, all the info' will be there.

I have had to standardise the firmware in a *Siemens Speedstream 4200* that Australia's national telco **Telstra**, supplies with VoIP port 5060 blocked!!!

---

