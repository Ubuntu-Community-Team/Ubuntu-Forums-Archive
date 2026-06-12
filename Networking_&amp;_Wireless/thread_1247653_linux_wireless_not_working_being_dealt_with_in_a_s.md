---
title: "linux wireless not working being dealt with in a strange manner"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by wjamoore on 2009-08-23
Hi,

I have the wireless issues that seem to be running for years and it strikes me that this is being tackled from the wrong perspective.

Some points to note:


[LIST]
[*]I cannot get associated with my wireless router (Netgear WRN2000).  I see the essid if I do iwconfig, but Access Point is "not associated" always
[/LIST]


[LIST]
[*]I can get onto wireless hotspots without problem (that's a clue)
[/LIST]


[LIST]
[*]I have full signal on wireless (i would hope so at a range of 3 ft)
[/LIST]


[LIST]
[*]I have the famous Atheros chipset and have tried many things (ath5k madwifi, wicd etc etc ) and always I end up at the same result.
[/LIST]


[LIST]
[*]I can see all 13 channel frequencies after adding the EU extra channels.   iwconfig wlan0 channel
[/LIST]


[LIST]
[*]I do notice in resolv.conf that my nameserver vanishes if I try to connect to my wireless router ???  Maybe or maybe not significant
[/LIST]
I have noticed the same exact problem since fiesty and yet each time it is treated as a PC to PC / driver to driver basis, but I also notice the problem for broadcom and atheros and many PC manufacturers, so that's telling me it's nothing to do with the driver or PC as such, but may be something that is enabled/not enabled or conflicting.

I do believe that it is a DHCP issue
Listening on LPF/wlan0/00:19:7e:84:7e:44  
 Sending on   LPF/wlan0/00:19:7e:84:7e:44  
 Sending on   Socket/fallback  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11  
 No DHCPOFFERS received.  
 No working leases in persistent database - sleeping.  
  * Reloading /etc/samba/smb.conf smbd only  
    ...done.  

I never recieve a DHCP offer

So what can be done at a more ubuntu level as opposed to cards and PCs?

Any advice appreciated

Aaron

---

