---
title: "how and which wifi driver to install for 9.04 on hp pavilion dv6000"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by doron387 on 2009-09-13
hey guys,
after 1.5 hours trying to figure it out by myself, using the way it worked before in the same machine with pclos2007, and trying some methods from posts from the forum and from the rest of the web i gave up.
i need to have wireless on my hp pavilion dv 6102eu laptop.
with the pclos i used ndiswrapper, as somehow i figured that i have a 'Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card', 
in ubuntu i don't know how to find it.
tried terminal : lspci, but it doesn't mention anything about wireless nor reminds that name.
so i am helpless.
can any body throw me a hand ?
thnx
doron387

---

### Post by Ayuthia on 2009-09-13
The fastest way to get that one running should be to go into System->Administration->Hardware Drivers and activate the Broadcom STA module.  It does not require a working internet connection and should work fine with that card if I recall correctly.  

You might want to confirm that it is a 4311 card by going into the Terminal and typing:
```
lshw -C network
```It should show you which model you have.

---

### Post by doron387 on 2009-09-14
Ayuthia, thnx for the answer, it actually gives a clue, this is the output, and it seems that the wireless network card is disabled (though i am not sure that that's what it says)

[COLOR="Red"]doron@laptop:~$[/COLOR] [COLOR="Blue"]lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:c5:47:af:28:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/COLOR]
[COLOR="Red"]doron@laptop:~$[/COLOR]

so, how do i enable it ?

---

### Post by Ayuthia on 2009-09-14
> **doron387 said:**
> Ayuthia, thnx for the answer, it actually gives a clue, this is the output, and it seems that the wireless network card is disabled (though i am not sure that that's what it says)

[COLOR="Red"]doron@laptop:~$[/COLOR] [COLOR="Blue"]lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:c5:47:af:28:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/COLOR]
[COLOR="Red"]doron@laptop:~$[/COLOR]

so, how do i enable it ?

