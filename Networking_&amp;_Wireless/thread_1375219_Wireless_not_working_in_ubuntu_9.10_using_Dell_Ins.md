---
title: "Wireless not working in ubuntu 9.10 using Dell Inspiron 600m"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by bluewolf_85 on 2010-01-07
The network icon and sound icon disappeared from the panel all of sudden one day while i was using ubuntu 9.10 and the network got disconnected. It used to work fine before when i was using ubuntu 9.04 and even after i updated to 9.10, but then that happened. I added the notification area back to the panel but now ubuntu cannot even find any wireless networks. When i connect a LAN cable to my laptop the internet works fine, but the wireless networks area in the network icon is grayed out and it doesn't show any wireless networks. I'm using a Dell Inspiron 600m laptop and my network card is Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05).

---

### Post by Saghaulor on 2010-01-11
> **bluewolf_85 said:**
> The network icon and sound icon disappeared from the panel all of sudden one day while i was using ubuntu 9.10 and the network got disconnected. It used to work fine before when i was using ubuntu 9.04 and even after i updated to 9.10, but then that happened. I added the notification area back to the panel but now ubuntu cannot even find any wireless networks. When i connect a LAN cable to my laptop the internet works fine, but the wireless networks area in the network icon is grayed out and it doesn't show any wireless networks. I'm using a Dell Inspiron 600m laptop and my network card is Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05).

Well, bluewolf_85, I can certainly try to help you get this working. Mind you I'm no expert, but I have had some experience with buggy wifi.

The good news is that you have an Intel chipset, so this should be easy to get working.

I apologize for the delayed response, I don't have internet at home so I'm limited to helping out during the week.

Let me get this straight, you did an upgrade from 9.04 to 9.10, and everything was working peachy, and then one day all by itself the top bar went screwy and your wifi hasn't worked since? I've had things like that happen to me before.

Let's do some diagnostics first. 

First, are you sure that the wifi switch is in the on position? It sounds silly but I've had it happen to me. If it is, then try the following.

Run the following command in the terminal so that we can be sure that your wifi card is still there. ```
sudo lspci
```That should tell us that your card is there.

