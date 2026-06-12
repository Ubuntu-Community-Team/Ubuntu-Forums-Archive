---
title: "Messed up my network manager, need help"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by Polydeuces on 2010-04-21
Hey all, I'm new to the forums and ubuntu (just installed it a few days ago) and have been hurdling over some issues. At first my internet was really choppy just using the default network manager, but I switched the kwlan and that was going pretty well, til I had to reboot and it decided to not work anymore. Now my kernel has no network manager, and I just need some guidance.

I tried downloading the original network manager deb packages from the ubuntu archives, but I couldn't get the core application to run (though I could get the GNOME applet) even wtih chmod I didn't have permission to do anything with it.

any and all help is appreciated!

---

### Post by bobyy on 2010-04-22
try to install WICD is a smaller and work great netw manager
#sudo aptitude install wicd

regard`s

---

### Post by bobyy on 2010-04-23
Well,,, any news ???

---

### Post by Polydeuces on 2010-04-25
I tried ignoring the problem for a few days, but I took your advice and am giving WICD a shot. I'll let you know how it goes :)

---

### Post by 2hot6ft2 on 2010-04-25
It would be more help to know what wifi adapter you have.
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

### Post by Polydeuces on 2010-04-25
Here are the results from terminal:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

After trying WICD for only a few moments, I'm still getting frequent drops and Transmission hardly works at all -- It'll download for a few moments and then taper off to idleness (same with the gnome network manager) Any ideas what I can do to fix this?

Thanks for your help, guys!

---

### Post by 2hot6ft2 on 2010-04-25
> **Polydeuces said:**
> Here are the results from terminal:

```

Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
**[COLOR="Red"]Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)[/COLOR]**
```

The first one is your Ethernet (wired adapter)
The second one in red is your wifi adapter. You're not the first to have problems with it.
It's not the network manager so changing to another one is not going to help until you get the adapters driver working right.

Let me see what I can find on it.

---

### Post by 2hot6ft2 on 2010-04-25
What do you get if you run
```
uname -r
```
in a terminal?
And are you running 32 bit or 64 bit ubuntu?

---

### Post by Polydeuces on 2010-04-25
> **2hot6ft2 said:**
> The first one is your Ethernet (wired adapter)
The second one in red is your wifi adapter. You're not the first to have problems with it.
It's not the network manager so changing to another one is not going to help until you get the adapters driver working right.

Let me see what I can find on it.

you're the man, 2hot6ft2. I appreciate you helping me out! 

I get "2.6.31-20-generic"

And I'm not even quite sure, to be honest. I downloaded the 9.10 netbook remix. Does that come in both versions?

---

### Post by 2hot6ft2 on 2010-04-25
> **Polydeuces said:**
> you're the man, 2hot6ft2. I appreciate you helping me out! 

I get "2.6.31-20-generic"

And I'm not even quite sure, to be honest. I downloaded the 9.10 netbook remix. Does that come in both versions?
I don't know if it does or not. I've never had one and I run Ubuntu Ultimate Edition.
Go to
System > Administration > Synaptic Package Manager
and search for
2.6.31-20
take a screenshot of what it finds and post it.
I fixed this once before but it was with a specific kernel and there are more than (1) 2.6.31-20 kernel. Hopefully it will just be a matter of changing it to the one that works.
Cross your fingers that's the case.

---

### Post by Polydeuces on 2010-04-25
[IMG]http://i44.tinypic.com/2nbeg42.png[/IMG]

*fingers crossed*

---

### Post by 2hot6ft2 on 2010-04-25
I can't see the end of the lines or the full kernel versions but these are the ones I was looking for
> linux-headers-2.6.31-20
linux-headers-2.6.31-20-generic **# the one with x86_64 at the end of the line**
linux-image-2.6.31-20-generic **# the one with x86_64 at the end of the line**
Meanwhile I may have found another fix
run
```
gksu gedit /etc/modprobe.d/blacklist-ath_pci.conf
```
Find this if it's there
> blacklist ath5k
and change it to this
> # blacklist ath5k
Save Close and reboot.
If that doesn't help we can still try the kernel route.

---

### Post by Polydeuces on 2010-04-25
Hmm, here's what I found in gedit: 
```

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```

I tried adding a #, saved/rebooted, but I haven't noticed any difference unfortunately. Would you recommend changing it to exactly what you mentioned?

---

### Post by 2hot6ft2 on 2010-04-25
> **Polydeuces said:**
> Hmm, here's what I found in gedit: 
```

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```

I tried adding a #, saved/rebooted, but I haven't noticed any difference unfortunately. Would you recommend changing it to exactly what you mentioned?
No if the at5k isn't there don't add it.
On the kernels are the ones I listed above the ones that are installed or are 2 of them different? Namely the 2 with **x86_64** at the end of the line.

---

### Post by Polydeuces on 2010-04-25
edit: stupidity.

---

### Post by 2hot6ft2 on 2010-04-25
You just said that look up.

---

### Post by Polydeuces on 2010-04-25
If I can find that in the description, then yes -- the headers/image I have are x86/x86_64.

Does that mean I'm out of luck? :(

---

### Post by 2hot6ft2 on 2010-04-25
> **Polydeuces said:**
> If I can find that in the description, then yes -- the headers/image I have are x86/x86_64.

Does that mean I'm out of luck? :(
For that solution unfortunately yes. But as a last resort (always a last resort in my opinion) there's backports so let me see what I can find now.

---

### Post by 2hot6ft2 on 2010-04-25
Last resort. Installing backports for compat-wireless from here:
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

# For Ubuntu 9.10 Karmic users:
```
sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```
[-o<

[I'm going to laugh if this is the solution]("http://ubuntuforums.org/showthread.php?t=1436256")

---

### Post by Polydeuces on 2010-04-25
Would it make sense to try that first? I can access my router settings. My roommate is running a window's PC and he suffers from extraordinarily slow internet.

---

### Post by 2hot6ft2 on 2010-04-25
> **Polydeuces said:**
> Would it make sense to try that first? I can access my router settings. My roommate is running a window's PC and he suffers from extraordinarily slow internet.
Definitely. If you're both affected then that's where to start.

:lolflag:

---

### Post by Polydeuces on 2010-04-25
> **2hot6ft2 said:**
> Definitely. If you're both affected then that's where to start.

:lolflag:
It's a bit different -- My internet is pretty fast when it's actually working, I just have frequent drops. He can't play any games online though, so I suppose I'll take a whack at that. I'll let you know how it goes!

Thanks!

Would you recommend changing the channel to something other than auto?

---

### Post by 2hot6ft2 on 2010-04-25
The solution I dread the most. What can I say I don't like windows drivers in linux.
[[SOLVED] ubuntu 9.10 LG r405 wireless Howto Atheros AR5001 AR5007EG AR242x]("http://ubuntuforums.org/showthread.php?t=1434524")

And a fixed link to the driver in that guide which doesn't work

[http://www.station-drivers.com/telechargement/atheros/wifi/Atheros_ar5xxx_7.7.0.466-xp(www.station-drivers.com).exe]("http://www.station-drivers.com/telechargement/atheros/wifi/Atheros_ar5xxx_7.7.0.466-xp(www.station-drivers.com).exe")

this link below is broken> **txtiger said:**
> 
Atheros_ar5xxx_7.7.0.466-xp([www.station-drivers.com).exe](www.station-drivers.com).exe)


---

### Post by 2hot6ft2 on 2010-04-25
> **Polydeuces said:**
> 
Would you recommend changing the channel to something other than auto?
Channels 1, 6, and 11 are usually the best so one of those.

---

### Post by Polydeuces on 2010-04-25
Hmm, so adjusting my router's settings (in all kinds of ways) hasn't done anything for me. Should I attempt the backport before this other proposed solution?

Again, thank you so much for your guidance. It means a lot to me.

---

### Post by 2hot6ft2 on 2010-04-26
> **Polydeuces said:**
> Hmm, so adjusting my router's settings (in all kinds of ways) hasn't done anything for me. Should I attempt the backport before this other proposed solution?

Again, thank you so much for your guidance. It means a lot to me.
I had to go make sure the other house didn't get damaged by the tornado last night.

Yes. I would try the backports before trying the windows driver.
And you're welcome.

---

### Post by 2hot6ft2 on 2010-04-26
You might want to post the results from
```
ifconfig
```
and
```
iwconfig
```
maybe it's something as simple as the TX rate.

---

### Post by Polydeuces on 2010-04-26
Ok, I'm going to post my current logs for comparison. 

```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:6e:9b:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73497 (73.4 KB)  TX bytes:73497 (73.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:6d:3e:bc  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe6d:3ebc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129206671 (129.2 MB)  TX bytes:49142367 (49.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-6D-3E-BC-36-64-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

kevin@kevin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"405 1/2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:86:41:3E   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Polydeuces on 2010-04-26
> **2hot6ft2 said:**
> Last resort. Installing backports for compat-wireless from here:
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

# For Ubuntu 9.10 Karmic users:
```
sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```[-o<

[I'm going to laugh if this is the solution]("http://ubuntuforums.org/showthread.php?t=1436256")

OK, the install you suggested for Ubuntu 9.10 Karmic Users is finished. Do I need to install compat-wireless separately, or are the lines of code you provided the only steps?

---

### Post by 2hot6ft2 on 2010-04-26
> **Polydeuces said:**
> OK, the install you suggested for Ubuntu 9.10 Karmic Users is finished. Do I need to install compat-wireless separately, or are the lines of code you provided the only steps?
That's it. That installed compat-wireless. Hope it helps.

---

### Post by Polydeuces on 2010-04-26
Oh noes! I rebooted and the internet doesn't work. How would you recommend restoring the original settings? I have an ext hard drive and a USB drive with the sample OS on it, so I can still access the internet and download things (I think)

---

### Post by 2hot6ft2 on 2010-04-26
Better remove those then. See why I don't like backports.
```
sudo apt-get purge linux-backports-modules-karmic
sudo apt-get purge linux-backports-modules-wireless-karmic-generic
```
Guess that leaves the windows driver. You never did post
```
iwconfig
```
But wait until after removing those.

---

### Post by Polydeuces on 2010-04-28
Sorry it's been awhile since I've posted. I went ahead and removed the backports, so here's my iwconfig.
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"405 1/2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:86:41:3E   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm going to check out a coffee shop that has wifi to see if it's not just my terrible internet, which it very well could be. I'm crossing my fingers that it's just the quality (or lack thereof) of a connection that I'm getting.

---

