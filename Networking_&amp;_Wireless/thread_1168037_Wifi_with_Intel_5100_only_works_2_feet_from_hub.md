---
title: "Wifi with Intel 5100 only works 2 feet from hub"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by pootle1 on 2009-05-23
I've recently installed 9.04 on my laptop, and the wifi is basically broken.  If I sit literally on top of the hub, it works fine, by the time I am 6 feet away it is nearly completely broken.

I had much the same experience with 8.10, but am now running 9.04 to get better sound and graphics drivers.

I've currently got the linuxwireless.org [stable compat-wireless releases]("http://linuxwireless.org/en/users/Download/stable/"), but it behaves the same - as far as I can see - as the standard distro.

Right now it managed to connect briefly when I rebooted, then died, and eventually reprompted for the WPA key - currently I am using a wired connection.

It sort of works, but there seems to be a big problem around gain / sensitivity signal going awry.

Here is a ping from the session that briefly worked from the room underneath the room with the router I am beside 2 other laptops using WiFi quite happily.

  	 	 	 	 	 	  $ ping 192.168.1.254 
 PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data. 
 64 bytes from 192.168.1.254: icmp_seq=21 ttl=64 time=93.9 ms 
 ^C 
 --- 192.168.1.254 ping statistics --- 
 59 packets transmitted, 1 received, 98% packet loss, time 58447ms 
 rtt min/avg/max/mdev = 93.991/93.991/93.991/0.000 ms 
 $
 
All the info as requested is in the attachment

If I sit a bit closer to the hub, I can sort of get a bit working, but web browsing is very hiccupy, and bits of pages break and fail to appear - ping shows response times fluctuating wildly between a few ms and 1000 ms, as well as many getting lost altogether

I've seen many posts which appear to be similar problems, but none of the answers provided have helped, and few have posted the diagnostic info, so I hope this is enough info for someone who knows a lot more than I do about wireless drivers (not difficult) to help.

---

### Post by pootle1 on 2009-05-25
bump....

---

