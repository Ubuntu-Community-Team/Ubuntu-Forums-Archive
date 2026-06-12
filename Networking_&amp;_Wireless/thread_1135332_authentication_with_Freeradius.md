---
title: "authentication with Freeradius"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by darryl_ on 2009-04-24
I am using freeradius-server-2.1.4 on 8.04.  I am able to authenticate with no problems on windows xp and ubuntu 9.04 desktop however i am having a problem with OSX Leopard.

I am getting a self-assigned ip 169.254.x.x, but the debug indicates that access has been accepted.



rad_recv: Access-Request packet from host 192.168.3.42 port 2100, id=251, length=149

    NAS-IP-Address = 192.168.3.42

    NAS-Port-Type = Wireless-802.11

    NAS-Port = 11

    Framed-MTU = 1400

    User-Name = "mactest"

    Calling-Station-Id = "001ec2a62f7f"

    Called-Station-Id = "00186ec5bfc0"

    NAS-Identifier = "Enterprise Wireless AP"

    State = 0xe984c8baef8cddd7c8299b5ebbba4fe8

    EAP-Message = 0x020800061500

    Message-Authenticator = 0xc9ad5a84b6171bf13de739dafa88fdbc

+- entering group authorize {...}

++[preprocess] returns ok

++[chap] returns noop

++[mschap] returns noop

[suffix] No '@' in User-Name = "mactest", looking up realm NULL

[suffix] No such realm "NULL"

++[suffix] returns noop

[eap] EAP packet type response id 8 length 6

[eap] Continuing tunnel setup.

++[eap] returns ok

Found Auth-Type = EAP

+- entering group authenticate {...}

[eap] Request found, released from the list

[eap] EAP/ttls

[eap] processing type ttls

[ttls] Authenticate

[ttls] processing EAP-TLS

[ttls] Received TLS ACK

[ttls] ACK handshake is finished

[ttls] eaptls_verify returned 3 

[ttls] eaptls_process returned 3 

[eap] Freeing handler

++[eap] returns ok

+- entering group post-auth {...}

++[exec] returns noop

Sending Access-Accept of id 251 to 192.168.3.42 port 2100

    MS-MPPE-Recv-Key = 0x25f5f8ac08dee213f0b5ea1c89ef26a2666693deff96e60543809a6f8d17e560

    MS-MPPE-Send-Key = 0x4915c102d56046598bff6e290d6f706ec51422d8ad4525c1a1d25b448e7a2a73

    EAP-Message = 0x03080004

    Message-Authenticator = 0x00000000000000000000000000000000

    User-Name = "mactest"

Finished request 7.

Going to the next request



Any suggestions?

---

