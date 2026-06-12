---
title: "IPSec over IPv6 using Racoon doesn't work"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by KarlIvan on 2009-06-24
Hello,
I'm trying to set up a solely IPv6 network that uses IPSec. Eventually I want it the keys to work with X509 certificates, but right now, I'm having trouble with just using racoon to generate keys based on the policies I've defined. Below is my "/etc/ipsec-tools.conf" file. It's pretty much "copied and pasted" from the internet tutorials out there. The commented out stuff is when I set up the keys staticly, and that all worked fine.
> #!/usr/sbin/setkey -f

## Flush the SAD and SPD

 flush;
 spdflush;

# AH SAs using 128 bit long keys
#add fec0::c fec0::e ah 0x900 -A hmac-md5
#        0xc0291ff014dccdd03874d9e8e4cdf3e6;
#add fec0::e fec0::c ah 0x800 -A hmac-md5
#        0x96358c90783bbfa3d7b196ceabe0536b;

# ESP SAs using 192 bit long keys (168 + 24 parity)
#add fec0::c fec0::e esp 0x901 -E 3des-cbc
#        0x7aeaca3f87d060a12f4a4487d5a5c3355920fae69a96c831;
#add fec0::e fec0::c esp 0x801 -E 3des-cbc
#        0xf6ddb555acfd9d77b03ea3843f2653255afe8eb5573965df;

# Security policies
spdadd fec0::e fec0::c any -P out ipsec
    esp/transport//require;
#    ah/transport//require;
spdadd fec0::c fec0::e any -P in ipsec
    esp/transport//require;
#    ah/transport//require;Then I commented out the stuff that needed to be, leaving only the flush commands, and the policy-setting commands, and that's what's left right now. By the way, I shouldn't need a fwd policy right now. My traffic is going through two other computers, but it shouldn't matter at this point. Besides that, I tried tunneling my IPSec traffic through those two computers, and still nothing.

I'm using wireshark, and I can monitor the traffic that goes across the connections. Basically, something is wrong with the policies, to the point where the host (start) computer won't send any traffic because it can't encrypt the traffic (I'm guessing). I turned IPv4 back on, and put those addresses in, and it went as far as the final destination, but it wouldnt do anything with it. this is what came across in wireshark in IPv4:
> 
Source _______          Destination ___Protocol _ Info
192.168.1.134 _192.168.1.136 _ISAKMP   _ Identity Protection(Main Mode)
and then when I expanded the details it basically restated all the information I had in my "/etc/racoon/racoon.conf" file. What it didn't have was the pre-shared-key that I had in the default "/etc/racoon/psk.txt" file. I'm assuming because at that point, it was hashed to send across an unsecured connection (then again, I couldn't find any number that I would imagine was a hashed number).
Anyway, here is my "/etc/racoon/racoon.conf" file:
> 
path pre_shared_key "/etc/racoon/psk.txt";
#path certificate "/etc/racoon/certs";

remote anonymous {
#    generate_policy off;
        exchange_mode main; #,aggressive;
    proposal_check obey ;
    lifetime time 8000 seconds ;
#    send_cert off; #do not send certificate (default is on)
#    send_cr off; #do not send certificate request (default is on)
#    verify_cert off; #do not verify certificate (default is on)
#    passive on; #do not initiate negotiation
    my_identifier address fec0::e ;
        proposal {
                encryption_algorithm 3des;
                hash_algorithm md5; #sha1;
                authentication_method pre_shared_key;
                dh_group modp1024;
        }
}
 
sainfo anonymous {
        pfs_group modp768;
#    lifetime time 10 hour ;
        encryption_algorithm 3des; #, blowfish,rijndael;
        authentication_algorithm hmac_md5; #, hmac_sha1;
        compression_algorithm deflate;
}
And I don't imagine anyone will need it, but here is my pre-shared-key file "/etc/racoon./psk.txt":
> 
# IPv4/v6 addresses
fec0::c        potato
Also, I have no idea where the default log file is (the listed one isn't there), so I run the command "sudo racoon -l /path/for/log/log.txt" and it prints out some stuff, and then at the very end, it prints out all the addresses associated with the host connection, and after each one says "address already in use". I don't really pay much attention to that though, because that only happens when I get racoon to use my log file while racoon is already in use. If I shut down racoon, and start it over fresh with that line, then it doesn't tell me that.

Anyway, I've been struggling with this for the past few days, and there seems to be nothing on the internet with these problems so any help would be awesome right now. Thanks in advance

Karl

EDIT: There's also a line in the log file that reads: 
> compression algorithm can not be checked because sadb message doesn't support it.although I'm really not sure what that means because, as I understand, there is only one compression algorithm that can be used anyway (deflate). And besides, I've seen people on other forums get it to work while still getting this line in the logs.

---

### Post by KarlIvan on 2009-06-25
OK,

Since I'm assuming nobody here knows how to do this then, can anybody point me at somebody that can? (or the right direction?)

---

### Post by nickpoorman on 2009-06-25
I would really like to know how to do this as well. I have been struggling for some time setting this up on ubuntu. To begin I installed ipsec-tools via apt-get as well as racoon. (I was under the impression that racoon was now part of ipsec-tools but I guess not). Some of the tutorials I have looked at are below: 
 
 [http://www.fukt.bsnet.se/~teddy/debian-ipsec]("http://www.fukt.bsnet.se/%7Eteddy/debian-ipsec")
 [http://www.ipsec-howto.org/x304.html](http://www.ipsec-howto.org/x304.html)
 
 [http://www.howtoforge.org/racoon_roadwarrior_vpn_p6](http://www.howtoforge.org/racoon_roadwarrior_vpn_p6)
  (although I am not trying to create a vpn, just establish connections between hosts automatically with ipsec as to keep my config file small)
 
 for generating x.509 keys:[ http://www.gallowglass.org/]("http://www.gallowglass.org/")
 
 I too have been able to get the config to work statically with setkey. However having a few hundred clients in a config file would begin to get a bit hard to manage. I have begun to think that there might be more needed to get racoon to work on ubuntu. Maybe some sort of iptables adjustment or other libraries that are needed by racoon? 

Any help would be greatly appreciated as this project is at a standstill at this point.

---

### Post by nickpoorman on 2009-06-25
now that I think about it I wonder if there is also anything that needs to be done with the kernel in order to get this to work properly.

---

### Post by KarlIvan on 2009-06-25
quick add on. do we need to have L2TP to run racoon?

---

### Post by nickpoorman on 2009-06-26
...gonna give strongSwan a try. looks promising...

---

### Post by KarlIvan on 2009-06-29
bump

---geez these forums get flooded easy

---

