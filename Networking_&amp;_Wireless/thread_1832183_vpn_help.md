---
title: "vpn help"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by bsliv on 2011-08-24
I've been assigned the task of setting up a remote backup machine.  I thought Ubuntu could handle the job but I've put in many hours trying and still can't get it.  

I'm testing the setup at home.  My desktop is acting as the vpn server.  My laptop is the Ubuntu 10.04 client.  The laptop uses the wireless nic to attach to a neighbors network.  I then tell the laptop to attach to the vpn.  Ubuntu says the wireless and vpn are both active.  Windows shows the new connection.  But when I try to access a shared folder, I get "Unable to mount location", "Failed to mount Windows share."  

The laptop also has Vista on it.  It only took about 10 minutes to get it functional.  If I was smart, I would have put Windows on a week ago and been done with it.  But I'm not too smart.  I've been trying to promote Linux as an alternative but am beginning to rethink things. Did I choose the wrong o/s?

---

### Post by e79 on 2011-08-24
On your Ubuntu laptop :

```
sudo apt-get install smbfs
```

> Did I choose the wrong o/s? 	

Maybe?

---

### Post by bsliv on 2011-08-24
"Done  smfs is already the newest version"

When I connect the Ubuntu laptop directly to my home network, I can see the Windows shares so I think parts are working.

I tried pasting the output of syslog but the forum says "You have included 11 images in your message..."

---

### Post by e79 on 2011-08-24
> **bsliv said:**
> "Done  smfs is already the newest version"

When I connect the Ubuntu laptop directly to my home network, I can see the Windows shares so I think parts are working.

I tried pasting the output of syslog but the forum says "You have included 11 images in your message..."

Have you tried to put the copy/paste of syslog between quotes using the widget in your thread ?

as in :
> text to be inserted here

So, If I understand correctly, your file server reside on a Windows machine...Are you able to access it via your Ubuntu laptop while being connected to your LAN ?

What if you try with the 'Connect to server...' option offered by Nautilus (click on top bar when nothing is selected on your desktop then --> File --> Connect to server) and enter the info like on this picture (but swap values with your) ?

---

### Post by bsliv on 2011-08-24
> **e79 said:**
> Have you tried to put the copy/paste of syslog between quotes using the widget in your thread ?

as in :


So, If I understand correctly, your file server reside on a Windows machine...Are you able to access it via your Ubuntu laptop while being connected to your LAN ?

That is correct.

What if you try with the 'Connect to server...' option offered by Nautilus (click on top bar when nothing is selected on your desktop then --> File --> Connect to server) and enter the info like on this picture (but swap values with your) ?

I get a box that says, 'Cannot display location "smb://workgroup;bill@192.168.1.34/stuff/" Failed to mount Windows share'

I can't ping the Windows machine from the laptop (unless I connect to the network directly).  

The Windows machine shows the connection under Network Connections.  If I click status of the connection on the Windows box, it shows bytes sent and received, the time connected, authentication type is ms chap v2, encryption is mppe 128, server ipv4 address is 192.168.1.50, client ipv4 address is 192.168.1.53.   But it also says ipv4 connectivity: not connected.  I'm not sure if that is correct or not.  Clicking Diagnose, Windows says 'Troubleshooting couldn't identify the problem".  

I have McAfee firewall on the Windows box (server).  When running Vista on the laptop, everything works ok.  To get Ubuntu on the laptop to connect, I have to disable the firewall.  One o/s goes thru, the other doesn't.  

I'll try to post the syslog output in a bit.

Thanks for your help so far.

---

### Post by bsliv on 2011-08-24
I can't paste the log because the forum is putting a smiley face where there is a colon followed by the letter p.  

A smiley face counts as an image.  Only 8 images allowed per post.  Not something a frustrated person wants to deal with.

---

