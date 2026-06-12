---
title: "VPN PPTP Connection fails when downloading"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by TheNTW on 2010-09-20
I am using relakks.com VPN Service and set it up with gnome's default nm-manager interface. 
Everything is just perfect when I'm browsing the web. I can do it for hours and nothing happens. 
On the other hand, when I open up a torrent client - after 15 seconds to 2 minutes - I get a nice kick off the VPN.

It goes like this:
```

Sep 20 08:25:11 NPC pptp[3496]: nm-pptp-service-3490 warn[decaps_gre:pptp_gre.c:426]: discarding bogus packet 94236 (expecting 93663)
Sep 20 08:25:11 NPC pptp[3496]: nm-pptp-service-3490 warn[decaps_gre:pptp_gre.c:426]: discarding bogus packet 94237 (expecting 93663)
Sep 20 08:25:11 NPC wpa_supplicant[820]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 20 08:25:11 NPC kernel: [ 2021.459230] ipw2200: Firmware error detected.  Restarting.
Sep 20 08:25:11 NPC NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected
Sep 20 08:25:11 NPC NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Sep 20 08:25:14 NPC wpa_supplicant[820]: Trying to associate with c0:3f:0e:72:a0:0e (SSID='Ida-Wireless' freq=2412 MHz)
Sep 20 08:25:14 NPC NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Sep 20 08:25:14 NPC wpa_supplicant[820]: Association request to the driver failed
Sep 20 08:25:14 NPC wpa_supplicant[820]: Associated with c0:3f:0e:72:a0:0e
Sep 20 08:25:14 NPC NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Sep 20 08:25:14 NPC NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Sep 20 08:25:17 NPC wpa_supplicant[820]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Sep 20 08:25:17 NPC wpa_supplicant[820]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 20 08:25:17 NPC NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> disconnected
Sep 20 08:25:17 NPC wpa_supplicant[820]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 20 08:25:17 NPC NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
^C

```

I'm on a laptop, and after this happens I have to Fn+disable wireless, Fn+enable wireless, or it won't connect to the internet.
I have No idea why this is happening. Please help. I'm desperate....

---

### Post by TheNTW on 2010-09-22
Once I get a disconnect from VPN, I can't retry the connection unless I reboot my network card, and this is how syslog looks like:

```

Sep 22 17:38:03 NPC NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Sep 22 17:38:03 NPC NetworkManager: <info>  VPN plugin state changed: 1
Sep 22 17:38:03 NPC NetworkManager: <info>  VPN plugin state changed: 3
Sep 22 17:38:03 NPC NetworkManager: <info>  VPN connection 'Relax' (Connect) reply received.
Sep 22 17:38:03 NPC pppd[6081]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Sep 22 17:38:03 NPC pppd[6081]: pppd 2.4.5 started by root, uid 0
Sep 22 17:38:03 NPC pppd[6081]: Using interface ppp0
Sep 22 17:38:03 NPC pppd[6081]: Connect: ppp0 <--> /dev/pts/3
Sep 22 17:38:03 NPC NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 22 17:38:03 NPC NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 22 17:38:03 NPC pptp[6085]: nm-pptp-service-6079 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Sep 22 17:38:24 NPC pptp[6087]: nm-pptp-service-6079 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
Sep 22 17:38:24 NPC pptp[6087]: nm-pptp-service-6079 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 93.182.159.2
Sep 22 17:38:24 NPC pptp[6085]: nm-pptp-service-6079 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Sep 22 17:38:24 NPC pppd[6081]: Modem hangup
Sep 22 17:38:24 NPC pppd[6081]: Connection terminated.
Sep 22 17:38:24 NPC NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 22 17:38:24 NPC NetworkManager: <info>  VPN plugin failed: 1
Sep 22 17:38:24 NPC pppd[6081]: Exit.
Sep 22 17:38:24 NPC NetworkManager: <info>  VPN plugin failed: 1
Sep 22 17:38:24 NPC NetworkManager: <info>  VPN plugin failed: 1
Sep 22 17:38:24 NPC NetworkManager: <info>  VPN plugin state changed: 6
Sep 22 17:38:24 NPC NetworkManager: <info>  VPN plugin state change reason: 0
Sep 22 17:38:24 NPC NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.


```

p.s. BUMP! HELP!

---

### Post by TheNTW on 2010-09-24
A bump.
Help ?

---

### Post by TheNTW on 2010-09-26
Come on! Can anyone help me !?

---

