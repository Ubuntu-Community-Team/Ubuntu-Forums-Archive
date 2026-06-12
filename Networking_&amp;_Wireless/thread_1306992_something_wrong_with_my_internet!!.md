---
title: "something wrong with my internet!!"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by jodi1819 on 2009-10-30
i got a dell mini 9 and it has ubuntu so i dnt really no how to use it..but when i got it, it would connect to other peoples wireless fine...and now its not working it says its connected but when i try search for stuff it keeps coming up address not found blah blah blah but its doing it for every thing i go onto?? i dnt no wat to do?

---

### Post by madScientist3 on 2009-10-30
I had exactly the same problem - I had a good wireless connection but no internet. In the end I discovered it was my router, it did not support IPV6.
To see if this is your problem, in a terminal type dmesg   if it gives you an error about ipv6 then there are plenty of fixes available with a google or ubuntu forum search.
I used the simplest and it worked immediately.
pardon my script as this is my first post and I do not know how to do the fancy boxes yet.

sudo su
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

to check if this has changed

cat /proc/sys/net/ipv6/conf/all/disable_ipv6

if it comes back with   1   then things are looking good.
then type exit

reboot to make sure and all being well the internet will work.

if not then go to firefox and disable ipv6 within firefox

about:config
filter for ipv6
toggle the disable_ipv6 line from false to true.
restart firefox


It has taken me hours to find this and I joined up so others could at least try my solution. 
Good luck:D

---

