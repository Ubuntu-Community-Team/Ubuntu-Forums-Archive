---
title: "resolv.conf always re-edited"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by johnhenry on 2009-11-09
I have been having problems with getting DHCP in Ubuntu 9.10, but was able to overcome this by editing the /etc/resolv.conf file to servers recommended by my ISP.

However, every time I boot up, the system (presumably the Network Manager?) insists on resetting resolv.conf to my router - 192.168.1.1. 

How can I stop it doing this? I have not been able to find this in any documentation or forum.

---

### Post by coffeecat on 2009-11-09
Every distro I've used over the last 4½ years has reset resolv.conf on a reboot, so it's best left alone.

Try this:

Right-click on the Network Manager applet and choose 'Edit connections'. Choose the Wired or Wireless tab as appropriate. Highlight your network connection and click on Edit. Click on the 'IPv4 Settings' tab and try either 'Manual' or 'Automatic (DHCP) addresses only'. Maybe the latter will suit your needs, but 'Manual' will certainly obviate any DHCP issues. Now click on 'Apply'.

**EDIT:** by the way, what exactly was the nature of the DHCP problem?

---

### Post by i.r.id10t on 2009-11-09
That is what is being sent by the dhcp server in your router.

You can either change it in the router (maybe, dependign on router) or you can tell dhcpclient to not ask for DNS servers /etc/dhcp3/dhclient.conf

---

### Post by johnhenry on 2009-11-09
Many thanks for your help, but unfortunately this does not seem to work, either with Manual or with DHCP only. In fact, for Manual the Apply button was greyed out anyway, so there was no way to use it.

The problem has been that 9.10 seems to have installed perfectly, yet is unable to access the internet. I have a desktop with wired connection thro' eth0, which has always worked and still works perfectly with 9.04, but with 9.10 one sees, eg. in Firefox, that it is trying to open the correct address, but nothing happens. I have assumed it is unable to resolve the address.

If I edit the resolv.conf file with suitable servers (from my ISP), it works perfectly until I next log out and boot up again, when I find that the file has been rewritten. Incidentally, I notice that the resolv.conf file in my 9.04 setup is also set to the default the same as 9.10, so clearly my partial solution is not the proper way, but at least it does work - temporarily.

---

### Post by Iowan on 2009-11-09
There is a "prepend" line in the aforementioned */etc/dhcp3/dhclient.conf* that *should* push your preferred nameserver(s) to the top of the list.

---

### Post by johnhenry on 2009-11-10
Many thanks Iowan. The prepend line solved it, so I am happy, though it does seem a bit of a "hack". Not quite what is intended by the system. But so whaT!!

---

