---
title: "VPN Connects &amp; Then Disconnects Shortly Thereafter"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by hayhursm on 2012-04-24
Hello Everyone,

I am able to establish a VPN connection using Ubuntu 11.10 (kernel: 3.0.0-17-generic) however, no web pages will load on my local browser and I cannot view any of the VPN's share folders, PC's, etc... Then anywhere from 30 seconds to 1.5 minutes it will disconnect with a failed message.  All of my Windows machines and even my iPhone can VPN into this server with no problems all day long but not Ubuntu.  I have attached my syslog if that helps any.  I have been dealing with this issue for a long time and for the life of me cannot figure it out, so any help will be greatly appreciated!!!!

---

### Post by excetara2 on 2012-04-27
Mate if you figure this out let me know. My vpn used to work (I have 10.04 and the current kernel) about 6 months ago. Haven't tried it since until a couple days ago but an upgrade since then has forced it to not work. It just keeps connecting and then fails. I reckon it was an update in the last couple months that caused this but I could be wrong.

---

### Post by hayhursm on 2012-04-27
> **excetara2 said:**
> Mate if you figure this out let me know. My vpn used to work (I have 10.04 and the current kernel) about 6 months ago. Haven't tried it since until a couple days ago but an upgrade since then has forced it to not work. It just keeps connecting and then fails. I reckon it was an update in the last couple months that caused this but I could be wrong.


I'm in the same situation, VPN seemed to work fine with everything up until 11.04.  What VPN server are you using?  I'm just using DD-WRT v24-sp2 (12/20/11) mega (*SVN revision* 18024) on a Linksys E3000 router.  I'm confident it has nothing to do with DD-WRT as I have tried different revisions plus my Windows machines and smart phones can VPN with no problems all day long.  Have you attempted VPN on 12.04?

---

### Post by excetara2 on 2012-04-28
Nope, maybe I'll give the cd a go later today or let me know if you do. Not sure of the vpn setup because setup by the IT and never really needed to know but uses pptp connection. Think it may be a bug in an update of the nm-applet or elsewhere. Not really sure how to debug the cause but imagine it was an update that is on 10.04 and above at least. I think it would be good to post a bug report maybe in nm-applet. They can probably tell us how to check whether it's a bug in an nm-applet update or elsewhere.

---

### Post by excetara2 on 2012-04-28
maybe post here with that syslog and i'll respond as well: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet)

---

### Post by SeijiSensei on 2012-04-28
Sometimes starting a job in a terminal to ping the other end of the tunnel continuously can help resolve disconnection problems like these.  That's obviously not a real solution, but it might help you stay connected while you figure out the correct approach.

---

### Post by hayhursm on 2012-04-28
> **excetara2 said:**
> maybe post here with that syslog and i'll respond as well: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet)


I found this during my search, not sure if it's related to our problem but you might check it out: [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient) scroll all the way down to "Troubleshooting" and look under "Packet Recursion".  I haven't had the extra time to try all the possible solutions but it maybe worth looking in to.

---

### Post by hayhursm on 2012-04-29
> **excetara2 said:**
> Nope, maybe I'll give the cd a go later today or let me know if you do. Not sure of the vpn setup because setup by the IT and never really needed to know but uses pptp connection. Think it may be a bug in an update of the nm-applet or elsewhere. Not really sure how to debug the cause but imagine it was an update that is on 10.04 and above at least. I think it would be good to post a bug report maybe in nm-applet. They can probably tell us how to check whether it's a bug in an nm-applet update or elsewhere.


I tried the VPN client on Ubuntu 12.04 Live and the problem still exists.  Definitely going to file a bug report now.

---

### Post by excetara2 on 2012-04-30
Post a link to the bug report here please...been really busy so haven't had time to look at this further but I'll look at the link you provided.

---

### Post by hayhursm on 2012-04-30
> **excetara2 said:**
> Post a link to the bug report here please...been really busy so haven't had time to look at this further but I'll look at the link you provided.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/991666](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/991666)

---

### Post by hayhursm on 2012-09-04
> **excetara2 said:**
> Mate if you figure this out let me know. My vpn used to work (I have 10.04 and the current kernel) about 6 months ago. Haven't tried it since until a couple days ago but an upgrade since then has forced it to not work. It just keeps connecting and then fails. I reckon it was an update in the last couple months that caused this but I could be wrong.


Hello,

I figured out what is causing this problem.  It's due to the fact that my LAN router is on the same subnet as the router I VPN into (both routers are running VPN servers).  Changing the IP addresses of both routers running the VPN servers to two different IP addresses does nothing to correct the issue.  I actually had to change the subnets so each router was on a different subnet (ie. 192.168.1.X and 192.168.2.X).  As long as both routers are on different subnets then I can VPN all day with absolutely no problems.  After doing some reading this seems to be an inherent issue when VPN'ing from a UNIX environment (MAC, iPhone, Ubuntu, and other Linux Distros) and not in the Windows environment.

Here's what helped me draw up these conclusions: 

[http://www.dd-wrt.com/wiki/index.php/Point-to-Point_PPTP_Tunneling_with_two_DD-WRT](http://www.dd-wrt.com/wiki/index.php/Point-to-Point_PPTP_Tunneling_with_two_DD-WRT)

[http://www.dd-wrt.com/wiki/index.php/PPTP_Server_Configuration](http://www.dd-wrt.com/wiki/index.php/PPTP_Server_Configuration)

---

