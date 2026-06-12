---
title: "snmpget and snmpdelta Issues with MIBS"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by igfud on 2011-02-06
Hello,

I'm trying to run snmpget or snmpdelta to monitor interface statistics off of 32 ports on a router.  

```
snmpget -m ALL -c rescore-public -v 2c IP_ADDRESS .iso.org.dod.internet.mgmt.mib-2.interfaces.ifTable.ifEntry.ifInOctets.1
IF-MIB::ifInOctets.1 = Counter32: 0
```

which gives the output:

```
Bad operator (INTEGER): At line 73 in /usr/share/mibs/ietf/SNMPv2-PDU
Unlinked OID in IPATM-IPMC-MIB: marsMIB ::= { mib-2 57 }
Undefined identifier: mib-2 near line 18 of /usr/share/mibs/ietf/IPATM-IPMC-MIB
Undefined OBJECT-GROUP (diffServMIBMultiFieldClfrGroup): At line 2195 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Undefined OBJECT-GROUP (diffServMultiFieldClfrNextFree): At line 2157 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Undefined OBJECT-GROUP (diffServMIBMultiFieldClfrGroup): At line 2062 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Expected "::=" (RFC5644): At line 493 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Expected "{" (EOF): At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Bad object identifier: At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Bad parse of OBJECT-IDENTITY: At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
IF-MIB::ifInOctets.1 = Counter32: 0

```

or 

```
snmpdelta -Cs -CS -Cp 600 -CT IP_ADDRESS IF-MIB:ifInOctets.1 = Counter32: 0
```

which gives the output:

```
=: Unknown Object Identifier (Sub-id not found: (top) -> =)

```

Could someone help me with the syntax of the arguments? I installed the snmp and snmp-mibs-downloader packages on Ubuntu 10.10 server edition.

Thanks!
igfud

---

