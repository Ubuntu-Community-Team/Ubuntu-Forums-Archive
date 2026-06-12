---
title: "correct network settings for different applications/tasks"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by rawlins02 on 2010-08-26
I'm trying to set up networking for various applications and tasks for a new machine running Lucid.  There are three main tasks.

1) accessing servers on a local network (including Windows share)

2) remote access to these linux boxes from offsite using ssh

3) setting up webserver

Regarding 1), I have another machine sitting here running Karmic (9.10) that IS accessing local network servers and Windows shares. So this shouldn't be hard.  But can't seem to get this working on 10.04. What must be done to enable access to local servers on my subnet?  For example, if I go to Places -> Network nothing shows but an icon for Windows Network.  On my machine running 9.10 I see several servers.  I'm using this tutorial here:

[http://linux.about.com/library/gnome/blgnome6n11a.htm](http://linux.about.com/library/gnome/blgnome6n11a.htm)

Under Nautilus I click 

File -> Connect to Server -> Windows share

and after entering information I get Error: Failed to mount Windows share. I should mention that I have internet connection and can ping between these two linux boxes. Once I get access to the Windows machine perhaps we can tackle 2 and 3 :-)

---

### Post by Lars Noodén on 2010-08-26
Two and three are easier.  My advice is (always) to avoid wasting time with Windows.  

What about ssh and httpd?

---

### Post by rawlins02 on 2010-08-26
Solved #1 by disabling firestarter firewall. I installed firestarter a few days ago, but am not sure when and how to use it.  Trust me, I only access Windows systems here when I must.

As far as #2, I think I need to set up fully qualified domain name on both my machines.  Right now my /etc/hosts file looks like this:

```

127.0.0.1	localhost
127.0.1.1	mustang

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



``` 


I assume I need a line like this:
XXX.XXX.XX.XX	mustang.mydomain.edu	mustang

But if assign the static IP that I use at work, what happens when I'm on wireless elsewhere?  That is, will setting my FQDN linked to a static IP cause a problem if my system is set up to use DHCP?

Goal is access to one of these linux machines at work when I'm at home. Later I'm going to test using ssh and IP address.

---

### Post by rawlins02 on 2010-08-27
I'm able to ping the IP address of, say, linuxbox1 from linuxbox2 when they are on the same subnet, but not when linuxbox2 is on another network. Assume I need to configure linuxbox1 for outside access. What configurations need to be checked to see if I'm set up for access?  I don't believe there is an institutional firewall in place (I'm on a university network) as I can ping a nearby Unix box while offsite.  System is running recently set up Lucid.

---

### Post by rawlins02 on 2010-08-30
bump

Still trying to establish fully functioning networking.

I can browse internet, but ping of sites like google and yahoo return nothing.  I CAN ping from linuxbox1 to linuxbox2 from a connection on my subnet.

As far as my webcam, these work:
[http://localhost/webcam.html](http://localhost/webcam.html)
[http://127.0.0.1/webcam.html](http://127.0.0.1/webcam.html)

But when using IP address in place of loopback, I get a black box instead of an image and "connecting, please wait" with a red, not green dot.

I'm hoping this is all related to firewall, or something similar.

---

