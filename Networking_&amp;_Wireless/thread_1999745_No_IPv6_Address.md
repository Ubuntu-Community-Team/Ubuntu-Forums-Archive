---
title: "No IPv6 Address"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by Jademalo on 2012-06-08
My network is configured to run a 6to4 IPv6 connection, and my Ubuntu 12.04 server runs fine. However, my 12.04 laptop does not - It only gets the link address. It does not get any global addresses at all. The only difference is it's connected wireless rather than wired, but my iPhone is obviously wireless and that supports the IPv6.

Can anyone help?

---

### Post by dandnsmith on 2012-06-08
I don't understand some of your terms -
what is 6to4 IPv6 connection?
what are the link and global addresses?

Perhaps you could post the results of *ifconfig* on the laptop,
and also the results of *lshw -c network* and then *sudo lspci -v*,
as these will help to explain things

---

### Post by ratcheer on 2012-06-08
What is the endpoint of your tunnel, a router or your Ubuntu 12.04 "server"? It sounds like it is your Ubuntu host. That is not the best way to do it, but it can be made to work.

Wherever it is, you need to install and configure radvd to advertise IPv6 to the other hosts on your LAN.

Tim

---

### Post by Jademalo on 2012-06-08
Right. 6to4 is a type of connection that allows someone with an ipv4 connection to have an ipv6 address and access to the internet. It's quite common.

The link and global addresses - when running an ip -6 addr show, it lists your addresses.

    inet6 2002:*****/64 scope global temporary dynamic
       valid_lft 86397sec preferred_lft 69552sec
    inet6 2002:*****/64 scope global dynamic
       valid_lft 86397sec preferred_lft 86397sec
    inet6 fe80:*****/64 scope link
       valid_lft forever preferred_lft forever

Thats them on my server censored obviously, I currently have no access to the laptop. The global is the internet address obviously, with temp being preferred on ubuntu 12.04 i believe. When running this on the laptop, it only gave me a scope link address, and not a global or global temporary address.

EDIT: It's my router that's setup with radvd, a Linksys E3200 running the latest DD-WRT mega. It works perfectly for my ubuntu server and my windows PC, its just this ubuntu laptop im having a problem with.
[http://www.dd-wrt.com/wiki/index.php/IPv6#6to4_on_current_builds_.28after_v24_sp1.29](http://www.dd-wrt.com/wiki/index.php/IPv6#6to4_on_current_builds_.28after_v24_sp1.29)
That is how it's configured, and as I say, it works fine for my Win7, iPhone, iPad and ubuntu server box.

---

### Post by Jademalo on 2012-06-10
Still having problems with this, anyone?

---

### Post by ratcheer on 2012-06-10
Ok, sorry. It does appear that you have things set up correctly, and that one client host is just not getting it.

I used to not be able to get IPv6 connectivity via wireless, but I just checked and it's working fine on 12.04. And I haven't changed anything on the router for a long time.

Maybe there is some way to delete the client's connection info and let it try to reestablish it, from scratch. I really don't know.

Tim

---

### Post by sanderj on 2012-06-27
> **Jademalo said:**
> Right. 6to4 is a type of connection that allows someone with an ipv4 connection to have an ipv6 address and access to the internet. It's quite common.

The link and global addresses - when running an ip -6 addr show, it lists your addresses.

    inet6 2002:*****/64 scope global temporary dynamic
       valid_lft 86397sec preferred_lft 69552sec
    inet6 2002:*****/64 scope global dynamic
       valid_lft 86397sec preferred_lft 86397sec
    inet6 fe80:*****/64 scope link
       valid_lft forever preferred_lft forever

Thats them on my server censored obviously, I currently have no access to the laptop. The global is the internet address obviously, with temp being preferred on ubuntu 12.04 i believe. When running this on the laptop, it only gave me a scope link address, and not a global or global temporary address.

EDIT: It's my router that's setup with radvd, a Linksys E3200 running the latest DD-WRT mega. It works perfectly for my ubuntu server and my windows PC, its just this ubuntu laptop im having a problem with.
[http://www.dd-wrt.com/wiki/index.php/IPv6#6to4_on_current_builds_.28after_v24_sp1.29](http://www.dd-wrt.com/wiki/index.php/IPv6#6to4_on_current_builds_.28after_v24_sp1.29)
That is how it's configured, and as I say, it works fine for my Win7, iPhone, iPad and ubuntu server box.


So, just checking: it's your router that's doing 6to4? And the router should advertise the IPv6 prefix to the LAN?
For your server this setup works? Wired or wireless?

On both your server and laptop, what is the result of

rdisc6 eth0
rdisc6 wlan0

For rdisc6 you need to "sudo apt-get install ndisc6" first.

HTH

---

