---
title: "I installed the available updates today, and it broke my wireless."
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by TheBiles on 2009-02-02
Now, I hadn't updated in about a week, but when I ran the auto update it completely broke my wireless.  I'm on an Acer Aspire One, and I'm using the madwifi driver ath_pci. Has anyone else had trouble with this?

---

### Post by Jahendo on 2009-02-03
Yep.  I am having the same problem.  It says I'm connected but I can't do anything online, wired or not. I'm typing this on my PS3 so I know it's not my network. Help!  I need my net back for my online classes!

---

### Post by TheBiles on 2009-02-03
I reinstalled the driver and restarted a couple times, and it magically started working again. @_@

EDIT:  Now it's back to not working.  It will detect the networks, but it won't connect, and when I restarted just now it won't even detect them. I thought Ubuntu was supposed to be so hassle-free. -_-

---

### Post by danni-la on 2009-02-03
I had no luck with the madwifi drivers on my aao. Instead I use the drivers from linux-backports-modules-intrepid-generic
I have installed all the updates and it is still working fine no problems at all.

hope this helps! 

Cheers Danni

---

### Post by nothingspecial on 2009-02-04
If you use the madwifi drivers you have to recompile them everytime you get a new kernel. This is very simple (although I appreciate that it`s not if you`ve never done it before)

If you still have the madwifi directory you downloaded and extracted originally -

```
cd madwifi*
```

```
make clean
```

```
make
```

```
sudo make install
```

If you have deleted your original madwifi directory then you will have to download and compile madwifi again as you did originally. This time keep it ready for the next kernel.

---

