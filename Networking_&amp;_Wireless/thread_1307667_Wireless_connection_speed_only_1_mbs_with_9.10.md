---
title: "Wireless connection speed only 1 mb/s with 9.10"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by AdamRG on 2009-10-31
A question from a complete newbie.  

I have a USB wireless adapter that worked fine with 9.04.  I upgraded to 9.10, and while the wireless connection is working, the registered speed is only 1 mb/s.  Another interesting note is the signal strength seems to be about only at about 50% most of the time as well.  With 9.04 the signal strength was at near 100% as my machine is close to the wireless router.  

I appreciate any help that you could provide.

---

### Post by s.dalas on 2009-10-31
> **AdamRG said:**
> A question from a complete newbie.  

I have a USB wireless adapter that worked fine with 9.04.  I upgraded to 9.10, and while the wireless connection is working, the registered speed is only 1 mb/s.  Another interesting note is the signal strength seems to be about only at about 50% most of the time as well.  With 9.04 the signal strength was at near 100% as my machine is close to the wireless router.  

I appreciate any help that you could provide.

When you say registered speed you mean the speed that you can get or the speed that is written if you click connection info? also can you give the output of ```
lsusb
``` (write this in terminal and post here the result)

---

### Post by AdamRG on 2009-10-31
That is the info provided when I look at the connection info.  Here is the output you requested.

Thanks!

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 002: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by s.dalas on 2009-10-31
it can see your adaptor... can you also post the output of ```
iwconfig
```?

---

### Post by AdamRG on 2009-10-31
Here it is.

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"2WIRE887"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:B3:44:B7:71   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/100  Signal level=46/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by s.dalas on 2009-10-31
i suppose you need to have 54mb/s as bit rate.
so try this out. 
-disconnect from the network
-open a terminal and type ```
sudo iwconfig wlan0 rate 54M
```
-close terminal and reconnect. 

Try this and please let us know the results so finally fix it ;)

---

### Post by AdamRG on 2009-10-31
That worked!  One other question as I lose this setting when I reboot.  Where would I configure this?

---

### Post by s.dalas on 2009-10-31
When you say it worked, you mean you have better connection or just the registered says 54mb/s?? cause what we need is to have better connection...
for the configuration question i don't know... sorry but i am looking for it

---

### Post by s.dalas on 2009-10-31
Other solution i can give you as i see around is to use NDISwrapper. a lot of people say that solved their problem.
[http://en.wikipedia.org/wiki/NdisWrapper]("http://en.wikipedia.org/wiki/NdisWrapper")

---

### Post by AdamRG on 2009-10-31
That fixed the problem as my connection speed is now where it should be.  Thanks!

---

### Post by s.dalas on 2009-10-31
Please specify which of these two methods solved your problem and then mark this thread as SOLVED if you are ok wirh everything!

---

### Post by AdamRG on 2009-10-31
It was resolved by changing the rate to 54mb/s.  I am not sure if it is display issue with the configuration, but I am now getting the proper speed speed on the network and out to the internet.

---

### Post by s.dalas on 2009-10-31
I am asking this cause some people notice that the display may change, but the real speed is not the proper one.

Glad to help you to solve this! ;)

Please mark the thread as ***[COLOR="DarkOrange"]SOLVED[/COLOR]***.

---

### Post by puppy on 2010-01-03
This is NOT solved.

For me, as soon as I reboot my wireless connection using zd1211rw goes back to 1mbps - I have to reissue the command "sudo iwconfig wlan1 rate 54M" everytime I log in.

Can anyone advise a solution using a script or whatever to resolve this issue, or link to another thread where a permanent solution is proposed (cos I can't find one...)

Thanks

---

