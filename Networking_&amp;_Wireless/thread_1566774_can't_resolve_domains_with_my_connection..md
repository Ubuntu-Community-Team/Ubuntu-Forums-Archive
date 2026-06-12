---
title: "can't resolve domains with my connection."
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by jazdrv on 2010-09-02
Wondering if someone might know how to point me in the right direction. 

Somehow, my setup no longer can resolve domains. (ie: [www.google.com](www.google.com)) from ping or from a browser, etc. But, I can ping the ip addresses just fine. And, no -- it's not the /etc/hosts file. I literally can't access any urls period...

Perhaps something to do with the latest updates -- and it knocked over some sort of network configuration settings? (I keep my system pretty up to date generally)...

Anyone know where I should look?

I was looking at this url for some ideas... [http://oreilly.com/catalog/linag2/book/ch06.html](http://oreilly.com/catalog/linag2/book/ch06.html)
stuff like "name resolution", "resolver config", etc. but this stuff is new for me.

---

### Post by llawwehttam on 2010-09-02
Your problem is DNS servers.

Have you tried turning it off and on again? Have you tried turning your router off and on?

Both could possibly fix it.

---

### Post by BkkBonanza on 2010-09-02
Your **/etc/resolv.conf** file determines where your system sends DNS requests.
Usually this is set during boot by a dhcp process with your router. If it has been changed accidentally, or if your router is misconfigured to provide incorrect dns addresses then you'll not be able to do dns lookup.

If that file appears to be correct then check your firewall settings and make sure outbound port 53 udp and tcp are not blocked.

The command **cat /etc/resolv.conf** will list that file's contents. You can post it here if you're unsure if it's correct.

---

### Post by jazdrv on 2010-09-02
well, i have two laptops. one can access through my router just fine. 

while the other can't.

i restarted the modem/router. still nothing with the faulty one.

and, interestingly, i restarted the faulty laptop with the ubuntu startup iso. works fine when doing it like that (infact i'm typing to you now in this environment). but when i chroot into my "real  environment on this laptop, it doesn't work. 

so: on the same machine, it works in the iso startup environment. doesn't work in the chroot.

i thought perhaps something to do with my .bashrc (i have alot of setup things i do), but i've disabled it. it comes in vanilla. and still nothing.

:(

---

### Post by llawwehttam on 2010-09-02
Could you give us the output of:
```

cat /etc/resolv.conf
```

That should help.

---

### Post by jazdrv on 2010-09-02
ah, the 2nd tip was very helpful.

indeed that file was blank.

so i was able to refer to my 2nd laptop, cut/paste. and i'm back in business.

thank you so very much! :)

---

### Post by BkkBonanza on 2010-09-02
If you are using chroot as you say then you need to be sure a workable /etc path exists in the new root. 

If your /etc/resolv.conf isn't set on rebooting then you have a networking dhcp config issue. **/etc/networking/interfaces** needs to be set for correct dhcp values to be pulled from your router on boot. Of course, if you chroot to a new root and there is no /etc files present then it won't matter what happened on boot because /etc/resolv.conf won't be there any more. Correctly using a chroot environment is a fairly advanced topic.

---

