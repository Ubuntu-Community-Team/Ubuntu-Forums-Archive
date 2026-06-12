---
title: "iwlagn AGN5300 hangs when sending &gt; 1k"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by danfan46 on 2009-11-13
Hi.
I got a new laptop in June  where the wireless card (Intel PRO 5300AGN) worked fairly well, disregarding "beacon losses".  Sometime in September, presumably after some automatic update I began to have problems with some websites, and  sending mails larger than 1K. I first put the blame on my D-Link router but could eventually pinpoint to the functionality of the wireless. 

[LIST]
[*]Wlan works OK on three other computers.
[*]Using eth0 cable works OK on this computer
[/LIST]
When sending a mail with attachment from Evolution I get the message[COLOR=Red] [COLOR=Black]
"[/COLOR]Data command failed: Connection reset by peer: mail not sent[/COLOR]"
Sending a small mail < 1k works OK.
Some websites, hotmail.com etc  (probably using large cookies) just hang. Eventually I get a message from Firefox saying "The connection was reset"
I see nothing of interest in the logs but lines like:
"[COLOR=Blue]Nov  9 15:57:49 ubuntu kernel: [  344.473804] Inbound IN=wlan0 OUT=MAC=00:16xxxxxxxxxxxxxx.. SRC=81.230.168.75 DST=192.168.0.50 LEN=576 TOS=0x00 PREC=0xC0 TTL=64 ID=19214 PROTO=ICMP TYPE=3 CODE=4 [SRC=192.168.0.50 DST=65.54.165.177 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=43858 DF PROTO=TCP SPT=41861 DPT=80 WINDOW=5840 RES=0x00 ACK URGP=0 ] MTU=1492[/COLOR]" 

I have Googled for similar problems, but found nothing like it.
I'm at a loss.

/dg

---

### Post by danfan46 on 2009-11-13
I just tried to send a megabyte file thru sftp from the problem machine to another local machine, and that works OK.
/dg

---

### Post by danfan46 on 2009-11-21
Hi!
 I swapped my Intel wifi card for a Realtec card, hoping that would help. It did not!
It is not hardware or wifi driver that causes the problem.
Do [COLOR=Blue]_YOU_[/COLOR] have any idea where to search? 
Can't send mail's larger than 1 K. Tried both Evolution  and Thunderbird. 
Can't access some websites like [www.hotmail.com](www.hotmail.com) and some pages just  hangs/time out  even in Ubuntu Forum
/DG

---

