---
title: "Setting Up a VPN for the first time Draytek 2820"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Jonners59 on 2011-01-06
OK, this is almost my first VPN, I did just about manage to set one up on Windows a couple of years ago with some help, but that's about it.  Now I want to set one up on my Ubuntu environment:

I am running 10.10 on all my machines and I use a DraytekVigor 2820Vn, Firmware Version: 3.3.3_RC5b.  It is able to runPPTP, IPSec and L2TP type VPNs and there is a whole raft of options and stuff.

I have three devices I would like to set up a VPN on.  A laptop in Italy (still running XP, but I will upgrade to 10.10 when I am out there next, so consider it 10.10.  A Toshiba Satellite Laptop running 10.10 and a HTC TP2 running WM 6.5, Ubuntu and Android, depending on my mood.  I have a softphone on the TP2 that I wish to connect via the VPN to the IP PBX, in fact I have one on all my machines.  I also wish to be able to browse, read and write files on machines here via the VPN.

SO far I have enabled PPTP on the router.  The PPP settings as PAP or CHAOP and 128bit MPPE.  Mutual Authentication.  I have craeted an account in Remote Dial In User.  PPTP and that's it on the router.

I am testing on a PC and have created an account via Network Manager - VPN.  Add VPN, then just added the fixed IP address of the router/gateway, username and password.  In advanced I have added: MSCHAP, Point to Point MPPE at 128 bit.  Allow BSD, Allow Deflate and Use TCP.....

When I try it it fails " because the VPN service failed to start".......

So what do I need to do, and how can I make things better, anyone, please?

---

### Post by thefix0r on 2011-01-06
MPPE is usually disabled by default in most pptp clients on linux, you might need to install a pptp client as well in the first place.

crowell@opteron:~$ aptitude search PPTP
p   network-manager-pptp                                                     - network management framework (PPTP plugin)
p   pptp-linux                                                               - Point-to-Point Tunneling Protocol (PPTP) Client
p   pptpd                                                                    - PoPToP Point to Point Tunneling Server

any of those fit your needs?

---

### Post by Jonners59 on 2011-01-07
I tried the cmd line and had to install aptitude, but once run it stated I had all installed.

I'll be very honest, I have not really got a clue here what I am doing and need quite a bit of hand holding.  Happy to start from scratch.

---

### Post by copycat on 2011-01-25
> **Jonners59 said:**
> I tried the cmd line and had to install aptitude, but once run it stated I had all installed.

I'll be very honest, I have not really got a clue here what I am doing and need quite a bit of hand holding.  Happy to start from scratch.

Hey,

I just have setup a 2820n.  The vpn trough ipsec works on xp.  The pptp works on my 10.04 without problems.

---

### Post by Jonners59 on 2011-01-26
> **copycat said:**
> Hey,

I just have setup a 2820n.  The vpn trough ipsec works on xp.  The pptp works on my 10.04 without problems.

Great, but I don't want to know that there are success stories, I am sure there are millions, I want to know how.

I have  a Draytek 2810 and 3 Laptops running 10.10 and a smartphone running Android and WM 6.5

I have had no success because I do not know what I am doing, so I need step by step instructions/help.

The first problem is the laptops, I get VPN failed to start.  See screenshot enclosed:  top right

The Smartphone just says Registration Failed

Can anyone help, please.  This thread had been open far too long

---

### Post by copycat on 2011-02-04
> **Jonners59 said:**
> Great, but I don't want to know that there are success stories, I am sure there are millions, I want to know how.

I have  a Draytek 2810 and 3 Laptops running 10.10 and a smartphone running Android and WM 6.5

I have had no success because I do not know what I am doing, so I need step by step instructions/help.

The first problem is the laptops, I get VPN failed to start.  See screenshot enclosed:  top right

The Smartphone just says Registration Failed

Can anyone help, please.  This thread had been open far too long

Ok about the laptop... I really didn't install anything extra.  Pptp was just installed in the default setup. (Lucid & Maverick)

The setup is straight forward like the wireless setup is on the same menu.
I just added the dyndns adress and username and password from the draytek.
I have a company portable with also a AT&T client and a netbook with a clean Maverick.

Then I configured the draytek.

* In the  Remote Access Control I enabled all 3 services.
* In the 	 PPP General Setup I have PAP or CHAP and Optional MPPE.  I filled in a 10.0.0.200 adress because that's the lan range from the draytek.

* The on Remote Dial-in User you click the first free number and enable the account.
You active the pptp checkbox and fill in the username and password that you are going to use in the connection.

Then it works.  You can try inside the lan to connect.  It also works.  
I just did setup a 2750n and this worked also with pptp form ubuntu and ipsec from xp.

Hope it helps!

---

### Post by Jonners59 on 2011-02-05
> **copycat said:**
> Ok about the laptop... I really didn't install anything extra.  Pptp was just installed in the default setup. (Lucid & Maverick)

The setup is straight forward like the wireless setup is on the same menu.
I just added the dyndns adress and username and password from the draytek.
I have a company portable with also a AT&T client and a netbook with a clean Maverick.

Then I configured the draytek.

* In the  Remote Access Control I enabled all 3 services.
* In the      PPP General Setup I have PAP or CHAP and Optional MPPE.  I filled in a 10.0.0.200 adress because that's the lan range from the draytek.

* The on Remote Dial-in User you click the first free number and enable the account.
You active the pptp checkbox and fill in the username and password that you are going to use in the connection.

Then it works.  You can try inside the lan to connect.  It also works.  
I just did setup a 2750n and this worked also with pptp form ubuntu and ipsec from xp.

Hope it helps!
Copycat
Cheers, much appreciated.  Same as my settings prety much, but I get an error on the laptop.  When I select VPN from the connection manager in the ribbon, it says:
"The VPN connection "VPN" failed because the VPN service failed to start"

Any ideas?

---

### Post by copycat on 2011-02-23
Hey,

sorry for the late reply.
I didn't subscribe on the post.

I think you should try to check and reïnstall your pptp client.
It is inside your gnome network manager I suppose.

If anyone is able to ipsec with ubuntu or mac to a draytek box.  I really would be happy to have the info.

I mailed draytek sales (HQ) to ask a status for this.
It isn't possible that they are going to stay ignoring the open-source.  The androids are taking over the world.  Many people are bying iphone/ipad or smartphones/tablets.  Pptp is not secure.  Therefore many network specialists do block the pptp ports. (hotels,airports,large companies) 
The need for a smart vpn client alternative is high.

There's a German [shrew howto with draytek]("http://www.draytek.de/Beispiele/VPN/ShrewSoft_Client.pdf").  But my 2750n has not every possible setting.  I think with the 2820 it is possible to use it.

regards

---

### Post by Jonners59 on 2011-02-24
Thanks Copycat
I'll look in to this, though my German is not very good(!) and I was hoping to sort this out during the quiet period, as I need to focus on finding a contract right now....  Will reply with my findings soonest

Big thanks you for this....

---

### Post by copycat on 2011-02-24
Update from Draytek :confused:

[I][B]
Thank you for your request for Technical Support.

We don't have plan for Smart VPN Client for MAC OSX & Linux,but I'll submit a wish
for it.[/B][/I]

---

### Post by Jonners59 on 2011-02-25
Mmm, not very reassuring.

They should make a nice wizard for the draytek that also craetes an image for the client devices to load....  That would be nice.  WIndows does one for their OS, but it would be better from the VPN HW manufactures themsleves.  Dream on.

---

