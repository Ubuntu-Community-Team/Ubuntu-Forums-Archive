---
title: "Fixes not working for Nvidia GeForce 6100"
date: 2008-11-07
forum: Multimedia Software
---

### Post by enofman on 2008-11-07
I have tried numerous fixes for my problem without any good results.
I upgraded to intrepid and now my nvidia on-board GeForce 6100 is not recognized no matter what I do.  I have uninstall all drivers and have tried every driver available.  I have tried to use glx 96, 173, and 177. I get the same results with all of them. I have used Envy and the hardware device driver selector. I continue to get a message on boot up which says no driver was selected. It does not matter what driver my video is not recognized. I have included lspci file and would very much appreciate any help. If there is something else that is needed please tell me where to find it and I will be more than happy to get the information needed.

Gary
enofman

---

### Post by cariboo on 2008-11-07
Are you using the right kernel? the new drivers won't work with anything less than kernel 2.6.27. To find out what kernel you are using in a terminal type:

```
uname -a
```

the result should look something lik this:

```
 uname -a
Linux alexis 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux
```

If you are running an older kernel, update and try installing the drivers again.

Jim

---

### Post by enofman on 2008-11-07
cariboo907
2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux
It appears to be the correct one. I have just discovered other problems. The dvd-cd reader writer is not being seen, my vitualbox is not working correctly. I guess one problem at a time.

Thanks

---

### Post by WelterPelter on 2008-11-09
I'm having the same problem with the 6100. 
Have tried all the fixes. 
Nothing works.

---

### Post by enofman on 2008-11-09
I guess the only way to fix this is to go back to Hardy, everything worked great in Hardy.
Gary

---

### Post by WelterPelter on 2008-11-17
I'm happy to report that the latest updates include the 96 driver. 
If you apt-get install this, everything works perfectly with the 6100.
Thanks!

---

### Post by texasjim on 2008-11-29
> **WelterPelter said:**
> I'm happy to report that the latest updates include the 96 driver. 
If you apt-get install this, everything works perfectly with the 6100.
Thanks!
WelterPelter:
Wish I had seen this post a week ago when you entered it. I have been beating my head against the GUI installer off and on for about a month. Have dualboot 8.10's on this machine, one worked one didn't. Finally re-installed today - no joy, just a thin white line or command line. 
 
apt-get install fixed it in 10 minutes.

  Thanks
   Jim

---

