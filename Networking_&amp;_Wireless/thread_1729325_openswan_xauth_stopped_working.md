---
title: "openswan xauth stopped working"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by jcoles on 2011-04-14
Sometime after 9-Apr-2011, my Openswan configuration to my employer stopped working. After phase1 is established, it should request my credentials for an XAUTH authentication. But now it just sits there. Repeating the ipsec auto --up command triggers the following repsonse:

```
"office" #2: initiating Quick Mode PSK+ENCRYPT+TUNNEL+PFS+UP+IKEv2ALLOW {using isakmp#1 msgid:8ed5aa5d proposal=3DES(3)_192-SHA1(2)_160, AES(12)_128-SHA1(2)_160 pfsgroup=OAKLEY_GROUP_MODP1536}
packet from <gateway_ip>:4500: Cannot do Quick Mode until XAUTH done.
```

So, where is my XAUTH? What happened?

I assume that nothing changed at work because my Windows netbook can still connect using Fortinet FortiClient. 

I changed nothing in my configuration. But, I may have accepted some updates through Update Manager. Is there some way to find out what updates I received in this time frame so that I might reverse this damage?

---

### Post by jcoles on 2011-04-15
I found the History function in Synaptic, but could not find any change that corresponds to the time when ipsec xauth stopped working. 

Reinstallation of openswan and xauth did not help.

---

### Post by jcoles on 2011-04-16
I checked with our IT guy and he told me the XAuth was temporarily turned off because of some issues with the LDAP server. 

Sure enough. OpenSwan worked just fine when I commented out the line 
leftxauthclient=yes

It's unfortunate that OpenSwan isn't smart enough to perform XAuth only if the other side requests it. FortiClient was not tripped up by this small configuration change. 

The OpenSwan log message was rather misleading, making it appear that the remote end was waiting for us to do XAuth when actually it was the other way around.

---

