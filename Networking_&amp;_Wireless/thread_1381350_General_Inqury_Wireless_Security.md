---
title: "General Inqury: Wireless Security"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by HuckBerry on 2010-01-14
I have been running DD-WRT on my Router for years now, and had never turned on encryption or anything because I didn't want the hassle of going to every computer and configuring passwords. I did however turn on the MAC filtering that is in the Wireless>>MAC Filter Menu. This was to keep out pesky neighbors.

As more and more visitors to my house come by, I've added a large number of MAC addresses to this list(most of which I no longer remember which device they belong to), and I was wondering if there wasn't a way to plop the MAC, hostname, Static IP and a comment field into a SQL table and have the dhcp assign everything via that table.

Enter freeRadius....

I noticed that DD-WRT had a option for RADIUS and I knew that it had something to do with authenticating users. I installed it and have worked with it for a few days and now I realize it might not be what I thought it was.

My general inqury is, what is the simplest way for a small network admin to manage a rapidly changing network of about 10 static hosts and 25 or so MAC's that come and go. While still remaining free of neighbors AND Linux friendly at the same time?

---

### Post by adam814 on 2010-01-14
Open wifi with MAC address filtering won't always keep your neighbors out of it if they know what they're doing.  They could change their NIC MAC address to match one of yours and your router would probably assign them an IP with it.  It also won't keep them from passively spying on you either.

Even WPA isn't bulletproof, but it's not WEP (cracked in 20 minutes).  But assuming they can crack your WPA passphrase they can STILL change their MAC address and get through.  Doesn't seem like something I'd want to count on for security.

My advice is to bite the bullet and set up WPA on the router and all the clients and not worry with MAC address filtering.  That way you can add new clients *from* the client and you don't have to go to another machine to add them just for perceived security.

---

### Post by changingstate on 2010-01-14
If you want to keep the neighbours off your connection, stop relying on MAC address filtering for security, bite the bullet and turn on the encryption. The commands needed to gain access to your network take less than two minutes to execute. The attack is trivial, once you know what you're doing.

---

### Post by HuckBerry on 2010-01-14
The part I don't like is the Pre-Shared Key business... People come and go so quickly and my key goes with them. Changing keys every week simply isn't an option. I'd prefer something centrally managed.

I'm aware MAC addresses can be easily cloned, but I see that as a less used route of attack then key cracking. I agree it should be encrypted soon though. The thought of using some type of certificate that I can drop on their PC once that is only good for their PC is nice, but I wouldn't know how to implement it. Or even a per-PC key that they can take with them and I don't have to worry about them sharing it.

---

### Post by changingstate on 2010-01-14
I had a little google, as I'm guessing using PEAP with WPA is what you're looking for, especially considering what you've been playing around with as far as freeradius goes. It's not something I've touched myself, but I have located an article on the similar EAP-TLS with should be close enough to give you a working illustration and may well prove satisfactory.

[http://www.linuxjournal.com/article/8095](http://www.linuxjournal.com/article/8095)

As far as your assertions that you think MAC address filtering is in any way a secure method of administering your wireless network, I invite you to install aircrack-ng and iw from the repositories ( assuming you have a machine with compatible hardware ) and actually look at what you're broadcasting to attackers.

---

### Post by HuckBerry on 2010-01-14
The certificate / CA scheme does seem like it is fairly secure (used over an encrypted protocol) and is great in the sense that I can install the cert and be done with it for that client. I think my issue resides with configuring the freeradius server to use them. It is supposedly explained in the followup to your link (which I will now read), but it does make me wonder about how devices like Ipods will handle this. 

MAC filtering is very hands off so the IPOD doesn't even know it's being filtered. I don't know if it is even possible to install a cert on an IPOD (and one of these devices is an offender, based on my logs). However I'd like to use my own of couse, so it is important that I don't have to make and exceptions for them.

(note, I am in no way defending MAC filtering. It is a bad-bad-bad form of security, but it is really simple, globally accepted, and centerally managed.)

---

### Post by changingstate on 2010-01-14
It depends very much on the device. Sadly, there's security versus usability issues with wireless security systems, much like the fact we all know we should set 20 character passwords but don't because it's damned inconvenient to have to type them constantly. 

Still later versions of the iphone and ipod touch firmware will, apparently : [https://wiki.thayer.dartmouth.edu/display/computing/Configuring+an+iPhone+or+iPod+Touch+for+the+Dartmouth+Secure+Wireless+Network](https://wiki.thayer.dartmouth.edu/display/computing/Configuring+an+iPhone+or+iPod+Touch+for+the+Dartmouth+Secure+Wireless+Network)

As far as what you said about MAC filtering, if you can't see that isn't not just bad-bad-bad but utterly useless in a situation where the clients are transmitting their MAC address constantly while online for anyone within range to sniff and most people with any sense know of the existence of the feature, all I can do is shake my head sadly and hope you don't live near black hats, spammers or paedophiles.

---

### Post by HuckBerry on 2010-01-14
The only one I'm worried about just moved back to Buffalo, New York (He's why this came to my attention). But it's a matter of what *should* be done just in case. And a matter of knowing how to do it - so that when it matters, it can be done right the first time.

---

### Post by HuckBerry on 2010-01-14
So I've decided to jump in headfirst into this wireless security overhual.
I setup a clean new Ubuntu.10 server, installed freeradius(and related packages).
and I started generating Certificates to use with EAP-TLS. Using the makefile that freeradius comes with, it seems the output is still lacking a client cert. Not sure why yet (maybe they intend for you to use PEAP or some other protocol) but that is a serious stumbling block at the moment cause WinXP wont authentcate w/o sending some type of cert to the RADIUS.

I've attempted to gen a few client certs on my own, but it is simply too late to be working on it now, so I will leave it here until tomorrow. When I get it working I will post a Big'Ole'N00b Walkthrough for everyone.

---

