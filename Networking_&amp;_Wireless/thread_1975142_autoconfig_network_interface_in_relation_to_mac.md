---
title: "autoconfig network interface in relation to mac"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by go4unkwn on 2012-05-07
hello all

i administrate all small network at a small school. til now we use windows vista home premium. but i have in mind to replace vista with ubuntu 11.10.

i will create a installation image that i can use with clonezilla live dvd. most of the network interfaces are configured as dhcp client's, but some of the school pc's needs a static network interface configuration.

my question: is there a way to configure the network interface in relation to the unique mac. my idea - if possible or not - i create one big interface file with all necessary configurations, but only the entry with the right mac is going to be active (some thing like if ... then). is this possible in the interfaces file or do i have to create a bash script that runs at boot.

any ideas are welcome!

kind regards, go4unkwn

---

### Post by papibe on 2012-05-07
Hi go4unkwn.

IMHO the simplest solution would be let the computers as they are (DHCP clients), and set your router or DHCP server to reserve addresses for specific macs (or hostnames).

Just a thought.
Regards.

---

### Post by go4unkwn on 2012-06-01
dear papibe

I agree with your opinion. All computers using dhcp are configured as static dhcp. so i can configugre dns on the router.
unfortunately there are 4 computers they need a fix ip delivered by the isp. and i have no possibility to chance this situation.

so the question is stil open: is there a way which helps me not to adapt the interface configuration after the clonezilla image is set up.

kind regards, go4unkwn

---

