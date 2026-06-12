---
title: "Can only ping windows box by full domain name"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by sibleytr on 2011-12-29
We are in the process of converting a backup file server in our domain from the Windows platform to an Ubuntu 11.10 Samba platform. One of the problems we are running into is being able to access the Windows Servers from the Samba Server by name.

We can ping the Samba box from anywhere in the domain, but the Samba box is unable to ping any of the Windows servers, by **just their name**.

An example of "**just their name**":
The Samba box can ping the Windows Servers by IP address, but when it comes to pinging the Windows Servers by name we have to use the fully qualified domain name. (ds1 is DataServer1)

ping ds1.domain.local     Works
ping ds1                  Does Not Work


**/etc/samba/smb.conf - Global Settings**
[global]
   netbios name = DRS0
   workgroup = OURDOMAIN
   server string = %h server
   wins server = 10.1.1.233
   dns proxy = no

**/etc/resolv.conf**
domain ourdomain
search ourdomain.local
nameserver 10.1.1.247
nameserver 10.1.1.250

Any ideas?

---

### Post by zacktu on 2011-12-29
Look at the /etc/hosts file.  Use the line for localhost as a model to append as many hostnames to the file as you need to.

For more information type "man hosts" in a terminal.

---

### Post by sibleytr on 2011-12-30
If I understand your reply I should simply update the /etc/hosts file with the server names and ip addresses that is needed. Unfortunately that gets to be very laborious in an enterprise environment (which is where we hope this project progresses).

Thank you for your post.

---

### Post by sibleytr on 2011-12-30
**[SOLVED]**

This is a lesson in cause and effect - our issue was laid beyond the Ubuntu box.

1 - When the server was first setup we edited the /etc/resolve.conf and added [COLOR="red"]**.local**[/COLOR] suffix to the search domain (which did not resolve our issue)

[B]domain ourdomain
search ourdomain*_[COLOR="Red"].local[/COLOR]_*
nameserver 10.1.1.247
nameserver 10.1.1.250
[/B]


2 - We did observe that if the /etc/resolve.conf file was further edited and the **[COLOR="red"]domain ourdomain[/COLOR]** reference removed we could ping by name

search ourdomain.local
nameserver 10.1.1.247
nameserver 10.1.1.250


3 - However when we rebooted the server we would loose our settings and the ability to ping by name. (Remember the box is experimental and still set to DHCP). After the reboot we also observed that the **/etc/resolve.conf** file would get recreated every time and we would be back to our original configuration

[B]domain ourdomain
search ourdomain
nameserver 10.1.1.247
nameserver 10.1.1.250[/B]


**[Solution]**
The DNS domain reference in our DHCP server was listed as:

**ourdomain** and not
**ourdomain.local**

Once we edited the entry and rebooted the server our /etc/reference.conf file was rewritten as:

[B]domain ourdomain.local
search ourdomain.local
nameserver 10.1.1.247
nameserver 10.1.1.250[/B]

Now the box can ping in DHCP mode as well as Static and maintains its settings after reboot.

---

