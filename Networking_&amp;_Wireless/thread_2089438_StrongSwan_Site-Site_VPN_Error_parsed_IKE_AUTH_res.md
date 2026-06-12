---
title: "StrongSwan Site-Site VPN Error: parsed IKE_AUTH response 1 [ N(AUTH_FAILED) ] ......!"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by zohns123 on 2012-11-29
[B]Error: parsed IKE_AUTH response 1 [ N(AUTH_FAILED) ] 
received AUTHENTICATION_FAILED notify error
[/B]
Error does seems similar to the one spread on the web but non of the  solution working in my case, here I'm providing a detail information of  all my configuration of strongswan, please help 

Also followed the documentation here [http://www.strongswan.org/docs/readme4.htm#section_2.1](http://www.strongswan.org/docs/readme4.htm#section_2.1)  still no luck so far..

Running strongswan on Ubuntu 12.10 32 bit, 

I'm trying to create a site-to-site vpn, where Site1=worli(worli.vpn) and Site2=noida(noida.vpn) 
Hosts file of all the system has been modified to resolve worli/worli.vpn and noida/noida.vpn  

----------------------------------------------------- 
------------------Site1(worli)------------------ 
----------------------------------------------------- 

============================================= 
Output after running "sudo ipsec up net-net" 
============================================= 


--start-- 
worli@worli:/etc/ipsec.d$ sudo ipsec up net-net 
initiating IKE_SA net-net[6] to 192.168.10.4 
generating IKE_SA_INIT request 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) ] 
sending packet: from 192.168.10.3[500] to 192.168.10.4[500] 
received packet: from 192.168.10.4[500] to 192.168.10.3[500] 
parsed IKE_SA_INIT response 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) CERTREQ N(MULT_AUTH) ] 
received cert request for "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
sending cert request for "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
authentication of 'C=IN, L=Mumbai, O=comp, CN=worli.vpn' (myself) with RSA signature successful 
sending end entity cert "C=IN, L=Mumbai, O=comp, CN=worli.vpn" 
establishing CHILD_SA net-net 
generating IKE_AUTH request 1 [ IDi CERT N(INIT_CONTACT) CERTREQ IDr  AUTH SA TSi TSr N(MOBIKE_SUP) N(ADD_4_ADDR) N(MULT_AUTH) N(EAP_ONLY) ] 
sending packet: from 192.168.10.3[4500] to 192.168.10.4[4500] 
received packet: from 192.168.10.4[4500] to 192.168.10.3[4500] 
parsed IKE_AUTH response 1 [ N(AUTH_FAILED) ] 
received AUTHENTICATION_FAILED notify error 
worli@worli:/etc/ipsec.d$ 
--end-- 

====================================== 
Output "sudo ipsec listall" 
====================================== 

