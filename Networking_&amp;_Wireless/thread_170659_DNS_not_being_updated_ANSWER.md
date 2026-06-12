---
title: "DNS not being updated ANSWER"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by nick4mony on 2006-05-05
A few people are having difficulties using DHCP and then finding that their computer is not registered with DNS.

The symptoms of the problem are that the computer (known as **mycomputer**) gets an IP Address, but then other computers on the network cannot [color=blue]ping mycomputer[/color] with a reply saying [color=blue]unknown host mycomputer[/color].

The quick answer is you need to use the [color=blue]nsupdate[/color] command inside a file like this:

/etc/dhcp3/dhclient-exit-hooks.d/donsupdate:
```
if [ "${new_ip_address}" ]
then
  hostfqdn=$(hostname --fqdn)
  revers=$(perl -e 'print join(".", reverse('"'${new_ip_address}'"' =~ /([0-9]+)[.]([0-9]+)[.]([0-9]+)[.]([0-9]+)/));').in-addr.arpa
  ping -c 1 ${new_domain_name_servers%% *}

  date >> /tmp/nickDns.txt
  echo "nsupdate" >> /tmp/nickDns.txt
  echo "update delete ${hostfqdn} "  >> /tmp/nickDns.txt
  echo send >> /tmp/nickDns.txt
  echo "update delete ${revers} "  >> /tmp/nickDns.txt
  echo send >> /tmp/nickDns.txt
  echo "update add ${hostfqdn} 337000 A ${new_ip_address}"  >> /tmp/nickDns.txt
  echo send >> /tmp/nickDns.txt
  echo "update add ${revers} 337000 PTR ${hostfqdn}"  >> /tmp/nickDns.txt
  echo send >> /tmp/nickDns.txt
  echo "----------------------------------" >> /tmp/nickDns.txt

  nsupdate <<EOF
update delete ${hostfqdn}
send
update delete ${revers}
send
update add ${hostfqdn} 337000 A ${new_ip_address}
send
update add ${revers} 337000 PTR ${hostfqdn}
send
EOF
fi
```
After you create this file, you must [color=grey]sudo[/color] [color=blue]chmod a+x /etc/dhcp3/dhclient-exit-hooks.d/donsupdate[/color]

---

