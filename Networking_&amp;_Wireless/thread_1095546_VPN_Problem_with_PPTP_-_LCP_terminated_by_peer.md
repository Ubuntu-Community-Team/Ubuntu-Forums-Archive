---
title: "VPN Problem with PPTP - LCP terminated by peer"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by jacob.david on 2009-03-13
I'm trying to connect to my work place VPN and I have installed all the necessary pptp components and configured it. However when I try to start the connection it fails and following is the corresponding log entry from syslog. I have searched the forums and many faced same problem. I tried few options (like removing the LCP etc) that people say fixed the issue but none works for me. Could someone please help me out? I have a Windows XP and Ubuntu 8.10 on the same box and the VPN works fine from Windows XP. 

Mar 14 10:59:58 G3JACK NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Mar 14 10:59:58 G3JACK NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 14959 
Mar 14 10:59:58 G3JACK NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Mar 14 10:59:58 G3JACK NetworkManager: <info>  VPN plugin state changed: 3 
Mar 14 10:59:58 G3JACK NetworkManager: <info>  VPN connection 'SUNGARD' (Connect) reply received. 
Mar 14 10:59:58 G3JACK pppd[14962]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Mar 14 10:59:58 G3JACK pppd[14962]: pppd 2.4.4 started by root, uid 0
Mar 14 10:59:58 G3JACK pppd[14962]: using channel 13
Mar 14 10:59:58 G3JACK pppd[14962]: Using interface ppp0
Mar 14 10:59:58 G3JACK pppd[14962]: Connect: ppp0 <--> /dev/pts/1
Mar 14 10:59:58 G3JACK pptp[14964]: nm-pptp-service-14959 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Mar 14 10:59:58 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Mar 14 10:59:58 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Mar 14 10:59:58 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Mar 14 10:59:59 G3JACK pppd[14962]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xce297760> <pcomp> <accomp>]
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 3031). 
Mar 14 10:59:59 G3JACK pppd[14962]: rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x62406aff> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:c8.00.86.b3.1e.ba.4f.2e.b2.98.42.7c.6d.17.16.dd.00.00.00.00]> < 17 04 02 da>]
Mar 14 10:59:59 G3JACK pppd[14962]: sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 02 da>]
Mar 14 10:59:59 G3JACK pppd[14962]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xce297760> <pcomp> <accomp>]
Mar 14 10:59:59 G3JACK pppd[14962]: rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0x62406aff> <pcomp> <accomp> <endpoint [local:c8.00.86.b3.1e.ba.4f.2e.b2.98.42.7c.6d.17.16.dd.00.00.00.00]>]
Mar 14 10:59:59 G3JACK pppd[14962]: sent [LCP ConfAck id=0x1 <mru 1400> <auth eap> <magic 0x62406aff> <pcomp> <accomp> <endpoint [local:c8.00.86.b3.1e.ba.4f.2e.b2.98.42.7c.6d.17.16.dd.00.00.00.00]>]
Mar 14 10:59:59 G3JACK pppd[14962]: sent [LCP EchoReq id=0x0 magic=0xce297760]
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Mar 14 10:59:59 G3JACK pppd[14962]: rcvd [EAP Request id=0x1a Identity <No message>]
Mar 14 10:59:59 G3JACK pppd[14962]: sent [EAP Response id=0x1a Identity <Name "G3JACK">]
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Mar 14 10:59:59 G3JACK pppd[14962]: rcvd [LCP EchoRep id=0x0 magic=0x62406aff]
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Mar 14 10:59:59 G3JACK pppd[14962]: rcvd [LCP TermReq id=0x3 "b@j\37777777777\000<\37777777715t\000\000\002\37777777663"]
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Mar 14 10:59:59 G3JACK pppd[14962]: LCP terminated by peer (b@jM-^?^@<M-Mt^@^@^BM-3)
Mar 14 10:59:59 G3JACK pppd[14962]: sent [LCP TermAck id=0x3]
Mar 14 10:59:59 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Mar 14 11:00:02 G3JACK pppd[14962]: Connection terminated.
Mar 14 11:00:02 G3JACK NetworkManager: <info>  VPN plugin failed: 1 
Mar 14 11:00:02 G3JACK pptp[14964]: nm-pptp-service-14959 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Mar 14 11:00:02 G3JACK pptp[14964]: nm-pptp-service-14959 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Mar 14 11:00:02 G3JACK pptp[14971]: nm-pptp-service-14959 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Mar 14 11:00:02 G3JACK pptp[14971]: nm-pptp-service-14959 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Mar 14 11:00:02 G3JACK pptp[14971]: nm-pptp-service-14959 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Mar 14 11:00:02 G3JACK NetworkManager: <info>  VPN plugin failed: 1 
Mar 14 11:00:02 G3JACK pppd[14962]: Script /usr/sbin/pptp 61.14.143.132 --nolaunchpppd --logstring nm-pptp-service-14959 finished (pid 14963), status = 0x0
Mar 14 11:00:02 G3JACK pppd[14962]: Modem hangup
Mar 14 11:00:02 G3JACK pppd[14962]: Exit.

