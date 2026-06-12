---
title: "Netgear WG511 Version 3 Made in China is Working"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by Verbious on 2005-12-15
I will try to explain what I did the best I can.  I am usually not good at documenting things, but I paid attention this time:  ;) The HowTos were a HUGE help and I thank those that have written them for their time.  Perhaps I can give back a little.

I have a Toshiba Satellite 1800-S253, PIII 850 192 Mb RAM, 15 GB HD.  I have wanted to go wireless in my house for some time.  I have recently discovered Ubuntu and love it.  I just got a super cheap wireless router from CompUSA for $19.99 after the rebates.

Back to the card.  I have the dreaded WG511 Version 3.  I decided to follow the instructions here:  [https://wiki.ubuntu.com//SetupNdiswrapperHowto]("https://wiki.ubuntu.com//SetupNdiswrapperHowto"), but unlike the How-TO, I am using the [COLOR="DarkOrange"]latest Ndiswrapper 1.7[/COLOR].  The instructions tell you to download and compile Ndiswrapper 1.1.  I simply replaced all the 1.1s in the instructions with 1.7s.  I had a problem compiling the driver.  I needed gcc-3.4.  I had to get and install it as well.   [COLOR="Blue"]I executed all of these instructions after I did sudo -s then entered the password.[/COLOR] 

The Netgear WG511 PCMCIA card came with a Windows driver disk.  I used the windows XP driver. 

[COLOR="Red"]Installed drivers:
wg511v2         driver present, hardware present
pat@ubuntu:~$[/COLOR]

The end of the tutorial tells you to go here:  [https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto).  

I followed all the steps down to ping 4.2.2.2 -c 4.  This failed.  I had a green light on the card.  I decided to check the WiFiRadar.  It showed my router.  i created a profile called "default".  I then used network-admin to deactivate my eth0.  I also activated my wlan0.  I was not able to connect.  I tried to go back to the WiFi Radar, but things started to lock up at this point.  I also tried to go back to network-admin, but it wasn't running too good.  I had a command line open so I tried to get the ifconfig -a, but it sorta stalled.  I finally just closed everything and tried to shut down.  The darned laptop wouldn't even shut off.  I held the power button in to shut it down and then turned it back on.  After the laptop rebooted, I let it stabilize for a minute or two, and then deactivated the eth0 in network-admin.  After I did this, I tried to connect to the web and lo and behold!  I was connected via the Netgear WG511 Version3 Made in China PCMCIA card.  What a pleasant surprise.

Here is my iwconfig:

pat@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11b  ESSID:"default"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0E:2E:6D:DD:6D
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-70 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Here are a few lines from dmesg:

[4294739.600000] ndiswrapper: using irq 11
[4294739.663000] ndiswrapper (IoCreateUnprotectedSymbolicLink:744): --UNIMPLEMENTED--
[4294740.667000] wlan0: vendor: ''
[4294740.667000] wlan0: ndiswrapper ethernet device 00:0f:b5:8a:ad:22 using driver wg511v2, 11AB:1FAA:1385:4E00.5.conf
[4294740.667000] wlan0: encryption modes supported: WEP; TKIP with WPA

I am going to play with this a bit more, shut it down, take out the card, try to break it, etc.  Just to see if it will still work.  I am hoping that I did it right this time.  

If anyone wants to see the output of anything just let me know.  I am still a bit of a linux Noob, but if you give me the exact command, I can get you the data.

The HowTos were extremely helpful and I recommend following them very closely.

---

### Post by Verbious on 2005-12-15
I did a connection test at [www.bandwidthplace.com](www.bandwidthplace.com) and these are the results:

Personal test results
Speed

1.1 megabits per second
Communications 1.1 megabits per second
Storage 133.4 kilobytes per second
1MB file download 7.7 seconds
Subjective rating Good
Explain results

Info
Date & time Thursday, December 15, 8:10PM*
Test type IDT4 Free
Connection type ADSL
Region Pennsylvania
Data size 1024KB
IP address 141.*.*.*
Provider
* EST (-0500)

Here is on from Verizon: 

Connection Types
Bits
Sec

Your Speed in
  	KBits/Sec 	KBytes/Sec
Ethernet 	10M 
& UP 	  	 	 
  	8M 	  	 	 
  	6M 	  	 	 
  	4M 	  	 	 
  	2M 	  	2659.6Kbits	332.4KBytes
T1 	1.5M 	  	 	 
  	1M 	  	 	 
  	768K 	  	 	 
  	512K 	  	 	 
  	256K 	  	 	 
2x ISDN 	128K 	  	 	 
1x ISDN 	64.0K 	  	 	 
  	56.0K 	  	 	 
v.90 Modem 	41.8K 	  	 	 
Analog Modem 	33.6K 	  	 	 
 
Download Size: 	[500]KBytes
Downloaded in: 	[1.504]Seconds

vzSpeedTest v2.4

I normally connect @ >2.5 Mbps on my wired LAN.  The fact that this is working is totally awesome!!!!

---

### Post by Verbious on 2005-12-16
the Netgear PCMCIA WG511 has been working well.  No problems with lockups or other issues.  

I did have a problem with WiFi Radar.  The system would act strange, and sluggish, after I tried to use it to set up a profile for the wireless router.  

I have had no problem getting on several wireless networks just by using the System> Administration > Networking tool.  I click on Activate then check the properties.  The networks are available in a drop down menu.  I simply pick the one I want to connect to and have had great success.

The card has been detected everytime I've shut down, restarted, and used the Networking Application.

I had previously tried to configure a CompUSA brand PCMCIA card with a Realtek 8185 Chipset with no success.

---

