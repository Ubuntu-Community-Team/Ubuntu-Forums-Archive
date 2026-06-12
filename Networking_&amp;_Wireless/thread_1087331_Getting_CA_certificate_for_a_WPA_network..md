---
title: "Getting CA certificate for a WPA network."
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Dynih on 2009-03-04
I'm trying to connect to my university's WPA encrypted wireless network, but the instructions for connecting are only for windows and mac. Both sets of instructions assume that the network configuration client somehow automatically downloads the needed CA certificate. There's no direct download link that I can find, and the network manager is not automatically downloading the certificate.

How do I get the certificate?

Links to mac/windows configuration instructions:
[http://www.yale.edu/its/network/wireless/wpa/index.html](http://www.yale.edu/its/network/wireless/wpa/index.html)

---

### Post by Flareside on 2009-03-05
I've been having the same problem since the end of January at my university. It worked before then, but suddenly one day I couldn't connect any more.

---

### Post by nightalon on 2009-03-25
Hi Dynih,

Same problem here.  Fellow Yalie.  Trumbull 2010.  Will let you know if I figure out anything.

---

### Post by nightalon on 2009-03-25
Hey Dynih,


Either of the two options listed under item 2 should work at the following link:

[http://www.geotrust.com/resources/root-certificates/](http://www.geotrust.com/resources/root-certificates/)

Ubuntu apparently doesn't include Equifax certificates by default, only Thawte or Computer Associates, I don't remember.

Aruba Networks, the people who supply our wireless, use Equifax certificates.

You just have to use the downloaded file in the YaleWPA/YaleWPA2 configuration.

Do you want to help me figure out the Yale VPN next?  The establishment can't get it, even though PPTP and Cisco configurations work fine in OS X 10.5.6 and Windows Vista.  I haven't had much luck either, even once I get past the fact that the whole password-supplying part of NetworkManager and the Seahorse keychain seems to be somewhat broken.


NighTalon

---

### Post by sgosnell on 2009-03-25
Perhaps [this thread](http://ubuntuforums.org/showthread.php?t=249654) will help.

---

### Post by tvst on 2009-04-30
Off-topic, but Yale VPN works for me using:

$ sudo apt-get network-manager-pptp

Then right-click on the network manager applet, choose edit connections. Go to VPN, click Add. Choose PPTP and use these settings:

(non-red values are used to indicate that they're default values)
[COLOR="Red"]connection nane: Yale VPN  (any name you want)
gateway: vpn.net.yale.edu
username/password: your NetID and password[/COLOR]
nt domain: [leave blank]
click on Advanced, then:
- allow methods: [select all]
[COLOR="Red"]- [X] use MPPE[/COLOR]
- security = all available
- [ ] allow stateful encryption
- [X] Allow BSD
- [X] Allow Deflate
- [X] Use TCP header
- [ ] Send PPP echo
--> press OK

ipv4 settings tab: leave on automatic
--> press Apply, then Close

Then connect by left-clicking the network manager, VPN connections, choose Yale VPN.

---

### Post by jbalat on 2010-03-19
The above solution didnt work for me. The thing is, I believe, that in order to connect to YaleSecure you dont need a certificate.

Just select YaleSecure, when the "authentication required" window opens do the following:

Authentication: PEAP
Anonymous identity: leave it empty
CA certificate: (None)
PEAP version: Automatic
Inner authentication: MSCHAPv2

and of course fill in your username and password, click Connect, it will then open a new window saying that you didnt choose any certificate, just click Ignore

that's it, this worked for me

---

### Post by leecarraher on 2010-09-08
the method above, ignoring the certificate is how our wpa secured wireless works at university of cincinnati, however this is not secure. 

sample attack:

a hacker(and not even a very good one) can very easily spoof a university access point, just by name alone. they then send you their public key, and because you do not verify the signature as being from your university you encrypt your username and password with that key. since its their public key, no one else can decrypt it accept for them using their private key. if they wanted to listen in on your network session they would simply redirect your packets to the real access point or hard link and record everything in the clear. or it may just be sufficient to record usernames and passwords. there is a very good reason for the cert, yet no one uses it. and it appears this is the case at more and more universities and businesses.

given this problem it might suffice to do this:

Is there a way using the given access points transmitted public key to generate the signature. this should be feasible since you are supposed to verify the signature (unless its a oneway hash function). 
i can at least feel somewhat secure that i am not accessing a spoofed access point and sending an attacker my username and password based on the fact that its the same public key for every access point everywhere around campus (security in numbers isnt the best but its better than none whatsoever).

---

