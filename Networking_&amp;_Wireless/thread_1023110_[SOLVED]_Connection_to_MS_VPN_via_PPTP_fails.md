---
title: "[SOLVED] Connection to MS VPN via PPTP fails"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by jesuspresley on 2008-12-27
When I am trying to connect to our office's network by the Network Manager
VPN tab (network manager pptp plugin is installed), an error message appears.

My syslog tells me:

```
Dec 27 21:02:04 ordenacito NetworkManager: <debug> [1230408124.066612] ensure_killed(): vpn service pid 6053 cleaned up 
Dec 27 21:02:45 ordenacito NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Dec 27 21:02:45 ordenacito NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6087 
Dec 27 21:02:46 ordenacito NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Dec 27 21:02:46 ordenacito NetworkManager: <info>  VPN plugin state changed: 1 
Dec 27 21:02:46 ordenacito NetworkManager: <info>  VPN plugin state changed: 3 
Dec 27 21:02:46 ordenacito NetworkManager: <info>  VPN connection 'company' (Connect) reply received. 
Dec 27 21:02:46 ordenacito NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'company' failed to connect: 'No VPN configuration options.'. 
Dec 27 21:02:46 ordenacito NetworkManager: <info>  (wlan1): writing resolv.conf to /sbin/resolvconf 

```
[LIST]
[*]I heard that there are some bugs for the new version of Network Manager in Intrepid - is this the buggy part or misconfiguration?
My version is 0.7.0

[*]Actually, I did not enter anything to the "Routes..." section in the VPN configuration. Is it mandatory to enter any data there?

[*]What else comes to your mind to help me?
[/LIST]

I checked these threads, too. But it seems the users have different log outputs:
[http://ubuntuforums.org/showthread.php?t=1023059](http://ubuntuforums.org/showthread.php?t=1023059)
[http://ubuntuforums.org/showthread.php?t=1015984](http://ubuntuforums.org/showthread.php?t=1015984)

---------------------------------------------------
Hard: Samsung NC10 Netbook 1GB RAM
Soft: Ubuntu 8.10 Intrepid Ibex

---

### Post by jesuspresley on 2008-12-29
In order to do SOMETHING, i now tried to reinstall the OpenVPN & PPTP package:
> 
sudo apt-get install --reinstall network-manager-openvpn network-manager-pptp

And then
> sudo /etc/init.d/networking restart

No success yet. Same messages in the syslog as before.

---

### Post by jesuspresley on 2008-12-31
I succeeded partially:

I downgraded to [actually reinstalled] **Ubuntu Hardy 8.04**, because there are still bugs reported for the Network Manager PPTP plugin under Intrepid 8.10.
What I did then was to follow [these instructions on ubuntugeek.com]("http://www.ubuntugeek.com/howto-connect-to-windows-vpn-server-pptp-with-ubuntu-710-gutsy-gibbon.html")

I will repeat the steps roughly here:

> sudo apt-get install network-manager-pptp
killall nm-applet
sudo /etc/init.d/dbus restart

Then I was able to enter the connection date when I clicked the network manager icon and save the VPN connection:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98229&stc=1&d=1230733637[/IMG]

I just had to follow the menu, select *Configure VPN* then add a new connection.
Note that on the *Authentication* tab you have to activate *Refuse CHAP.*

When I start the VPN connection, I get the following outpout from
> tail -f /var/log/messages
```

Dec 31 15:20:16 biggubuntu pppd[9678]: Plugin nm-pppd-plugin.so loaded.
Dec 31 15:20:16 biggubuntu pppd[9678]: nm-pppd-plugin: plugin initialized.
Dec 31 15:20:16 biggubuntu pppd[9679]: pppd 2.4.4 started by root, uid 0
Dec 31 15:20:16 biggubuntu pppd[9679]: Using interface ppp0
Dec 31 15:20:16 biggubuntu pppd[9679]: Connect: ppp0 <--> /dev/pts/2
Dec 31 15:20:17 biggubuntu pppd[9679]: nm-pppd-plugin: CHAP check hook.
Dec 31 15:20:18 biggubuntu pppd[9679]: nm-pppd-plugin: CHAP credentials requested.
Dec 31 15:20:18 biggubuntu pppd[9679]: CHAP authentication succeeded
Dec 31 15:20:18 biggubuntu pppd[9679]: MPPE 128-bit stateless compression enabled
Dec 31 15:20:20 biggubuntu pppd[9679]: local  IP address 192.168.0.114
Dec 31 15:20:20 biggubuntu pppd[9679]: remote IP address 192.168.0.129
Dec 31 15:20:20 biggubuntu pppd[9679]: primary   DNS address 192.168.0.251
Dec 31 15:20:20 biggubuntu pppd[9679]: secondary DNS address 213.160.20.146
```

I have a working VPN connection now, and I can ping the servers:
> ping 192.168.0.251

But I cannot see any shares in Nautilus. I guess that Nautilus itself needs some PPTP plugin also? 

Can anyone help me?

---

### Post by wmoore on 2008-12-31
I tried and tried to get VPN working in NM in both Fedora and Ubuntu but gave up. I'm now using kvpnc, which works beautifully.

---

### Post by jesuspresley on 2008-12-31
Well, the last step is not too tricky. 
From the panel, I can choose *Places > Connect to Server*

I choose *Windows Share*. Then I have to enter the IP address or DNS name of the server I want to connect to, not to forget username and domain.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98236&stc=1&d=1230735755[/IMG]

Sometimes I get an error first [bug?] that the location is not mounted. But when I open the folder bookmark from my desktop, the system mounts the connection automatically and displays the shares. 

YIPPIEH!!!

---

### Post by levidos on 2009-01-01
i have the same problem.. .i;m trying to pptp-connect to a windows 2003 server but i get that error message.
do you mean i have to downgrade to 8.04 ??

---

### Post by jesuspresley on 2009-01-02
For me, this was the quickest solution because Intrepid was a fresh install, so by reinstalling I did not loose any data. 

*If* you have not succeeded doing it by [this tutorial]("http://olafsblog.sysbsb.de/?p=68") [did not work for me] AND you are not an experienced *Ubuntu Geek* you should consider downgrading.

---

### Post by zonyl on 2009-01-20
Got it working in 8.10 using the link in the preceding post.  Thank you very much.

In addition I turned off CHAP (advanced), had to leave the "domain" field blank, and used my AD domain in the username like 'zonyl@company.com'

---

