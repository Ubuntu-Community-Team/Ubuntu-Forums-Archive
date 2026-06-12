---
title: "really slow downloads in intrepid ibex"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Jara04 on 2009-02-25
Hello:

I'm sorry to post another thread regarding the same issue, but i haven't been able to speed-up my downloads (ftp, http and torrents) i've tried several guides to improve this, but none seems to work.

I'd appreciate the help, here is some info about my config

My board is an ASUS M2NPV-VM and the lan card is a d-link dwa-510

javier@javier-desktop:~$ sysctl -a 2> /dev/null | grep -iE "_mem |_rmem|_wmem"
net.ipv4.tcp_mem = 187000	187000	187000
net.ipv4.tcp_wmem = 4096	30000	187000
net.ipv4.tcp_rmem = 4096	30000	187000
net.ipv4.udp_mem = 292128	389504	584256
net.ipv4.udp_rmem_min = 4096
net.ipv4.udp_wmem_min = 4096

iwconfig

wlan0     IEEE 802.11bg  ESSID:"19769173"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:46:C7:AD:86   
          Bit Rate=54 Mb/s   Tx-Power=18 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=94/100  Signal level:-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've tried this guide and seemed to have done the best improvement
[http://ubuntuforums.org/showthread.php?t=872346&highlight=mtu+internet](http://ubuntuforums.org/showthread.php?t=872346&highlight=mtu+internet)

here's my /etc/sysctl.conf

#internet
net.ipv4.tcp_mem=187000 187000 187000
net.ipv4.tcp_wmem=4096 30000 187000
net.ipv4.tcp_rmem=4096 30000 187000
net.ipv4.tcp_no_metrics_save=1
net.ipv4.tcp_moderate_rcvbuf=1

Thanks for reading

Regards

---

