---
title: "VPN problem, Kubuntu 10.10, 64 Bit"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by cwill on 2011-04-15
Hi folks,

I have a problem with establishing a VPN connection, it's driving me nuts already.
No matter what I try, which packages I (re)install, or how many configuration settings i change.. the result is always the same (see syslog at the end of this post).

On the same machine, but on a different harddrive, I have installed Windows 7. The VPN connection works without any problems on this system.

As I could see I am not the only one facing this problem. But none of the posted solutions could help me to get this work.
I played already with KNetworkManager, NetworkManagerm, KVpn and so on. Further I re-installed each VPN- and network packages multiple times (eg KNetworkManager, NetworkManager, network-manager-pptp, pptp-linux). Further I tested almost every possible VPN configuration (PAP,CHAP,MSCHAP(v2),EAP,MPPE, stateful encryption, no password, BSD compression)...

My syslog is as follow:

```
Apr 13 18:15:02 defcon-inc pppd[3721]: LCP: timeout sending Config-Requests
Apr 13 18:15:02 defcon-inc pppd[3721]: Connection terminated.
Apr 13 18:15:02 defcon-inc pptp[3731]: anon log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Apr 13 18:15:02 defcon-inc pptp[3731]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Apr 13 18:15:02 defcon-inc pptp[3731]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr 13 18:15:02 defcon-inc avahi-daemon[1100]: Withdrawing workstation service for ppp0.
Apr 13 18:15:02 defcon-inc NetworkManager[1137]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 13 18:15:03 defcon-inc pppd[3774]: pppd 2.4.5 started by root, uid 0
Apr 13 18:15:03 defcon-inc NetworkManager[1137]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 13 18:15:03 defcon-inc NetworkManager[1137]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr 13 18:15:03 defcon-inc modem-manager: (net/ppp0): could not get port's parent device
Apr 13 18:15:03 defcon-inc pppd[3774]: Using interface ppp0
Apr 13 18:15:03 defcon-inc pppd[3774]: Connect: ppp0 <--> /dev/pts/2
Apr 13 18:15:03 defcon-inc pptp[3776]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr 13 18:15:03 defcon-inc pptp[3784]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Apr 13 18:15:03 defcon-inc pptp[3784]: anon log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Apr 13 18:15:03 defcon-inc pptp[3784]: anon log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr 13 18:15:04 defcon-inc pptp[3784]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Apr 13 18:15:27 defcon-inc NetworkManager[1137]: <info> Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Apr 13 18:15:27 defcon-inc NetworkManager[1137]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 3786
Apr 13 18:15:27 defcon-inc NetworkManager[1137]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' appeared, activating connections
Apr 13 18:15:27 defcon-inc NetworkManager[1137]: <info> VPN plugin state changed: 3
Apr 13 18:15:27 defcon-inc NetworkManager[1137]: <info> VPN connection 'Liberty VPN' (Connect) reply received.
Apr 13 18:15:27 defcon-inc pppd[3787]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr 13 18:15:27 defcon-inc pppd[3787]: pppd 2.4.5 started by root, uid 0
Apr 13 18:15:27 defcon-inc NetworkManager[1137]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Apr 13 18:15:27 defcon-inc NetworkManager[1137]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Apr 13 18:15:27 defcon-inc pppd[3787]: Using interface ppp1
Apr 13 18:15:27 defcon-inc pppd[3787]: Connect: ppp1 <--> /dev/pts/5
Apr 13 18:15:27 defcon-inc modem-manager: (net/ppp1): could not get port's parent device
Apr 13 18:15:27 defcon-inc pptp[3790]: nm-pptp-service-3786 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr 13 18:15:27 defcon-inc pptp[3784]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Apr 13 18:15:34 defcon-inc pppd[3774]: LCP: timeout sending Config-Requests
Apr 13 18:15:34 defcon-inc pppd[3774]: Connection terminated.
Apr 13 18:15:34 defcon-inc pptp[3784]: anon log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Apr 13 18:15:34 defcon-inc pptp[3784]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Apr 13 18:15:34 defcon-inc pptp[3784]: anon log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Apr 13 18:15:34 defcon-inc pptp[3784]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Apr 13 18:15:34 defcon-inc pptp[3784]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr 13 18:15:34 defcon-inc pppd[3787]: Modem hangup
Apr 13 18:15:34 defcon-inc pppd[3787]: Connection terminated.
Apr 13 18:15:34 defcon-inc NetworkManager[1137]: <warn> VPN plugin failed: 1
```
 
Does anyone here has a clue for me? I am really almost close to surrender..

PS: If I forgot to post any important information just tell me.

Thanks,
Christopher

---

### Post by kir77 on 2011-06-07
Similar problem with 10.10 x64, but alittle different logs:

Jun  5 14:35:21 Ksidorin pppd[5574]: Connect: ppp1 <--> /dev/pts/2
Jun  5 14:35:29 Ksidorin pppd[5574]: CHAP authentication succeeded
Jun  5 14:35:29 Ksidorin pppd[5574]: MPPE 128-bit stateless compression enabled
Jun  5 14:35:30 Ksidorin pppd[5574]: local  IP address xxx.xxx.xxx.xxx
Jun  5 14:35:30 Ksidorin pppd[5574]: remote IP address yyy.yyy.yyy.yyy
Jun  5 14:35:30 Ksidorin pppd[5574]: primary   DNS address zzz.zzz.zzz.zzz
Jun  5 14:35:30 Ksidorin pppd[5574]: secondary DNS address aaa.aaa.aaa.aaa
Jun  5 14:36:10 Ksidorin pppd[5574]: Terminating on signal 15
Jun  5 14:36:10 Ksidorin pppd[5574]: Connect time 0.7 minutes.
Jun  5 14:36:10 Ksidorin pppd[5574]: Sent 0 bytes, received 0 bytes.
Jun  5 14:36:10 Ksidorin pppd[5574]: Child process /usr/sbin/pptp z-company.tunnel.net --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-5572 (pid 5576) terminated with signal 15
Jun  5 14:36:10 Ksidorin pppd[5574]: Connection terminated.
Jun  5 14:36:10 Ksidorin pppd[5574]: Exit.

so connection suceeded, but nothing sent.
Reason was ufw settings (iptables in ubuntu)
short ufw service stopping helps to check if it is the reason (sudo service ufw stop).

---

### Post by novinick on 2011-06-07
I think linux is not supporting all mppe or mppc or  only ono of two is supported.
  Was droped in late 2.6.15 due to standard-conflicting implementation.

It  was working on 2.4.30 i think

this is for second post, in first post is completly different issue :)

---

