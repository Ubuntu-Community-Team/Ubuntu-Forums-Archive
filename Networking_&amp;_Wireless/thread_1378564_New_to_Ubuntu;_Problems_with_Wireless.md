---
title: "New to Ubuntu; Problems with Wireless"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by astroblack on 2010-01-11
Hi there. I've been searching all over on how to get my wireless to work. I'm currently running Ubuntu 9.10 on a Dell Inspiron 2200. The wireless adapter I'm currently using is a Linksys WPC54G ver. 3. When I enter iwconfig lo, eth0 and wmaster0 have no wireless extensions. wlan0 says
IEEE 802.11bg  ESSID:""
Mode:Managed  Frequency 2.412 GHz  Access Point: Not-Associated
Tx-Power=0 dBM
Retry  long limit:7 RTS  thr:off  Fragment thr:off
Power Management:off
Link Quality:0  Signal level : 0  Noise level : 0
Rx inavalid nwid : 0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid msic:0  Missed beacon:0

I tried following the instructions here [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) 

But when I enter sudo ifdown eth0 it says internet eth0 not configured. then  wlan0 it acts like it doesn't even exist. 

I'm really confused on where to start from and how to get the wireless working. Can someone help me please?

---

### Post by tbae2000 on 2010-02-05
I followed the steps found at [http://marshallim.posterous.com/installing-linksys-wpc54g-wireless-network-ca](http://marshallim.posterous.com/installing-linksys-wpc54g-wireless-network-ca) after installing Ubuntu 9.10 side by side with Windows XP on my HP laptop with Linksys WPC54G v3. I had to install **ndisqtk **while I was connected to the internet using wired LAN. For some reason, I could not install **ndiswrapper** from the 9.10 installation CD.
 

Steps are as follows:[LIST=1]
[*][[COLOR=#bc7134]Install **ndisgtk**[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") via the Synaptic Package Manager ('ndiswrapper-utils' was applied automatically).
[*]Download and extract v3.0 ([COLOR=#ff0000]not v3.1[/COLOR]) of the [[COLOR=#bc7134]Linksys WPC54G driver[/COLOR]]("http://www.linksysbycisco.com/US/en/support/WPC54G/download"). Version 3.1 is an .exe file; whereas v3.0 is a .zip file.
[*]In Ubuntu, open: *System* > *Administration* > ***Windows Wireless Drivers***
[*]Point the **Windows Wireless Drivers** application to the **LSBCMNDS.inf** in the "NT" sub-folder of the extracted folder created in *step 2*. ***Ignore the error message: "Unable to see if hardware is present."***
[*]Use: *System* > *Preferences* > ***Network Connections*** to add an SSID and WEP/WAP data for an available wireless network. Reboot the computer.
[/LIST]Hope this helps.

---

