---
title: "Strange Bluetooth behaviour"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by marduk667 on 2009-07-23
Hi together,

i really have a weird problem with my bluetooth.
I want to do the following:

- Ubuntu Jaunty
- blueman from ppa
- sony w880i

So i connect to the mobile via blueman and create a dialup port. The network manager recognizes the GSM connection and i can start it. After the connection is established i start a ping to google and everything seems to be fine:

> 64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=125 ttl=47 time=177 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=126 ttl=47 time=229 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=127 ttl=47 time=216 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=128 ttl=47 time=196 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=129 ttl=47 time=212 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=130 ttl=47 time=196 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=131 ttl=47 time=204 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=132 ttl=47 time=200 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=133 ttl=47 time=184 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=135 ttl=47 time=248 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=136 ttl=47 time=259 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=137 ttl=47 time=212 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=138 ttl=47 time=184 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=139 ttl=47 time=195 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=140 ttl=47 time=203 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=141 ttl=47 time=234 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=142 ttl=47 time=190 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=143 ttl=47 time=178 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=144 ttl=47 time=183 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=145 ttl=47 time=195 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=146 ttl=47 time=301 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=147 ttl=47 time=180 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=148 ttl=47 time=188 ms


So i can start a SSH session to another server and it works as expected, but, if i want to surf in the web the ping times get worse and i cant open a web page:

> 64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=185 ttl=47 time=316 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=186 ttl=47 time=256 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=187 ttl=47 time=310 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=188 ttl=47 time=227 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=189 ttl=47 time=180 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=190 ttl=47 time=14188 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=191 ttl=47 time=13187 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=192 ttl=47 time=12178 ms
^C64 bytes from 74.125.77.106: icmp_seq=193 ttl=47 time=11171 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=194 ttl=47 time=10169 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=195 ttl=47 time=9201 ms
64 bytes from 74.125.77.106: icmp_seq=196 ttl=47 time=8200 ms
64 bytes from 74.125.77.106: icmp_seq=197 ttl=47 time=7194 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=198 ttl=47 time=6194 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=199 ttl=47 time=7325 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=200 ttl=47 time=7417 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=201 ttl=47 time=6637 ms
64 bytes from ew-in-f106.google.com (74.125.77.106): icmp_seq=202 ttl=47 time=9289 ms


Even if i close the browser again it does not get better any more, i first have to close the connection and reconnect the dialup port.

If i use the mobile phone with the usb-cable everything works perfect!

Regards,
Dennis

---

### Post by sandeepjshenoy on 2009-07-24
@[marduk667]("http://art.ubuntuforums.org/member.php?u=730969") I too have a sony ericsson k810i. I tried pairing with jaunty using blueman, but i dont get the option to search/setup devices when I right click on the bluetooth icon in the task bar. What did you do to pair the phone and pc? Can u please tell me the packages/configurations you have used?

---

