---
title: "have dialup issues"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by linuxnewbee1 on 2010-10-03
hello can u please help me make dial up work properly i have a conext hsf modem it has the drivers to go with it i am using ubuntu 10.4lts and it dials up but comes up with connected but not a second later it says disconnected due to pap and chap premisson denied can u help

---

### Post by dineshs on 2010-10-04
[This]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9") guide may help> If you lose the connection a short time after connecting (30 sec - 3 min), you might need to edit options for pppd:

gksudo gedit /etc/ppp/options

Find lcp-echo-interval30 and lcp-echo-failure4. Comment out these options by adding a '#' at the start of these lines, eg. # lcp-echo-interval30 and # lcp-echo-failure4. 
Are you using wvdial?Can you post the error message.Have you tried *sudo wvdial*?

---

### Post by linuxnewbee1 on 2010-10-04
i think that problems is solved just need to know now if there is anyway of speeding up the connection the speed is running between 1.3 and highest is about 2.7 - 3.0 KB/s

---

### Post by klemes on 2010-10-04
Not much you can do in that area.Maybe activate modem and/or software compression for your connection.(I do not know the exact commands for your modem but you can look it up in your AT commands index in your modem's manual).One indirect way of coping this is downloading and installing Opera.It has a 'turbo' function specifically designed for slow connections.Give it a try.:popcorn:

---

