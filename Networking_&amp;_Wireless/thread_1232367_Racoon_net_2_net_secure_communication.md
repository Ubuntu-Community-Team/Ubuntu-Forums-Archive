---
title: "Racoon net 2 net secure communication"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by FFT on 2009-08-05
Good day everybody!
Have some problem with securing linking between two networks.

There are two servers:

**Desktop 1 Ubuntu 9.0.4 2.6.28-15-generic i686 GNU/Linux**
int1 192.168.1.200/22
int2 10.0.0.1/8

**Server 2 Ubuntu 9.0.4 2.0.4.28-15-server Ubuntu SMP i686**
int1 192.168.1.201/22
int2 172.16.1.1/16

IPSEC-TOOLS 0.7.2
RACOON 0.7.2

There is no ping host to host.
**Desktop CONFIG**
***racoon.conf:***
_________________________________
path include "/etc/racoon";
path pre_shared_key "/etc/racoon/psk.txt";
path certificate "/etc/racoon/cert";
log notify;
padding
{
   maximum_length 20;
   randomize off;
   strict_check off;
   exclusive_tail off;
}

listen
{
   isakmp 192.168.1.200 [500];
}

timer
{
   counter 5;
   interval 20 sec;
   persend 1;
   phase1 30 sec;
   phase2 15 sec;
}

#IKE phase 1
remote 192.168.1.201
{
   exchange_mode main, aggressive;
   doi ipsec_doi;
   situation identity_only;
   my_identifier address;
   lifetime time 1 hour;
   initial_contact on;
   proposal_check obey;

   proposal
   {
      encryption_algorithm 3des;
      hash_algorithm sha1;
      authentication_method pre_shared_key;
      dh_group 2;
   }
}

sainfo address 10.0.0.0/8 any address 172.16.0.0/16 any
{
pfs_group 2;
lifetime time 12 hour ;
encryption_algorithm blowfish ;
authentication_algorithm hmac_sha1, hmac_md5 ;
compression_algorithm deflate ;
}
sainfo address 192.168.1.200/32 any address 172.16.0.0/16 any
{
pfs_group 2;
lifetime time 12 hour ;
encryption_algorithm blowfish ;
authentication_algorithm hmac_sha1, hmac_md5 ;
compression_algorithm deflate ;
}
sainfo address 192.168.1.200/32 any address 192.168.1.201/32 any
{
pfs_group 2;
lifetime time 12 hour ;
encryption_algorithm blowfish ;
authentication_algorithm hmac_sha1, hmac_md5 ;
compression_algorithm deflate ;
}
sainfo address 10.0.0.0/8 any address 192.168.1.201/32 any
{
pfs_group 2;
lifetime time 12 hour ;
encryption_algorithm blowfish ;
authentication_algorithm hmac_sha1, hmac_md5 ;
compression_algorithm deflate ;
}

***ipsec-tools.conf:***
__________________________________________

#!/usr/sbin/setkey -f

# NOTE: Do not use this file if you use racoon with racoon-tool
# utility. racoon-tool will setup SAs and SPDs automatically using
# /etc/racoon/racoon-tool.conf configuration.
#

## Flush the SAD and SPD
#
flush;
spdflush;
spdadd 10.0.0.0/8 172.16.0.0/16 any -P out ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;
spdadd 10.0.0.0/8 192.168.1.201/32 any -P out ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;
spdadd 192.168.1.200/32 192.168.1.201/32 any -P out ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;
spdadd 192.168.1.200/32 172.16.0.0/16 any -P out ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;
spdadd 172.16.0.0/16 10.0.0.0/8 any -P in ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;
spdadd 172.16.0.0/16 192.168.1.200/32 any -P in ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;
spdadd 192.168.1.201/32 10.0.0.0/8 any -P in ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;
spdadd 192.168.1.201/32 192.168.1.200/32 any -P in ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;


**Server Config**:
***racoon.conf:***
path include "/etc/racoon";
path pre_shared_key "/etc/racoon/psk.txt";
path certificate "/etc/racoon/cert";
log notify;
padding
{
   maximum_length 20;
   randomize off;
   strict_check off;
   exclusive_tail off;
}

listen
{
   isakmp 192.168.1.201 [500];
}

timer
{
   counter 5;
   interval 20 sec;
   persend 1;
   phase1 30 sec;
   phase2 15 sec;
}

