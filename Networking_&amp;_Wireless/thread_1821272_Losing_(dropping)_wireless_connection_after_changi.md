---
title: "Losing (dropping) wireless connection after changing MAC addr"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by aefavant on 2011-08-08
Hello there all. 
Sorry if this has already been solved;answered anywhere else - I tried looking it up but to no avail. The problem persists & the hints I found around the forum did not provide a solution to the case, neither other net solutions i looked up

So, I run Winblows at the lab and sometimes take my Ubuntu PC with me. There is an open Wireless network where they set MAC permission, and there's no pwd to access. It so should be fairly easy to change m MAC and access it, right! No. I run ifconfig and macchange, successfully change my MAC addr BUT the connection drops!
Then if I change it back (MAC to my original address) it goes back online.
And yes, I shut down the service -- "ifconfig wlan0 down" and then up....but no good.

WHAT ON EARTH am I doing wrong??? No webpages touch this 'trouble-frigging-shooting instance!:confused:

cheers all

---

### Post by Basher101 on 2011-08-08
Do you know what your MAC adress even is? Why do you try to change it? The MAC adress is a uniqe number/letter combination that internet interfaces have (wired ethernet and wlan alike) so sticking to your MAC without changing it wouldnt cause no problems.

---

### Post by aefavant on 2011-08-09
Yes Basher. that's not the point, mate. I'm just trying to 're-address' my packets not change it for good coz that's not even possible. That wifi network is mac addr protected (no password) and I want to change my mac nr during my Linux connection to my allowed mac addr. I know it's possible and there's a lot of threads saying so, it's just not working on my Linux.
It will be good to have my other notebook running as well form time to time to get my projects done! Now you see why I WANT to change my mac.
cheers

---

