---
title: "SOLUTION for ATHEROS AR5007EG wireless issues."
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by mplinux on 2009-03-13
**FIXED!!! **
Here is what I did per bmartin and other threads tips. After many hours of reviewing several threads, attempting several fixes and multiple installations. very user friendly specially for noobs like me!!

Prereq:
I had a Clean install of Ubuntu 8.10.
Atheros AR5007EG card. 

1ST STEP:
Installed NDIS wrapper from Synaptic Package Manager(Search for NDISGTK) or Add/Remove Applications (search for ndis) **Because I'm not to familiar with terminal I preferred to download the NDIS wrapper Interface**

2ND STEP:
Downloaded the appropriate driver for my 64-bit driver. If you have  32-bit just make sure to download that driver. I grabbed the link from this [**THREAD**]("http://ubuntuforums.org/showthread.php?t=512828")
Click [ here ]("http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz").for 64 bit driver. 
Click [here]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz").for 32 bit driver. 
- Opened downloaded File on Desktop --> Extracted files to my home folder.

4TH STEP:
Open NDIS wrapper that I installed earlier by going to SYSTEM>ADMINISTRATION>WINDOWS WIRELESS DRIVERS. 
- SELECTED +Install New Driver
- Located net5211.inf file by going to Ar5007eg folder -->ar5007eg-->net5211.inf
- Select Install

3rd STEP
Go to SYSTEM> ADMINISTRATION> HARDWARE DRIVERS
Deactivate "Support for Atheros 802.11 wireless LAN cards."

4TH STEP
Rebooted and my Wireless Card is now WORKING!! 

**The only problem I had was that Network Manager did not want to accept my password for my router for some reason. I knew it was correct...I decided to try out WICD network manager. Quote:"Wicd is an open source wired and wireless network manager for Linux which aims to provide a simple interface to connect to networks with a wide variety of settings"

5TH
I went to [WICD]("http://wicd.sourceforge.net/download.php") web page.

This is the instructions to download and set up WICD on their website. 

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    ```
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
```

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, **intrepid**).**MAKE SURE YOU REPLACE HARDY with intrepid**. You'll also need to add the key used for signing Wicd by running the following command in a terminal:

   ```
 wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 
```

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.


6TH STEP:
REBOOTED Selected my network from WICD tray Icon. Selected network...selected WPA2 for my security settings/set password... and it was like MAGIC!! now I have a fully functional connection!!!

I hope this helps!!! There is hope out there for those of us using the darn Atheros AR5007EG cards!

---

