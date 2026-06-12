---
title: "DNS in 9.10 only appears randomly"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by wanglemoose on 2009-12-10
hi all, 
        don´t know if any one else has had this problem, but when I connect my usb modem (MF636BP through bigpond) the network manager always connects and the modem always 
gets the blue flashing light (to say its connected) but when i go to go online it tells me that the server cannot be found. I disconnect, unplug, re-plug and re-connect and it all works fine. this is random tho sometimes you have to unplug umpteen times. 

Now the only difference i can find is in the network manager connection information as such:
                                 [SIZE=2]
[/SIZE]
[SIZE=2]Telstra connection (default)[/SIZE]
 

 [SIZE=2]Interface:        GSM (ttyUSB2)[/SIZE]
 [SIZE=2]Hardware Address:[/SIZE]
 [SIZE=2]Driver:            generic[/SIZE]
 [SIZE=2]Speed:            Unknown[/SIZE]
 [SIZE=2]Security:        Unknown[/SIZE]
 

 [SIZE=2]IP Address:        121.219.171.69[/SIZE]
 [SIZE=2]Broadcast Address:    121.219.171.69[/SIZE]
 [SIZE=2]Subnet Mask:        255.255.255.255[/SIZE]
 [SIZE=2]Default Route:                  10.64.64.64[/SIZE]
 
                                 connected with blue light flashing, no internet
note NO primary or secondary dns


and


                                  [SIZE=2]Telstra connection (default)[/SIZE]
 

 [SIZE=2]Interface:        GSM (ttyUSB2)[/SIZE]
 [SIZE=2]Hardware Address:[/SIZE]
 [SIZE=2]Driver:            generic[/SIZE]
 [SIZE=2]Speed:            Unknown[/SIZE]
 [SIZE=2]Security:        Unknown[/SIZE]
 

 [SIZE=2]IP Address:        58.170.67.220[/SIZE]
 [SIZE=2]Broadcast Address:    58.170.67.220[/SIZE]
 [SIZE=2]Subnet Mask:        255.255.255.255[/SIZE]
 [SIZE=2]Default Route:        10.64.64.64[/SIZE]
 [SIZE=2]Primary DNS:        61.9.211.1[/SIZE]
 [SIZE=2]Secondary DNS:        61.9.242.33[/SIZE]


[SIZE=2]The DNS change every time they appear and so does the IP and broadcast address. No matter what the DNS numbers are if they are there i can go online no probs.[/SIZE]


[SIZE=2]Is there any way to to set a static dns or something so that it is there every time i connect the modem.
[/SIZE]


[SIZE=2]
[/SIZE]

---

### Post by wanglemoose on 2009-12-10
hi all, 
        don´t know if any one else has had this problem, but when I connect my usb modem (MF636BP through bigpond) the network manager always connects and the modem always 
gets the blue flashing light (to say its connected) but when i go to go online it tells me that the server cannot be found. I disconnect, unplug, re-plug and re-connect and it all works fine. this is random tho sometimes you have to unplug umpteen times. 

Now the only difference i can find is in the network manager connection information as such:
                                 [SIZE=2]
[/SIZE]
[SIZE=2]Telstra connection (default)[/SIZE]
 

 [SIZE=2]Interface:        GSM (ttyUSB2)[/SIZE]
 [SIZE=2]Hardware Address:[/SIZE]
 [SIZE=2]Driver:            generic[/SIZE]
 [SIZE=2]Speed:            Unknown[/SIZE]
 [SIZE=2]Security:        Unknown[/SIZE]
 

 [SIZE=2]IP Address:        121.219.171.69[/SIZE]
 [SIZE=2]Broadcast Address:    121.219.171.69[/SIZE]
 [SIZE=2]Subnet Mask:        255.255.255.255[/SIZE]
 [SIZE=2]Default Route:                  10.64.64.64[/SIZE]
 
                                 connected with blue light flashing, no internet
note NO primary or secondary dns


