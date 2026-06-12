---
title: "fix networking gtalk pidgin"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by ciapecki on 2009-11-26
ubuntu 9.10 Karmic 
2.6.31-15-generic-pae

I had everything working, but then it happened, I tried firestarter, iptables, etc...

currently I removed all of them and iptables is empty.

But some networking is still not working:
1. pidgin (2.6.3, 2.6.2) gtalk gives: Server closed the connection
   debug window:
```

[COLOR=#000000](21:29:23) **account:** Connecting to account ciapecki@googlemail.com/pidgin.
(21:29:23) **connection:** Connecting. gc = 0x9cbc950
(21:29:23) **dns:** DNS query for 'talk.google.com' queued
[/COLOR][COLOR=#660000](21:29:23) **dns:** Wait for DNS child 14653 failed: No child processes
[/COLOR][COLOR=#000000](21:29:23) **dns:** Created new DNS child 14758, there are now 1 children.
(21:29:23) **dns:** Successfully sent DNS request to child 14758
(21:29:23) **dns:** Got response for 'talk.google.com'
(21:29:23) **dnsquery:** IP resolved for talk.google.com
(21:29:23) **proxy:** Attempting connection to 209.85.137.125
(21:29:23) **proxy:** Connecting to talk.google.com:5222 with no proxy
(21:29:23) **proxy:** Connection in progress
(21:29:23) **proxy:** Connecting to talk.google.com:5222.
(21:29:23) **proxy:** Connected to talk.google.com:5222.
[/COLOR][COLOR=#666666](21:29:23) **jabber:** Sending: <?xml version='1.0' ?>
(21:29:23) **jabber:** Sending: <stream:stream to='googlemail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
[/COLOR][COLOR=#000000](21:29:23) **jabber:** Recv (143): <stream:stream from="googlemail.com" id="0AE4D5BBBCFCE528" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
(21:29:23) **jabber:** Recv (210): <stream:features><starttls xmlns="urn:ietf:params:xml:ns:xmpp-tls"><required/></starttls><mechanisms xmlns="urn:ietf:params:xml:ns:xmpp-sasl"><mechanism>X-GOOGLE-TOKEN</mechanism></mechanisms></stream:features>
[/COLOR][COLOR=#666666](21:29:23) **jabber:** Sending: <starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'/>
[/COLOR][COLOR=#000000](21:29:23) **jabber:** Recv (50): <proceed xmlns="urn:ietf:params:xml:ns:xmpp-tls"/>
(21:29:23) **nss:** subject=CN=googlemail.com,O=Google Inc.,L=Mountain View,ST=California,C=US issuer=OU=Equifax Secure Certificate Authority,O=Equifax,C=US
(21:29:23) **nss:** subject=OU=Equifax Secure Certificate Authority,O=Equifax,C=US issuer=OU=Equifax Secure Certificate Authority,O=Equifax,C=US
(21:29:23) **certificate/x509/tls_cached:** Starting verify for talk.google.com
(21:29:23) **certificate/x509/tls_cached:** Checking for cached cert...
(21:29:23) **certificate/x509/tls_cached:** ...Found cached cert
(21:29:23) **nss/x509:** Loading certificate from /home/chris/.purple/certificates/x509/tls_peers/talk.google.com
(21:29:23) **certificate/x509/tls_cached:** Peer cert matched cached
(21:29:23) **certificate:** Successfully verified certificate for talk.google.com
[/COLOR][COLOR=#ff0000](21:29:23) **jabber:** XML parser error for JabberStream 0x9c494d0: Domain 1, code 5, level 3: Extra content at the end of the document
[/COLOR][COLOR=#666666](21:29:23) **jabber:** Sending (ssl): <stream:stream to='googlemail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
[/COLOR][COLOR=#000000](21:29:23) **jabber:** Recv (ssl)(143): <stream:stream from="googlemail.com" id="1C24B86BE11B2760" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
(21:29:23) **jabber:** Recv (ssl)(166): <stream:features><mechanisms xmlns="urn:ietf:params:xml:ns:xmpp-sasl"><mechanism>PLAIN</mechanism><mechanism>X-GOOGLE-TOKEN</mechanism></mechanisms></stream:features>
[/COLOR][COLOR=#666666](21:29:23) **jabber:** Sending (ssl): <auth xmlns='urn:ietf:params:xml:ns:xmpp-sasl' xmlns:ga='http://www.google.com/talk/protocol/auth' ga:client-uses-full-bind-result='true' mechanism='PLAIN'>password removed</auth>
[/COLOR][COLOR=#000000](21:29:25) **util:** Writing file accounts.xml to directory /home/chris/.purple
(21:29:25) **util:** Writing file /home/chris/.purple/accounts.xml
(21:29:43) **connection:** Connection error on 0x9cbc950 (reason: 0 description: Server closed the connection)
(21:29:43) **account:** Disconnecting account ciapecki@googlemail.com/pidgin (0x966de88)
(21:29:43) **connection:** Disconnecting connection 0x9cbc950
[/COLOR][COLOR=#666666](21:29:43) **jabber:** Sending (ssl): </stream:stream>
[/COLOR][COLOR=#ff0000](21:29:43) **jabber:** XML parser error for JabberStream 0x9c494d0: Domain 1, code 5, level 3: Extra content at the end of the document
[/COLOR][COLOR=#000000](21:29:43) **connection:** Destroying connection 0x9cbc950[/COLOR]

```[COLOR=#000000]

2. cannot send email from my work network (before I could)
(the workaround for this one is to install firestarter and turn the firewall off in firestarter)

Where actually could I start digging to correct that mess?

thanks,
chris


[/COLOR]

---

### Post by ciapecki on 2009-11-27
just a quick update.
do not know what actually happened but all is working now, I did not install anything new, nor removed, but it seems part of the problem was the work VPN,

---

