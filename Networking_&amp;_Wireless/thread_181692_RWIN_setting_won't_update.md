---
title: "RWIN setting won't update"
date: 2006-05-24
forum: Networking &amp; Wireless
---

### Post by isotonic on 2006-05-24
I've followed this tutorial to update my rwin settings:
[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

Here are my config settings from /etc/sysctl.conf:

dev.cdrom.lock=0
vm.swappiness=10

# Tweaks for faster broadband...
net.core.rmem_default = 253088
net.core.rmem_max = 253088
net.core.wmem_default = 253088
net.core.wmem_max = 253088
net.ipv4.tcp_wmem = 253088 253088 253088
net.ipv4.tcp_rmem = 253088 253088 253088
#net.ipv4.tcp_mem = 253088 253088 253088
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

So after issuing the update command:
sysctl -p

I go to speedguide.net and check my settings:

[SIZE=2]
[/SIZE]                                                                                     [SIZE=2][**MTU**]("http://ubuntuforums.org/javascript%3Cb%3E%3C/b%3E://%20What%20is%20mtu%20?") = **1478**
[/SIZE][SIZE=2][COLOR=#ff0000]MTU is not fully optimized for broadband. Consider increasing your MTU to 1500 for better throughput. If you are using a router, it could be limiting your MTU regardless of Registry settings.

[/COLOR][/SIZE]                                                                                     [SIZE=2][**MSS**]("http://ubuntuforums.org/javascript%3Cb%3E%3C/b%3E://%20What%20is%20mss%20?") = **1438**
Maximum useful data in each packet = 1426, which is less than MSS because of Timestamps, or other TCP/IP options used.
[/SIZE]
                                                               [SIZE=2]**[[B]Default TCP Receive Window (RWIN)**]("http://ubuntuforums.org/javascript%3Cb%3E%3C/b%3E://%20What%20is%20RWIN%20?") = **5840** 

RWIN Scaling (RFC1323) = 4 bits                          (scale factor of 8)
                        Unscaled TCP Receive Window = 365 

RWIN seems to be set to a very small number. If you're on a broadband connection, consider using a larger value.[/B]

[B]For optimum performance, consider changing RWIN to a multiple of MSS.
Other RWIN values that might work well with your current MTU/MSS: [/B][/SIZE]                         [SIZE=2][COLOR=#228b22]
506176 (MSS x 44 * scale factor of 8)
253088 (MSS x 44 * scale factor of 4)
126544 (MSS x 44 * scale factor of 2)
 63272 (MSS x 44)[/COLOR][/SIZE][SIZE=2]
[/SIZE]                                                                                                            [SIZE=2]
[**bandwidth**** * delay product**]("http://www.speedguide.net/faq_in_q.php?category=89&qid=185") (Note this is not a speed test):

 Your TCP Window limits you to: 233.6 kbps (29.2 KBytes/s) @ 200ms
 Your TCP Window limits you to: 93.44 kbps (11.68 KBytes/s) @ 500ms
Consider increasing your RWIN value to optimize TCP/IP for broadband.
[/SIZE]                                                                                     [SIZE=2][B]
[MTU Discovery (RFC1191)]("http://ubuntuforums.org/javascript%3Cb%3E%3C/b%3E://%20What%20is%20MTU%20?") = ON[/B]
[/SIZE]                                                                                     [SIZE=2]
[**Time to live left**]("http://ubuntuforums.org/javascript%3Cb%3E%3C/b%3E://%20What%20is%20TTL%20?") = **58 hops**
[/SIZE][SIZE=2][COLOR=#22b200]TTL value is ok.[/COLOR][/SIZE][SIZE=2]
[/SIZE]                                                                                     [SIZE=2][B]
[Timestamps (RFC1323)]("http://ubuntuforums.org/javascript%3Cb%3E%3C/b%3E://%20What%20is%20Timestamps%20?") = ON[/B]
*Note: Timestamps add 12 bytes to the TCP header of each packet, reducing the space available for useful data.*[/SIZE]                                                                                     [SIZE=2][B]

[Selective Acknowledgements (RFC2018)]("http://ubuntuforums.org/javascript%3Cb%3E%3C/b%3E://%20What%20is%20SackOpts%20?") = ON[/B]
[/SIZE]                                                                                     [SIZE=2][B]
[IP type of service field (RFC1349)]("http://www.speedguide.net/tcpoptimizer.php#advanced_qos")[/B] = **00000000 (0)**[/SIZE]

---

### Post by isotonic on 2006-05-24
Now most of the flag settings at the end seems to work but the Rwin section (in bold) always shows a small value for Rwin so that my transfer rates are also slow.

I currently have upgraded to 2Mb ADSL so I should obtain better speeds than this...

PLEASE HELP!!! :confused:

---

