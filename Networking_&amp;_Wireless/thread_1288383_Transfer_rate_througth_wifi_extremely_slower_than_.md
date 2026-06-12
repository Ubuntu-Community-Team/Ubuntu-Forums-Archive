---
title: "Transfer rate througth wifi extremely slower than vista"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by rmoutinho on 2009-10-11
Hi,

   I have a pavilion with windows vista and ubuntu 8.04LTS installed. This notebook connects to a linksys w160n runnning dd-wrt and there's a desktop running ubuntu connected to this linksys through ethernet cable.

When I transfer files from ubuntu on laptop using scp to the desktop the transfer rates go as low as 50KB/s (or even slower). Doing the same test on windows vista I get 1MB/s. Anyone knows what might be wrong here ?

Most relevant info here (I think):

renato@laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"casa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:E5:59:E5:BC   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=78/100  Signal level=-55 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

renato@laptop:~$ lspci | grep BCM
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)


As suggested on a sticky topic, i'm attaching a file with lots of info for debugging. Thanks in advance,

Renato Moutinho

---

### Post by houstonbofh on 2009-10-11
> **rmoutinho said:**
> When I transfer files from ubuntu on laptop using scp to the desktop the transfer rates go as low as 50KB/s (or even slower). Doing the same test on windows vista I get 1MB/s. Anyone knows what might be wrong here ?

Most relevant info here (I think):

renato@laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"casa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:E5:59:E5:BC   
          **Bit Rate=1 Mb/s**   Tx-Power=16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=78/100  Signal level=-55 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

There are known issues with some of these cards setting the bit rate two low, and disassociating and reconnecting often.  One 'fix' is ndis wrapper, and another is setting the rate manually.  A quick search on 'BCM4312 slow' will find lots of people with this issues, and lot of fixes, depending on your comfort level.  I would point you at a fix, but I don't really like any of them myself yet.

---

### Post by rmoutinho on 2009-10-11
Just to close the topic: my understanding is that this is a problem with the current driver version.. Is that right ? If that's the case, do you know whether there's an open bug to fix that ?

Regards,

Renato Moutinho

---

### Post by houstonbofh on 2009-10-12
Yes, but it does not seem to be making much progress.  Cross your fingers!

---

