---
title: "problem with cable modem+usb"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Moti on 2010-01-28
I'm trying to help a friend that has some problem connecting to the Internet.
the problem is like that :the eth0 is ok, when used with adsl modem and dialer connected without a problem.
now he switched to cable modem which should give him ip.
ifconfig shows nothing about ipv4 address.
he switched to a non dialer connection (should get ip via dhcp automatically) just in case, but nothing.
i suggested he would try connect a usb instead of Ethernet and for a while it was ok, somehow.
now again, no INTERNET, no ip.
what can i check to see why his computer don't pull any ip via cable+usb?
and idea would be greatly appreciated.
it's ubuntu 9.10.

---

### Post by mörgæs on 2010-01-29
Does the connection work with a fixed IP number?

---

### Post by Moti on 2010-01-29
> **mörgæs said:**
> Does the connection work with a fixed IP number?

it's not really fixed ip although it doesn't tend to change much since  it's auto assigned by the cable company.
i guess it's the equal of "get ip by dhcp".

---

### Post by mörgæs on 2010-01-29
Sorry, I was not being clear. I meant: Have you tried giving the computer a fixed IP (192.168.x.x) in stead of using DHCP?

---

### Post by Moti on 2010-01-30
> **mörgæs said:**
> Sorry, I was not being clear. I meant: Have you tried giving the computer a fixed IP (192.168.x.x) in stead of using DHCP?

No. i will  try, but since the all technology rely on dhcp, don't think it will work.
anyway, thanx for th help.
think i will just visit the guy with my laptop, see what i can come up with/

---

