---
title: "UTStarcom UT-300R2U ADSL Modem working on Live CD"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by kagashe on 2006-07-04
Hi,

I have got my Ubuntu 6.06 CDs but yet to install/upgrade on my Laptop.

I am very happy to report that my ADSL modem UTStarcom UT-300R2U is working on Live CD out of the box without doing any set up.

kagashe

---

### Post by drsdinesh on 2006-07-07
hi,
i'm a newbie to linux. installed ubuntu 6.06. have a broadband connection using UTStarcom UT-300R2 ADSL Modem - through the ethernet port. my system is a AMD64 3500+ on ASUS motherboard.
although the pppoeconf has installed, no net connection is available. am absolutely lost. could you tell me how to connect to the net after a fresh install?

---

### Post by kagashe on 2006-07-07
> **drsdinesh said:**
> hi,
i'm a newbie to linux. installed ubuntu 6.06. have a broadband connection using UTStarcom UT-300R2 ADSL Modem - through the ethernet port. my system is a AMD64 3500+ on ASUS motherboard.
although the pppoeconf has installed, no net connection is available. am absolutely lost. could you tell me how to connect to the net after a fresh install?I hope your modem is already configured by using Windows XP. You need not bother about pppoeconf etc. in Ubuntu since it is already set up in the modem (the modem is another PC and it has pppoe, built in firewall and so many things). I hope you have not tried to configure pppoe in Ubuntu. There may be a conflict if you do so.

Ubuntu Dapper Drake 6.06 automatically detects the modem and configures it as eth0 or eth1. You don't have to manually configure anything. Just click on System/Administration/Networking and see whether the device is active or not.

I don't know anything about AMD64 version of Ubuntu if it is different from what I have. I am talking about PC edition of Ubuntu for Intel x86 (including Intel Pentium and AMD Athlon). The network connection is working even on the Live CD without any manual configuration.

kagashe

---

### Post by drsdinesh on 2006-07-08
Hi there,
   that was a quick response. Thanks.
  but the problem is still there. the problem about not being able to connect to the net seems to be my only angst against Ubuntu right now. i didn't change any config settings, though i did try to follow araz' advice by changing the DHCP to static IP. Still nothing. even went to the extent of downloading PCLinux OS and Mandriva One and running the Live CD's to check if other distos handle things differently. No solution there too. Mandriva didn't even boot up!! am I to blame the hardware for the problems??
  thanks once again,
dinesh.

---

### Post by kagashe on 2006-07-08
> **drsdinesh said:**
> Hi there,
   that was a quick response. Thanks.
  but the problem is still there. the problem about not being able to connect to the net seems to be my only angst against Ubuntu right now. i didn't change any config settings, though i did try to follow araz' advice by changing the DHCP to static IP. Still nothing. even went to the extent of downloading PCLinux OS and Mandriva One and running the Live CD's to check if other distos handle things differently. No solution there too. Mandriva didn't even boot up!! am I to blame the hardware for the problems??
  thanks once again,
dinesh.
Let me tell you once again that if PPPOE of any Linux system (be it Mandriva , PCLinux OS or Ubuntu) if configured creates conflict with this modem. Both Mandriva and PC Linux OS detect it as ADSL modem and present you the PPPOE configuration screen. In these OS (Mandriva and PC Linux OS) you have to delete the PPPOE and tell it as if it is normal eth connection (and not an ADSL) and it works. Fortunately, Ubuntu Dapper does not detect it as ADSL modem (it detects as if it is a normal eth connection) and configures it through DHCP.

