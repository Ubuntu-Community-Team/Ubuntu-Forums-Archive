---
title: "Xdmcp not work"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by darkshvein on 2011-05-26
Client show "Display not authorized to connect"
ubuntu 11.04 
kdmrc: 
[Xdmcp] Enable=true 
 Willing=/etc/kde4/kdm/Xwilling 
cat /etc/kde4/kdm/Xwilling 
 #! /bin/sh
# The output of this script is displayed in the chooser window

# (instead of "Willing to manage").

load=`uptime|sed -e 's/^.*load[^0-9]*//'`
nrusers=`who|cut -c 1-8|sort -u|wc -l|sed 's/^[         ]*//'`
s=""; [ "$nrusers" != 1 ] && s=s

echo "${nrusers} user${s}, load: ${load}"

Network wired, Via router. M.b. any port blocked?[br]

---

