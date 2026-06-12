---
title: "basic wireless question"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2009-09-03
Hi there
I want to have a static I.P address whilst using wireless.So i go to:
System-->preferences-->Network-Connections
Then under wireless i select the wireless connection then go to edit.Which method should i select next to the word Method:
I'm assuming it's manual right?.Then i add the addresses/netmask adding my router's address as the DNS server.Then under DNS server it has the search Domain option.I added what i thought was the relevant bit from /etc/resolv.conf
it said:
domain Belkin
search Belkin
nameserver 192.168.2.1
When i clicked apply network manager edited /etc/resolv.conf.I was able to wirelessly connect using DHCP, prior to this happening.Now because, i think, of the edited /etc/resolv.conf, i can't connect wirelessly DHCP OR manual.How do i get the original /etc/resolv.conf?
By the way i can still connect using the wired interface. But i can't find what the search Domain option is from network manager by looking at the wired interface settings because it uses DHCP.Ah i've just looked at /etc/resolv.conf again and the file is as it originally was.This still doesn't solve the mystery of why i could connect wirelessly(using DHCP) but now i can't 
I don't know what to do.Need help.Thank you for your time

---

### Post by methodtwo on 2009-09-03
Ah I've just disconnected the wired connection and the wireless connection.Then i tried re-connecting the wireless connection and it worked(for DHCP).There is still the mystery of why static I.P addresses don't work with my wireless configuration?.Also is there anything that i must do to have the wireless connection automatically be the connection that starts on boot?.Also I need a static I.P address so i can use this machine as an NFS server.Which line out of my /etc/resolv.conf should i put under the System-->preferences-->network Connections-->wireless-->edit-->ipv4 settings-->search domains ??
Here is my /etc/resolv.conf:
```
domain Belkin
search Belkin
nameserver 192.168.2.1

```
Any help would be great.Thank you for your time

---