---start--- 
worli@worli:/etc/ipsec.d$ sudo ipsec listall 
000   
000 List of Public Keys: 
000   
000   identity: 'C=IN, L=Mumbai, O=comp, CN=worli.vpn' 
000   pubkey:    RSA 1024 bits, until Nov 26 16:41:48 2014 ok 
000   keyid:     d4:90:10:a8:53:ca:64:9d:f6:bc:95:6c:0e:e5:f2:2e:fa:0e:a1:59 
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   serial:    02 
000   
000 List of X.509 End Entity Certificates: 
000   
000   subject:  "C=IN, L=Mumbai, O=comp, CN=worli.vpn" 
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   serial:    02 
000   validity:  not before Nov 26 16:41:48 2012 ok 
000              not after  Nov 26 16:41:48 2014 ok 
000   pubkey:    RSA 1024 bits, has private key 
000   keyid:     d4:90:10:a8:53:ca:64:9d:f6:bc:95:6c:0e:e5:f2:2e:fa:0e:a1:59 
000   subjkey:   36:76:4d:54:a9:79:d3:7f:18:f7:b1:8f:b5:ba:14:86:75:1b:e4:13 
000   authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
000   
000 List of X.509 CA Certificates: 
000   
000   subject:  "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   serial:    01 
000   validity:  not before Nov 26 16:31:09 2012 ok 
000              not after  Nov 26 16:31:09 2015 ok 
000   pubkey:    RSA 1024 bits 
000   keyid:     35:65:36:91:2c:31:0e:c3:99:69:a9:7f:89:fb:bc:e2:87:10:4e:e2 
000   subjkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
000   authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
000   
000 List of X.509 CRLs: 
000   
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   revoked:   0 certificates 
000   distPts:  'file:///etc/ipsec.d/crls/compvpnca.crl' 
000   updates:   this Nov 29 13:52:18 2012 
000              next Nov 30 13:52:18 2012 warning (expires in 22 hours) 
000   
000 List of registered IKEv1 Algorithms: 
000   
000   encryption: BLOWFISH_CBC[openssl] 3DES_CBC[des] AES_CBC[aes] CAMELLIA_CBC[openssl] 
000   integrity:  HMAC_MD5[md5] HMAC_SHA1[sha1] HMAC_SHA2_256[sha2] HMAC_SHA2_384[sha2] HMAC_SHA2_512[sha2] 
000   dh-group:   MODP_1024[openssl] MODP_1536[openssl] MODP_2048[openssl] MODP_3072[openssl] MODP_4096[openssl] 
000               MODP_6144[openssl] MODP_8192[openssl] ECP_256[openssl] ECP_384[openssl] ECP_521[openssl] 
000               MODP_1024_160[openssl] MODP_2048_224[openssl] MODP_2048_256[openssl] ECP_192[openssl] ECP_224[openssl] 
000   random-gen: RNG_STRONG[random] RNG_TRUE[random] 
000   
000 List of registered ESP Algorithms: 
000   
000   encryption: DES_CBC 3DES_CBC CAST_CBC BLOWFISH_CBC NULL AES_CBC AES_CTR AES_CCM_8 AES_CCM_12 AES_CCM_16 AES_GCM_8 
000               AES_GCM_12 AES_GCM_16 CAMELLIA_CBC AES_GMAC SERPENT_CBC TWOFISH_CBC 
000   integrity:  HMAC_MD5 HMAC_SHA1 HMAC_SHA2_256 HMAC_SHA2_384 HMAC_SHA2_512 HMAC_RIPEMD AES_XCBC_96 NULL HMAC_SHA2_256_96 

List of X.509 End Entity Certificates: 

  subject:  "C=IN, L=Mumbai, O=comp, CN=worli.vpn" 
  issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  serial:    02 
  validity:  not before Nov 26 16:41:48 2012, ok 
             not after  Nov 26 16:41:48 2014, ok  
  pubkey:    RSA 1024 bits, has private key 
  keyid:     d4:90:10:a8:53:ca:64:9d:f6:bc:95:6c:0e:e5:f2:2e:fa:0e:a1:59 
  subjkey:   36:76:4d:54:a9:79:d3:7f:18:f7:b1:8f:b5:ba:14:86:75:1b:e4:13 
  authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 

List of X.509 CA Certificates: 

  subject:  "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  serial:    01 
  validity:  not before Nov 26 16:31:09 2012, ok 
             not after  Nov 26 16:31:09 2015, ok  
  pubkey:    RSA 1024 bits 
  keyid:     35:65:36:91:2c:31:0e:c3:99:69:a9:7f:89:fb:bc:e2:87:10:4e:e2 
  subjkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
  authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 

List of X.509 CRLs: 

  issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  revoked:   0 certificates 
  updates:   this Nov 29 13:52:18 2012 
             next Nov 30 13:52:18 2012, ok (expires in 22 hours)  

