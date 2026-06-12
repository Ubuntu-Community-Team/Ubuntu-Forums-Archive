---
title: "Wireless Internet connection stops after downloading"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by crazy_23_1999_04290 on 2013-04-02
running ubuntu 12.10 usb wireless card is N300. Internet works fine when just surffing the web but once i start to download anything ie bitorrents and even updates the N300 stops working. I still have a connection on the top right hand side but no internet activity at all. First i thought maybe the card was junk so i went out to got a N600 still the samething. Then i tried with a windows laptop the connection was great even downloaded a movie 1gb in 12 minutes with no problem. Any ideas????

---

### Post by chili555 on 2013-04-02
I wonder if there are any clues in the logs. Try to download a big file and trigger the behavior and then run and post:```
cat /var/log/syslog | grep -e ndis -e wlan | tail -n20
```

---

### Post by crazy_23_1999_04290 on 2013-04-02
danny@danny-CM1745:~$ cat /var/log/syslog | grep -e ndis -e wlan | tail -n20
Apr  2 13:07:58 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 192.168.1.1 port 67
Apr  2 13:07:58 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed renew -> renew

---

### Post by chili555 on 2013-04-03
Nothing of interest here. syslog periodically archives itself and starts a new file. Let's try again and check both the current and archived syslog. Try to download a big file and trigger the behavior and then run and post:```
cat /var/log/syslog | grep -e ndis -e wlan | tail -n20
cat /var/log/syslog[COLOR="#FF0000"].1[/COLOR] | grep -e ndis -e wlan | tail -n20
```

---

### Post by crazy_23_1999_04290 on 2013-04-03
danny@danny-CM1745:~$ cat /var/log/syslog | grep -e ndis -e wlan | tail -n20
Apr  3 15:45:53 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  3 15:45:53 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr  3 15:45:53 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  3 15:45:53 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  3 15:45:53 danny-CM1745 dhclient: Listening on LPF/wlan0/10:0d:7f:37:c2:07
Apr  3 15:45:53 danny-CM1745 dhclient: Sending on   LPF/wlan0/10:0d:7f:37:c2:07
Apr  3 15:45:53 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  3 15:45:56 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  3 15:45:56 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  3 15:45:56 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  3 15:45:56 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr  3 15:45:57 danny-CM1745 NetworkManager[736]: <warn> (wlan0): failed to change interface MTU
Apr  3 15:45:57 danny-CM1745 NetworkManager[736]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  3 15:45:57 danny-CM1745 NetworkManager[736]: <info> Policy set 'NETGEAR13' (wlan0) as default for IPv4 routing and DNS.
Apr  3 15:45:57 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) successful, device activated.
Apr  3 15:45:57 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr  3 15:46:14 danny-CM1745 NetworkManager[736]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr  3 15:46:14 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr  3 15:46:14 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr  3 15:46:14 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
danny@danny-CM1745:~$ cat /var/log/syslog.1 | grep -e ndis -e wlan | tail -n20
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  2 20:20:16 danny-CM1745 dhclient: Listening on LPF/wlan0/10:0d:7f:37:c2:07
Apr  2 20:20:16 danny-CM1745 dhclient: Sending on   LPF/wlan0/10:0d:7f:37:c2:07
Apr  2 20:20:16 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  2 20:20:19 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <warn> (wlan0): failed to change interface MTU
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Policy set 'NETGEAR13' (wlan0) as default for IPv4 routing and DNS.
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) successful, device activated.
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
danny@danny-CM1745:~$

---

### Post by chili555 on 2013-04-03
I see two things, one not very suspicious and the other even less so.> Apr 3 15:46:14 danny-CM1745 NetworkManager[736]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 3 15:46:14 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 3 15:46:14 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 3 15:46:14 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.You might set Network Manager to ignore IPv6 and see if that has any effect. Please see attached.

Second, I see this:> Apr 2 20:20:20 danny-CM1745 NetworkManager[736]: <warn> (wlan0): failed to change interface MTUDo you have some different MTU set in Network Manager or elsewhere? In almost every case, the default works well.

---

### Post by crazy_23_1999_04290 on 2013-04-03
Its still doing the samething i copy and paste the same command you gave me in post #4 

danny@danny-CM1745:~$ cat /var/log/syslog | grep -e ndis -e wlan | tail -n20
Apr  3 16:57:47 danny-CM1745 wpa_supplicant[1137]: wlan0: CTRL-EVENT-CONNECTED - Connection to 20:e5:2a:17:0f:5c completed (auth) [id=0 id_str=]
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NETGEAR13'.
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  3 16:57:47 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  3 16:57:47 danny-CM1745 dhclient: Listening on LPF/wlan0/10:0d:7f:37:c2:07
Apr  3 16:57:47 danny-CM1745 dhclient: Sending on   LPF/wlan0/10:0d:7f:37:c2:07
Apr  3 16:57:47 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  3 16:57:50 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  3 16:57:50 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  3 16:57:50 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  3 16:57:50 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr  3 16:57:51 danny-CM1745 NetworkManager[736]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  3 16:57:51 danny-CM1745 NetworkManager[736]: <info> Policy set 'NETGEAR13' (wlan0) as default for IPv4 routing and DNS.
Apr  3 16:57:51 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) successful, device activated.
Apr  3 16:57:51 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
danny@danny-CM1745:~$ cat /var/log/syslog.1 | grep -e ndis -e wlan | tail -n20
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  2 20:20:16 danny-CM1745 dhclient: Listening on LPF/wlan0/10:0d:7f:37:c2:07
Apr  2 20:20:16 danny-CM1745 dhclient: Sending on   LPF/wlan0/10:0d:7f:37:c2:07
Apr  2 20:20:16 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  2 20:20:19 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <warn> (wlan0): failed to change interface MTU
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Policy set 'NETGEAR13' (wlan0) as default for IPv4 routing and DNS.
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) successful, device activated.
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.


IPv6 is set to ignore
MTU is set to automatic

---

### Post by chili555 on 2013-04-04
> Apr 2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
[COLOR="#FF0000"]Apr 2 20:20:39[/COLOR] danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

Please check the timestamps. Those are the exact same messages as we saw before. After you made the changes, did you try a big download or do anything to trigger the behavior? Please try a reboot.

---

### Post by crazy_23_1999_04290 on 2013-04-04
This is what  did. Check setting as to post #6 settings correct, restart. Try to download to trigger the behavior got the behavior again. Then back to post #4 put in terminal got it as listed below
danny@danny-CM1745:~$ cat /var/log/syslog | grep -e ndis -e wlan | tail -n20
Apr  4 15:23:59 danny-CM1745 NetworkManager[1025]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  4 15:23:59 danny-CM1745 NetworkManager[1025]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  4 15:23:59 danny-CM1745 NetworkManager[1025]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  4 15:23:59 danny-CM1745 dhclient: Listening on LPF/wlan0/10:0d:7f:37:c2:07
Apr  4 15:23:59 danny-CM1745 dhclient: Sending on   LPF/wlan0/10:0d:7f:37:c2:07
Apr  4 15:23:59 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  4 15:24:01 danny-CM1745 avahi-daemon[1046]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::120d:7fff:fe37:c207.
Apr  4 15:24:01 danny-CM1745 avahi-daemon[1046]: New relevant interface wlan0.IPv6 for mDNS.
Apr  4 15:24:01 danny-CM1745 avahi-daemon[1046]: Registering new address record for fe80::120d:7fff:fe37:c207 on wlan0.*.
Apr  4 15:24:02 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  4 15:24:02 danny-CM1745 NetworkManager[1025]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  4 15:24:02 danny-CM1745 NetworkManager[1025]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  4 15:24:02 danny-CM1745 NetworkManager[1025]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr  4 15:24:02 danny-CM1745 avahi-daemon[1046]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.5.
Apr  4 15:24:02 danny-CM1745 avahi-daemon[1046]: New relevant interface wlan0.IPv4 for mDNS.
Apr  4 15:24:02 danny-CM1745 avahi-daemon[1046]: Registering new address record for 192.168.1.5 on wlan0.IPv4.
Apr  4 15:24:03 danny-CM1745 NetworkManager[1025]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  4 15:24:03 danny-CM1745 NetworkManager[1025]: <info> Policy set 'NETGEAR13' (wlan0) as default for IPv4 routing and DNS.
Apr  4 15:24:03 danny-CM1745 NetworkManager[1025]: <info> Activation (wlan0) successful, device activated.
Apr  4 15:24:03 danny-CM1745 NetworkManager[1025]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
danny@danny-CM1745:~$ cat /var/log/syslog.1 | grep -e ndis -e wlan | tail -n20
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  2 20:20:16 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  2 20:20:16 danny-CM1745 dhclient: Listening on LPF/wlan0/10:0d:7f:37:c2:07
Apr  2 20:20:16 danny-CM1745 dhclient: Sending on   LPF/wlan0/10:0d:7f:37:c2:07
Apr  2 20:20:16 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  2 20:20:19 danny-CM1745 dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr  2 20:20:19 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <warn> (wlan0): failed to change interface MTU
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Policy set 'NETGEAR13' (wlan0) as default for IPv4 routing and DNS.
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) successful, device activated.
Apr  2 20:20:20 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr  2 20:20:39 danny-CM1745 NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

---

### Post by chili555 on 2013-04-07
These are the same dates and timestamps as you posted in two previous posts. May we conclude that when you provoked the behavior again *AFTER* that, that there was no message at all in the logs?? None?  :confused:

---

