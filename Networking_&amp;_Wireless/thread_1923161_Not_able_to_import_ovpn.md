---
title: "Not able to import ovpn"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by jlperry on 2012-02-10
Kubuntu 11.04 
KDE 4.7

I have been pulling my hair out trying to setup a vpn network.

I have installed openvpn and network manager.
```
$ apt-get install -y network-manager-openvpn-kde
```

When I try to import the 'select file window' filters for only *.pcf files. I have tried to change the filter but to no success.

Does anybody have any ideas??

---

### Post by WthIteh on 2012-02-10
The ovpn file is a text file.
Open it with a text editor and look inside.

Instead of importing it, create a new VPN connection and fill it with information provided in the ovpn text file manually.

---

### Post by jlperry on 2012-02-10
@WthIteh thanks for your reply

The ovpn file comes from a vpn service. I have opened the file and tried to re-create the connection manually but can't seem to get that to work either. 

There are a lot of settings in the ovpn file and it appears that I don't seem to understand all of them. The option is there to easily import. The settings and I would really like to figure out how to get it to work if anybody can help?

---

### Post by tehowe on 2012-07-10
> **jlperry said:**
> @WthIteh thanks for your reply

The ovpn file comes from a vpn service. I have opened the file and tried to re-create the connection manually but can't seem to get that to work either. 

There are a lot of settings in the ovpn file and it appears that I don't seem to understand all of them. The option is there to easily import. The settings and I would really like to figure out how to get it to work if anybody can help?

This is the procedure I followed to get it working. There's a bug in network manager where it doesn't do ovpn import properly - since 2010 (!)

[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/606365](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/606365)

Until that's fixed, I found this site

[http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu](http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu)

PROCEDURE

Create a new folder in your home dir - I called mine vpn.config
Copy your downloaded client.ovpn file into the new folder

Open client.opvn in an editor

Open a new file
Cut the lines between <ca> tags in client.ovpn
Paste into new file, save this file as ca.crt
Remove both <ca> tags from client.ovpn

Open a new file
Cut the lines between <cert> tags in client.ovpn
Paste into new file, save this file as client.crt
Remove both <cert> tags from client.ovpn

Open a new file
Cut the lines between <key> tags in client.ovpn
Paste into new file, save this file as client.key
Remove both <key> tags from client.ovpn

Open a new file - this is the last one :-)
Cut the lines between <tls-auth> tags in client.ovpn
Paste into new file, save this file as ta.key
Remove both <tls-auth> tags from client.ovpn

And remove this line:
key-direction 1


Now position the cursor in client.ovpn, right above the line # -----BEGIN RSA SIGNATURE-----

Insert the following lines

ca ca.crt
cert client.crt
key client.key
tls-auth ta.key 1

Save and close all the files.

Goto Network Manager -> Edit Connections ->VPN
click Import, browse to the modified client.ovpn in the folder you recently created - and where your certificates are, and import that file
Enter vpn username and password if prompted
On the VPN page, select Advanced
On the General Tab, uncheck the first option, "Use custom gateway"

Save

Use...

---