List of registered IKEv2 Algorithms: 

  encryption: AES_CBC[aes] 3DES_CBC[des] DES_CBC[des] DES_ECB[des] CAMELLIA_CBC[openssl] RC5_CBC[openssl] 
              IDEA_CBC[openssl] CAST_CBC[openssl] BLOWFISH_CBC[openssl] NULL[openssl] AES_CTR[ctr] CAMELLIA_CTR[ctr] 
  integrity:  AES_XCBC_96[xcbc] CAMELLIA_XCBC_96[xcbc] HMAC_SHA1_96[hmac] HMAC_SHA1_128[hmac] HMAC_SHA1_160[hmac] 
              HMAC_SHA2_256_128[hmac] HMAC_SHA2_256_256[hmac] HMAC_MD5_96[hmac] HMAC_MD5_128[hmac] 
              HMAC_SHA2_384_192[hmac] HMAC_SHA2_384_384[hmac] HMAC_SHA2_512_256[hmac] 
  aead:       AES_CCM_8[ccm] AES_CCM_12[ccm] AES_CCM_16[ccm] CAMELLIA_CCM_8[ccm] CAMELLIA_CCM_12[ccm] 
              CAMELLIA_CCM_16[ccm] AES_GCM_8[gcm] AES_GCM_12[gcm] AES_GCM_16[gcm] 
  hasher:     HASH_SHA1[sha1] HASH_SHA224[sha2] HASH_SHA256[sha2] HASH_SHA384[sha2] HASH_SHA512[sha2] HASH_MD5[md5] 
              HASH_MD2[openssl] HASH_MD4[openssl] 
  prf:        PRF_KEYED_SHA1[sha1] PRF_FIPS_SHA1_160[fips-prf] PRF_AES128_XCBC[xcbc] PRF_CAMELLIA128_XCBC[xcbc] 
              PRF_HMAC_SHA1[hmac] PRF_HMAC_SHA2_256[hmac] PRF_HMAC_MD5[hmac] PRF_HMAC_SHA2_384[hmac] 
              PRF_HMAC_SHA2_512[hmac] 
  dh-group:   MODP_2048[openssl] MODP_2048_224[openssl] MODP_2048_256[openssl] MODP_1536[openssl] ECP_256[openssl] 
              ECP_384[openssl] ECP_521[openssl] ECP_224[openssl] ECP_192[openssl] MODP_3072[openssl] MODP_4096[openssl] 
              MODP_6144[openssl] MODP_8192[openssl] MODP_1024[openssl] MODP_1024_160[openssl] MODP_768[openssl] 
              MODP_CUSTOM[openssl] 
  random-gen: RNG_STRONG[random] RNG_TRUE[random] 
worli@worli:/etc/ipsec.d$  
---end--- 


================================== 
Configuration in /etc/ipsec.conf 
================================== 

--start-- 
# ipsec.conf - strongSwan IPsec configuration file 

# basic configuration 

config setup 
    # plutodebug=all 
    # crlcheckinterval=600 
    # strictcrlpolicy=no 
    # cachecrls=yes 
    # nat_traversal=yes 
    # charonstart=yes 
    # plutostart=yes 

# Add connections here. 

# Sample VPN connections 

#conn sample-self-signed 
#      left=%defaultroute 
#      leftsubnet=10.1.0.0/16 
#      leftcert=selfCert.der 
#      leftsendcert=never 
#      right=192.168.0.2 
#      rightsubnet=10.2.0.0/16 
#      rightcert=peerCert.der 
#      auto=start 

#conn sample-with-ca-cert 
#      left=%defaultroute 
#      leftsubnet=10.1.0.0/16 
#      leftcert=myCert.pem 
#      right=192.168.0.2 
#      rightsubnet=10.2.0.0/16 
#      rightid="C=CH, O=Linux strongSwan CN=peer name" 
#      keyexchange=ikev2 
#      auto=start 

conn net-net 
     left=%defaultroute 
     leftsubnet=192.168.111.0/24 
     leftcert=worlicert.pem 
     right=192.168.10.4 
     rightsubnet=192.168.222.0/24 
     rightid="C=IN, O=comp, CN=noida.vpn" 
     auto=start 
--end-- 


================================= 
/etc/ipsec.secret 
================================= 

