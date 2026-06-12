---
title: "/etc/network/interfaces being ignored?"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by twinight on 2009-07-08
I was originally running 9.04, but built a new machine and decided to go with 8.04 LTS just to simplify my life somewhat since this is a simple server box, mostly used for IRC and such.

My interfaces file presently looks like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.1.1
```

Which works fine for days at a stretch and then -- seemingly randomly, as I'm never doing anything particular, nor is a cronjob running that coincides with the times -- the box drops itself off of x.x.x.2 and picks up a DHCP address.

I have absolutely no idea how this can happen, as the only configuration I'm familiar with for the networking is /etc/network/interfaces.  I'm hoping I've just got a dumb mistake somewhere or there is some other place I should be making changes to ensure it keeps itself on .2.

There are no IP conflicts for that address, the router isn't being reset, et cetera.  All my other machines maintain their IPs and the issue wasn't present in 9.04.  Just this one machine running 8.04 seems to enjoy randomly dropping its defined IP and picking up a DHCP address.  It's a little frustrating.  :/

Restarting eth0 causes it to pick up the correct IP again, but of course does little to solve the fact that it likes to unpredictably discard it.

I'd appreciate any help!

---

### Post by chili555 on 2009-07-08
192.168.[COLOR="Red"]0[/COLOR].x is a different neighborhood than 192.168.[COLOR="Red"]1[/COLOR].x. You are addressing a letter to New York City, Texas. I am actually surprised that it works at all! I suggest you amend your interfaces file to:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```Please let us know the outcome.

---

### Post by twinight on 2009-07-08
Oh, geez, I knew I was probably overlooking something stupidly simple.

Well don't I feel silly.

Changed!  Hopefully that'll fix it up.

---

