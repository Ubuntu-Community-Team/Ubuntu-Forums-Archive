---
title: "FreeRADIUS + OpenLDAP + PEAP Problem"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Constabla on 2009-05-13
Hello,

For a school project I am setting up a Wireless environment.
I have 2 (virtual) Ubuntu 8.04LTS Server machines.
One running FreeRADIUS, one running OpenLDAP.
I want to be able to log on to my wireless network using PEAP (MsCHAPv2) authentication.

OpenLDAP and FreeRADIUS are both running and the network configuration is good, machines can ping each other and the accesspoint.

I made the LDAP users using phpldapadmin, i made Samba3 users so they have an sambaLMPassword and sambaNTPassword attribute. For the rest i basically folowed [this]("http://vuksan.com/linux/dot1x/802-1x-LDAP.html#PEAP_with_OpenLDAP") howto.

When i try to log in I receive the following errors in my log files.

OpenLDAP :
```
May  6 15:21:16 wifi-lab-ldap slapd[4196]: conn=13 op=40 SRCH base="dc=fnt,dc=hu,dc=nl" scope=2 deref=0 filter="(uid=john)" 
May  6 15:21:17 wifi-lab-ldap slapd[4196]: conn=13 op=40 SRCH attr=userPassword radiusNASIpAddress radiusExpiration acctFlags Password sambaLMPassword radiusCallingStationId radiusCalledStationId radiusSimultaneousUse radiusAuthType radiusCheckItem radiusTunnelPrivateGroupId radiusTunnelMediumType radiusTunnelType radiusReplyMessage radiusLoginLATPort radiusPortLimit radiusFramedAppleTalkZone radiusFramedAppleTalkNetwork radiusFramedAppleTalkLink radiusLoginLATGroup radiusLoginLATNode radiusLoginLATService radiusTerminationAction radiusIdleTimeout radiusSessionTimeout radiusClass radiusFramedIPXNetwork radiusCallbackId radiusCallbackNumber radiusLoginTCPPort radiusLoginService radiusLoginIPHost radiusFramedCompression radiusFramedMTU radiusFilterId radiusFramedRouting radiusFramedRoute radiusFramedIPNetmask radiusFramedIPAddress radiusFramedProtocol radiusServiceType radiusReplyItem sambaNTPassword uid sasdefaultloginsequence 
May  6 15:21:17 wifi-lab-ldap slapd[4196]: conn=13 op=40 SEARCH RESULT tag=101 err=0 nentries=1 text= 
May  6 15:27:15 wifi-lab-ldap slapd[4196]: conn=13 op=41 UNBIND 
May  6 15:27:15 wifi-lab-ldap slapd[4196]: conn=13 fd=14 closed 
May  6 15:27:29 wifi-lab-ldap slapd[4196]: daemon: shutdown requested and initiated. 
May  6 15:27:29 wifi-lab-ldap slapd[4196]: slapd shutdown: waiting for 0 threads to terminate 
May  6 15:27:29 wifi-lab-ldap slapd[4196]: slapd stopped. 
```

FreeRADIUS:
```

Wed May 13 12:28:35 2009 : Info: Using deprecated naslist file.  Support for this will go away soon.
Wed May 13 12:28:35 2009 : Info: rlm_exec: Wait=yes but no output defined. Did you mean output=none?
Wed May 13 12:28:35 2009 : Info: rlm_eap_tls: Loading the certificate file as a chain
Wed May 13 12:28:35 2009 : Info: Ready to process requests.
Wed May 13 12:31:47 2009 : Info: rlm_eap_mschapv2: Issuing Challenge
Wed May 13 12:31:47 2009 : Auth: Login incorrect: [john/<no User-Password attribute>] (from client localhost port 0)
Wed May 13 12:31:47 2009 : Auth: Login incorrect: [john/<no User-Password attribute>] (from client colubris port 1 cli 00-1D-7E-06-AD-4F)

```

I've attached my radiusd.conf, eap.conf and ldap.attrmap.

Help is greatly appreciated!

---