---start--- 
# This file holds shared secrets or RSA private keys for inter-Pluto 
# authentication.  See ipsec_pluto(8) manpage, and HTML documentation. 

# RSA private key for this host, authenticating it to any other host 
# which knows the public part.  Suitable public keys, for ipsec.conf, DNS, 
# or configuration of other implementations, can be extracted conveniently 
# with "ipsec showhostkey". 

# this file is managed with debconf and will contain the automatically created private key 
: RSA worlikey.pem 
---end--- 



----------------------------------------------------- 
------------------Site2(noida)------------------ 
----------------------------------------------------- 

============================================= 
Output after running "sudo ipsec up net-net" 
============================================= 

--start-- 
noida@noida:/etc/ipsec.d/certs$ sudo ipsec up net-net 
initiating IKE_SA net-net[2] to 192.168.10.3 
generating IKE_SA_INIT request 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) ] 
sending packet: from 192.168.10.4[500] to 192.168.10.3[500] 
received packet: from 192.168.10.3[500] to 192.168.10.4[500] 
parsed IKE_SA_INIT response 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) CERTREQ N(MULT_AUTH) ] 
received cert request for "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
sending cert request for "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
authentication of 'C=IN, L=Mumbai, O=comp, CN=noida.vpn' (myself) with RSA signature successful 
sending end entity cert "C=IN, L=Mumbai, O=comp, CN=noida.vpn" 
establishing CHILD_SA net-net 
generating IKE_AUTH request 1 [ IDi CERT N(INIT_CONTACT) CERTREQ IDr  AUTH SA TSi TSr N(MOBIKE_SUP) N(ADD_4_ADDR) N(MULT_AUTH) N(EAP_ONLY) ] 
sending packet: from 192.168.10.4[4500] to 192.168.10.3[4500] 
received packet: from 192.168.10.3[4500] to 192.168.10.4[4500] 
parsed IKE_AUTH response 1 [ N(AUTH_FAILED) ] 
received AUTHENTICATION_FAILED notify error 
noida@noida:/etc/ipsec.d/certs$  
--end-- 


====================================== 
Output "sudo ipsec listall" 
====================================== 

---start--- 
noida@noida:/etc/ipsec.d/certs$ sudo ipsec listall 
[sudo] password for noida:  
000   
000 List of Public Keys: 
000   
000   identity: 'C=IN, L=Mumbai, O=comp, CN=noida.vpn' 
000   pubkey:    RSA 1024 bits, until Nov 26 16:54:56 2014 ok 
000   keyid:     ee:38:90:46:b4:fe:0d:1e:37:4e:26:ea:b3:af:44:58:82:a5:5a:62 
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   serial:    03 
000   
000 List of X.509 End Entity Certificates: 
000   
000   subject:  "C=IN, L=Mumbai, O=comp, CN=noida.vpn" 
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   serial:    03 
000   validity:  not before Nov 26 16:54:56 2012 ok 
000              not after  Nov 26 16:54:56 2014 ok 
000   pubkey:    RSA 1024 bits, has private key 
000   keyid:     ee:38:90:46:b4:fe:0d:1e:37:4e:26:ea:b3:af:44:58:82:a5:5a:62 
000   subjkey:   3c:c1:06:6b:0d:4a:a1:e3:0f:97:b3:4e:6e:a7:73:9b:4d:6e:a9:1b 
000   authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
000   
000 List of X.509 CA Certificates: 
000   
000   subject:  "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   serial:    01 
000   validity:  not before Nov 26 16:31:09 2012 ok 
000              not after  Nov 26 16:31:09 2015 ok 
000   pubkey:    RSA 1024 bits 
000   keyid:     35:65:36:91:2c:31:0e:c3:99:69:a9:7f:89:fb:bc:e2:87:10:4e:e2 
000   subjkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
000   authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
000   
000 List of X.509 CRLs: 
000   
000   issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
000   revoked:   0 certificates 
000   distPts:  'file:///etc/ipsec.d/crls/compvpnca.crl' 
000   updates:   this Nov 29 13:56:12 2012 
000              next Nov 30 13:56:12 2012 warning (expires in 22 hours) 
000   
000 List of registered IKEv1 Algorithms: 
000   
000   encryption: BLOWFISH_CBC[openssl] 3DES_CBC[des] AES_CBC[aes] CAMELLIA_CBC[openssl] 
000   integrity:  HMAC_MD5[md5] HMAC_SHA1[sha1] HMAC_SHA2_256[sha2] HMAC_SHA2_384[sha2] HMAC_SHA2_512[sha2] 
000   dh-group:   MODP_1024[openssl] MODP_1536[openssl] MODP_2048[openssl] MODP_3072[openssl] MODP_4096[openssl] 
000               MODP_6144[openssl] MODP_8192[openssl] ECP_256[openssl] ECP_384[openssl] ECP_521[openssl] 
000               MODP_1024_160[openssl] MODP_2048_224[openssl] MODP_2048_256[openssl] ECP_192[openssl] ECP_224[openssl] 
000   random-gen: RNG_STRONG[random] RNG_TRUE[random] 
000   
000 List of registered ESP Algorithms: 
000   
000   encryption: DES_CBC 3DES_CBC CAST_CBC BLOWFISH_CBC NULL AES_CBC AES_CTR AES_CCM_8 AES_CCM_12 AES_CCM_16 AES_GCM_8 
000               AES_GCM_12 AES_GCM_16 CAMELLIA_CBC AES_GMAC SERPENT_CBC TWOFISH_CBC 
000   integrity:  HMAC_MD5 HMAC_SHA1 HMAC_SHA2_256 HMAC_SHA2_384 HMAC_SHA2_512 HMAC_RIPEMD AES_XCBC_96 NULL HMAC_SHA2_256_96 

