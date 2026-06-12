---
title: "DHCP using hostname"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by ffxigotenks on 2009-11-03
I have an old laptop running as the DHCP server and I have it assigning static leases to several computers on the network. yet on the router it's showing all the devices as "*" and I want to be able to:

a)  see the hostname on the router so I don't have to memorize MAC addresses
b) be able to use hostnames in commands (like "ssh *hostname*")

I'm not entirely sure what makes this work in windows, so I have no idea what can do it in linux...

here's the dhcpd.conf from the server
```

        range 192.168.1.100 192.168.1.200;
        option domain-name-servers 208.67.222.222, 208.67.220.220;
        option broadcast-address 192.168.1.255;                   
        option routers 192.168.1.1;                               
        group {                                                   
        use-host-decl-names on;                                   
        host syraria  {                                           
                hardware ethernet xx:xx:xx:xx:xx:xx;              
                fixed-address 192.168.1.15;                       
                        }                                         
        host jessica  {                                           
                hardware ethernet xx:xx:xx:xx:xx:xx;              
                fixed-address 192.168.1.13;                       
                        }                                         
        host evelyn   {                                           
                hardware ethernet xx:xx:xx:xx:xx:xx;              
                fixed-address 192.168.1.24;                       
                        }
        host auroradeux {
                hardware ethernet xx:xx:xx:xx:xx:xx;
                fixed-address 192.168.1.16;
                        }
        }
        filename "pxelinux.0";
}

```

---

### Post by Iowan on 2009-11-03
Check **dnsmasq**. I have it running on a server and it does what you want.

---

### Post by ffxigotenks on 2009-11-04
ok.. I have a router that is running dd-wrt and it has dnsmasq... any idea how to configure that for my needs?

EDIT: never mind.. found my answer here [http://www.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server](http://www.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server)

---

