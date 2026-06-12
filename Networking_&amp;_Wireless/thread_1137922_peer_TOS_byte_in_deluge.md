---
title: "peer TOS byte in deluge"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by anystupidname on 2009-04-26
Could somebody please explain the purpose of the "peer TOS byte" changing option in the deluge torrent client?

---

### Post by B0rat on 2009-07-28
I'd be interested in knowing what this does also.

---

### Post by inkrypted on 2009-08-27
Settings for the Type Of Service it basically boils down to.

        tos-minimize-delay       0x10/0x10
        tos-maximize-throughput  0x08/0x08
        tos-maximize-reliability 0x04/0x04
        tos-minimize-cost        0x02/0x02
        tos-normal-service       0x00/0x1e

---

### Post by graysky on 2010-02-13
What he said.  [http://www.shorewall.net/3.0/manpages/shorewall-tcclasses.html](http://www.shorewall.net/3.0/manpages/shorewall-tcclasses.html)

> tos=0xvalue[/0xmask] (mask defaults to 0xff)

    This lets you define a classifier for the given value/mask combination of the IP packet's TOS/Precedence/DiffSrv octet (aka the TOS byte). Please note that classifiers override all mark settings, so if you define a classifer for a class, all traffic having that mark will go in it regardless of any mark set on the packet by a firewall/mangle filter.

Aliases for the following TOS octet value and mask encodings. TOS encodings of the "TOS byte" have been deprecated in favor of diffserve classes, but programs like ssh, rlogin, and ftp still use them.

        tos-minimize-delay       0x10/0x10
        tos-maximize-throughput  0x08/0x08
        tos-maximize-reliability 0x04/0x04
        tos-minimize-cost        0x02/0x02
        tos-normal-service       0x00/0x1e

---