List of X.509 End Entity Certificates: 

  subject:  "C=IN, L=Mumbai, O=comp, CN=noida.vpn" 
  issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  serial:    03 
  validity:  not before Nov 26 16:54:56 2012, ok 
             not after  Nov 26 16:54:56 2014, ok  
  pubkey:    RSA 1024 bits, has private key 
  keyid:     ee:38:90:46:b4:fe:0d:1e:37:4e:26:ea:b3:af:44:58:82:a5:5a:62 
  subjkey:   3c:c1:06:6b:0d:4a:a1:e3:0f:97:b3:4e:6e:a7:73:9b:4d:6e:a9:1b 
  authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 

List of X.509 CA Certificates: 

  subject:  "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  serial:    01 
  validity:  not before Nov 26 16:31:09 2012, ok 
             not after  Nov 26 16:31:09 2015, ok  
  pubkey:    RSA 1024 bits 
  keyid:     35:65:36:91:2c:31:0e:c3:99:69:a9:7f:89:fb:bc:e2:87:10:4e:e2 
  subjkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 
  authkey:   9a:76:da:f2:a9:a2:18:63:a4:b7:b4:54:26:dc:1d:f7:29:f7:e4:e1 

List of X.509 CRLs: 

  issuer:   "C=IN, L=Mumbai, O=comp, CN=compvpn ca" 
  revoked:   0 certificates 
  updates:   this Nov 29 13:56:12 2012 
             next Nov 30 13:56:12 2012, ok (expires in 22 hours)  