---

### Post by jacob.david on 2009-03-15
Could someone please help solving my problem?

---

### Post by sindrit on 2009-03-30
I'm having exactly the same issue, I'll post something if I figure out what's going on.

---

### Post by cbibeep on 2009-04-02
The problem you are experiencing is because of EAP authentication on the remote end, you'll need to pass "refuse-eap" option to pppd.

Unfortunately this option is not available in NetworkManager, we'll need to launch a terminal and execute gconf-editor.

navigate to /system/networking/connections

Here you'll find some numbered folders, these are your connections, try and find the one describing your vpn configuration (it's probably the last one), there you'll find a "vpn" folder, click on it.

Right-click on the right pane and choose "new-key" on the context-menu.

Fill the form as follows:

Name: refuse-eap
Type: string
Value: yes

click "ok" and you're done!

---

### Post by trungd_t on 2009-04-03
cbibeep,

thanks for providing the information. I tried this, and I'm still getting the problem. Any more ideas?

```
Apr  3 15:41:31 guido NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Apr  3 15:41:31 guido NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6406 
Apr  3 15:41:31 guido NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Apr  3 15:41:31 guido pppd[6407]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Apr  3 15:41:31 guido NetworkManager: <info>  VPN plugin state changed: 3 
Apr  3 15:41:31 guido pppd[6407]: pppd 2.4.4 started by root, uid 0
Apr  3 15:41:31 guido NetworkManager: <info>  VPN connection 'My-VPN1' (Connect) reply received. 
Apr  3 15:41:31 guido pppd[6407]: Using interface ppp0
Apr  3 15:41:31 guido pppd[6407]: Connect: ppp0 <--> /dev/pts/1
Apr  3 15:41:31 guido pptp[6409]: nm-pptp-service-6406 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Apr  3 15:41:31 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Apr  3 15:41:32 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Apr  3 15:41:32 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr  3 15:41:32 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 18235). 
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Apr  3 15:41:33 guido pppd[6407]: CHAP authentication succeeded
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Apr  3 15:41:33 guido pptp[6416]: nm-pptp-service-6406 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Apr  3 15:41:33 guido pppd[6407]: LCP terminated by peer (PM-^\^MM-W^@<M-Mt^@^@^BM-f)
Apr  3 15:41:36 guido NetworkManager: <info>  VPN plugin failed: 1 
Apr  3 15:41:36 guido pppd[6407]: Connection terminated.
Apr  3 15:41:36 guido pptp[6409]: nm-pptp-service-6406 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Apr  3 15:41:36 guido pptp[6409]: nm-pptp-service-6406 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Apr  3 15:41:36 guido pptp[6416]: nm-pptp-service-6406 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Apr  3 15:41:36 guido pptp[6416]: nm-pptp-service-6406 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Apr  3 15:41:36 guido pptp[6416]: nm-pptp-service-6406 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr  3 15:41:36 guido NetworkManager: <info>  VPN plugin failed: 1 
Apr  3 15:41:36 guido pppd[6407]: Modem hangup
Apr  3 15:41:36 guido pppd[6407]: Exit.
Apr  3 15:41:36 guido NetworkManager: <info>  VPN plugin failed: 1 
Apr  3 15:41:36 guido NetworkManager: <info>  VPN plugin state changed: 6 
Apr  3 15:41:36 guido NetworkManager: <info>  VPN plugin state change reason: 0 
Apr  3 15:41:36 guido NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Apr  3 15:41:36 guido NetworkManager: <info>  (eth1): writing resolv.conf to /sbin/resolvconf 
Apr  3 15:41:36 guido NetworkManager: <info>  Policy set 'Auto PalaRanch8' (eth1) as default for routing and DNS. 
Apr  3 15:41:48 guido NetworkManager: <debug> [1238798508.763261] ensure_killed(): waiting for vpn service pid 6406 to exit 
Apr  3 15:41:48 guido NetworkManager: <debug> [1238798508.763429] ensure_killed(): vpn service pid 6406 cleaned up 

```

