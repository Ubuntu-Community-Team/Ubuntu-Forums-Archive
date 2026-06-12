---
title: "Cannot connect to a wireless network 9.10"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by wit_273 on 2009-10-30
I updated to 9.10 last night and I like it a lot—it is much faster booting and general usage.  I have one complaint.  In 6 or 7 years of using Linux I have installed many distro's on many computers.  I have never had a problem getting wireless to work (probably the biggest complaint I hear about Linux—yet I have never experienced a problem) until upgrading to 9.10.  I can search for wireless networks and see my neighbors and my network—but cannot connect.  So hear are some details any suggestions on what to try would be greatly appreciated.

Toshiba Tecra A8

> 
# lshw -C network
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:47:fc:a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:ffaff000-ffafffff


>  
# lsmod | grep iwl3945
iwl3945                77212  0 
iwlcore               112508  1 iwl3945
mac80211              181236  2 iwl3945,iwlcore
led_class               4096  3 iwl3945,iwlcore,sdhci
cfg80211               93052  3 iwl3945,iwlcore,mac80211


> 
# iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
root@mylaptop:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:CB:EF:E0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"Geo_Home"  #my SSID
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000014151d183
                    Extra: Last beacon: 1644ms ago
                    IE: Unknown: 000847656F5F486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020010000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


Thanks for any assistance --George

---

### Post by wit_273 on 2009-10-31
Well, I resolved the problem.  I saw in another topic someone suggest getting rid of network-manager and installing WICD (I had it in one of my repositories so all that was needed to install was 'apt-get install wicd').  Worked like champ.  With all the comments I am seeing on wireless issues I think someone messed up on the 9.10 release--wireless is in too much demand now to let it slip.  

Other then wireless I really like it.  Usually when you upgrade your system slows down a little as hardware requirement increase.  So far my system has sped way up since upgrading.  Seems to be a lot cleaner system, greatly reducing the hardware needs.

I hope the wireless issues get resolved very soon--it is enough to frustrate someone and override the improvements of the system altogether.

---

### Post by iliketv01 on 2009-10-31
How would I do that without an internet connection? I'm really new to linux and am trying to give it a chance but my only source of internet through my laptop is a wireless connection since my wired ethernet port is screwed up.

---

### Post by wit_273 on 2009-10-31
You can download the .deb file from [here]("http://wicd.net/download/1.5.9/deb"). On another computer download the file to a USB stick.  Then when you get the file on your laptop double click the file--that should open they package installer.  You can also install it from terminal with ```
sudo dpkg -i wicd_1.5.9_all.deb
```

Welcome to the world of Linux.  It may be somewhat intimidating at first but there are a lot of sources to get help.  You will find that most people in the Linux community are more then willing to help. 

George

---

### Post by VladCE on 2009-10-31
Sorry to jump in, but I have a similar problem. I always use WICD and the latest version 1.6.2 appears to be broken from the previous one I used 1.5.9. First It connects wirelessly then for some reason it immediately drops the connection. The log file mentions DHCLIENT -r eth1 and WPI_CLI -i eth1 terminate ??!!!

Please help. If possible I would roll back to the previous WICD 1.5.9 but I don't know how to do it and if it's possible at all in the "bad Karmic" release.

---

