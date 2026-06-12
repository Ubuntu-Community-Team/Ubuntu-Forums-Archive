---
title: "connect bsnl huawei ec 325 cdma modem in ubuntu 8.04"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by rajusenthi on 2009-02-15
I purchased the Huawei EC325 modem from BSNL WLL which uses a USB cable to connect to the PC. My inital reaction was since it was a USB connection and was using a custom software to connect to the net, it would not be possible to connect to the net in Linux using this modem.After searching various linux forums I 've reached the stage of modem inialized.Finaly the message from Terminal is
ATZ 
OK 
--> Modem initialized. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
CONNECT 230400 
--> Carrier detected.  Starting PPP immediately. 
--> Starting pppd at Sat Feb 14 23:13:45 2009 
--> Pid of pppd: 6067 
--> Using interface ppp0 
--> pppd: `?[06][08]`?[06][08]??[06][08] 
--> pppd: `?[06][08]`?[06][08]??[06][08] 
--> pppd: `?[06][08]`?[06][08]??[06][08] 
--> pppd: `?[06][08]`?[06][08]??[06][08] 
--> pppd: `?[06][08]`?[06][08]??[06][08] 
--> Disconnecting at Sat Feb 14 23:13:52 2009 
--> The PPP daemon has died: Authentication error. 
--> We failed to authenticate ourselves to the peer. 
--> Maybe bad account or password? (exit code = 19) 
--> man pppd explains pppd error codes in more detail. 
--> I guess that's it for now, exiting 
--> The PPP daemon has died. (exit code = 19) 
what is the problem? please help me. :KS

---

### Post by x33a on 2009-02-15
the problem seems to be of authentication.

have you entered the correct account information in your modem settings.

---

