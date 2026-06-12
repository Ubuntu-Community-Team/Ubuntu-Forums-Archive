---
title: "who is using my bandwidth"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by jmathus on 2011-05-27
well i have an issue on ubuntu maverick,i'am so worried. why in world my connection is working i have nothing opened. please i need some help to find what is using my connection on wlan1 a send you a screenshot only process working is java

i do 
lsof | grep TCP
netstat -top and netstat -topl seems to be ok but system monitor says im transfering something this is so anoying please guy i need some help
[edit]
i nstalled nethogs but doesnt detect any process using wlan1(wlan1 is my only wifi card eth1 is not connected)
[/edit]
[edit]
i do sudo netstat -plantu and i find java foreign address pointing to two adresses
83.103.82.85
216.93.246.14


please help also i do a whois to this address and this is the result

_**83.103.82.85**_
```

% APNIC found the following authoritative answer from: whois.ripe.net % This is the RIPE Database query service. % The objects are in RPSL format. % % The RIPE Database is subject to Terms and Conditions. % See [http://www.ripe.net/db/support/db-terms-conditions.pdf](http://www.ripe.net/db/support/db-terms-conditions.pdf) % Note: this output has been filtered. %       To receive output for a database update, use the "-B" flag. % Information related to '83.103.82.80 - 83.103.82.95' **_inetnum_**:      83.103.82.80 - 83.103.82.95 netname:      FASTWEB-Reitek descr:        Reitek public subnet country:      IT admin-c:      [GC4384-RIPE]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=GC4384-RIPE&form_type=advanced") tech-c:       [IRS2-RIPE]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=IRS2-RIPE&form_type=advanced") status:       ASSIGNED PA mnt-by:       [FASTWEB-MNT]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=FASTWEB-MNT&form_type=advanced") remarks:      In case of improper use originating from our network, remarks:      please mail customer or [email]abuse@fastweb.it[/email] source:       RIPE # Filtered **person**:       Giovanni Carbone address:      Viale Monza, 265 address:      Milano address:      Italy phone:        +39 02 27070111 fax-no:       +39 02 27070930 e-mail:       [email]itadmin@reitek.com[/email] _nic-hdl_:      GC4384-RIPE source:       RIPE # Filtered **person**:         ip registration service address:        Via Caracciolo, 51 address:        20155 Milano MI address:        Italy phone:          +39 02 45451 fax-no:         +39 02 45451 e-mail:         [email]IP.RegistrationService@fastweb.it[/email] _nic-hdl_:        IRS2-RIPE mnt-by:        [ FASTWEB-MNT]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=%20FASTWEB-MNT&form_type=advanced") remarks: remarks:        In case of improper use originating from our network, remarks:        please mail customer or [email]abuse@fastweb.it[/email] remarks: source:         RIPE # Filtered % Information related to '83.103.0.0/17AS12874' **_route_**:        83.103.0.0/17 descr:        Fastweb Networks block _origin_:       [AS12874]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=AS12874&form_type=advanced") remarks:      5th block released to it.fastweb local registry. mnt-by:       [FASTWEB-MNT]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=FASTWEB-MNT&form_type=advanced") remarks:      In case of improper use originating from our network,               please mail customer or [email]abuse@fastweb.it[/email] source:       RIPE # Filtered % Information related to '83.103.64.0/18AS12874' **_route_**:          83.103.64.0/18 descr:          Fastweb Networks block _origin_:        [ AS12874]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=%20AS12874&form_type=advanced") mnt-by:        [ FASTWEB-MNT]("http://wq.apnic.net/apnic-bin/whois.pl?searchtext=%20FASTWEB-MNT&form_type=advanced") remarks: remarks:        In case of improper use originating from our network, remarks:        please mail customer or [email]abuse@fastweb.it[/email] remarks: source:         RIPE # Filtered 

```
_**216.93.246.14**_
```

*% This is the RIPE Database query service.* *% The objects are in RPSL format.* % *% The RIPE Database is subject to Terms and Conditions.* *% See [http://www.ripe.net/db/support/db-terms-conditions.pdf](http://www.ripe.net/db/support/db-terms-conditions.pdf)* *% Note: this output has been filtered.* *%       To receive output for a database update, use the "-B" flag.* *% Information related to '0.0.0.0 - 255.255.255.255'* **inetnum**:         0.0.0.0 - 255.255.255.255 netname:         IANA-BLK descr:           The whole IPv4 address space country:         EU # Country is really world wide org:             [ORG-IANA1-RIPE]("http://www.db.ripe.net/whois?searchtext=ORG-IANA1-RIPE&inverse_attributes=org&form_type=simple") admin-c:         [IANA1-RIPE]("http://www.db.ripe.net/whois?searchtext=IANA1-RIPE&inverse_attributes=admin-c&form_type=simple") tech-c:          [IANA1-RIPE]("http://www.db.ripe.net/whois?searchtext=IANA1-RIPE&inverse_attributes=tech-c&form_type=simple") status:          ALLOCATED UNSPECIFIED remarks:         The country is really worldwide. remarks:         This address space is assigned at various other places in remarks:         the world and might therefore not be in the RIPE database. mnt-by:          [RIPE-NCC-HM-MNT]("http://www.db.ripe.net/whois?searchtext=RIPE-NCC-HM-MNT&inverse_attributes=mnt-by&form_type=simple") mnt-lower:       [RIPE-NCC-HM-MNT]("http://www.db.ripe.net/whois?searchtext=RIPE-NCC-HM-MNT&inverse_attributes=mnt-lower&form_type=simple") mnt-routes:      [RIPE-NCC-RPSL-MNT]("http://www.db.ripe.net/whois?searchtext=RIPE-NCC-RPSL-MNT&inverse_attributes=mnt-routes&form_type=simple") source:          RIPE # Filtered **organisation**:    ORG-IANA1-RIPE org-name:        Internet Assigned Numbers Authority org-type:        IANA address:         see [http://www.iana.org](http://www.iana.org) remarks:         The IANA allocates IP addresses and AS number blocks to RIRs remarks:         see [http://www.iana.org/ipaddress/ip-addresses.htm](http://www.iana.org/ipaddress/ip-addresses.htm) remarks:         and [http://www.iana.org/assignments/as-numbers](http://www.iana.org/assignments/as-numbers) e-mail:          [email]bitbucket@ripe.net[/email] admin-c:         [IANA1-RIPE]("http://www.db.ripe.net/whois?searchtext=IANA1-RIPE&inverse_attributes=admin-c&form_type=simple") tech-c:          [IANA1-RIPE]("http://www.db.ripe.net/whois?searchtext=IANA1-RIPE&inverse_attributes=tech-c&form_type=simple") mnt-ref:         [RIPE-NCC-HM-MNT]("http://www.db.ripe.net/whois?searchtext=RIPE-NCC-HM-MNT&inverse_attributes=mnt-ref&form_type=simple") mnt-by:          [RIPE-NCC-HM-MNT]("http://www.db.ripe.net/whois?searchtext=RIPE-NCC-HM-MNT&inverse_attributes=mnt-by&form_type=simple") source:          RIPE # Filtered **role**:            Internet Assigned Numbers Authority address:         see [http://www.iana.org](http://www.iana.org). e-mail:          [email]bitbucket@ripe.net[/email] admin-c:         [IANA1-RIPE]("http://www.db.ripe.net/whois?searchtext=IANA1-RIPE&inverse_attributes=admin-c&form_type=simple") tech-c:          [IANA1-RIPE]("http://www.db.ripe.net/whois?searchtext=IANA1-RIPE&inverse_attributes=tech-c&form_type=simple") nic-hdl:         IANA1-RIPE remarks:         For more information on IANA services remarks:         go to IANA web site at [http://www.iana.org](http://www.iana.org). mnt-by:          [RIPE-NCC-MNT]("http://www.db.ripe.net/whois?searchtext=RIPE-NCC-MNT&inverse_attributes=mnt-by&form_type=simple") source:          RIPE # Filtered > 

```
[/edit]


appreciate your help im trying to kill java but it doesnt die

---

