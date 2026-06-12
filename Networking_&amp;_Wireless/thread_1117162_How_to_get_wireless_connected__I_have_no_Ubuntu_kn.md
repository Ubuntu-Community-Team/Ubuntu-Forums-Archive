---
title: "How to get wireless connected?  I have no Ubuntu knowledge whatsoever."
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by vinay427 on 2009-04-05
Hi.  This is my first post here.  I just installed Ubuntu on a Toshiba laptop and everything went great.  I am trying to get wireless internet to work, but can't.  The laptop has built-in wireless but it broke some time ago so I am trying to use an external USB wireless adaptor.  I know Ubuntu recognizes it because in the internet status menu next to the volume control slider it says:

Wired Network
Auto Ethernet
[B]Wireless Network (Belkin F5D6050 802.11b)
wireless is disabled[/B]
Wireless Network (Intel PRO/Wireless 3945ABG [Golan])
wireless is disabled
VPN Connections>

My common sense tells me I'm supposed to enable the wireless.  I've already made sure the network is broadcasting in 802.11b.  I'm quite tech savvy with things other than Linux.  I have two networks, one with 802.11g/b and WPA2 and the other with 802.11g/b and WEP for older computers.  By the way, I'm using Ubuntu 8.10.  All the choices except the VPN one are grayed out.  If you have any suggestions, please put in it Linux n00b form because, well, I am one. ;)  I'm extremely familiar with Mac and Windows though.

If it makes a difference, I'm installed Ubuntu 8.10 over Vista because the laptop was pretty close to broken anyway, even thought it's only a year old.  I want to use it as a home media server sort of thing.  Does anyone know how to stream iTunes from a Mac to something on Ubuntu?

Thanks a lot in advance!  I really appreciate the help.

chipset: 050d:0050

iwconfig results:
> wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wlan2     IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:43:EB:8D   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by x22 on 2009-04-05
here's what I use to setup my WEP-enabled 802.11b
connection:

ifconfig wlan0 up
iwconfig wlan0 essid chris
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 12345abcde
iwconfig wlan0 key open
dhclient wlan0 

modify to suit local conditions and run as root
or put in yr /etc/rc.local startup file

---

### Post by vinay427 on 2009-04-05
> **x22 said:**
> here's what I use to setup my WEP-enabled 802.11b
connection:

ifconfig wlan0 up
iwconfig wlan0 essid chris
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 12345abcde
iwconfig wlan0 key open
dhclient wlan0 

modify to suit local conditions and run as root
or put in yr /etc/rc.local startup file

Uhh...how do I run as root?  Something in terminal?  What do I modify?   Can you like bold the things I should change?

---

### Post by vinay427 on 2009-04-05
Sorry for the bump but I really need an answer quickly. Thatnk again!

---

### Post by vinay427 on 2009-04-05
So now I got the driver from [here]("http://burnthesorbonne.com/?page_id=38") and unzipped the .exe but can't unzip the .cab files.  It says "sudo: unshield: command not found"  I can't figure out how to install unshield.  Please help!  Thanks.

---

### Post by dukasmc on 2009-04-05
to run as root go into a terminal and type *sudo -i*
this will promt you for the sudo password which is your login password (assuming you are the administor of the computer)
after you enter the password the command line shoud say: root@Computer_Name #
then you can run as root

---

### Post by vinay427 on 2009-04-05
> **vinay427 said:**
> So now I got the driver from [here]("http://burnthesorbonne.com/?page_id=38") and unzipped the .exe but can't unzip the .cab files.  It says "sudo: unshield: command not found"  I can't figure out how to install unshield.  Please help!  Thanks.

Thanks to the poster right before me, it worked great!  But I still am confused about this.

---

### Post by vinay427 on 2009-04-06
So now I found [this thread]("http://ubuntuforums.org/showthread.php?t=169498") that sort of helps.  So should I get an ethernet connection first, then run *sudo apt-get install unshield*?  To extract .cab files, do I also need cabextract?  That is what it said in the other thread.  Please help!  I'm so confused with Ubuntu.

---

### Post by vinay427 on 2009-04-06
I finally figured out how to extract the .cab files.  Now what do I do?  I just have each .cab file in a seperate file on the desktop and the rest of the driver in another folder.  I'm even more confused now!

---

### Post by vinay427 on 2009-04-06
> **vinay427 said:**
> I finally figured out how to extract the .cab files.  Now what do I do?  I just have each .cab file in a seperate file on the desktop and the rest of the driver in another folder.  I'm even more confused now!

Someone please help!  My family is mad at me because I have a Ethernet cable wired through the house until I can get wireless working.

---

### Post by vinay427 on 2009-04-12
Here are the complete instructions.

#
Card: Belkin F5D6050

    *
      Chipset: Atmel at76c503-rfmd
    *
      pciid: 050d:0050
    *
      Driver: Belkin [http://www.belkin.com/support/download/files/F5D6050z.exe](http://www.belkin.com/support/download/files/F5D6050z.exe)
    *
      Other: Download the driver. Extract
      to a new directory using unzip. Extract the CAB files (DATA1.CAB,
      DATA1.HDR, DATA2.CAB) using “unshield x” . cd Drivers/WINXP . edit
      bkusb.in_ and uncomment the CopyFile.XP.Sys section. Run ndiswrapper -i
      bkusb.in_ as root followed by ndiswrapper -m . modprobe ndiswrapper.
      ifdown wlan0. ifup wlan0 and you are there.

---

