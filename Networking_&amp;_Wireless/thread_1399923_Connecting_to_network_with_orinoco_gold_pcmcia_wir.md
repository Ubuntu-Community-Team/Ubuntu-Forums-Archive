---
title: "Connecting to network with orinoco gold pcmcia wireless card"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by Mates87 on 2010-02-06
Hi,
 

 I´m a newbie in Ubuntu. I´m working with this systém just about a year and I have got only basic knowledge about Ubuntu. I´m trying to run my Orinoco Gold PCMCIA wireless card by Lucent Technologies with Hermes I chipset on Ubuntu 9.10. But my card doesnt see any network in my neighborhood. Lights on card are blinking so I think that card is not broken. In network manager I can see my eth3 interface which is orinoco but it is inactive.
 

 At home I´m using network with WPA2. I know that my Orinoco doesnt support WPA2. But in my neighborhood are few networks which are open for public or which using WEP. In my machine which is Lenovo 3000 n100 is integrated card by intel and it works perfectly. But i like to learn and I like to know how stuff works so thats the reason why I trying to run my Orinoco. Last year I was working for few days with Backtrack 3. There was similar problem to get connect with my integrated card. I solve this problem with manualy set wpa_supplicatnt. But now in ubuntu and orinoco it seems its not working. I thing i remember that this orinoco was actualy work in Backtrack.
 

 I spend a lot of time find the way how to make it work on Ubuntu. Browsing forums and etc. Trying a lot of „howto“ like this one [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) but nothing works.I will be very glad if somebody of you will rediect me to some helpfull thread which solves this problem or just give me some advice.
 Maybe it is just one command in terminal that i missing.
 

                         
 Here are some outputs:
 

 Orinoco is eth3.
 

 laptop:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wmaster0  no wireless extensions. 
  
 wlan0     IEEE 802.11abg  ESSID:"MaKo"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:4F:62:12:C0:23    
           Bit Rate=48 Mb/s   Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr: off   Fragment thr: off 
           Power Management: off 
           Link Quality=61/70  Signal level=-49 dBm  Noise level=-127 dBm 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon: 0 
  
 pan0      no wireless extensions. 
  
 eth3      IEEE 802.11b  Nickname:"HERMES I" 
           Mode:Managed  Frequency:2.457 GHz  Access Point: None    
           Bit Rate:11 Mb/s   Sensitivity:1/3   
           Retry limit:4   RTS thr: off   Fragment thr: off 
           Power Management: off 
           Link Quality=0/92  Signal level=-93 dBm  Noise level=-122 dBm 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag: 0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon: 0 
  

 

 laptop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWadr 00:0f:b0:d2:af:0c   
           AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ MULTICAST  MTU:1500  Metrika:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame: 0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier: 0 
           kolizí: 0 délka odchozí fronty:1000  
           P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B) 
           P&#345;erušení:21 Vstupn&#283;/Výstupní port:0x2000  
  
 eth3      Link encap:Ethernet  HWadr 00:02:2d:73:b4:11   
           inet adr:169.254.214.165  Všesm&#283;r:169.254.255.255  Maska:255.255.0.0 
           inet6-adr: fe80::202:2dff:fe73:b411/64 Rozsah:Linka 
           AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ MULTICAST  MTU:1500  Metrika:1 
           RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0 
           TX packets: 0 errors:2 dropped:2 overruns: 0 carrier: 0 
           kolizí:0 délka odchozí fronty:1000  
           P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B) 
           P&#345;erušení:3 Vstupn&#283;/Výstupní port:0x2100  
  
 lo        Link encap:Místní smy&#269;ka   
           inet adr:127.0.0.1  Maska:255.0.0.0 
           inet6-adr: ::1/128 Rozsah: Po&#269;íta&#269; 
           AKTIVOVÁNO SMY&#268;KA B&#282;ŽÍ  MTU:16436  Metrika:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           kolizí:0 délka odchozí fronty:0  
           P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B) 
  
 wlan0     Link encap:Ethernet  HWadr 00:1b:77:02:5c:78   
           inet adr:192.168.0.200  Všesm&#283;r:192.168.0.255  Maska:255.255.255.0 
           inet6-adr: fe80::21b:77ff:fe02:5c78/64 Rozsah:Linka 
           AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;ŽÍ MULTICAST  MTU:1500  Metrika:1 
           RX packets:17457 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:17221 errors:0 dropped:0 overruns:0 carrier:0 
           kolizí:0 délka odchozí fronty:1000  
           P&#345;ijato bajt&#367;: 14000002 (14.0 MB) Odesláno bajt&#367;: 3374091 (3.3 MB) 
  
 wmaster0  Link encap:NEZNÁM  HWadr 00-1B-77-02-5C-78-30-32-00-00-00-00-00-00-00-00   
           AKTIVOVÁNO B&#282;ŽÍ  MTU:0  Metrika:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           kolizí:0 délka odchozí fronty:1000  
            P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B) 
 

 

 home/mates# lsmod | grep orinoco 
 

 orinoco_cs             13312  1  
 orinoco                63600  1 orinoco_cs 
 pcmcia                 36808  1 orinoco_cs 
 pcmcia_core            36528  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic 
 

 I appreciate any helpful posts.
 P.S. Excuse my english please, its not my born laguage.            
 

                                                Martin

---