and


                                  [SIZE=2]Telstra connection (default)[/SIZE]
 

 [SIZE=2]Interface:        GSM (ttyUSB2)[/SIZE]
 [SIZE=2]Hardware Address:[/SIZE]
 [SIZE=2]Driver:            generic[/SIZE]
 [SIZE=2]Speed:            Unknown[/SIZE]
 [SIZE=2]Security:        Unknown[/SIZE]
 

 [SIZE=2]IP Address:        58.170.67.220[/SIZE]
 [SIZE=2]Broadcast Address:    58.170.67.220[/SIZE]
 [SIZE=2]Subnet Mask:        255.255.255.255[/SIZE]
 [SIZE=2]Default Route:        10.64.64.64[/SIZE]
 [SIZE=2]Primary DNS:        61.9.211.1[/SIZE]
 [SIZE=2]Secondary DNS:        61.9.242.33[/SIZE]


[SIZE=2]The DNS change every time they appear and so does the IP and broadcast address. No matter what the DNS numbers are if they are there i can go online no probs.[/SIZE]


[SIZE=2]Is there any way to to set a static dns or something so that it is there every time i connect the modem.

When the modem works i have normal speeds (up to 400Kb/s) and no dropouts its just a pain in the *** getting it to run.

[/SIZE]


[SIZE=2]
[/SIZE]

---

### Post by wanglemoose on 2009-12-10
[SIZE=2]hi all, 
don´t know if any one else has had this problem, but when I connect my usb modem
(MF636BP through bigpond) the network manager always connects and the modem always 
gets the blue flashing light (to say its connected) but when i go to go online it tells me that the server cannot be found. I disconnect, unplug, re-plug and re-connect and it all works fine. this is random tho sometimes you have to unplug umpteen times. 

Now the only difference i can find is in the network manager connection information as such:


Telstra connection (default)


Interface: GSM (ttyUSB2)
Hardware Address:
Driver: generic
Speed: Unknown
Security: Unknown


IP Address: 121.219.171.69
Broadcast Address: 121.219.171.69
Subnet Mask: 255.255.255.255
Default Route: 10.64.64.64

connected with blue light flashing, no internet
note NO primary or secondary dns


and


Telstra connection (default)


Interface: GSM (ttyUSB2)
Hardware Address:
Driver: generic
Speed: Unknown
Security: Unknown


IP Address: 58.170.67.220
Broadcast Address: 58.170.67.220
Subnet Mask: 255.255.255.255
Default Route: 10.64.64.64
Primary DNS: 61.9.211.1
Secondary DNS: 61.9.242.33


The DNS change every time they appear and so does the IP and broadcast address. No matter what the DNS numbers are if they are there i can go online no probs.


Is there any way to to set a static dns or something so that it is there every time i connect the modem.[/SIZE]

---

### Post by wanglemoose on 2009-12-10
[SIZE=2]hi all, 
don´t know if any one else has had this problem, but when I connect my usb modem
(MF636BP through bigpond) the network manager always connects and the modem always 
gets the blue flashing light (to say its connected) but when i go to go online it tells me that the server cannot be found. I disconnect, unplug, re-plug and re-connect and it all works fine. this is random tho sometimes you have to unplug umpteen times. 

Now the only difference i can find is in the network manager connection information as such:


Telstra connection (default)


Interface: GSM (ttyUSB2)
Hardware Address:
Driver: generic
Speed: Unknown
Security: Unknown


IP Address: 121.219.171.69
Broadcast Address: 121.219.171.69
Subnet Mask: 255.255.255.255
Default Route: 10.64.64.64

connected with blue light flashing, no internet
note NO primary or secondary dns


and


Telstra connection (default)


Interface: GSM (ttyUSB2)
Hardware Address:
Driver: generic
Speed: Unknown
Security: Unknown


IP Address: 58.170.67.220
Broadcast Address: 58.170.67.220
Subnet Mask: 255.255.255.255
Default Route: 10.64.64.64
Primary DNS: 61.9.211.1
Secondary DNS: 61.9.242.33


The DNS change every time they appear and so does the IP and broadcast address. No matter what the DNS numbers are if they are there i can go online no probs.


Is there any way to to set a static dns or something so that it is there every time i connect the modem.[/SIZE]

---

### Post by Iowan on 2009-12-10
If you use DHCP for IP address, you can edit /etc/dhcp3/dhclient.conf and modify the "prepend" line to include your DNS server(s).

---

### Post by cariboo on 2009-12-10
Please don't create multiple threads on the same subject. I have merged your 4 threads.

---