### Post by TheNTW on 2010-09-28
I will keep on bumping until I get a reply [-(

---

### Post by TheNTW on 2010-09-29
I guess I'll have to do the longest topic bumping in the world. I wonder if I can apply for Guiness records for that and get loads of cash to pay some developer to fix my issue :)

---

### Post by TheNTW on 2010-10-01
Bump!
Can Anyone help me ?
Is there a a tool maybe which could help me reconnect as soon as connection is lost or something ?
**HELP!**

---

### Post by TheNTW on 2010-10-02
Bumpity!

---

### Post by TheNTW on 2010-10-03
Bump!

---

### Post by TheNTW on 2010-10-06
**bump!**

---

### Post by TheNTW on 2010-10-07
Bump!

---

### Post by TheNTW on 2010-10-08
bump

---

### Post by TheNTW on 2010-10-09
Bump!:guitar:

---

### Post by TheNTW on 2010-10-10
Bump:KS

---

### Post by TheNTW on 2010-10-11
bamp!

---

### Post by TheNTW on 2010-10-12
Bump!

---

### Post by TheNTW on 2010-10-14
**bump**

---

### Post by TheNTW on 2010-10-15
Another bump.
Seems like when there is a real question - no one can answer it!

---

### Post by TheNTW on 2010-10-16
bump

---

### Post by TheNTW on 2010-10-17
pmub

---

### Post by TheNTW on 2010-10-18
[b]bump
come on! Help me![/b]

---

### Post by TheNTW on 2010-10-19
nobody knows....

---

### Post by TheNTW on 2010-10-20
Bump.:confused:

---

### Post by TheNTW on 2010-10-21
Bummmp.

---

### Post by TheNTW on 2010-10-26
Long time no bump!

---

### Post by TheNTW on 2010-10-27
Bump. This isn't fun anymore.

---

### Post by TheNTW on 2010-10-28
bump

---

### Post by utilitytrack on 2010-10-28
> **TheNTW said:**
> [b]bump
come on! Help me![/b]

Be quiet, I'm here :)

Please give output of these commands when you experience some troubles with connection:

```

$ uname -a
$ ifconfig -a
$ lspci -nn | grep -i -E 'Ethernet|Network'
$ cat /etc/network/interfaces
$ cat /etc/ppp/options.pptp
$ dpkg -l pptp-linux
$ route -n
$ ping -c 10 209.85.229.104
# cat /etc/ppp/peers/provider 
# iptables --list -n
# netstat --inet --numeric-hosts -a -p -e -n -c
# lshw -C network
```

Next:
```
$ dmesg > dmesg_full.log
```

And attach this file to post.

Next: describe your network setup, how work your regular connection with ISP, tell us when such problem happened first time, under what conditions disconnection happened (what programs did you use exactly), have you experienced anything similar on other Linux-based systems, describe (if you can) how this connection worked under DefautOS. AND: did you make contact with Relakks technical service?

Please give accurate answers to my questions.

---

### Post by TheNTW on 2010-11-02
I think in my first post you can view dmesg part, what happens when I get disconnected and a little before that.
I attached a file with all the commands you asked.

The only thing I think I could find to blame would be the router. It's a NETGEAR WNR-1000v2 I think. I have tried almost everything. I've disabled every otpion on it and enabled everything as well. Nothing helped.
Now I found a half-solution. I open deluge and set the maximum connections to about 40, I get a little lower download speed, but a little smaller amounts of disconnects. 

Thank you for finally replying :P

---

### Post by TheNTW on 2010-11-05
Bump!

---

### Post by zyrg on 2010-11-07
I am just "patch" my pptp.
I replace 408 line in pptp_gre.c from
> else if ( seq < seq_recv + MISSING_WINDOW ||
                WRAPPED(seq, seq_recv + MISSING_WINDOW) ) 
to
>  else if (1)
Very dirty hack but ... it just works for me.

---

### Post by TheNTW on 2010-11-08
What does it do ?

---

### Post by Centx on 2010-11-25
> **TheNTW said:**
> What does it do ?

Hi, I'm having the same problem myself. This hack probably removes some check of some sort that has with packets received (by pptp, I assume).

I'll put up a bug-report on launchpad about this, as I I've had this bug for quite some time, and just now bothered to dig deep enough (lol, checking logs) to have something to report.

---

### Post by Centx on 2010-11-25
Some more info I found about this around the net can be found in the bug-report I put up. The fix is still probably a hack, but probably less dirty than the proposed if(1) :P

[https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/681617]("https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/681617")

cheers

---

### Post by mbaitoff on 2012-04-11
The patch has been created to workaround this problem. The patch allows specifying the size of a packet window in command line: [https://launchpadlibrarian.net/100566402/pptp-1.7.2-specify-missing-window.patch](https://launchpadlibrarian.net/100566402/pptp-1.7.2-specify-missing-window.patch)

---

### Post by anyfm on 2012-05-13
> **mbaitoff said:**
> The patch has been created to workaround this problem. The patch allows specifying the size of a packet window in command line: [https://launchpadlibrarian.net/100566402/pptp-1.7.2-specify-missing-window.patch](https://launchpadlibrarian.net/100566402/pptp-1.7.2-specify-missing-window.patch)

How do i apply this patch? Should i apply it on server- or client side?

---

### Post by hasardeur on 2012-05-13
Client Side - you need to download the source code and then apply the provided patch. both versions should work just fine.

---

