---
title: "wireless not working"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by tons-of-funs on 2009-10-12
ok i have a gateway laptop and i just installed ubuntu 8.04 lts and i cant get my wireless internet up and going, there are two possible connections i know i can get a netgear and a at&t 2wire and niether are connecting, to topit off i clicked on the connection icon on my toolbar and it decided to disappear, any help?

---

### Post by Iowan on 2009-10-12
A few Capital letters and a period (.)  or two would improve readability.  Hardy (8.04) does not seem to be as friendly as Jaunty for wireless (though I haven't tried Hardy's wireless). What are results of **lshw -C network** (via a terminal)?

---

### Post by PrePenguin on 2009-10-12
Disable lan in Bios see if wireless will then work.. They often conflick this is a common problem..

---

### Post by tons-of-funs on 2009-10-12
ok 8.04 made me angry so i redownloaded 9.04 im still having the same problem, right now i have it wired so i can connect to the internet. i know my wireless card works because i can still turn it on and off but its almost as if ubuntu is just not recognizing that i have a wireless card, i will try disabling lan and see if that works if not i will be back on, thanks guys for your help, and i am a newbie so you might have to explain things a little more carefully, i understand most things but i am still working on my linux lingo and such, again thank you for help it means alot to me that people are still willing to help newbies on the internet

---

### Post by PrePenguin on 2009-10-12
> **tons-of-funs said:**
> ok 8.04 made me angry so i redownloaded 9.04 im still having the same problem, right now i have it wired so i can connect to the internet. i know my wireless card works because i can still turn it on and off but its almost as if ubuntu is just not recognizing that i have a wireless card, i will try disabling lan and see if that works if not i will be back on, thanks guys for your help, and i am a newbie so you might have to explain things a little more carefully, i understand most things but i am still working on my linux lingo and such, again thank you for help it means alot to me that people are still willing to help newbies on the internet
 
 
 
More then likely once your lan is disabled the wireless will work they often conflick with a resource IRQ in ubuntu for some reason let us know oneway or another and if that dont work we can try something else..

---

### Post by tons-of-funs on 2009-10-12
ok just tried disabling the lan and it still didnt work, my laptop is a prebuilt gateway mx6121 its old but still runs good, the network manager is acting as if there are no wireless networks but i am in range of two, i know i have said this before but just reiterating to make it more easily understood

---

### Post by tons-of-funs on 2009-10-12
ok i went into the system->administration->hardware drivers and found a broadcom driver, downloaded it and my wireless is working perfectly thank you to all who helped it means alot to me

---

### Post by Iowan on 2009-10-12
Unplugging the cable *should* be enough... 
Have you checked **lshw -C network** (via a terminal)? This might let you know if the wireless interface as acquired an alias an if it has an associated driver. **ifconfig -a** (also from a terminal) will probably show no IP address (if it shows the interface at all). Also, check in */etc/network/interfaces* for anything other than the two lines defining "lo".

Must have been working on a reply when you announced your solution. Congrats!

---

### Post by tons-of-funs on 2009-10-12
solved

---

