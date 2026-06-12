---
title: "SSH Tunnel/Router"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by davidgriswold on 2012-10-02
I am not sure if this is the correct forum for this question, or it should be security, but it covers both areas.

I  am a 21 year IT pro and was installing slackware on floppies in '93 on  kernel .9something, and have had much experience with Linux/*nix over  the years, just so you know at what level to assume I know what the hell  I am talking about.  Not really sure that made sense, but anyway...

I  have two installs of Ubuntu server 12.04 LST (referred to as the  'servers') that can talk fully to each other in two different  locations.  not that it matters, but these are both VMs on vmware 4.1.   At the production site, the server has a NIC on a private, non-routed,  iscsi network.  There is a SAN on this private network that needs to  talk to a SAN on the network at the DR site, where the second ubuntu  server resides.

I am following this guide [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN) and I have been able to work up to [Configuring the Interfaces]("https://help.ubuntu.com/community/SSH_VPN#Configuring_the_interfaces"), but I am unable to ping either side of the tunnel from the other side.

I  can provide as much additional details as needed, but since I am not  sure where I might have screwed up, I am going to leave the details open  ended.

Thanks,
David

---

### Post by davidgriswold on 2012-10-02
OK, update. I left a ping running from the production side to the DR site, and it just started working after 16 and a half minutes.  I did nothing on either side to change the tunnel during this time.  I am, however, still unable to ping from the DR site to the production site.  I am going to take the tunnel down and start it in the other direction to see if that matters.

---

### Post by davidgriswold on 2012-10-02
Never mind - I figured it out.  I had setup the tunnel with the routeable IP network and not the private IP network, and so the production side had two paths to the DR site and didn't know which to use.  Once I reconfigured with the private network, it works great.

---

