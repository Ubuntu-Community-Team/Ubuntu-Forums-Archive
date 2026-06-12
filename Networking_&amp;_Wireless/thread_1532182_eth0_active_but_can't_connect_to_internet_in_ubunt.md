---
title: "eth0 active but can't connect to internet in ubuntu 10.04"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by sahil44 on 2010-07-16
hi,
this is my first post to ubuntu forums. ):P

i was using [SIZE=2]ubuntu 9.10 [/SIZE]till recently when i decided to upgrade to [SIZE=2]ubuntu lucid 10.04[/SIZE]. turns out the internet icon shows connected after fresh installation but when i try to use firefox , after an long wait it shows server not found.
i did a research of my own and found that i am not able to ping even my router.
using [SIZE=2]*sudo dhclient eth0*[/SIZE] doesn't recieve offers , but surprisingly when i tried *[SIZE=2]dhclient eth0[/SIZE] *in [SIZE=2]*root shell with networking*[/SIZE] internet got configured very quickly and i can ping the router and any website...!!

i forgot to mention i have a[SIZE=2]* wired connection*[/SIZE] which i am trying to connect and the net is working fine with windows 7 on the same PC.

can't figure out the prob. :confused::confused: been trying for over a week.
can anyone give help to this nubee...:):):)  would really appreciate any help...
thanks

---

### Post by auroraa9420 on 2010-07-16
> **sahil44 said:**
> hi,
this is my first post to ubuntu forums. ):P

i was using [SIZE=2]ubuntu 9.10 [/SIZE]till recently when i decided to upgrade to [SIZE=2]ubuntu lucid 10.04[/SIZE]. turns out the internet icon shows connected after fresh installation but when i try to use firefox , after an long wait it shows server not found.
i did a research of my own and found that i am not able to ping even my router.
using [SIZE=2]*sudo dhclient eth0*[/SIZE] doesn't recieve offers , but surprisingly when i tried *[SIZE=2]dhclient eth0[/SIZE] *in [SIZE=2]*root shell with networking*[/SIZE] internet got configured very quickly and i can ping the router and any website...!!

i forgot to mention i have a[SIZE=2]* wired connection*[/SIZE] which i am trying to connect and the net is working fine with windows 7 on the same PC.

can't figure out the prob. :confused::confused: been trying for over a week.
can anyone give help to this nubee...:):):)  would really appreciate any help...
thanks


yes a lot of people are having this same problem

i beleve it has something to do with the new kernel...but it cannot be because this started since i was back from vacation :S (probably some smartass updated my PC wile i wasn't home :S)

---

### Post by sahil44 on 2010-07-16
;) HEY thanks for the reply auroraa9420..!!

i got frustrated by this issue ](*,)
so, finally i took the quick solution and reinstalled the 9.10 version of ubuntu. worked like a charm and my wired connection is now working at its full speed. :guitar:

wonder why they haven't come up with a solution to this problem when so many users are facing it.
i ll see if  the version that's gonna come this october is better for my pc...:-\"

thanks again

---

