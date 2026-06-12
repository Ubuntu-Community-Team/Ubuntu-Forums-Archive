---
title: "university wifi hell (eastern kentucky university)"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by wiley89 on 2009-04-09
Basically I've been at this all day. To get online using my university's secured wifi I have to download and run a .exe

So first I tried running it with wine. After some tooling around and getting winetricks and installing the appropriate things, I finally got the message, 

ERROR:  Failed to extract exe from cab.  Cab: c:\windows\temp\\Cloudpath Networks\cabs\XpressConnect.cab Exe: c:\windows\temp\\Cloudpath Networks\XpressConnect.exe.


Basically I have two questions

1. Is it possible to teach wine to extract .cabs
2. I used cabextract to extract the .cab, is it possible to fool the program into thinking the extraction was successful so it will go on to the next task?

I'd really like to get my friends using Ubuntu, but a major drawback is the difficulty of logging on to the schools secure wifi.

---

### Post by juancarlospaco on 2009-04-09
WTF?, Who implement this thing? use a Cautive Portal, FreeRadius, there's better options...

We have a Cautive Portal authentication.

Use PeaZIP to see and extract the CAB file:
[http://downloads.sourceforge.net/peazip/peazip_2.5.1.LINUX.GTK2-2_i386.deb]("http://downloads.sourceforge.net/peazip/peazip_2.5.1.LINUX.GTK2-2_i386.deb")

.

---

### Post by cariboo on 2009-04-09
There is an app called cabextract in the repositories, If i remember correctly it gets instlled when you install the ubuntu-restricted-extras. Have a look [here]("http:///linux.die.net/man/1/cabextract") for options.

Jim

---

### Post by redmk2 on 2009-04-09
> **wiley89 said:**
> Basically I've been at this all day. To get online using my university's secured wifi I have to download and run a .exe


I believe you can configure the wifi manually.  See: [[COLOR="Indigo"]**EKU Wireless Help & Support**[/COLOR]]("http://www.wireless.eku.edu/help.php").  

Note step # 6

Nothing in the .exe is applicable to a Linux install

> 

So first I tried running it with wine. After some tooling around and getting winetricks and installing the appropriate things, I finally got the message, 

ERROR:  Failed to extract exe from cab.  Cab: c:\windows\temp\\Cloudpath Networks\cabs\XpressConnect.cab Exe: c:\windows\temp\\Cloudpath Networks\XpressConnect.exe.


Basically I have two questions

1. Is it possible to teach wine to extract .cabs
2. I used cabextract to extract the .cab, is it possible to fool the program into thinking the extraction was successful so it will go on to the next task?

I'd really like to get my friends using Ubuntu, but a major drawback is the difficulty of logging on to the schools secure wifi.

---

### Post by WirelessK on 2009-12-17
The executable you have is the Windows executable.  There is an Ubuntu version in beta that works in conjunction with Network Manager.  For now, you can manually configure the SSID via Network Manager.

---

### Post by Awalton on 2010-01-10
Actually, the problem is entirely licensing, which is an unfortunate but true part of the Ubuntu environment today. However, not all is lost.

For Lucid and greater users:

You've lucked out. The latest version of FreeRADIUS included in Lucid supports EAP networks, and can easily be set up through network-manager.

Step 1) install FreeRADIUS.
This is as easy as opening a terminal and throwing in 'sudo apt-get install freeradius'. This will actually install the FreeRADIUS server, but along with it comes the client libraries needed.
Step 2) Disconnect from your current wireless network.
Step 3) Click on the network-manager icon and choose "Connect to Hidden Wireless Network"
Network Name: eku_secure
Wireless Security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP)
CA Certificate: [blank] (note: if you have the cert, it's more secure, but it's not required)
PEAP Version: Automatic
Inner Authentication: MSCHAPv2 (default)
Username: your EKU ID (e.g. the first part of your email address, so if you are [email]john_smith6@eku.edu[/email], your EKU ID is john_smith6)
Password: your EKU ID password (same as your email's password)

Press connect and you're on.

For non-Lucid users:
I wish this could be easier. You could file a bug asking The Powers That Be to backport FreeRADIUS 2.1.8 to your Ubuntu version, or you can build it yourself.

The instructions to build FreeRADIUS are the same as building any package, really.
'sudo apt-get install build-essential debuild', then 'sudo apt-get build-dep freeradius'.
From there, you can download the freeradius 2.1.8 package from their website ([ftp://ftp.freeradius.org/pub/freeradius/freeradius-server-2.1.8.tar.gz](ftp://ftp.freeradius.org/pub/freeradius/freeradius-server-2.1.8.tar.gz)), extract it, cd freeradius-server-2.1.8 and debuild (FreeRADIUS is debianized upstream).

If really pressed, I can try to whip up some PPAs with properly build FreeRADIUS clients for people not using lucid, but right now I'm on one machine which runs lucid, so it'd be a bit of work. If you still can't get it working, message me here or on IRC (as awalton__) and we'll see if I can help, or find the 6' tall heavy guy with the Dell computer with all the crazy Ubuntu stickers on the back of it and he'll help you get it straightened out.

---

### Post by Maximus_ARNP on 2010-05-21
Following instructions worked like a charm.

> **Awalton said:**
> 
For Lucid or greater, or Linux Mint 10.10 users [potential for Android Froyo 2.2 as well]:

Step 1) Disconnect from your current wireless network.
Step 3) Click on the network-manager icon and choose "Connect to Hidden Wireless Network"
Network Name: eku_secure
Wireless Security: WPA & WPA2 Enterprise
Authentication: Protected EAP (PEAP)
CA Certificate: [blank] (note: if you have the cert, it's more secure, but it's not required)
PEAP Version: Automatic
Inner Authentication: MSCHAPv2 (default)
Username: your EKU ID (e.g. the first part of your email address, so if you are [email]john_smith6@eku.edu[/email], your EKU ID is john_smith6)
Password: your EKU ID password (same as your email's password)

Press connect and you're on.


In the past if you have ever made connection via **ekuwifi**, then you will automatically get connected to **ekuwifi** at login. To remove **ekuwifi** from auto-connection, and for **eku_secure** to automatically connect at login, I had to delete **ekuwifi** from my auto connect list as follows:

Network Manager ----> Edit Connectins ----> Wireless ----> Delete "**Auto ekuwifi**". Now, on next login, you should be automatically get connected to **eku_secure**.

Sincerely.

Raj.

---