If you have sufficient RAM (atleast 256 MB), I suggest you try Live CD (don't bother for your installed Dapper for the present) and open Firefox and try to browse. Remember to switch on the modem first and check whether the "Link" light blinks and establishes a connection to internet. Then boot your PC with the Live CD. If this does not work there is a problem with your modem settings (may be it is set to use the external PPPOE or DHCP  is not enabled in it) which needs to be changed. The modem should use its own PPPOE and DHCP enabled to work with Live CD.

kagashe

---

### Post by drsdinesh on 2006-07-13
hi,
  thanks again.
  was down with viral fever, so couldn't visit the forum. but i'd already tried the live cd route as soon as i saw your original post.
  so i guess i'll need to deal with the modem's settings. but am a little scared. don't know much about devices and their configurations. anyhow, desperately want to get ubuntu to connect to the net, so i can chuck windows totally.
  any help available about resetting the modem - i seem to have misplaced the owner's manual along with the carton?

dinesh.

---

### Post by kagashe on 2006-07-14
Hi Dinesh,

I have uploaded the Modem document here. You can download:
[URL="http://rapidshare.de/files/25796577/Manual.doc.html"]http://rapidshare.de/files/25796577/Manual.doc.html
[/URL]
I will also post here to guide you for the modem settings.

By the way where are you located in India and who is your ISP?
You can also PM me this information.

kagashe

---

### Post by kagashe on 2006-07-14
Hi Dinesh,

I hope you are using this modem in Windows. When it is active in windows type the following in the browser:
[http://192.168.1.1/]("http://192.168.1.1/")

You should get a pop up screen (disable pop ups if required) asking for username and password. Enter "admin" in both fields (These are default username and password. It will work if default settings have not been changed, otherwise, enter the password which was set up earlier).

The first screen will give following information:
> Device Info
 
Board ID: 	XXXXXX-XX-XX
Software Version ID: 	V8.4.01.01
Firmware Version: 	3.00L.03.A2pB017l.d15h
Bootloader (CFE) Version: 	1.0.37-0.7
 
LAN IP Address: 	192.168.1.1
MAC Address: 	XX-XX-XX-XX-XX
Default Gateway: 	XX.XXX.XX.XXX
Primary DNS Server: 	XXX.XX.XXX.XX
Secondary DNS Server: 	XXX.XX.XXX.XX
You can compare the Firmware Version, Bootloader Version and tell me if it is different from above.

Click on DSL Status on left side menu bar. You will get the following:
> DSL Status

Status 	SHOWTIME 
Mode 	G.DMT 
Type 	Fast 
 
  	Downstream 	Upstream
Rate (Kbps) 	288  	256 
SNR Margin (dB) 	30.3  	24.0 
Attenuation (dB) 	29.5  	17.5 
Output Power (dBm) 	3.8  	0.2 
Super Frames 	56929  	56927 
Super Frame Errors 	0  	0 

Please post here if your settings are different.

Click on WAN. You will get the following:
> Wide Area Network (WAN) Setup

Choose Add, Edit, or Remove to configure WAN interfaces.
Choose Save/Reboot to apply the changes and reboot the system.

VPI/VCI 	Service 	Protocol 	State 	Status 	IP Address 	Remove 	Edit
0/32 	pppoe_0_32_1 	PPPoE 	Enabled 	Up 	XX.XXX.XX.XX 		

Please post here if your VPI/VCI settings are different or you don't see "PPPoE" enabled on this screen.

Click on LAN. You will get the following:
> Lan Setup

You must reboot the router to make the new configuration effective of this page.


IP Address: 192.168.1.1
Subnet Mask:255.255.255.0


DHCP Server
  Disable
  Enable
       Start IP Address: 192.168.1.2	
       End IP Address: 	192.168.1.254
       Leased Time(hour): 24
Please post here if DHCP is disabled in your case.

Click on DSL Settings. You will get the following:
> DSL Settings

    Select the modulation below.    (Notice: If you don't understand parameter below, please keep defalut settings.)


  	  	G.Dmt Enabled 	  	  	 
  	  	G.lite Enabled 	  	  	 
  	  	T1.413 Enabled 	  	  	 
  	
  	  	ADSL2 Enabled 	  	Bitswap Enabled 	 
  	  	AnnexL Enabled 	  	SRA Enabled 	 
 	 	ADSL2+ Enabled	 	 	 
  	  	AnnexM DISABLED 	  	
Please tell me which boxes have check marks in the above settings.

After getting your current settings I can tell you what is happening in your case.

kagashe

---

### Post by srinig on 2006-07-14
> **drsdinesh said:**
> hi,
i'm a newbie to linux. installed ubuntu 6.06. have a broadband connection using UTStarcom UT-300R2 ADSL Modem - through the ethernet port. my system is a AMD64 3500+ on ASUS motherboard.
although the pppoeconf has installed, no net connection is available. am absolutely lost. could you tell me how to connect to the net after a fresh install?

Hi Dinesh,

If you are living in India and if you are using dataone, you may want to have a look at [this guide]("http://www.calcuttatelephones.com/dataoneinstall/bb006.html").

Open System->Administration->Networking and go to the properties of ethernet connection. Check 'Enable this connection', choose Static IP address for configuration and fill out the other details as given in the above mentioned page. After this open 192.168.1.1 in your browser and follow the subsequent instructions in that page. 

This way, you don't need pppoeconfig or rppppoe. Just switch on your modem to connect and switch off to disconnect! Hope this helps.

~Srini.

---

### Post by drsdinesh on 2006-07-15
hi Kagashe,
  thanks again. i really wonder how you guys can keep replying so fast. but i'm sorry that you lost me totally there! did try playing around with the modem settings... none of the outputs seemed close to what you've put up. i even tried srinig's suggestion. all to no avail. ubuntu remains steadfast in denying me access to the net. :(
  thanks for the manual copy.
  by the way, i'm from Tamilnadu. my service provider is BSNL.
  i appreciate all the help,
Dinesh.

---

### Post by drsdinesh on 2006-07-15
hi srini,
  thanks for your suggestion. didn't work for me though.
  i'm ready to give trying to access the net from ubuntu. though haven't stopped dreaming of doing the same sometime in the future when i have more time to devote to linux.
  thanks again,

Dinesh.

---

### Post by mips on 2006-07-15
For BSNL India users:

[http://blog.taragana.com/wp-content/upload/bb7.swf](http://blog.taragana.com/wp-content/upload/bb7.swf)

Configure your router as per the above guide then use DHCP in Ubuntu to get your IP settings or do a static IP config in Ubuntu.

---

### Post by drsdinesh on 2006-07-17
:D 
hi guys,
 thanks to mips there, finally connectec to the net via ubuntu in static IP config. can't get DHCP to work though. why do i want it??
  most of the websites don't open when i type it in the address bar. DNS problem?
  in that case, how do i solve it?
ecstatically yours,
dinesh.

---

### Post by mips on 2006-07-17
manually configure your isp's dns servers int the /etc/resolv.conf file.

Also disable IPv6 might help.

---

### Post by anurag_gupta on 2006-09-14
is there anyway that i could use the modem via the USB port? i thinkthe vendor has provided with the usb driver src.?????????????

---

### Post by kagashe on 2006-09-14
> **anurag_gupta said:**
> is there anyway that i could use the modem via the USB port? i thinkthe vendor has provided with the usb driver src.?????????????
It is working on USB port as well as Ethernet port. You don't require any of the vendor's driver since the modem UTStarcom UT-300R2U gets connected to internet just by switching it on (even when your PC is yet to be switched on). If you connect through USB the required USB driver is automatically loaded by the Linux Kernel and a new eth port (eth1 or eth2) appears on your PC.

Hope it helps.

kagashe

---

### Post by anurag_gupta on 2006-09-23
hi there
thanz for ur reply but nothing happened on connecting the modem via usb but i noticed dat there's a new port sit0. what is this?

---

### Post by ajinkyakulkarni87 on 2007-10-24
How to connect same modem in Ubuntu 7.10. Even when modem is switched on it is not get detected! Any suggestion?

---

### Post by nathan23 on 2008-02-06
hey
iv done ma settings on the modem.. the problem im havin is im nt gettin download speeds on torrent.. d download speeds frm sites go2 200 but frm torrents it doesnt cross 30.. any idea wat the problem might be??

---

