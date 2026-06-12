---
title: "intrepid pppoe problem"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by madmax1735 on 2008-12-29
hey i am having problem connecting to internet............. my internet stops working even though ppp0 shows connected in ifconfig.

only problem i could figure out is in plog: heres my sudo plog output:

max@alienware:~$ sudo plog
[sudo] password for max: 
Dec 30 09:09:27 alienware pppd[17610]: replacing old default route to eth0 [192.168.1.1]
Dec 30 09:09:27 alienware pppd[17610]: Cannot determine ethernet address for proxy ARP
Dec 30 09:09:27 alienware pppd[17610]: local  IP address 59.93.207.188
Dec 30 09:09:27 alienware pppd[17610]: remote IP address 59.93.192.1
Dec 30 09:09:27 alienware pppd[17610]: primary   DNS address 218.248.240.179
Dec 30 09:09:27 alienware pppd[17610]: secondary DNS address 218.248.240.79

also i figured that thrs something wrong in syslog aswell

Dec 30 09:09:21 alienware pppd[17608]: Plugin rp-pppoe.so loaded.
Dec 30 09:09:21 alienware pppd[17610]: pppd 2.4.4 started by root, uid 0
Dec 30 09:09:21 alienware pppd[17610]: PPP session is 3835
Dec 30 09:09:21 alienware pppd[17610]: Using interface ppp0
Dec 30 09:09:21 alienware pppd[17610]: Connect: ppp0 <--> eth0
Dec 30 09:09:24 alienware pppd[17610]: CHAP authentication succeeded: Authentication success,Welcome!
Dec 30 09:09:24 alienware pppd[17610]: CHAP authentication succeeded
Dec 30 09:09:24 alienware pppd[17610]: peer from calling number 00:E0:FC:46:20:C7 authorized
Dec 30 09:09:27 alienware pppd[17610]: replacing old default route to eth0 [192.168.1.1]
Dec 30 09:09:27 alienware pppd[17610]: Cannot determine ethernet address for proxy ARP
Dec 30 09:09:27 alienware pppd[17610]: local  IP address 59.93.207.188
Dec 30 09:09:27 alienware pppd[17610]: remote IP address 59.93.192.1
Dec 30 09:09:27 alienware pppd[17610]: primary   DNS address 218.248.240.179
Dec 30 09:09:27 alienware pppd[17610]: secondary DNS address 218.248.240.79
Dec 30 09:17:01 alienware /USR/SBIN/CRON[18125]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 09:24:16 alienware dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 192.168.1.1 port 67
Dec 30 09:24:16 alienware dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Dec 30 09:24:16 alienware dhclient: bound to 192.168.1.2 -- renewal in 1545 seconds.
Dec 30 09:27:55 alienware pppd[17610]: Terminating on signal 15
Dec 30 09:27:55 alienware pppd[17610]: Connect time 18.5 minutes.
Dec 30 09:27:55 alienware pppd[17610]: Sent 709521 bytes, received 1348422 bytes.
Dec 30 09:27:55 alienware pppd[17610]: restoring old default route to eth0 [192.168.1.1]
Dec 30 09:27:55 alienware pppd[17610]: Connection terminated.
Dec 30 09:27:55 alienware pppd[17610]: Exit.
Dec 30 09:28:01 alienware pppd[18962]: Plugin rp-pppoe.so loaded.
Dec 30 09:28:01 alienware pppd[18964]: pppd 2.4.4 started by root, uid 0
Dec 30 09:28:01 alienware pppd[18964]: PPP session is 1885
Dec 30 09:28:01 alienware pppd[18964]: Using interface ppp0
Dec 30 09:28:01 alienware pppd[18964]: Connect: ppp0 <--> eth0
Dec 30 09:28:04 alienware pppd[18964]: CHAP authentication succeeded: Authentication success,Welcome!
Dec 30 09:28:04 alienware pppd[18964]: CHAP authentication succeeded
Dec 30 09:28:04 alienware pppd[18964]: peer from calling number 00:E0:FC:46:20:C7 authorized
Dec 30 09:28:04 alienware pppd[18964]: replacing old default route to eth0 [192.168.1.1]
Dec 30 09:28:04 alienware pppd[18964]: Cannot determine ethernet address for proxy ARP
Dec 30 09:28:04 alienware pppd[18964]: local  IP address 59.93.194.212
Dec 30 09:28:04 alienware pppd[18964]: remote IP address 59.93.192.1
Dec 30 09:28:04 alienware pppd[18964]: primary   DNS address 218.248.240.179
Dec 30 09:28:04 alienware pppd[18964]: secondary DNS address 218.248.240.79
Dec 30 09:41:34 alienware -- MARK --
Dec 30 09:50:01 alienware dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 192.168.1.1 port 67
Dec 30 09:50:01 alienware dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Dec 30 09:50:01 alienware dhclient: bound to 192.168.1.2 -- renewal in 1629 seconds.
Dec 30 09:53:57 alienware kernel: [166373.005467] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 30 09:53:57 alienware kernel: [166373.005506] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec 30 09:53:57 alienware kernel: [166373.005510]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec 30 09:53:57 alienware kernel: [166373.005515]          res 58/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Dec 30 09:53:57 alienware kernel: [166373.005527] ata2.00: status: { DRDY DRQ }
Dec 30 09:53:57 alienware kernel: [166373.005581] ata2: soft resetting link
Dec 30 09:53:58 alienware kernel: [166373.233758] ata2.00: configured for UDMA/33
Dec 30 09:53:58 alienware kernel: [166373.233796] ata2: EH complete
Dec 30 09:57:59 alienware pppd[18964]: Terminating on signal 15
Dec 30 09:57:59 alienware pppd[18964]: Connect time 30.0 minutes.
Dec 30 09:57:59 alienware pppd[18964]: Sent 833862 bytes, received 1546850 bytes.
Dec 30 09:57:59 alienware pppd[18964]: restoring old default route to eth0 [192.168.1.1]
Dec 30 09:57:59 alienware pppd[18964]: Connection terminated.
Dec 30 09:57:59 alienware pppd[18964]: Exit.
Dec 30 09:58:17 alienware pppd[20880]: Plugin rp-pppoe.so loaded.
Dec 30 09:58:17 alienware pppd[20882]: pppd 2.4.4 started by root, uid 0
Dec 30 09:58:17 alienware pppd[20882]: PPP session is 10353
Dec 30 09:58:17 alienware pppd[20882]: Using interface ppp0
Dec 30 09:58:17 alienware pppd[20882]: Connect: ppp0 <--> eth0
Dec 30 09:58:17 alienware pppd[20882]: CHAP authentication succeeded: Authentication success,Welcome!
Dec 30 09:58:17 alienware pppd[20882]: CHAP authentication succeeded
Dec 30 09:58:17 alienware pppd[20882]: peer from calling number 00:E0:FC:46:20:C7 authorized
Dec 30 09:58:17 alienware pppd[20882]: replacing old default route to eth0 [192.168.1.1]
Dec 30 09:58:17 alienware pppd[20882]: Cannot determine ethernet address for proxy ARP
Dec 30 09:58:17 alienware pppd[20882]: local  IP address 59.93.223.14
Dec 30 09:58:17 alienware pppd[20882]: remote IP address 59.93.192.1
Dec 30 09:58:17 alienware pppd[20882]: primary   DNS address 218.248.240.179
Dec 30 09:58:17 alienware pppd[20882]: secondary DNS address 218.248.240.79


the weird thing is that i never gave it a command to get ipadd from dhcp around 9:50 . i dont know why this is happening is the error in plog cause of the problem???

help??

thnx

---

### Post by madmax1735 on 2008-12-30
hummm............. can no one figure it out???

lill help???

---

### Post by madmax1735 on 2008-12-30
well i changed the default ip lease period  on the modem....... it seems to b working fine foe quite some time now.......... could that have been the cause of the problem????

---