### Post by bsliv on 2011-08-24
Aug 24 15:11:29 toshiba NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Aug 24 15:11:29 toshiba NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1545
Aug 24 15:11:29 toshiba NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Aug 24 15:11:29 toshiba NetworkManager: <info>  VPN plugin state changed: 1
Aug 24 15:11:29 toshiba NetworkManager: <info>  VPN plugin state changed: 3
Aug 24 15:11:29 toshiba NetworkManager: <info>  VPN connection 'Home' (Connect) reply received.
Aug 24 15:11:29 toshiba pppd[1547]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug 24 15:11:29 toshiba pppd[1547]: pppd 2.4.5 started by root, uid 0
Aug 24 15:11:29 toshiba pppd[1547]: Using interface ppp0
Aug 24 15:11:29 toshiba pppd[1547]: Connect: ppp0 <--> /dev/pts/1
Aug 24 15:11:29 toshiba NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 24 15:11:29 toshiba NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 24 15:11:29 toshiba pptp[1551]: nm-pptp-service-1545 log[main ptp.c:314]: The synchronous pptp option is NOT activated
Aug 24 15:11:30 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_rep ptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Aug 24 15:11:30 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_disp ptp_ctrl.c:739]: Received Start Control Connection Reply
Aug 24 15:11:30 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_disp ptp_ctrl.c:773]: Client connection established.
Aug 24 15:11:31 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_rep ptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Aug 24 15:11:31 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_disp ptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug 24 15:11:31 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_disp ptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 51193).
Aug 24 15:11:31 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_disp ptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 57564
Aug 24 15:11:31 toshiba pptp[1558]: nm-pptp-service-1545 log[ctrlp_disp ptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Aug 24 15:11:31 toshiba pptp[1558]: nm-pptp-service-1545 warn[ctrlp_disp ptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Aug 24 15:11:31 toshiba pppd[1547]: CHAP authentication succeeded
Aug 24 15:11:31 toshiba kernel: [  147.802488] padlock: VIA PadLock Hash Engine not detected.
Aug 24 15:11:31 toshiba modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-33-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Aug 24 15:11:31 toshiba kernel: [  147.804765] PPP MPPE Compression module registered
Aug 24 15:11:31 toshiba pppd[1547]: MPPE 128-bit stateless compression enabled
Aug 24 15:11:33 toshiba pppd[1547]: found interface wlan0 for proxy arp
Aug 24 15:11:33 toshiba pppd[1547]: local  IP address 192.168.1.54
Aug 24 15:11:33 toshiba pppd[1547]: remote IP address 192.168.1.50
Aug 24 15:11:33 toshiba pppd[1547]: primary   DNS address 68.105.28.11
Aug 24 15:11:33 toshiba pppd[1547]: secondary DNS address 68.105.29.11
Aug 24 15:11:33 toshiba NetworkManager: <info>  VPN connection 'Home' (IP Config Get) reply received.
Aug 24 15:11:33 toshiba NetworkManager: <info>  VPN Gateway: 70.189.239.33
Aug 24 15:11:33 toshiba NetworkManager: <info>  Tunnel Device: ppp0
Aug 24 15:11:33 toshiba NetworkManager: <info>  Internal IP4 Address: 192.168.1.54
Aug 24 15:11:33 toshiba NetworkManager: <info>  Internal IP4 Prefix: 32
Aug 24 15:11:33 toshiba NetworkManager: <info>  Internal IP4 Point-to-Point Address: 192.168.1.50
Aug 24 15:11:33 toshiba NetworkManager: <info>  Maximum Segment Size (MSS): 0
Aug 24 15:11:33 toshiba NetworkManager: <info>  Internal IP4 DNS: 68.105.28.11
Aug 24 15:11:33 toshiba NetworkManager: <info>  Internal IP4 DNS: 68.105.29.11
Aug 24 15:11:33 toshiba NetworkManager: <info>  DNS Domain: '(none)'
Aug 24 15:11:33 toshiba NetworkManager: <info>  Login Banner:
Aug 24 15:11:33 toshiba NetworkManager: <info>  -----------------------------------------
Aug 24 15:11:33 toshiba NetworkManager: <info>  (null)
Aug 24 15:11:33 toshiba NetworkManager: <info>  -----------------------------------------
Aug 24 15:11:34 toshiba NetworkManager: <WARN>  nm_system_device_set_ip4_route(): Failed to set IPv4 route on 'ppp0': Sucess#012
Aug 24 15:11:34 toshiba NetworkManager: <info>  VPN connection 'Home' (IP Config Get) complete.
Aug 24 15:11:34 toshiba NetworkManager: <info>  Policy set 'Home' (ppp0) as default for routing and DNS.
Aug 24 15:11:34 toshiba NetworkManager: <info>  VPN plugin state changed: 4
Aug 24 15:11:34 toshiba nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

---

### Post by e79 on 2011-08-25
Could you try uninstalling the 'Windows Live Sign-In Assistant' from your Windows 7 box while you do some tests ? Couple of similar problems were solved using this method as described here :

[http://ubuntuforums.org/showthread.php?t=1640474](http://ubuntuforums.org/showthread.php?t=1640474)

---

### Post by bsliv on 2011-08-25
Thanks for continuing to offer suggestions, all will be considered.  I ran across that thread and did uninstall the only Windows Live program that showed up in add/remove programs.

I think its a samba issue.  When I'm connected directly to the network, smbtree shows all the shares.  But when I connect via vpn, no shares show with smbtree.

---

### Post by e79 on 2011-08-25
No problem,

I must admit I never browsed the share in smbtree when accessing it over VPN...I always used the `connect to server` and added a  Bookmark in Nautilus.

---