Usually your wireless card should be listed as an eth0 or wlan0 instead of pan0.  I can't remember what pan0 is for but it usually is not the wireless card.  Are there any other entries?  You might try the following also:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If that works, then you just need to blacklist the b43 and ssb modules:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
```I am guessing that you already went into System->Adminstration->Hardware Drivers and activated the Broadcom STA module.

---

### Post by doron387 on 2009-09-14
output:

doron@laptop:~$ sudo modprobe -r b43 ssb wl
[sudo] password for doron: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
doron@laptop:~$ sudo apt-get install ndiswrapper
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
doron@laptop:~$ sudo apt-get install ndiswrapper
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
doron@laptop:~$ sudo modprobe -r b43 ssb wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
doron@laptop:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
doron@laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

doron@laptop:~$ 

please understand, i can copy/paste the commands into terminal but i don't understand what they mean, so i can not even doubt whether it is the right thing to type in and most of the times i don't understand the output. (except when it says ERROR, but with my experience with ubuntu, sometimes people say just to ignore these ERROR messages so i am confused)

so, do you have any idea ?

---

### Post by Ayuthia on 2009-09-14
The error message usually means that you have Synaptic or Add/Delete Programs (I think that is the name) running.  Or it could mean that either Synaptic or apt-get was stopped part way through installing something and the lock flag has not been removed.  You will need to close it if you want to run apt-get.

The warning messages just mean that it will still use the /etc/modprobe.d/ndiswrapper in Jaunty, but in future releases, it needs to be stored as /etc/modprobe.d/ndiswrapper.conf.  This is not a big deal.

I am not for sure if you have ndiswrapper installed already or not.  You can try the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

If it does not provide any wireless sites, please post the results of:
```
lshw -C network
dmesg|grep -e wl -e ndis
```

---

### Post by doron387 on 2009-09-14
thnx Ayuthia,

no program is running in the background.
here is the output, something very weird is happening here.
wireless did work in the same machine under pclos.
so what is wrong ?

------------------
doron@laptop:~$ sudo modprobe -r b43 ssb wl ndiswrapper
[sudo] password for doron: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
doron@laptop:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
doron@laptop:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
doron@laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

doron@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:c5:47:af:28:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
doron@laptop:~$ dmesg|grep -e wl -e ndis
doron@laptop:~$ 
-------------------------------

thnx
doron387

---

### Post by Ayuthia on 2009-09-14
The device seems to be missing.  Are you able to see it using:
```
lspci -nn
```

There have been issues with some of the dv6000 where the wireless device will disappear.  I had to get might repaired through HP (under one of their special warranties--they did not call it a recall).

---

### Post by doron387 on 2009-09-14
this is what i got, it seems that it is not recognized, right ? :

doron@laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
doron@laptop:~$

---

### Post by Ayuthia on 2009-09-14
It does not look like the system found the wireless card.  If you have Windows installed on it, are you able to get the wireless to work?  This is how my laptop was.  I was able to get my wireless to work occasionally in Vista, but after a while, it failed.  Fortunately, HP covered it and was able to fix it and return it back to me within a week.  I will admit that I was a chicken and installed Vista back on my laptop before sending it to them.  I feared that they would not look at it if it had another OS on it.

I would first check and see if you can see the wireless card using a liveCD or go through Windows first.  Usually if lspci does not find it, it indicates that there is a hardware issue.

---

### Post by doron387 on 2009-09-15
well, thanks for trying to help.
it seems that it is a hardware issue indeed.
can it just happen that a machine that's in home on the table, almost not being moved out of home losses its device ?
i don't know how this thing even looks like.
i give up.
thanks g-d i have another machine and from now i gon'a use the hp machine just as a table pc
thanks again
doron387
israel

---

### Post by Ayuthia on 2009-09-15
> **doron387 said:**
> well, thanks for trying to help.
it seems that it is a hardware issue indeed.
can it just happen that a machine that's in home on the table, almost not being moved out of home losses its device ?
i don't know how this thing even looks like.
i give up.
thanks g-d i have another machine and from now i gon'a use the hp machine just as a table pc
thanks again
doron387
israel

From what I understood about what happened to mine, the BIOS was not regulating the fan correctly so over time, the laptop got too hot and the motherboard was no longer able to find the wireless card.  You might want to read this and see if yours falls under this:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=uk&docname=c01087194](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=uk&docname=c01087194)

You might be able to get it fixed without charge.

---

### Post by doron387 on 2009-09-15
Ayuthia, 
a lot of thanks, 
i have a pavilion dv6102eu, which does fall within the product numbers supplied in the table, so i should have it fixed for free.
but, my question is :
(english is not my 1st language as u probably have noticed...lol)
i wish to be sure that i understood it right :
i had warranty for 1 year, i have he laptop for less than 3 years, so i do deserve an enhancment of warranty, right ? 
which means that i should get it fixed for free.
but they also mention this bios upgrade issue.
my bios version is F18, and they say that if i have prior version to F3D (which as far as i understand i do) than i have to update it. 
and another but (!) : 
should i do it now or if i have already eperienced one of these problems (which i do) then i should not upgrade it but just send it to their lab to get fixed.
my 'fear' is that because i have ubuntu on the machine and not one of the m$win systems they want be able to upgrade the bios, though i wish to believe that it is possible to do it.
well, i have so many questions.... let me here you respond first and i assume that some of my future questions will be already answered by you.
and again, thanks a lot, i would think of looking for this thing in hp's site, i feel that they r so mSlaves....
bye
doron387

---

### Post by Ayuthia on 2009-09-15
> **doron387 said:**
> Ayuthia, 
a lot of thanks, 
i have a pavilion dv6102eu, which does fall within the product numbers supplied in the table, so i should have it fixed for free.
but, my question is :
(english is not my 1st language as u probably have noticed...lol)
i wish to be sure that i understood it right :
i had warranty for 1 year, i have he laptop for less than 3 years, so i do deserve an enhancment of warranty, right ? 
which means that i should get it fixed for free.
but they also mention this bios upgrade issue.
my bios version is F18, and they say that if i have prior version to F3D (which as far as i understand i do) than i have to update it. 
and another but (!) : 
should i do it now or if i have already eperienced one of these problems (which i do) then i should not upgrade it but just send it to their lab to get fixed.
my 'fear' is that because i have ubuntu on the machine and not one of the m$win systems they want be able to upgrade the bios, though i wish to believe that it is possible to do it.
well, i have so many questions.... let me here you respond first and i assume that some of my future questions will be already answered by you.
and again, thanks a lot, i would think of looking for this thing in hp's site, i feel that they r so mSlaves....
bye
doron387

It looks like they are only covering it for 2 years so I am not for sure about if they will cover it or not.  It might be best to call and ask.

I am not for sure about sending it in without the original OS installed.  I am not for sure about how they will handle it if you don't have it.  I think that HP is going with OpenSUSE with some of their hardware, but I could be wrong.  So there might be a chance that it is ok.

It might be better to update the BIOS (just to take away a chance that they make you do it and then call them back), but I don't think that it is going to fix the issue.  I had F3D as soon as it was out and my laptop failed with it while it was in use.

As for your English, I could not tell that it was not your first language.

---

### Post by doron387 on 2009-09-15
Ayuthia, 
well, i read it again and i do understand that they give this warranty for 2 years from purchasing, so i am not covered by it.
i googled a bit and found some ways to flash the bios under linux.
if you have some better way to do it i will be glad to hear, as it is a little bit intimidating (first time updating the bios).
i have bios version f18 (isn't that vvveeeerrrryyyy old ?)
i am a little bit afraid, 'cause if it doesn't work properly i might lose the whole machine, right ?
is it worth at all in order to just have this wireless
 capability ? 
i use another dual cpu machine, whose wireless works well. 
(yep, it's an xp w/ubuntu in wubi (i need some 3cad softs that work only in xp.
as 4 my english, you should here my israeli accent and understand what i am talking about.....LOL

---

### Post by Ayuthia on 2009-09-15
> **doron387 said:**
> Ayuthia, 
well, i read it again and i do understand that they give this warranty for 2 years from purchasing, so i am not covered by it.
i googled a bit and found some ways to flash the bios under linux.
if you have some better way to do it i will be glad to hear, as it is a little bit intimidating (first time updating the bios).
i have bios version f18 (isn't that vvveeeerrrryyyy old ?)
i am a little bit afraid, 'cause if it doesn't work properly i might lose the whole machine, right ?
is it worth at all in order to just have this wireless
 capability ? 
i use another dual cpu machine, whose wireless works well. 
(yep, it's an xp w/ubuntu in wubi (i need some 3cad softs that work only in xp.
as 4 my english, you should here my israeli accent and understand what i am talking about.....LOL

If you are not planning on sending the laptop in to get fixed, I am not sure if you want to take the risk of updating the BIOS through Linux.  The update will make some system adjustments for your fan, but it will not bring back the wireless.  They had to replace the motherboard on mine.

I am not for sure how easy it is to recover if the flashing does not work.  I don't know if you can recover the HP one.  I have not heard anything about that.  Like you said, if the BIOS flashing fails, the computer won't work.

---

