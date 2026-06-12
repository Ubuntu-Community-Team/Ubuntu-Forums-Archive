---
title: "Class Help Needed"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by laura112199 on 2006-05-03
Hi, I'm new to the forum. I'm currently enrolled at YTI in York Pa. I'm one of 4 and the only woman to ever take Cyber Security. My Data Communications teacher has asked our class to do a networking project.  This is not due until July.
These are the requirements; 
must have 2000 employees-company can do whatever we want
no limit on cost
must list  what is needed and brand names of items needed to network everyone together, and why we chose those items(security etc)
list programs and OS to run business

My neighbor suggested your wonderful ubuntu forum for help, after I mentioned wanting to run a Linux based OS.

I have a general idea of what is needed, but could really use some help. I had networking class last term and passed it with 100%, but came away feeling like I hadn't learned anything, since my teacher was one of those who knew his stuff but couldn't teach it.

Thanking all you wonderful people in advance.
Laura

---

### Post by nanotube on 2006-05-03
so... what is it that you are actually planning to do? like, design the whole network infrastructure for your 2000-employee company? are you dealing with just the network and security, or also business-oriented software? what line of business is the company in?

i mean, basically... you are encouraged to specify more precisely what it is that you want to accomplish, because otherwise it is hard to give any suggestions. i mean, you don't expect us to do ALL of your homework for you, do you? :)

---

### Post by laura112199 on 2006-05-03
The instructor was not that specific. I guess I have to design the whole network infrastructure for the 2000 employees, along with network and security, routers,firewalls, pc's,laptops,cabling,printers etc, and we have to list the software the business is running. I would like to have it based on  a small health care organization.

Yes there are days when I wish the good fairy could do my homework for me!

---

### Post by BoneKracker on 2006-05-03
Here are a couple of starting points that might be helpful.

a) do some research (e.g., google <subject below>) to learn how linux fits into a secure, networked environment
b) Make some more posts to establish contact with individuals in these forums who are knowledgeable in these areas (i.e., post title: "need help with <any subject below>").

selinux (security-enhanced linux)
RSBAC (rule-set-based access control)
openVPN
openLDAP
SAMBA
unix filesystems (extended attributes, encryption)
linux firewalls
IP tables
OpenSSL
GPG
virtualization

These are just some items off the top of my head, and you'll end up with a completely different list of what's truly important.

---

### Post by nanotube on 2006-05-03
heh seems like a fun assignment, i suppose.
bonekracker gives some good suggestions.
and of course, everyone should be running ubuntu, instead of ms windows. that ougtta save a ton on software costs, and fixing your user's computers costs (adware+viruses, anyone?). 

in general, the simplest setup would be uplink > router/firewall > a bunch of computers
and you would start building up from that. need network storage/backups? shove in a SAN. need remote access? shove in openvpn. need email? outsource the stuff to some email hosting provider. :)

of course, choosing healthcare entails its own problems, as they have a bunch of private data to access and whatnot, and are subject to a bunch of regulations regarding that. so you would have to do research on that. or switch to an unregulated industry :)

---

### Post by mips on 2006-05-03
How many sites/buildings/floors do these 2000 people reside in ?
Do you have centrlised or distributed servers ?
What data line infrastructure are you using, private or VPN ?
Is there internet involved ?
For routers/switches look at Cisco and if security is a issue ensure they have ipsec IOS images. To this you can add Radius servers, Pix/OpenBSD Firewalls, OpenBSD/SELinux Servers and the list goes on......

You need to supply a whole lot more information before anybody can even begin to help you.

Feels like I'm back at work.

PS Is'nt the point of an assignment for you to do it in order to actually learn something out of the exercise ?

---

