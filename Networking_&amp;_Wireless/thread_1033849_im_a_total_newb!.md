---
title: "im a total newb!"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Ronnie Foxxx on 2009-01-07
ok so i got my gmas sony vio she wasnt useing. installed ubuntu 8.10.
i dont have an internet connection in myroom, but i have wireless in my house. im currently online with my macbook. what do i need to do to get my ubuntu desktop machine to go wireless???

again im a total newb by i HAD to try linux. it seeems so very f***ing kewl.

thnk u in advance.
Ronnie Foxxx

---

### Post by dougpan on 2009-01-07
If you want to try Linux I think you've made the best choice for a newbi.

I would suggest going to Sun Microsystems site at: [http://www.virtualbox.org](http://www.virtualbox.org) and download VirtualBox for the Mac and then install Ubuntu on it.

It lets you run Linux on your Mac very gracefully.

I also have a Sony VIAO and picked up a Linksys wireless adapter.

Works just fine.

---

### Post by albinootje on 2009-01-07
> **Ronnie Foxxx said:**
> ok so i got my gmas sony vio she wasnt useing. installed ubuntu 8.10.
i dont have an internet connection in myroom, but i have wireless in my house. im currently online with my macbook. what do i need to do to get my ubuntu desktop machine to go wireless???


If it didn't work out of the box, try the Ndiswrapper solution :
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

And post the output of the following commands in a terminal :
```

lspci
lshw -c network
ifconfig -a
iwconfig

```

---