Thanks for the help.

Regards,
Trung

---

### Post by nightfrost on 2009-04-04
I'm also having this exact problem.

I was able to connect a couple of days ago.

---

### Post by simplic8 on 2009-04-06
Hey, 

PPTP in network manager is pretty tricky, there are a couple of things that you need to make sure you have done correctly.

1. Username should be domain\username

Note: do not fill out domain in the VPN configuration.

Under the advanced option make sure you have the following configuration.

[IMG]http://simplic8.files.wordpress.com/2009/03/nm-connection-editor.jpg[/IMG]

and as long as you have added the refuse-eap option outlined by cbibeep everything should be working, if you cannot find the refuse-eap option, let me know and I can show you an alternative fix via the terminal rather then gconf.

---

### Post by nightfrost on 2009-04-10
Thanks!

What I was missing was the "Use point-to-point encryption (MPPE)" option.

It works well now.

---

### Post by jacob.david on 2009-06-14
[FONT="Comic Sans MS"]Thanks a lot cbibeep and simplic8. :KS:KS:KS:KS:KS to you guys. Please accept my apology for the late reply. I just tried the trick by adding the key for refuse-eap and it did the trick. I'm now able to connect to my office VPN. 
   For the remote desktop I tried with rdesktop and it seems to be bit slow. Do you have any good suggestion for remote desktop client?
Thanks once again.
- Jack
 [/FONT]

---

### Post by simplic8 on 2009-06-14
> **jacob.david said:**
> [FONT="Comic Sans MS"]Thanks a lot cbibeep and simplic8. :KS:KS:KS:KS:KS to you guys. Please accept my apology for the late reply. I just tried the trick by adding the key for refuse-eap and it did the trick. I'm now able to connect to my office VPN. 
   For the remote desktop I tried with rdesktop and it seems to be bit slow. Do you have any good suggestion for remote desktop client?
Thanks once again.
- Jack
 [/FONT]

Hi Jack,

I use Gnome RDP or Terminal Server Client (tsclient) to be honest, I've never found a decent RDP client for linux.. never been able to find the same performance as mstsc :-(

also note, since this post Ubuntu 9.10 has been released, PPTP connections contain refuse-eap by default.

Cheers,

Shayne.

---

### Post by spre on 2009-09-17
Hi, I am using Karmic (9.10) and still have this problem -- All the switches are set as stated but authentication wont succeed. What can I do? Let me know what information you need

---

### Post by demonye on 2009-11-20
> **spre said:**
> Hi, I am using Karmic (9.10) and still have this problem -- All the switches are set as stated but authentication wont succeed. What can I do? Let me know what information you need

I'm having the same issue.

