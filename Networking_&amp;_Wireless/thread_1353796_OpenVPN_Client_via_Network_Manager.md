---
title: "OpenVPN Client via Network Manager"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by jame86 on 2009-12-13
Hey All,

Firstly sorry if this has been answered elsewhere but I have tried searching!

I have a working OpenVPN server running on Ubuntu 9.10 at a remote location.  I successfully join to it with my Windows 7 laptop, but I want to join my two home Ubuntu boxes to it also.

I can successfully join to the VPN via the openvpn command in console, and all works find.  But I want to be able to join the VPN automaticly when the machine turns on.  The reason for this is automated backups to the remote location.

I have the OpenVPN module installed in network-manager, but dont know what goes where!  I have the client.ovpn file from the server which works elseware, but how do I extract the various certificates that NM wants?

I hope that all makes sense!

Thanks

Jame86  :P

---

### Post by jame86 on 2009-12-18
self-bump!!

---

### Post by tacom6 on 2010-10-09
> **jame86 said:**
> self-bump!!

Trying to figure out the same thing. :)

---

### Post by annec on 2010-10-09
Hi

First, I am no expert!
But: I am currently figuring stuff out with openvpn and NM. And I got it to work. 

I am not sure this will entirely answer your question but you should:

- Left click on the icon of NM
- VPN>Configure VPN
- A window pops up > import
- Find your *.conf or *.ovpn file
- then, it depends on your provider and your NM version

Can you edit here your conf or ovpn file? I may be able to guide you then.

---

### Post by annec on 2010-10-09
Actually, here is a nice tutorial from the strongPN support team. They explain better than I would ever :)

[https://www.smallvpn.com/setup-howto/ubuntu-openvpn-setup-tutorial/](https://www.smallvpn.com/setup-howto/ubuntu-openvpn-setup-tutorial/)

Keep us posted.

---

### Post by tacom6 on 2010-10-10
> **annec said:**
> Actually, here is a nice tutorial from the strongPN support team. They explain better than I would ever :)

[https://www.smallvpn.com/setup-howto/ubuntu-openvpn-setup-tutorial/](https://www.smallvpn.com/setup-howto/ubuntu-openvpn-setup-tutorial/)

Keep us posted.

Thank you!

Well, the thing is I am using OpenVPN Access Server and it the ovpn file has everything bunched up into one text file. So I have been unsuccessful so far in breaking it into pieces that have to be fed directly into the NM.

I have seen Viscosity is able to import Access Server files, I might go that direction and see how it does it.

I will let you know. :)

---

### Post by sphantom on 2010-12-01
tacom6: Did you ever make any progress on this? I'm having the same problem. I use OpenVPN-AS and am trying to get network manager to parse the .ovpn

---

### Post by piet.petersen on 2011-02-24
You can manually insert the configuration parameters in network-manager-openvpn

First you need the certificates in separate files you get these by entering the following commands on the Access server console.

1.cd [I]/usr/local/openvpn_as/scripts

2. [/I]./sacli -a ADMIN -o OUTPUT_DIRECTORY --cn COMMON_NAME get5
     ADMIN = openvpn access server administrator
     -o = directory where you want the certificates stored
     --cn = same as username, except for autologin profiles, append "_AUTOLOGIN" to the common name.

3.  copy the certificates to a folder on your pc
4.  click on the network manager, chose "VPN connections" --> "configure VPN"
5.  click add
6.  choose Openvpn click create
7.  type in your gateway eg. vpn.mydomain.com
8.  in "type" choose "password with certificates (TLS)"
9.  in "user name" type in your openvpn user name
10. in "user certificate" choose the **client.crt** file you got earlier
11. in "CA certificate" choose the **ca.crt** file you got earlier
12. in "private key" choose the **client.key** file you got earlier
13. click "Advanced"
14. set your port number (default 1194)
15. click on the "use LZO data compression"
16. select tap "TLS Authentication"
16. check the "Use additional authentication 
17. in "key file" select the **ta.key **file you got earlier
18. in "key direction" choose 1
19. click okay
20. click appy
21. click close
You should now be able to connect to your openVPN access server

NOTE: these settings are based on a standard openvpn access server setup and other setting may be needed for your setup, please check your client.ovpn file for correct settings to setup your connection. 

I hope someone find this guide help full.

Kind regards
Piet   


**

---

### Post by smoff on 2011-05-01
This is my first ubuntu forums post and I am no expert on this but I had a similar problem in that openvpn from command line worked, but under NetworkManager it failed.  After comparing the configuration I realised that our work server must require the mac address setting lladdr.  This option was not available through the NetworkManager GUI.

The only way I could get round it was by the following hack....

As root
  cd /usr/sbin
  mv openvpn openvpn.orig
  vi openvpn
    insert 
       exec /usr/sbin/openvpn.orig --lladdr <my mac address> $*
  chmod 755 openvpn

Seems to be working now, but I am sure it will fail on the next openvpn patch.  So if anyone has any other suggestions how to get round this, please let me know.

Thanks
Smoff

---

