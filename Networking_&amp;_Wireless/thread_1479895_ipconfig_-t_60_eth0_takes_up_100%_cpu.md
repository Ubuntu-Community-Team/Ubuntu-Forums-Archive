---
title: "ipconfig -t 60 eth0 takes up 100% cpu?"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by CazperII on 2010-05-11
I recently did a clean install of Ubuntu 10.04 (only kept my /home partition). Now a strange thing occurs. Whenever I boot the following message appears before the Ubuntu boot screen:

> IP-config eth0 hardware address [MY MAC ADDRESS] MTU 1500 RARP

Then when I log in my gnome session one of my cores takes up 100% cpu. When I check which process it is with htop:

> ipconfig -t 60 eth0

I think it is very suspicious. I mean i**p**config? Not ifconfig?

I can manually kill the process and all is well but I want to get rid of the cause.

Sincerely,

Maarten

---

### Post by eltommo on 2010-05-18
I'm having exactly the same problem and agree this seems a bit suspicious. Sorry I cant offer any insight to this, but if someone else has some ideas they would be greatly appreciated!

---

### Post by eltommo on 2010-06-05
problem is solved with most recent kernel update

---

### Post by tito_carnivora on 2010-08-03
today 3 of August 2010  i have made full update and upgrade of My Ubuntu 10.4 LTS. I have Lenovo T61 laptop and have seen also a ipconfig process that takes 100% of my CPU. I repeat that is not ifconfig but ipconfig, i was able to kill the process with kill -9 but that reapear, i have updated my kernel but still that process pops up randomly and  puts the CPU on high load, I am using the 64 bit version of Ubuntu. If someone knows how to delete that command please write it here so others can also fix their problems.

---

### Post by hal2100 on 2010-09-17
I have the same issue, I will file a bug...

---

### Post by Jeyadheepan on 2011-01-30
I am also having the same problem of [CazperII]("http://ubuntuforums.org/member.php?u=310642")

Please any one help us in this regard...


Thank you in advance...

---

