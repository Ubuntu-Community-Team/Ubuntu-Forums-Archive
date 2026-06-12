---
title: "How to import openvpn settings in network manager"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by Betelgeuse on 2010-11-08
I have an openvpn connection to my office network. 
The vpn server is a smoothwall with openvpn addition.
I have given two files (and a secret password); one .p12 file and a .ovpn file for settings.

The network manager in ubuntu 10.10 can import the .ovpn file and it works. I'm using 10.10 on my netbook and it works fine.

But ubuntu 10.04 can not import the file and can not use the .p12 file as certificate. I'd like to use 10.04 lts on my main work laptop and desktop computers because I do not want to update every 6 months. 

is there any package that I can update the openvpn client in 10.04? or what should I do?

FYI: I'm using ubuntu 10.04 64bit.

---

### Post by cjohnson19791979 on 2010-12-25
can you explain how you got network manager in 10.10 to import the .ovpn and .p12 files to make a working connection?

---

### Post by Betelgeuse on 2010-12-26
> **cjohnson19791979 said:**
> can you explain how you got network manager in 10.10 to import the .ovpn and .p12 files to make a working connection?

I have two files given to me for vpn connection, a .p12 file and .ovpn file. .ovpn file is a text file with vpn configuration and .p12 file contains keys.

on ubuntu 10.10, I have to install openvpn and network-manager-openvpn-gnome packages from synaptics. after installing those packages, now there is openvpn in network-manager applet on the gnome menu bar. There I've simply choose import to import the settings and it works.


On a fresh install of ubuntu, there is only pptp in network manager and I think openvpn and network-manager-openvpn-gnome packages should be installed by default.

---

### Post by cjohnson19791979 on 2010-12-26
> There I've simply choose import to import the settings and it works.


that only imports the ovpn config file. at that point you're only halfway there. you still need to import the key files as well. how did you get that part to work?

---

### Post by Betelgeuse on 2010-12-26
> **cjohnson19791979 said:**
> that only imports the ovpn config file. at that point you're only halfway there. you still need to import the key files as well. how did you get that part to work?

When the .ovpn config file import finishes, there are three certificate file fields and they are filled with the one .p12 that I have and there is a password field which I entered my password.

---

### Post by vipseixas on 2011-01-21
have you ever managed to use the p12 files? I am at the same situation here, 10.10 at my notebook (works just fine) and 10.04 at my desktop (can't use the p12 files).

> **Betelgeuse said:**
> I have an openvpn connection to my office network. 
The vpn server is a smoothwall with openvpn addition.
I have given two files (and a secret password); one .p12 file and a .ovpn file for settings.

The network manager in ubuntu 10.10 can import the .ovpn file and it works. I'm using 10.10 on my netbook and it works fine.

But ubuntu 10.04 can not import the file and can not use the .p12 file as certificate. I'd like to use 10.04 lts on my main work laptop and desktop computers because I do not want to update every 6 months. 

is there any package that I can update the openvpn client in 10.04? or what should I do?

FYI: I'm using ubuntu 10.04 64bit.

---

### Post by cjohnson19791979 on 2011-01-21
vip...   

i had the same issue with 10.04. it seems as though in 10.10 there is a newer version of network manager included (0.8.1), as opposed to 10.04 (0.8.) release notes from the network manager site show....

> 
**0.8.1**

 This release was tagged in late July 2010 and includes bug fixes the following features. 
 
**New Features**

 
[LIST]
[*]Bluetooth Dial-Up Networking (DUN) support ([bgo #432774]("https://bugzilla.gnome.org/show_bug.cgi?id=432774"))
[*]Enhanced IPv6 support including DHCPv6 capability ([bgo #556915]("https://bugzilla.gnome.org/show_bug.cgi?id=556915"))
[*]Command-line interface
[*]Mobile broadband signal strength, status, and roaming display
[*]Support for restricting mobile broadband roaming behavior
[*]Enhanced logging and debugging infrastructure
[*]Better handling of suspend/resume
[*]Enhancements to the 'keyfile' system connection format
[*]Ability to suppress periodic scans by locking connection to a BSSID
[/LIST]

it's the "Enhancements to the 'keyfile' system connection format" feature that i believe enables the use of p12 keys with openvpn. for those of you that want to keep 10.04, i'm not sure as far as dependencies go if you could just update network manager by itself or not. could be a possibility though.

---

### Post by vipseixas on 2011-01-21
Ok, it seems that we have to update network-manager-openvpn package to the latest version so it can understand p12 files. But there is a fairly simple way to generate the 3 .pem files needed at the old version using the original .p12 file:

openssl pkcs12 -nocerts -in file.p12 -out priv_key.pem
openssl pkcs12 -nokeys -clcerts -in file.p12 -out user_cert.pem
openssl pkcs12 -nokeys -cacerts -in file.p12 -out ca_cert.pem

Then use these 3 files at the OpenVPN configuration, mine is working fine now. I do not know if openssl is installed by default at Lucid, but it is in the repositories.

---

### Post by Betelgeuse on 2011-01-21
> **vipseixas said:**
> Ok, it seems that we have to update network-manager-openvpn package to the latest version so it can understand p12 files. But there is a fairly simple way to generate the 3 .pem files needed at the old version using the original .p12 file:

openssl pkcs12 -nocerts -in file.p12 -out priv_key.pem
openssl pkcs12 -nokeys -clcerts -in file.p12 -out user_cert.pem
openssl pkcs12 -nokeys -cacerts -in file.p12 -out ca_cert.pem

Then use these 3 files at the OpenVPN configuration, mine is working fine now. I do not know if openssl is installed by default at Lucid, but it is in the repositories.

Thank you very much for that info.
I had to upgrade my main work computer just to use p12 files. No I can use them in 10.04 too.

---

