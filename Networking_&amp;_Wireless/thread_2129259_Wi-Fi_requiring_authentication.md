---
title: "Wi-Fi requiring authentication"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by MemoNick on 2013-03-25
Hi, I'm a Windows user, and today I decided to give Ubuntu 12.10 a try. I downloaded it and installed it normally on my Acer Aspire One C70. So far, so good. However, when I tried to connect the internet through the wi-fi, I wasn't allowed to do so. After feeding it the password (correct password, double-checked), the Network Manager tries to connect for around half a minute, then tells me that authentication is required. I tried to look for solutions online, but none worked.

The wireless security is set to WPA & WPA2 Personal. I checked with a laptop (using Windows 7) and the setting was also set to WPA2 so I doubt if that's the problem. Also note that the box 'Available to all users' is also ticked.

Would anyone be kind enough to guide me on what I should do to access the internet from my netbook please? Thanks in advance :)

PS Since I'm a new Ubuntu user, I'd appreciate it if you told HOW to do thing, instead of just telling me what to do... i.e. if you ask me to provide a log, please tell me from where to retrieve it.

---

### Post by ahallubuntu on 2013-03-25
~

---

### Post by MemoNick on 2013-03-25
The drivers are: r8169 and rtl8192ce. Thanks for your reply :)

---

### Post by ahallubuntu on 2013-03-25
~

---

### Post by MemoNick on 2013-03-26
Hi, and thanks for your reply. I downloaded the latest stable build and extracted it onto my Desktop. I'm trying to follow instructions, yet no luck so far. In the terminal I'm typing:
[I]
cd '/home/memonick/Desktop/compat-wireless-3.6.8-1/scripts/driver-select' rtlwifi

[/I]Note that I also tried variations; such as removing the ' ' from the path, to no avail.

I know that the path is correct because I'm drag-dropping the folder into the terminal window. However, I'm getting an error that it is not a directory. I also tried this line before it: 

[I]sudo apt-get install linux-headers-$(uname -r) build-essential

[/I]However, I got this in the terminal: *E: Unable to locate package build-essential.*

---

### Post by MemoNick on 2013-03-26
I typed *'**/home/memonick/Desktop/compat-wireless-3.6.8-1/scripts/driver-select' rtlwifi *(same as before, without *cd*), and I got this: Must run */home/memonick/Desktop/compat-wireless-3.6.8-1/scripts/driver-select from the compat-wireless top level directory*. Any help please?

---

### Post by MemoNick on 2013-03-26
Any help please? I've been trying to follow instructions from the second answer here: [http://askubuntu.com/questions/233575/how-to-install-network-drivers-in-dell-inspiron-5420](http://askubuntu.com/questions/233575/how-to-install-network-drivers-in-dell-inspiron-5420)

However, I haven't had any luck. When I finished and got to the last step, I typed 'sudo modprobe rtlwifi' and 'sudo modprobe rtl8192ce'. Then I rebooted, yet nothing seemed to happen and I still can't connect to the wifi. Any help would be appreciated since I've been without internet since yesterday.

PS When I unload wifi modules using sudo make wlunload, the only thing I get is 'Unloading rtl8192ce...'

EDIT: I also started again, this time replacing rtlwifi by rtl8192ce. However, when I input '[FONT=Ubuntu Mono]./scripts/driver-select rtl8192[/FONT]' I get the error that the driver is not supported, even though it is my network card.

---

### Post by MemoNick on 2013-03-26
Sorry to bump this, but I desperately need wifi to be working on my netbook by tomorrow. If you need any additional information, please ask for it.

---

### Post by ahallubuntu on 2013-03-26
~

---

### Post by MemoNick on 2013-03-26
Thanks again, I did what you told me to - I used sudo apt-get update, installed the build-essential and all. When it came to setting the directory, I set cd /home/memonick/Desktop/compat-wireless-3.6.8-1, then I used ./scripts/driver-select rtlwifi and ran normally. I installed it correctly, or so I assume. In the end, I used sudo make unload, then sudo modprobe rtlwifi. However, the wifi still doesn't work. I also rebooted, to no avail.

EDIT: Note that when I entered sudo modprobe rtlwifi, it seems like nothing happened. Also, is it normal that whenever I double-click driver-select and choose Run in terminal or Run, nothing happens (in the case of Run in terminal, the terminal appears then closes)?

---

### Post by ahallubuntu on 2013-03-26
~

---

### Post by MemoNick on 2013-03-26
No luck, I'm afraid :( I'm going to switch to Windows 7. Thanks anyway buddy, I'm very sorry for wasting so much of your time, and hope that one day I'll be able to use Ubuntu.

---

### Post by JullyMartin on 2013-03-27
[COLOR=#000000]thank for your assistance..
[/COLOR][COLOR=#000000]I'm trying to follow instructions.[/COLOR]

---

### Post by kurt18947 on 2013-03-27
A wimp's solution is to buy an adapter known to be "plug 'n' play".  A few that I've had good luck with are Netgear WNA1100 (uses an Atheros 9271/ath9k chipset/module),  TrendNet TEW-649UB (uses RealTek 8192SU chipset) and recently a generic Ralink micro USB adapter using the RT5370 chipset and RT2800USB module.  My experience is that these adapters are plug 'n' play on 12.04 and newer.  I paid $6 for the generic USB delivered off Ebay.  Even if you want to get an internal adapter working, it can still be useful to have a plug 'n' play adapter to download drivers, patches etc.

One of the gotcha's of such recommendations is that manufacturers sometimes changes chipsets on a device without changing model #s.  For example, Dlink makes a model DWA131.  Ver. 1 uses the RealTek 8192SU chipset and works great out of the box.  They introduced a Ver. 2 which uses a chipset which is similar but not yet plug 'n' play.  How to tell if you're getting ver. 1 or ver. 2?  The only way I know is to open the package and read the label on the device.  Not a great solution but the only one I know.

---

