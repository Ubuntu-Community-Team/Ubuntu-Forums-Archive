---
title: "ICMP redirects now obeyed"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by jpmeijers on 2011-11-01
I upgraded to Ubuntu 11.10 about a week ago after running the pre-release versions in a VM. The problem I'll describe now was seen in both the VM, my final install and a friend's install with a very similar network setup than me. 

Since running it I've been experiencing weird network behavior. After "sudo apt-get update" I won't be able to access the repository server on any port or even ping it. After a restart it would work again. The same was later also seen with other servers I access regularly.

I did a tcpdump and saw that when this happens the packets were sent to the wrong gateway on my network, disobeying my routing table. ip route get <repo ip> gave me the reason. ICMP redirects added a new route, but my system used the wrong source IP address. Disabling accept_redirects in sysctl fixed the problem.

My network setup is weird in the sense that I'm running two IP ranges on my subnet, NATing the one subnet behind my router and then sending network packets to the ISP's router. As I realized only today this will cause my router to send out ICMP redirects due to packets arriving and leaving through the same port on it [[http://www.cisco.com/en/US/tech/tk365/technologies_tech_note09186a0080094702.shtml]](http://www.cisco.com/en/US/tech/tk365/technologies_tech_note09186a0080094702.shtml]). This then caused my Ubuntu machine to think that there is a better route available, sending the packet directly to my ISP's gateway, using my "internal" networks IP as the source. A answer never arrives as my ISP would then ignore my private IP.

On my older Ubuntu installs (11.04 and older) this never caused a problem, likely due to ICMP packets being ignored by the default kernel setup. I just did a "cat /proc/sys/net/ipv4/conf/all/accept_redirects" on a Ubuntu 10.04 machine also being NATed, and it gave "1". The kernel thus ignores these ICMP redirects even though they are set to be accepted.

So after struggling to find the cause of my network problems, I only have two questions.

1) Is there a way to delete a route set by a redirect? Neither ip route delete <ip>, ip route flush cache or ip neigh flush cache works.

2) Was there a bug in previous Ubuntu distros or pre kernel v3's that made them ignore ICMP redirects?

---

