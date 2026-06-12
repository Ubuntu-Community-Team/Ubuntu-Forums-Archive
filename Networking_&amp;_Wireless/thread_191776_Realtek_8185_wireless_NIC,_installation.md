---
title: "Realtek 8185 wireless NIC, installation"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by SharpBlade on 2006-06-08
Hello.
It is my first message on this forum and I hope somebody has come across the issue I have experienced.  I am mainly a Windows user (laptop preinstalled OS). I hope I am hereby providing enough information to understand the issue and that somebody more experienced could help me.  I have just installed Ubuntu Dapper Drake on a crawling/crashing desktop that used to run Windows Millennium.  This desktop was wirelessly connected to my ADSL router at home.  The installation went very well: scanner Epson 1240U, printer Epson Color 460, sound card, dial-up modem, USB MP3 player, DVD player, CD-writer... everything was recognised and correctly installed by Ubuntu.... This is quite a success as now I can startup/shutdown the computer without the computer crashing...  But the wireless NIC, a **Realtek 8185** sold as a **Dick Smith XH8343** here in New Zealand, has not been recognised: I am eager to get that working so that I can use the printer from my laptop through the network (This is the challenge after the wireless NIC installation ;-)).

I went to the Ubuntu wiki and thought I would try to use the Windows driver for the card and wrap it in ndiswrapper.  I followed the instructions at the following link:
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto")

1.) I successfully installed the Debian packages ndiswrapper-utils and ndisgtk and I have now the following extra application: *System->Administration->Windows wireless drivers*

2.)From the Windows wireless drivers applications, I installed the Windows driver, a file called *net8185.inf*.  I got the Windows driver from the following link [http://www.dse.co.nz/cgi-bin/dse.filereader?4488af2b0730a3762741c0a87f990728+EN/catalogs/SUPXH8343]("http://www.dse.co.nz/cgi-bin/dse.filereader?4488af2b0730a3762741c0a87f990728+EN/catalogs/SUPXH8343")

3.)I ran the command *ndiswrapper -l* to check that the ndis driver and the hardware are present.

4.)I configured the network settings:
ssid name
WEP key

5.)Following the instructions I then ran:
  *sudo depmod -a*
  *sudo modprobe ndiswrapper*

6.)I ran *tail /var/log/messages* and could not see any error.

7.)When I run ifconfig or iwconfig, the interface name *wlan0* and all the associated parameters are well displayed.

8.)When I run *sudo ifup wlan0*, I can see requests being sent to my ADSL router but error messages are displayed:
***No DHCPOFFERS received. No working leases in persistent database - sleeping.***
Please note my ADSL router is setup as a DHCP server and has WEP encryption enabled.  I wirelessly access this router and the internet without any problem from my Windows laptop.  In my router status page, I can see my Windows laptop as being *authorized* whereas the computer including the Realtek PCI card has the *associated* status.

9.)I can not ping (Error ***network unreachable***).

S1.)The RealTek 8185 **Windows driver** can possibly not successfully be wrapped into ndis?
S2.)Is there a **native linux driver** for the Realtek 8185?  Can I use the one available from the Realteck website or is it specific to Fedora: 
[http://www.realtek.com.tw/]("http://www.realtek.com.tw/")
S3.)Is this **open source linux driver **the one to use even though it has not been refreshed for a while:
[http://sourceforge.net/projects/rtl8180-sa2400]("http://sourceforge.net/projects/rtl8180-sa2400")

Which solution actually works, S1, S2 or S3?  What is then the actual way to implement the solution?  Is there a positive outcome?  I have spent a couple of hours on S1 as well as on the internet looking for clues to get around this issue without success.

Thks in advance,

---

### Post by Ivan Matveich on 2006-06-08
You might try disabling the encryption.

---

### Post by Ivan Matveich on 2006-06-08
You might try disabling the encryption. Or work around the problem by running an ethernet cable.

---

### Post by SharpBlade on 2006-06-08
I am investigating further the issues with the installation of the Realtek 8185 wireless NIC PCI card.

So, I disabled the encryption on wlan0 and configured it first as a DHCP address and later as a static IP address.  I configure wlan0 using the application *System->Administration->Windows wireless drivers* available since I installed the Debian packages *ndiswrapper-utils* and *ndisgtk*.  After each change of configuration I reactivate the wlan0 interface.  Also, after each configuration change I check that the changes are well saved into file */etc/network/interfaces*.

File */etc/network/interfaces* includes the following lines(DHCP config):
-----------------
[B]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto eth3
iface eth3 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid MY_SSID

auto wlan0
[/B]
-----------------

_SCENARIO 1_
After the **DHCP configuration** of wlan0 is applied and wlan0 is restarted using command *sudo ifup wlan0*:
-Messages in */var/log/messages* notify me that the association with the wireless Access Point is successful and that G rates are in use.  This is good :) 
-Several **DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval x** are displayed and eventually **NO DHCPOFFERS received**.  This is bad :mad:  Of course I can not ping the wireless access point: I get the error message **connect: Network is unreachable**.
 

_SCENARIO 2_
After the **static IP configuration** of wlan0 is applied and wlan0 is restarted using command *sudo ifup wlan0*:
-Messages in */var/log/messages*  notify me that the association with the wireless access point is successful and that G rates are in use.  This is good :) 
-Trying to ping the wireless access point returns several **Destination Host Unreachable**.  This is as bad as in SCENARIO 1 :mad: 


I am starting to be very accustomed to the various network commands and I have the feeling I am not far from having a working solution BUT it still does not run ](*,) 

Any idea out there?

---

### Post by SharpBlade on 2006-06-08
I could possibly try to wrap into ndiswrapper (please note I installed the latest stable version of the ndiswrapper utils Deb package [version 1.8]) the Windows driver from the Realtek 8185 website (version 04/13/2006, 5.1060.0413.2006) instead of the one I downloaded from the Dick Smith website (version 11/18/2004, 5.102.1118.2004, this is quite old)?

Will try and will report whether or not this has improved anything...

---

### Post by SharpBlade on 2006-06-09
I installed the most up-to-date Windows driver from Realtek(see previous post regarding actual version) in ndiswrapper ( version 1.8 ) but the outcome is exactly the same as before.  No improvement whatsoever and same symptoms as in my previous posts....  Is there a way out? ... I am starting to get desperate.
Things look quite advanced as the Realtek 8185 is seen as being associated in the status page of my ADSL router.  There is a missing part in the jigsaw and I do not know what.  Does anybody have any hint on what should be the next step to tackle this issue? :-k

---

### Post by SharpBlade on 2006-06-10
I eventually got my Realtek 8185 working :D 

Call me stupid...the problem was that I did not save my ADSL router configuration and it was still configured to use WPA encryption when I was assuming there was no encryption!

Now, I enabled the WEP encryption and it is working perfectissimo :mrgreen: 
So if somebody out there has a Realtek 8185 wireless NIC... It works in Ubuntu Dapper Drake using ndiswrapper and the windows driver from the Realtek website.

---

### Post by infomar on 2008-02-10
I can confirm this. The realtek 8185 works. Just a couple of "funny" things:

[LIST]
[*]I had to replace the included network driver for the ndiswrapper one (I got one using the installation CD for windows. I followed [this ]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/") guide.
[*]For an unknown reason, the network card was "stuck" on the last configuration even after reset my computer. I had to shut it down and turn it again... I spend some bad time trying to figure out this.
[/LIST]

Regards!

---

