---
title: "Wireless won't connect - Belkin N Wireless USB"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by WyldeJ on 2010-05-14
Hey, total noob here - just wondering if anybody could shed some light on it all for me. 

 ```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:8c:e0:fa:50
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:27 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febf0000-febfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:df:6a:45:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
```

If any more information is needed to help please prompt me. I've read around blacklisting but I'm not sure on what I should be blacklisting really. A simple (if possible) step by step guide would be **much** appreciated.

Thanks in advance.

---

### Post by WyldeJ on 2010-05-14
Shameless bump. Any info would be much appreciated.

---

### Post by mark bower on 2010-05-14
have you left clicked the wireless icon in the upper rt corner (system tray and selected your SSID (access point)?

---

### Post by WyldeJ on 2010-05-14
Yeah, I've entered my pass and it attempts to connect for a while then it pops up with anprompt for the password again. I've definitely got the correct password...

---

### Post by kwalters on 2010-05-14
I had exactly the same problem with the same USB adapter which worked OK under Ubuntu 9.10 but not under 10.04.  It APPEARED to be working under 10.04, and showed my WEP protected network. but kept repeating demands for the WEP passphrase without ever connecting.

Step 1: click on Systems and Administration and see if there is a "Windows Wireless Drivers" entry in the drop down menu.  If not, you might need to install NDISWrapper.

If there is no entry, you might still have a problem.  To install NDISwrapper without resorting to the terminal complications so beloved of most users of this forum, you need an internet connection.  If the Belkin N adapter is your only means of connecting, that could be difficult.

In my case, I already had a Belkin G adapter which fitted in the same fitting and worked perfectly under 10.04 without any intervention from me.  If that had not been there, I would have been reduced to moving the PC to somewhere with a wired connection.

Step 2  With a web connection, select System and Administration and Synaptic Package Manager.  When the quick search window appears at the top, type in NDIS.  INstall NDIS wrapper and any other files it suggests.

Step 3: you need the drivers that appear in Windows\System32 to be available in Ubuntu. They are all called RT2870 dot something and the key one is dot inf.  If you are dual booting with Windows like I am, that is easy. If you get stuck, email me on [email]keithwalters2002@yahoo.co.uk[/email] and I will send them to you.  Mind you, I am going away for 3 days starting early tomorrow morning, so there might be a wait.

Step 4: select System and Administration and you should be able to click on Windows Wireless Drivers (or something similar)  Ask it to add a driver and point it to the RT2870.inf file.  With the driver installed, you MIGHT have to reboot before it works.  But it worked for me when I had been tearing my hair out.

KW

---

### Post by myurkiw on 2010-05-16
Hello.  I am having the same problem.  I installed the driver net8192su.inf from the CD with ndskwrapper and I am using WEP 128 key, but it keeps asking for the Wireless Network Authentication Required password.  If I disable the security on the router, it connects fine.  Any ideas?

---

### Post by kwalters on 2010-05-17
Don't want to teach my grandmother, but have you made certain of the difference between the (hex) "key" and the (text) "passphrase" in terms of what you enter?

KW

---

### Post by myurkiw on 2010-05-18
KW - I am putting in the key directly and not generating on from a passphrase.  They match.  Other PCs and my sons xbox works with the WEP key.  My old laptop that has been upgraded to 10.04 is working.  But this is a new install on a Dell desktop.  It only works unsecured.  Thanks for any advice.

---

### Post by kwalters on 2010-05-20
I only have 2 suggestions left, then I am clean out of ideas.

1.  Double check that you are using the correct dotINF file.  Your title is different from the form used in all my other Belkin devices.  Do you have a Windows XP installation upon which you could use the CD and double check whether any dotINF files like the ones I mentioned above (RT2870.inf) appear in \Windows\system32

2   Try uninstalling the driver and reinstalling it (followed by a reboot).  It worked for me once.  It is fairly straightforward in the GUI form

System/Administration\Wireless Windows Drivers  (or whatever) and follow the instructions

KW

---

### Post by myurkiw on 2010-05-24
KW -  I got it working!  I had to black list the rt2800 and change to WPA.  Can't get WEP to connect, but WPA is working.  It seems to ask for the password each time I log in though.  I tried editing and saving the connection, but it continues to prompt each time I log on.  I guess I deal with that.  Thanks for your help.

---

### Post by myurkiw on 2010-05-25
Never mind.  I had to check off the Apply To All Users toggle and now it automatically signs in.   :)

---

### Post by myurkiw on 2010-05-25
Got it.  I had to check off the Apply To All Users toggle and now it automatically logs in.  :)

---