List of registered IKEv2 Algorithms: 

  encryption: AES_CBC[aes] 3DES_CBC[des] DES_CBC[des] DES_ECB[des] CAMELLIA_CBC[openssl] RC5_CBC[openssl] 
              IDEA_CBC[openssl] CAST_CBC[openssl] BLOWFISH_CBC[openssl] NULL[openssl] AES_CTR[ctr] CAMELLIA_CTR[ctr] 
  integrity:  AES_XCBC_96[xcbc] CAMELLIA_XCBC_96[xcbc] HMAC_SHA1_96[hmac] HMAC_SHA1_128[hmac] HMAC_SHA1_160[hmac] 
              HMAC_SHA2_256_128[hmac] HMAC_SHA2_256_256[hmac] HMAC_MD5_96[hmac] HMAC_MD5_128[hmac] 
              HMAC_SHA2_384_192[hmac] HMAC_SHA2_384_384[hmac] HMAC_SHA2_512_256[hmac] 
  aead:       AES_CCM_8[ccm] AES_CCM_12[ccm] AES_CCM_16[ccm] CAMELLIA_CCM_8[ccm] CAMELLIA_CCM_12[ccm] 
              CAMELLIA_CCM_16[ccm] AES_GCM_8[gcm] AES_GCM_12[gcm] AES_GCM_16[gcm] 
  hasher:     HASH_SHA1[sha1] HASH_SHA224[sha2] HASH_SHA256[sha2] HASH_SHA384[sha2] HASH_SHA512[sha2] HASH_MD5[md5] 
              HASH_MD2[openssl] HASH_MD4[openssl] 
  prf:        PRF_KEYED_SHA1[sha1] PRF_FIPS_SHA1_160[fips-prf] PRF_AES128_XCBC[xcbc] PRF_CAMELLIA128_XCBC[xcbc] 
              PRF_HMAC_SHA1[hmac] PRF_HMAC_SHA2_256[hmac] PRF_HMAC_MD5[hmac] PRF_HMAC_SHA2_384[hmac] 
              PRF_HMAC_SHA2_512[hmac] 
  dh-group:   MODP_2048[openssl] MODP_2048_224[openssl] MODP_2048_256[openssl] MODP_1536[openssl] ECP_256[openssl] 
              ECP_384[openssl] ECP_521[openssl] ECP_224[openssl] ECP_192[openssl] MODP_3072[openssl] MODP_4096[openssl] 
              MODP_6144[openssl] MODP_8192[openssl] MODP_1024[openssl] MODP_1024_160[openssl] MODP_768[openssl] 
              MODP_CUSTOM[openssl] 
  random-gen: RNG_STRONG[random] RNG_TRUE[random] 
noida@noida:/etc/ipsec.d/certs$  
---end---  


================================== 
Configuration in /etc/ipsec.conf 
================================== 

--start-- 
# ipsec.conf - strongSwan IPsec configuration file 

# basic configuration 

config setup 
    # plutodebug=all 
    # crlcheckinterval=600 
    # strictcrlpolicy=no 
    # cachecrls=yes 
    # nat_traversal=yes 
    # charonstart=yes 
    # plutostart=yes 

# Add connections here. 

# Sample VPN connections 

#conn sample-self-signed 
#      left=%defaultroute 
#      leftsubnet=10.1.0.0/16 
#      leftcert=selfCert.der 
#      leftsendcert=never 
#      right=192.168.0.2 
#      rightsubnet=10.2.0.0/16 
#      rightcert=peerCert.der 
#      auto=start 

#conn sample-with-ca-cert 
#      left=%defaultroute 
#      leftsubnet=10.1.0.0/16 
#      leftcert=myCert.pem 
#      right=192.168.0.2 
#      rightsubnet=10.2.0.0/16 
#      rightid="C=CH, O=Linux strongSwan CN=peer name" 
#      keyexchange=ikev2 
#      auto=start 

conn net-net 
     left=%defaultroute 
     leftsubnet=192.168.222.0/24 
     leftcert=noidacert.pem 
     right=192.168.10.3 
     rightsubnet=192.168.111.0/24 
     rightid="C=IN, O=comp, CN=worli.vpn" 
     auto=start 
--end-- 


================================= 
/etc/ipsec.secret 
================================= 

---start--- 
# This file holds shared secrets or RSA private keys for inter-Pluto 
# authentication.  See ipsec_pluto(8) manpage, and HTML documentation. 

# RSA private key for this host, authenticating it to any other host 
# which knows the public part.  Suitable public keys, for ipsec.conf, DNS, 
# or configuration of other implementations, can be extracted conveniently 
# with "ipsec showhostkey". 

# this file is managed with debconf and will contain the automatically created private key 
: RSA noidakey.pem 
---end---

---