#IKE phase 1
remote 192.168.1.200
{
   exchange_mode main, aggressive;
   doi ipsec_doi;
   situation identity_only;

   my_identifier address;

   lifetime time 1 hour;
   initial_contact on;
   proposal_check obey;

   proposal
   {
      encryption_algorithm 3des;
      hash_algorithm sha1;
      authentication_method pre_shared_key;
      dh_group 2;
   }
}

##IKE phase 2

sainfo address 172.16.0.0/16 any address 10.0.0.0/8 any
{
        pfs_group 2;
        lifetime time 12 hour ;
        encryption_algorithm blowfish ;
        authentication_algorithm hmac_sha1, hmac_md5 ;
        compression_algorithm deflate ;
}

sainfo address 172.16.0.0/16 any address 192.168.1.200/32 any
{
        pfs_group 2;
        lifetime time 12 hour ;
        encryption_algorithm blowfish ;
        authentication_algorithm hmac_sha1, hmac_md5 ;
        compression_algorithm deflate ;
}

sainfo address 192.168.1.201/32 any address 192.168.1.200/32 any
{
        pfs_group 2;
        lifetime time 12 hour ;
        encryption_algorithm blowfish ;
        authentication_algorithm hmac_sha1, hmac_md5 ;
        compression_algorithm deflate ;
}

sainfo address 192.168.1.201/32 any address 10.0.0.0/8 any
{
        pfs_group 2;
        lifetime time 12 hour ;
        encryption_algorithm blowfish ;
        authentication_algorithm hmac_sha1, hmac_md5 ;
        compression_algorithm deflate ;
}

***ipsec-tools.conf:***
#!/usr/sbin/setkey -f

# NOTE: Do not use this file if you use racoon with racoon-tool
# utility. racoon-tool will setup SAs and SPDs automatically using
# /etc/racoon/racoon-tool.conf configuration.
#

## Flush the SAD and SPD
#
flush;
spdflush;
spdadd 172.16.0.0/16 10.0.0.0/8 any -P out ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;
spdadd 172.16.0.0/16 192.168.1.200/32 any -P out ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;
spdadd 192.168.1.201/32 10.0.0.0/8 any -P out ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;
spdadd 192.168.1.201/32 192.168.1.200/32 any -P out ipsec esp/tunnel/192.168.1.201-192.168.1.200/require;
spdadd 10.0.0.0/8 172.16.0.0/16 any -P in ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;
spdadd 10.0.0.0/8 192.168.1.201/32 any -P in ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;
spdadd 192.168.1.200/32 192.168.1.201/32 any -P in ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;
spdadd 192.168.1.200/32 172.16.0.0/16 any -P in ipsec esp/tunnel/192.168.1.200-192.168.1.201/require;

[B]
Any Idea?
Thanks for the answers. Excuse Me for My English. It is not native.[/B]

---

### Post by FFT on 2009-08-05
There is no error in /var/log 

Aug  5 21:24:20 mobian racoon-tool[5593]: racoon stopped.
Aug  5 21:24:20 mobian racoon-tool[5593]: flushed SAD and SPD.
Aug  5 21:24:20 mobian racoon-tool[5593]: unloaded IPSEC/crypto modules
Aug  5 21:24:21 mobian racoon-tool[5593]: loaded IPSEC/crypto modules.
Aug  5 21:24:21 mobian racoon-tool[5593]: flushed SAD and SPD.
Aug  5 21:24:21 mobian racoon-tool[5593]: loaded SAD and SPD.
Aug  5 21:24:21 mobian racoon-tool[5593]: configured racoon.
Aug  5 21:24:21 mobian racoon: INFO: @(#)ipsec-tools 0.7 ([http://ipsec-tools.sourceforge.net](http://ipsec-tools.sourceforge.net)) 
Aug  5 21:24:21 mobian racoon: INFO: @(#)This product linked OpenSSL 0.9.8g 19 Oct 2007 ([http://www.openssl.org/](http://www.openssl.org/)) 
Aug  5 21:24:21 mobian racoon: INFO: Reading configuration from "/var/lib/racoon/racoon.conf" 
Aug  5 21:24:21 mobian racoon: INFO: Resize address pool from 0 to 255 
Aug  5 21:24:21 mobian racoon-tool[5593]: racoon started.


Have IDEA???

---

