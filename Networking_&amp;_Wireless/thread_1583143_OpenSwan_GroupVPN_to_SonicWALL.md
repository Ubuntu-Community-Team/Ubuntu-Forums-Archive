---
title: "OpenSwan GroupVPN to SonicWALL"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by jwerwie on 2010-09-27
Hello. I am trying set set up an IPSEC vpn into a SonicWALL NSA2400. I have searched through many forums and was unable to find a configuration that works. Here are my sonicwall settings:

**General:**

IKE using Preshared Secret
Name: WAN GroupVPN
Shared Secret: secret

**Proposals:**
_IKE (Phase 1) Proposal_
DH Group: Group 2
Encryption: 3DES
Authentication: SHA1
Life Time: 28800
_Ipsec (Phase 2) Proposal_
Protocol: ESP
Encryption: 3DES
Authentication: SHA1
Life Time (seconds) 28800

**_ipsec.conf_**
config setup
	nat_traversal=yes
	nhelpers=1
	interfaces="ipsec0=eth1"

conn sonicwall
	type=tunnel
	left=192.168.1.115
	leftsubnet=192.168.1.115/24
	leftid=@GroupVPN
	leftxauthclient=yes
	right=someip
	rightsubnet=192.168.200.0/24
	rightid=@SonicWALLUID
	rightxauthserver=yes
	keyingtries=0
	pfs=no
	auto=add
	auth=esp
	esp=3des-sha1
	ike=3des-sha1-modp1536
	authby=secret
	aggrmode=yes

**_ipsec.secrets_**
@GroupVPN @SonicWALLUID : PSK "secret"

Terminal Result

112 "sonicwall" #11: STATE_AGGR_I1: initiate
003 "sonicwall" #11: Informational Exchange message must be encrypted

Thanks in advance.

---

### Post by carl.davis on 2010-11-15
Were you ever able to get this working?

---

### Post by jwerwie on 2010-11-17
No. I gave up and set up SSLVPN and used netExtender to connect. It seems to work very well. I like it better than group VPN.

---

### Post by jgranados on 2010-12-08
Hello guys, if you're still interested in getting this working, I think you need the following changes.

On Sonicwall configuration, check:

**VPN settings:**

Check "Enable VPN"
Set a "Unique Firewall Identifier" (You'll need it later)

**General:**

IKE using Preshared Secret
Name: WAN GroupVPN
Shared Secret: secret

**Proposals:**
_IKE (Phase 1) Proposal_
DH Group: Group 5 (not 2)
Encryption: 3DES
Authentication: SHA1
Life Time: 28800
_Ipsec (Phase 2) Proposal_
Protocol: ESP
Encryption: 3DES
Authentication: SHA1
Check "Enable Perfect Forward Secrecy"
DH Group: Group 5
Life Time (seconds) 28800

On Ubuntu configuration, check:

**_ipsec.conf_**
version 2.0

config setup
     	nat_traversal=yes
     	nhelpers=1
     virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
     oe=off
     protostack=netkey

conn sonicwall
     	type=tunnel
     	left=X.X.X.X (ip address of laptop)
     	leftsubnet=X.X.X.X/Y (usually the subnet is the same as the ip address with the last X replaced as 0 and Y = 24)
     	leftid=@GroupVPN
     	leftxauthclient=yes
     	right=X.X.X.X (public ip address of sonicwall adapter or fqdn)
     	rightsubnet=X.X.X.X/Y (subnet of the LAN side of the sonicwall)
     	rightid=@UNIQUEFIREWALLIDENTIFIER (as you set it on the sonicwall's VPN settings)
     	rightxauthserver=yes
     	keyingtries=0
     	pfs=no
     	auto=add
     	auth=esp
     	esp=3DES-SHA1
     	ike=3DES-SHA1
     	authby=secret
     	aggrmode=yes

**_ipsec.secrets_**
@GroupVPN @UNIQUEFIREWALLIDENTIFIER : PSK "secret"

Then run on a terminal:

**To start the VPN connection:**

sudo ipsec setup --start
sudo ipsec auto --replace sonicwall
sudo ipsec auto --add sonicwall
sudo ipsec whack --isten
sudo ipsec whack --name sonicwall --initiate

[B]To stop the VPN connection:

[/B]sudo ipsec whack --name sonicwall --terminate
sudo ipsec setup --stop



Please send your comments if you need further help.

---

### Post by jgranados on 2010-12-08
Sorry, forgot to spescify the following:

Please make shure you tab all entries in the /etc/ipsec.conf file exept for the following:

version 2.0
config setup
conn sonicwall

Best regards,

---

### Post by lechien73 on 2011-02-09
I know the thread is a couple of months old, but I had exactly the same problem. I eventually managed to solve it - and have put the solution here: [http://blog.mattrudge.net/2011/02/09/openswan-to-sonicwall-tz170/](http://blog.mattrudge.net/2011/02/09/openswan-to-sonicwall-tz170/)

I hope it helps others, because I had been scratching my head for ages over this!!

---

### Post by jwerwie on 2011-04-17
Wow thanks. That worked like a charm!

---