You could try running this too, to see if the driver modules are loading. ```
sudo lsmod
``` That will output all the loaded modules, you're looking for modules that are related to your wifi chipset. You can use this code to narrow it down to just your wifi drivers. ```
sudo lsmod | grep 2915
``` The above code should work, but it may not if the module for your card is called something else, hence, my reason for having your run lsmod for all loaded modules.

Now, if the wifi switch is in the on position, and your modules are loaded, let's see if the wifi card works without Network Manager.

First, let's make sure that it's showing up. Run, ```
sudo iwconfig
```, it should show up as wlan0 or something like that. If it is showing up, trying the following.
```
sudo iwlist wlan0 scan
``` That will scan for any active wifi networks. If anything shows up, then your wifi card is working, and the problem is with Network Manger, or some corrupted configuration file in your Home directory. I believe it's probably the latter based on your description. 

Let me know how it goes.

---

### Post by homeuser1 on 2010-01-11
Bluewolf_85 should also check the output of rfkill list.  More than likely he has a hard blocked. I have the same problem, but can't figure out how to unblock it.  

[HTML]dell@dell-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
dell@dell-laptop:~$ 
[/HTML]

---

### Post by Saghaulor on 2010-01-11
> **homeuser1 said:**
> Bluewolf_85 should also check the output of rfkill list.  More than likely he has a hard blocked. I have the same problem, but can't figure out how to unblock it.  

[HTML]dell@dell-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
dell@dell-laptop:~$ 
[/HTML]

Great tip, thanks for the input.

---

### Post by bluewolf_85 on 2010-01-12
thanks guys for replying to my thread. i actually solved the problem after a lot of reading and searching. simply, the **wireless card was turned off from the BIOS**! and my Dell inspiron 600m laptop doesn't have a wireless switch so that's why i couldn't figure it out from the beginning. of course it was working' fine like i said but then i got hit with that bug in 9.10, and it deleted my notification area and apparently turned off the wireless card from the BIOS. when i ran the command "sudo lshw -C network" i saw that my wireless card is recognized and everything looks fine, it showed broadcast=yes, driver=ipw2200, multicast=yes...etc, but then it showed **wireless= radio off**! so i knew somethin' was turned off but there isn't  a switch on my laptop and the wireless settings in ubuntu r all activated and on. after reading this thread "http://ubuntuforums.org/showthread.php?t=885847&highlight=comprehensive+wireless" (which is a really good one), it says in step 6 of the post that "In rare cases, your wireless card (or the PCI bus holding it) may be disabled in your computer's BIOS for some reason", so i went and checked in BIOS and yes wirelss was turned off from there! i guess it is one of them rare cases lol. anyways guys thanks again for replying. :)

---

### Post by p_motch on 2010-01-17
I was experiencing this exact issue with a Dell Inspiron 600m. After trying a couple of things, it turned out it was a pretty simle fix. Function Key (FN) + F2 turns on and off the wireless radio (the F2 key has a dark blue antenna icon on it next to the white F2 label). Pretty obvious, but I just wasn't thinking it could be something simple like that.

If anything is odd about it, the BIOS says the wireless radio is on, but a default Ubuntu install reports the radio off. Hitting FN + F2 fixed it immediately and the wireless access points SSIDs showed up.

---

### Post by Don Bowen on 2010-01-17
I also have the Inspiron 600m.  Celeron 1.5Ghz.  1 gig ram.
Ubuntu 9.10 (386 desktop) installs, but after it's done, if you run a program like Firefox, Ubuntu hangs.
If Ubuntu had a BSOD, it would surely be showing me one.
I was able to run a few games,...
but if I run OpenOffice write, it hangs.
If I try to do a system update...hang...

serious hang...where you have to hold the power button down for six seconds to get it to go off!

I'm going to see if the wireless is turned on or off...as that's the only thing I can think of.
Any thoughts?  It's not an off-brand machine, or maker or BIOS  (phoenix a17), so I'm amazed... Ubuntu is so good at installing on all sorts of machines, I can't explain why it hangs on this one.
thank you for your reply.

---

### Post by dexteer555 on 2010-01-18
Hi Guys
I am using a Dell Latitude D600 and I am running wubi.
I tried "sudo iwlist wlan0 scan" to scan for available networks but my pc says
 [B]"Interface doesnt support scanning : Network Down"
[/B]
Can any one advice on what to do to make my wireless work??

---

### Post by bluewolf_85 on 2010-01-22
Don Bowen try upgrading ubuntu using terminal. type the command sudo apt-get update, then type sudo apt-get upgrade. make sure you have internet connection when doing that.

---

### Post by bluewolf_85 on 2010-01-22
dexteer555 type the command **sudo lshw -C network** in terminal and post the result so i can see what your network card is and whether it's recognized or not.

---

### Post by W7DAH on 2010-01-31
Love Ubuntu EXCEPT this wireless network driver cluster. This Dell Latitude D810 is headed back to Windoz. Too much time already wasted trying to get this laptop's wireless to work in Ubuntu.Sheez.

---

### Post by abrazafi on 2010-01-31
Hi,

I have the Dell latitude D600. Running kubuntu 9.10. The wireless connection was working fine ... Since I did an automatic update on January 22nd, 2010 then my wireless connection stopped working. I'm scratching my head to figure out what is going on...Many thanks for helping me out.

Abdon.


Herewith some output:
> sudo lshw -C network
  *-network:0                     
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation                
       physical id: 0                              
       bus info: pci@0000:02:00.0                  
       logical name: eth1                          
       version: 01                                 
       serial: 00:0f:1f:9e:b1:46                   
       size: 100MB/s                               
       capacity: 1GB/s                             
       width: 64 bits                              
       clock: 66MHz                                
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                                                                                 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5705-v3.16 ip=192.168.0.127 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s     
       resources: irq:11 memory:faff0000-faffffff                                                          
  *-network:1                                                                                              
       description: Wireless interface                                                                     
       product: PRO/Wireless 2200BG [Calexico2] Network Connection                                         
       vendor: Intel Corporation                                                                           
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 05
       serial: 00:0e:35:21:27:49
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:5 memory:fafef000-fafeffff

---

### Post by abrazafi on 2010-01-31
Hi,

It is again me, herewith the log from system: /var/log/syslog

Jan 31 21:36:29 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:37:09 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:37:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:38:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:39:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:40:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:41:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:42:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:43:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:44:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:45:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:46:59 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:47:14 dell NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 0)
Jan 31 21:47:14 dell NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Jan 31 21:47:14 dell NetworkManager: <info>  (eth0): taking down device.
Jan 31 21:47:14 dell avahi-daemon[724]: Withdrawing address record for fe80::20e:35ff:fe21:2749 on eth0.
Jan 31 21:47:18 dell NetworkManager: <info>  (eth0): bringing up device.
Jan 31 21:47:18 dell NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 0)
Jan 31 21:47:18 dell NetworkManager: <info>  (eth0): supplicant interface state:  starting -> ready
Jan 31 21:47:18 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:47:19 dell avahi-daemon[724]: Registering new address record for fe80::20e:35ff:fe21:2749 on eth0.*.
Jan 31 21:47:28 dell kernel: [  736.076035] eth0: no IPv6 routers present
Jan 31 21:47:38 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS 
Jan 31 21:48:08 dell wpa_supplicant[820]: CTRL-EVENT-SCAN-RESULTS

---

### Post by bluewolf_85 on 2010-02-05
W7DAH the problem might not be with your wireless driver, it could be from something else. most dell laptops have intel drivers that are mostly supported in linux. post the results of the commands **lspci** and **sudo lshw -C network** so i could see what the problem is.

---

### Post by bluewolf_85 on 2010-02-05
abrazafi your network driver is recognized so this is good. in sudo lshw -c network it says "link=no" and "wireless=unassociated", i'm guessing you have a problem in the wireless settings. if not, if you have a wireless switch check if it's on. if u don't have a switch on your laptop, since you have a dell laptop check if you can press the Fn button and F2 at the same time so u can turn on your wireless (should be Fn + one of the F keys where the wireless icon is drawn on it). does your network manager show any wireless networks? try the **iwlist scan** command to see if it shows any wireless networks.

---

