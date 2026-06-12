---
title: "Mobile Broadband Slow Connection (SmartBro/Globe Tattoo)"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by carlexpc on 2010-04-22
Hi everyone,

I have successfully configured my Mobile Broadband (USB 3G/HSDPA modem) via NetworkManager. Both SmartBro & Globe Tattoo, (these are both providers in the Philippines) connect successfully to their respective networks but my observation is the connection is slow if we are to benchmark these connections running on M$ Windows.

Is there any tweak available to enable the connection speed to improve? I know that there are other factors that affect the connection such as the signal and PC speed. I am currently using a brand new Intel Atom netbook.  Any help is greatly appreciated.

---

### Post by alexfish on 2010-04-22
To monitor network speed you can install netspeed as this will monitor different connections  , can also be added to your panel
 

 To monitor ppp then you could install pppstatus , this will show speed and packets etc + packet loss it also has a config file so you can monitor costs and possibly check email
 

 as for signal strength I resort to using a serial terminal such as minicom, when configured to the correct port send the command AT+CSQ this should  return two values see below
 

 

 **+CSQ: <rssi>,<ber>**
where
<rssi> is the Received Signal Strength Indicator
0 = 113 dBm or less
1 = 111 dBm
2 to 30 = 109 to 53 dBm
31 = 51 dBm or greater
<ber> is the Bit Error Rate, in percent (99 is not known or not detectable)
 

 if the signal strength is below 10 then GPRS connections are unreliable. Values around 15 are good, 25 is excellent. The screen shot below is a serial port terminal available in Gambas examples . So could be adapted to use the timer function or a loop , then report the signal strength at regular intervals.
 

 There is VMC (Vodafone Mobile Connect) from Betavine should work with huawei devices ,and possibly others .However there maybe problems getting this to work Depending on version of Ubuntu,
 

 As regards to the connection speed, this is mainly governed by your ISP,or how busy the severs are.
 However some ISP have slow servers. To overcome this try setting the Ipv4 in NM to use Automatic(PPP) address only and enter the address or addresses of an open nic , some use the servers used by google, in EU there is a one in Germany (Primary DNS 217.115.138.24
Alternative DNS 83.217.93.246, this proved to be very fast . For United States this came up on a search.
 


 [http://www.opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns](http://www.opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns)


added for SMS texts you could also try wammu


regards
alexfish

---