### Post by wit_273 on 2009-10-31
I am using version 1.6.1 with no problem.  I actually had not heard of WICD until tonight so I will be of little help with trouble shooting it.  This may help though--looks like 1.6.2 may have a bug with WPA that can be worked around.  [http://wicd.net/punbb/viewtopic.php?id=699](http://wicd.net/punbb/viewtopic.php?id=699)

But if you want to roll back to 1.5.9 for now you can always uninstall the version you have --I am assuming you installed the .deb package and not by source. (if by source you will need to delete the files)

```
sudo apt-get remove wicd
```

You can always download the 1.5.9 deb package and install per previous instruction.

> You can download the .deb file from [here]("http://wicd.net/download/1.5.9/deb"). On another computer download the file to a USB stick. Then when you get the file on your laptop double click the file--that should open they package installer. You can also install it from terminal with

sudo dpkg -i wicd_1.5.9_all.deb



Hope that helps.

George

---

### Post by claracc on 2009-10-31
I had the same problem. When i used jaunty 9.04 i had never any problem with my wireless. I use a router edimax br6204wg, no propietary drivers.

This morning i upgraded to karmic 9.10, apparently everything went well except when rebooting the wireless connects and a few time later disconnects, and so on all the time. So i couldn't use internet.

I have been reding some posts about this problem, i install through synaptic and a wired net the package bcmwl-kernel-source, as some posts indicates, the problem didn't solve.

I only could solve the problem with your advice:
uninstall network-manager
install wicd from synaptic
I obtained the 1.6.1 release and it works perfect after configuring.
Now i have my wireless net working.

Thank you very much wit_273.

I hope this problem with network-manager and wireless net will be solved soon.

---

### Post by VladCE on 2009-10-31
Thank you, George. I installed 1.5.9, now it drops connection not at once, like 1.6.2, but after about 5 sec timeout. So I believe the problem is in "Karmic" 9.10 release.

They have the followin announcement on their WICD IRQ channel:

>Started talking in wicd on Saturday 10/31/2009 4:00:02 PM
		*Room topic is: #wicd -- [http://wicd.net](http://wicd.net) -- A network connection manager for Linux -- Current release is 1.6.2.2 (bzr-none) -- [https://launchpad.net/wicd/1.6](https://launchpad.net/wicd/1.6) -- [http://wicd.net/moinmoin/FAQ](http://wicd.net/moinmoin/FAQ) -- **1.6.2.1 is broken, use 1.6.2.2** instead*

All I can add is that 1.6.2.2 is not available yet thru Synaptics, so I'll probably keep "Karmic" 9.10 and wait for the fix.

---

### Post by VladCE on 2009-10-31
> **claracc said:**
> 
I hope this problem with network-manager and wireless net will be solved soon.

The network-manager broke soon after I got it with Ubuntu 9.04 and never worked since then. I am surprised with what a P. O. S. is included as the standard Ubuntu distro package and nobody seems to care.

---

### Post by VladCE on 2009-10-31
> **wit_273 said:**
> I am using version 1.6.1 with no problem.
George

Yes! Version 1.6.1 works with no problem!! (That's the latest available thru Synaptics right now).

---

### Post by simonrico on 2010-01-28
Hi all,

I am new to Linux and Ubuntu, I decided to give it a go due to being pretty fed up with MS!
That said I am writing this from my laptop currently running on Vista!!!
I installed Ubuntu 9.10 earlier today and I must say the overall feel of it is excellent and it does seem smoother than any Windows platform I have ever used. However..... I am experiencing the same problem as all of the other users within this topic! I have tried to follow all of the information from other users but nothing seems to work for me, or to put it another way, I am not doing it right!
I wonder if anyone would be good enough to post an idiots guide to how to install the WCID program from scratch?

Thanking you in advance

Simon

---

### Post by claracc on 2010-01-29
I tell you what works for me.

Go to system, administration, software manager synaptic, there you look for wicd thick it to install, synaptic uninstall automatically network-manager -gnome and network manager common and will install wicd.

If the problem persists with wicd, you look for package hostapd in synaptic and install it also.

So, the wifi will be automatically detected and hope you will have internet.

I hope it can help.

---

### Post by simonrico on 2010-01-29
Hi Claracc,

Many thanks for your advice, how do I get the WCID program onto synaptic, I have searched but cannot find it!

Thanks again

Simon

---

### Post by claracc on 2010-01-29
The name of the program is wicd.

In the synaptic software manager window you introduce the name wicd in the quick find box, enter and it is shown wicd.

You select it and clik on package, mark to install.

Regards

---

### Post by bacchusmarsh on 2010-01-30
i tried this, removed network manager and installed wicd 1.5.9 from USB deb file but it would not load. the icon appeared in the top menu bar but when i tried to run it just did nothing(?).

add/remove programs showed it as installed(?)

any ideas?

---

### Post by claracc on 2010-01-31
I don know what is the problem with the .deb file you want to install, but i recommend to install wicd 1.6.1 from synaptic manager. This is the software which works for me.

---

### Post by simonrico on 2010-02-03
Hi bacchusmarsh,

I have had exactly the same problem, what I don't understand is how to install t his WCID program from the synaptic manager as it does not appear on mine!? I have the 1.5.9 on USB as you do but I had exactly the same problem, does anyone know how to get hold of the new version and then any idot proof help as to how to install?!

Thanks

---

### Post by claracc on 2010-02-03
WICD, no WCID.

---

### Post by simonrico on 2010-02-03
Thanks Clara,

But I have searched for WICD, its just my mistake on typing in this forum!

Simon

---

### Post by Michalxo on 2010-02-14
I just have similar problem with Network Manager (NM) vs Edimax br-6204wg router. It just kept disconnecting me all the time and all people on wireless network were dropping with me. (my laptop was the cause).

Seems like wicd 1.6.1 is the cure for my koala. So, just a short tutorial how to obtain it:

Probably you will need at least this package
python-urwid, wicd    

(the best thing you can fiddle out what you need to install is to type 
```

sudo aptitude install wicd

```)
It will list all the necessary files you need to download. You can grab them all from here
```

http://packages.ubuntu.com/karmic/python-urwid
http://packages.ubuntu.com/karmic/wicd

```
(amd64 = for 64bit system; i386 = for 32b system)

Install them by opening. (first python-urwid or other you'll need for wicd, and lastly wicd)

After installing press alt+f2 and type there ```
sudo wicd
``` 
and continue with alt+f2 ```
wicd-client
```

After that, you should see wicd's icon in tray (on panel). That's it ;-)

I hope I haven't done so many mistakes in this "guide".
Cheers Mich

---

### Post by bentenmen on 2010-02-14
Michalxo
thanks for that very useful walk through, after 3 frustrating weeks of trawling forums and requesting help i can at last connect via wireless.

---

### Post by scmaruthi on 2010-03-03
Thanks alot. This was most useful.

---