While it works when I did 2 things below
    1. uncheck the EAP in the Authentication list
    2. check 'Use Point-to-Point encryption (MPPE)'

You can try it too.

---

### Post by Mu Blinking on 2009-11-22
After a lot of fiddling around, I got PPTP VPN to work under Karmic. Here is what worked for me:

1. Enter gateway, for example "vpn.example.com"

2. Enter user name as "DOMAIN\user". Do _not_ fill out password or NT domain.

3. Make sure that EAP is _not_ selected. Select PAP, CHAP, MSCHAP, MSCHAPv2.

4. Select Point-to-Point-encryption (MPPE).

For troubleshooting, check for error messages in /var/log/daemon.log . BTW, even though it eventually worked, I still got the error messages I had seen before, and a few more:

```
Nov 22 16:31:59 scylla pptp[2184]: nm-pptp-service-2179 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov 22 16:31:59 scylla NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 22 16:31:59 scylla NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.

...

Nov 22 16:32:00 scylla pptp[2190]: nm-pptp-service-2179 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Nov 22 16:32:00 scylla modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.31-14-generic/kernel/drivers/crypto/padlock-sha.ko): No such device

...

Nov 22 16:32:03 scylla nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

```

---

### Post by revdode on 2009-11-22
I'm having a similar problem. After trying for some time I finally go my connection working (Ubuntu 9.10, also on Kubuntu 9.10 with gnome network manager).

On both I get a connection sometimes, but not always. When I connect the connection is rock solid and everything is ok. The problem I have is that this isn't reliable. Without changing anything sometimes I get a connection, sometimes not. This can be in a period of a few minutes. After four hours of no problems shutting down the VPN then opening again gives me a VPN connection failure.

I'm stumped and a little frustrated, under windows XP I get no problems.

---

### Post by sayantandas on 2009-12-30
ok. now, just to make sure, the following should also be done.

in advanced iptions:
1. under MPPE , check allow stateful encryption
2.uncheck allow BSD data 
3. Uncheck allow deflate data compression

then
4. uncheck available to all users

this seemed to be working for a lot many ppl.

---

### Post by kallon on 2010-03-09
I had the same problem on Ubuntu 9.10.  Couldn't connect to the microsoft pptp vpn using the gnome network manager.

I ended up uninstall the default gnome network manager and then I installed KNetworkManager, which is the same thing but it is KDE.  I had no problems with it, except eventually I found out I had to restart the network every single time i made a configuration change for the full effect of the change to work.  So I went through and changed each vpn advanced setting that was hinted at in a tail -f /var/log/syslog.  And restarted the network each time:
service network-manager restart
 or
 /etc/init.d/network-manager restart
whatever works for you.

My final settings that worked to connect the vpn are:

Login: [login name]
Password: [password]
NT Domain: [blank]

PAP unchecked
CHAP unchecked
MSCHAP checked
MSCHAPv2 checked
EAP unchecked

Use MPPE  checked
Crypto: Any
Use Stateful encryption unchecked

Allow BSD compression checked
Allow Deflate checked
Allow TCP header checked

Send PPP echo unchecked

I found that each setting played an important part in getting success, wether on or off

---

### Post by nilindra on 2010-09-12
I am using Ubuntu 10.04 and tried the same steps which ended up with the following error.

<<<>>>> pppd[2042]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
<<<>>>> pppd[2042]: pppd 2.4.5 started by root, uid 0
<<<>>>> pppd[2042]: Using interface ppp1
<<<>>>> pppd[2042]: Connect: ppp1 <--> /dev/pts/1
<<<>>>> pppd[2042]: LCP terminated by peer (<REMOVED>)
<<<>>>> pppd[2042]: Connection terminated.
<<<>>>> pppd[2042]: Modem hangup
<<<>>>> pppd[2042]: Exit 

Finally I tried with the following.

username@domain for the username field

It worked !!!

Hope some one out there with the same problem will benefit from this post. ;)

---

