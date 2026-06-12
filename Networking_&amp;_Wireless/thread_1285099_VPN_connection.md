---
title: "VPN connection"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by lupeatx on 2009-10-07
I'm new to all this so please bare with me. My boss gave me a project to work on. We want a dedicated (24/7) VPN tunnel from a Ubuntu Linux Box (server) with only terminal access (not x-windows, GUI) to a Watchguard Firebox x550 running Fireware 10.2. Now what all info (from server and firebox) do I need to get started? :-\"

---

### Post by BQAggie2006 on 2009-10-07
Check out these guides from the Ubuntu Community Documentation:

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[https://help.ubuntu.com/community/VPNServer](https://help.ubuntu.com/community/VPNServer)

---

### Post by k3yb0ardn1nja on 2011-08-08
The company I work for uses a Watchguard Firebox 750e. I was able to successfully setup ssl-vpn connection on Ubuntu10.04 with a little help from a [german guide]("http://www.stoeps.de/ssl-vpn-von-ubuntu-zu-watchguard-firebox/") I found. I was planning on re-writing this excellent guide in more comprehensive english than the google translator provides.


**[SIZE="2"]Connecting to watchguard firebox via ssl-vpn:[/SIZE]**


**1.) Retrieve the client.wgssl file from the Firebox**


This can be done a couple of ways.


1.) Directly from firewall:

[FONT="System"]https://gateway:4100/?action=sslvpn_download&filename=client.wgssl&usern 
ame=my_name&password=my_password[/FONT]


2.) If you have access to the "*WatchGuard System Manager*" utility, you can open the "*FireBox System Manager*". Then, select the "*Status Report*" tab. Click on the button labeled "*Support*" in the bottom right corner of the window. From here, you can select a directory and "*retrieve*" the archive.

- Extract the file named "[FONT="System"]Fireware_XTM_Support.tgz[/FONT]" from the archive we retrieved.

- Now extract the file "[FONT="System"]client.wgssl[/FONT]" located in the [FONT="System"]support/debug/[/FONT] directory of the "[FONT="System"]Fireware_XTM_Support.tgz[/FONT]" archive.



**2.) Configuring our connection**


a.) Rename the "[FONT="System"]client.wgssl[/FONT]" file to "[FONT="System"]client.wgssl.tgz[/FONT]"


b.) Now, unpack the archive using the following command:
[FONT="System"]tar -xvzf client.wgssl.tgz[/FONT]


c.) You should receive the following files form the archive:

[FONT="System"]ca.crt
client.crt
client.pem
client.ovpn
VERSION
MD5SUM[/FONT]


d.) We need to modify the "[FONT="System"]client.ovpn[/FONT]" file, so that the DNS settings can be aquired. Add the following lines:

[FONT="System"]script-security 2
up /etc/openvpn/update-resolve-conf
down /etc/openvpn/update-resolve-conf[/FONT]


Re-install the resolvconf package with this command:

[FONT="System"]sudo apt-get install resolvconf[/FONT]


e.) Create directory [FONT="System"]/etc/openvpn[/FONT] with the following command:
[FONT="System"]sudo mkdir /etc/openvpn[/FONT]


f.) Move all of the files that we extracted from "[FONT="System"]client.wgssl.tgz[/FONT]" to the "[FONT="System"]/etc/openvpn[/FONT]" directory we just created:
[FONT="System"]sudo mv 'filename' /etc/openvpn/[/FONT]


g.) Install the openvpn Netowrk Manager:
[FONT="System"]sudo apt-get install network-manager-openvpn[/FONT]



**3.) Connecting the VPN**

Build the vpn tunnel:
(must run command from [FONT="System"]/etc/openvpn/[/FONT])

[FONT="System"]cd /etc/openvpn
sudo openvpn ./client.ovpn[/FONT]


You can use Ctrl+C to close the tunnel.


Original Article: [http://www.stoeps.de/ssl-vpn-von-ubuntu-zu-watchguard-firebox/]("http://www.stoeps.de/ssl-vpn-von-ubuntu-zu-watchguard-firebox/")

---

