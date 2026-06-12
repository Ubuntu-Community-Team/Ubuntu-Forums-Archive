---
title: "SSH webserver - can't connect over internet"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by veaviticus on 2009-09-18
First off this is the specs I've got :

Jetway mini Atx motherboard with built in atom 330
running Ubuntu server 9.04
Linksys 160N router running the latest version of DD-WRT firmware

I'm stuck. I've set up a webserver with Ubuntu Server 9.04 on it. I've configured it according to this tutorial, [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) , so its running apache. I can ssh into the webserver from within the local network according to its static IP address. I set up my router to give the server a static IP of 192.168.1.250 and I forwarded port 22 to the server. I've got a DynDns set up to map my IP to a domain name, and my router is set up to keep my dynamic IP updated on DynDns. When I attempt to ssh into the server by using the domain name, however, I get a Permission Denied (Publickey) error. 

I ran ssh - v on it and I got this output : 

rob@rob-desktop:~$ ssh -v server@216.70.26.237
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 216.70.26.237 [216.70.26.237] port 22.
debug1: Connection established.
debug1: identity file /home/rob/.ssh/identity type -1
debug1: identity file /home/rob/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/rob/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.2p1 Debian-7ubuntu3.1
debug1: match: OpenSSH_4.2p1 Debian-7ubuntu3.1 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '216.70.26.237' is known and matches the RSA host key.
debug1: Found key in /home/rob/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/rob/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/rob/.ssh/identity
debug1: Trying private key: /home/rob/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

If I (with my limited knowledge) am reading that correctly, I'm connecting to the server just fine, but its not authenticating my login. So I tried forcing it using 

ssh -v server -o stricthostkeychecking=no host.tld

and that allowed me to type in my password. But it wouldn't recognize the password, and then it kicked me back out again. So I figured I'd set up a public key access (yeah really not sure what that is). I looked around and found a tutorial for it. [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

it had me set up an rsa key pair on the server. Now I didn't know how to get the public key  back to my desktop, since I couldn't ssh from the server to my desktop (didn't work). I managed to get a USB drive mounted and moved the key over to the authenticated_keys file on my desktop. And yet the exact same thing happens when I try to ssh to the server - Permission Denied (publickey). 

One thing that I did note was that the public key said server@server on it. (my webserver is named server). Now when I ssh to server@server, it lets me in with my password. I don't have a computer outside of this network right now to try it out on, I'd have to wait till tomorrow when I get back to school where my laptop is. 

So, any ideas on how to get it so I can ssh to my DynDns domain name and access my webserver?

---

### Post by veaviticus on 2009-09-21
*bump*

---

