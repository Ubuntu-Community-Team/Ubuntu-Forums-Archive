---
title: "Mapping from hardware to a interface name"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by baggins on 2009-10-14
Does any one know where the mapping from hardware to the ethX interface names happen?

At work I moved the hard drive from one laptop to another identical laptop. On the original machine the interfaces were named eth0 for wired and eth1 for wireless. On the new system the interfaces are named eth2 and eth3 for wired and wireless respectively.
So somehow the system must recognize that the interfaces on the new laptop is different from the original.

It's not really a problem, everything still works as it's supposed to using network manager.
I didn't even notice until the employee that uses the laptop asked me why he didn't have an eth0 interface anymore. 

However my (not so) inner geek demands that I find an explanation :D So can any one give me with one ??

-- Jon

---

### Post by chili555 on 2009-10-14
> Does any one know where the mapping from hardware to the ethX interface names happen?I do! It is located in */etc/udev/rules.d/70-persistent-net.rules*. If your inner geek needs further guidance, ask him/her to post back.

---

### Post by baggins on 2009-10-14
Aha! of course that's it, thanks 
(I can now go to bed with an easy heart knowing that I will not have nightmares of ever changing ethernet interfaces :D )

-- Jon

Ps. Actually this is slightly embarrassing, I have been using linux for close to 13 years, the last 4 years for a living. I really ought to have guessed that it would be somewhere in the udev system. 
Oh well lets hope that my boss don't find out (or else merciless laughter will ensue :) )

---

### Post by chili555 on 2009-10-14
It seems like it's in a different place in every different distribution. Incidentally, if you have your interfaces configured in */etc/network/interfaces*, rather than using Network Mangler, be sure to make the corresponding changes there, too. Then I suggest a reboot.> the last 4 years for a living.I see the professionals quite a bit here on the forum. We're just one big, happy community!

Have a great night!

---

