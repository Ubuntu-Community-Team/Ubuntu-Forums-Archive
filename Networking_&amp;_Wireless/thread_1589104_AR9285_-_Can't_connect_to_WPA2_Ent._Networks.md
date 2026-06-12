---
title: "AR9285 - Can't connect to WPA2 Ent. Networks"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by chris7667667 on 2010-10-05
So, made the switch from Windows to Linux, this is the only problem I've had so far. I'm running the latest release; (10.04?)

My wireless card works just fine on WEP and Unsecured networks. However, I cannot connect to my University's WPA2 Enterprise network. The Network Manager attempts to authenticate, and times out. When I was running Win7, I could connect just fine, so I know the card's compatible on that end. 

I've tried WICD, no change. I've tried the wpa_gui, it shows no adapter and can't connect to wpa_supplicant. 

According to lshw -c network, the card is seen and is functional on my home network, a WEP secured network. It shows ath9k as the driver. 
```
chris@chris-netbook:~/Desktop$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: b4:82:fe:c8:d1:0d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0100000-f010ffff

```

Something I saw of note that might mean something;
```
chris@chris-netbook:~/Desktop$ lsmod | grep ath9k
ath9k                 306138  0 
mac80211              205402  1 ath9k
ath                     7611  1 ath9k
cfg80211              126496  3 ath9k,mac80211,ath
led_class               2864  1 ath9k

```

With each instance of ath9k showing in red. Being new to the system, I have no idea what that means. The Used By 0 tends to make me think that something might be amiss.But I don't really know. 

My intuition tells me something is up with wpa_supplicant, but I really can't say that with any confidence. I've done a pretty comprehensive search regime on anything I could think of relating to this, and haven't found anything that's been able to help me. 

Any help is much appreciated, if more information would help, let me know and I'll provide.

---

### Post by NotTheMessiah on 2010-10-05
I am willing to bet $5 that if you downgrade to 9.10 it will work. i remember that 9.10 remix had no problems with my uni's wifi and then i upgraded to 10.04(which is miles faster but wifi is a big problem)

sorry i am not much help to you....i've installed 10.10(which i hate) to see if it has the same problem.xp has no problems connecting btw

---

### Post by P4man on 2010-10-06
There might be a better solution, but using ndiswrapper and feeding it a windows driver might solve it.

---

### Post by chris7667667 on 2010-10-06
I have tried ndiswapper. Every driver I've been able to find has given me an "Invalid Driver" message when loaded.

---

### Post by P4man on 2010-10-06
You have to feed ndiswrapper the .INF file, so if the drivers come as a .exe or  .zip or .cab or whatever, you will have extract the inf and sys files. You also need the 64 windows driver if you are using 64 bit ubuntu.

---

### Post by kcs11 on 2013-02-17
> **chris7667667 said:**
> So, made the switch from Windows to Linux, this is the only problem I've had so far. I'm running the latest release; (10.04?)

My wireless card works just fine on WEP and Unsecured networks. However, I cannot connect to my University's WPA2 Enterprise network. The Network Manager attempts to authenticate, and times out. When I was running Win7, I could connect just fine, so I know the card's compatible on that end. 

I've tried WICD, no change. I've tried the wpa_gui, it shows no adapter and can't connect to wpa_supplicant. 


My intuition tells me something is up with wpa_supplicant, but I really can't say that with any confidence. I've done a pretty comprehensive search regime on anything I could think of relating to this, and haven't found anything that's been able to help me. 

Any help is much appreciated, if more information would help, let me know and I'll provide.

***Bump!!***
Ditto of every words you said here, I've tried them.  

I'm always on **WPA2 -PSK** with **AR9285** Wireless Network Adapter, Atheros Communications Inc., driver=**ath9k**

I've been dual booting Ubuntu 11.10 along with my Windows 7 for about half a year with no (wireless) problem on my Asus Eee PC 1001PX (netbook).  One day, all of a sudden, network manager knocks my wifi offline along with the annoying repeated textbox "***wireless* *authentication required***" showing. Then, I did a clean installation with the latest ubuntu 12.10.  No luck.  Afterwards, I tried every possible troubleshooting with all possible keyword search on google hoping for a resolution before I resort to *WICD*.  Finally, no success of that either.  Every solution I seek, had failed! :mad:   

It must have been a kernel update or a change of it through the Software Updater which could have impaired the wireless functionality.

I wonder if this will be the same issue if I install other Linux O.S. such as BackTrack?

The only thing I can think of for now is....[SIZE=3][B][SIZE=4]why did Linux programmers continue to neglect this prominent issue? [/SIZE]

[/B][SIZE=2]As you can see, it  had been a major problem to those in the past years... but I'm surpris[SIZE=2]e it[/SIZE] still is the same issue to so many [SIZE=2]of us users at pres[SIZE=2]ent[/SIZE].  WHERE ARE THE FIXES WE STILL BEEN WAITING[SIZE=2] FOR?!  [/SIZE] _ Every year, _[SIZE=2]_each_[SIZE=2]_ linux d_[SIZE=2]_istributions, esp. Ubuntu,_[SIZE=2]_ ma[SIZE=2]inly focusing to the [/SIZE]chang[SIZE=2]es of[/SIZE] the GUI look_.  **[SIZE=2]WHAT GOOD IS IT IF YOU HAVE A B[SIZE=2]E[SIZE=2]AUTIFUL USER INTERFACE WHEN [SIZE=2]THE[SIZE=2] SOFTWARE APPLICATIONS [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]**[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2]**WITHIN IT ARE **[SIZE=2]**RIDDLED WITH FLAWS?? ** [/SIZE][/SIZE]Y[SIZE=2]et [SIZE=2]stability improv[SIZE=2]ements[SIZE=2], bug fixes, and all other errors[SIZE=2] [SIZE=2]are left aside to the users to "figure[SIZE=2]-[/SIZE]it[SIZE=2]-[/SIZE]out".   **[SIZE=2]Ubuntu slog[SIZE=2]an, "It couldn&#8217;t be easier to use" or "user-friendly" [SIZE=2]apparently [SIZE=2]never really reach to that promising sta[SIZE=2]n[/SIZE]dard.[/SIZE][/SIZE][/SIZE][/SIZE]**[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

