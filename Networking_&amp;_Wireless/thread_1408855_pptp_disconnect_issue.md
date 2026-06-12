---
title: "pptp disconnect issue"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by mitch428 on 2010-02-16
I'm new to using Linux, so please bear with me. I did spend time searching the forums, but couldn't find another thread with the same symptoms I am seeing. If there is, I apologize, and respectfully ask to provide a link.
 
I am having an issue with pptp. I am using Ubuntu 9.10 (64 bit) inside a virtual machine (host OS is Windows 7 64 bit), and have applied all updates that are available and recommended with the system update feature.
 
I followed the guides from this website and have pptp set up and can connect with no problems. Everything seems in order (I can browse though the tunnel fine), but the issue I have is when I start a Bittorrent through the VPN tunnel, the tunnel will break. I have also seen this happen when downloading packages through the package manager as well.
 
I am using the Network Manager plugin for pptp.
 
I did a tail -f /var/log/messages before starting a tunnel and this is the output:
 
Feb 16 18:02:23 ubuntu pppd[3665]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Feb 16 18:02:23 ubuntu pppd[3665]: pppd 2.4.5 started by root, uid 0 
Feb 16 18:02:23 ubuntu pppd[3665]: Using interface ppp0 
Feb 16 18:02:23 ubuntu pppd[3665]: Connect: ppp0 <--> /dev/pts/1 
Feb 16 18:02:25 ubuntu pppd[3665]: CHAP authentication succeeded 
Feb 16 18:02:25 ubuntu pppd[3665]: MPPE 128-bit stateless compression enabled 
Feb 16 18:02:26 ubuntu pppd[3665]: local IP address 216.131.102.89 
Feb 16 18:02:26 ubuntu pppd[3665]: remote IP address 169.254.130.88
Feb 16 18:02:26 ubuntu pppd[3665]: primary DNS address 216.131.95.20
Feb 16 18:02:26 ubuntu pppd[3665]: secondary DNS address 216.131.94.5 
 
Everything up to this part is fine. Below is when the tunnel stops responding to traffic:
 
 
Feb 16 18:05:55 ubuntu pppd[3665]: No response to 5 echo-requests 
Feb 16 18:05:55 ubuntu pppd[3665]: Serial link appears to be disconnected.
Feb 16 18:05:55 ubuntu pppd[3665]: Connect time 3.5 minutes.
Feb 16 18:05:55 ubuntu pppd[3665]: Sent 2347377 bytes, received 41360163 bytes.
Feb 16 18:05:58 ubuntu pppd[3665]: Connection terminated.
Feb 16 18:05:58 ubuntu pppd[3665]: Terminating on signal 15 
Feb 16 18:05:58 ubuntu pppd[3665]: Child process /usr/sbin/pptp wn45.reliablehosting.com --nolaunchpppd --logstring nm-pptp-service-3662 (pid 3666) terminated with signal 15 
Feb 16 18:05:58 ubuntu pppd[3665]: Modem hangup 
Feb 16 18:05:58 ubuntu pppd[3665]: Exit.
 
 
 
My external router is a Cisco ASA 5505. I don't have the message handy, but when this happened there was a corresponding firewall entry in the ASA that read something like the following:
 
DENY - no translation found for src:internal to dst:StrongVPN for ICMP (type 3, code 2), original payload: ip 47 (gre) from src:StrongVPN to dst:internal
 
From what I see, the tunnel was already broken, my box was trying to send the message to the VPN provider (type 3, code 2 is a protocol unreachable message) but there was no 'initiating' ICMP request for the type 3, code 2 response from StrongVPN OUTSIDE the tunnel. Does this make sense?
 
 
I don't think there is a configuration problem with the ASA, as I can use the VPN without issue UNTIL I start a high bandwith/high connection download. Also, I have used the same tunnel from the Windows 7 OS through the ASA with no problems whatsoever using bittorrent and/or downloading directly (i.e. an ISO for Ubuntu).   
 
 
Anyway, I was hoping someone here may be able to shed some light on something I may doing wrong or be able to point me in the direction to try to resolve this.
 
 
Thanks.

---

### Post by sonicb00m on 2010-06-01
this is also happening to me. It must be a bug since this doesn't happen with my connection in windows.

---

### Post by asleepyhead on 2010-10-21
The same happens to me but not just when I start a torrent (surfing). After a while it just disconnects. I use ubunu 10.10 64bit. Has anyone a clue how to fix this?

---

### Post by rainyu_2002 on 2011-03-15
Hi I figured out the issue. 

I have same issue before. Error log before connection disconnected.

[I]Feb 23 08:57:15 rain-ThinkPad-SL pppd[3074]: appear to have received our own echo-reply!
Feb 23 08:58:41 rain-ThinkPad-SL pppd[3074]: last message repeated 2 times
Feb 23 08:58:46 rain-ThinkPad-SL pppd[3074]: No response to 4 echo-requests
Feb 23 08:58:46 rain-ThinkPad-SL pppd[3074]: Serial link appears to be disconnected.
Feb 23 08:58:46 rain-ThinkPad-SL pppd[3074]: Connect time 2.0 minutes.[/I]

You can change configuration of pppd to avoid this happened.

As I know, we have two ways to complete pppoe connection in Ubuntu 10.10.(I am using this one, I am just familiar with this edition)

1. Network Manager
2. By command "pon dsl-provider"

[FONT="Arial Black"]How to solve the issue.[/FONT]
[COLOR="Red"]IMPORTANT! BACKUP FILES BEFORE YOU EDIT IT.[/COLOR]

If you are using the "1. Network Manager", please do followings.
[LIST]
[*]vim /etc/NetworkManager/system-connections/pppoe1.[pppoe1 is the name of DSL connection you named in Network Manager]
[*]Change the parameter lcp-echo-interval value to 65535. ```
lcp-echo-interval=65535
```
[*]Reboot NetworkManager with command: /etc/init.d/network-manager restart
[/LIST]


If you are using the "2. By command "pon dsl-provider"", please do followings.

[LIST]
[*]vim /etc/ppp/options
[*]Change the parameter lcp-echo-interval value to 65535
[*]```
lcp-echo-interval=65535
```
[/LIST]

[LIST]
[*]vim /etc/ppp/peers/dsl-provider
[*]Change the parameter lcp-echo-interval value to 65535
[*]```
lcp-echo-interval=65535
```
[/LIST]

If you still engage the same problem, I suggest you restart your OS. May be someone knows how to make these changes effect, please comment. This will help a lot of people including me.

---

### Post by Hohoman on 2012-12-18
Thank you!

I have searched from time to time to solve this problem. The trick in my case was to activate "Send PPP echo". Unsure about the spelling, I have swedish installed.

---

### Post by Hohoman on 2012-12-18
I was a bit to quick with my recent reply. The problem is still there :(

---

