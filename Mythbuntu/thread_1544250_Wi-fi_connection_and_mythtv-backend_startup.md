---
title: "Wi-fi connection and mythtv-backend startup"
date: 2010-08-02
forum: Mythbuntu
---

### Post by yono3333 on 2010-08-02
Hi,

I have a problem with a Myth install, from reading around it seems that my mythtv-backend will not start as my wi-fi connection comes up later in the boot process.

I can get the frontend to start with a .gnomerc file with the following text: 

```
sleep 20 && mythwelcome > /tmp/mythwelcome.log 2>&1 &
```Is it possible to use this file to: sleep...start the backend...sleep some more...then start the frontend?  If so, would anyone be so kind as to tell me the correct syntax to put in my .gnomerc file?

Many thanks in advance

---

### Post by superm1 on 2010-08-02
> **yono3333 said:**
> Hi,

I have a problem with a Myth install, from reading around it seems that my mythtv-backend will not start as my wi-fi connection comes up later in the boot process.

I can get the frontend to start with a .gnomerc file with the following text: 

```
sleep 20 && mythwelcome > /tmp/mythwelcome.log 2>&1 &
```Is it possible to use this file to: sleep...start the backend...sleep some more...then start the frontend?  If so, would anyone be so kind as to tell me the correct syntax to put in my .gnomerc file?

Many thanks in advance
Try making the connection system wide instead (apply to all users).  That should cause it to come up earlier.

---

### Post by yono3333 on 2010-08-03
Many thanks superm1,

I have checked my settings, both 'connect automatically' and 'available to all users' are ticked

Any other suggestions?

Thanks again

---

### Post by nickrout on 2010-08-03
get rid of network manager and start your network the old fashioned way by setting the appropriate bits in /etc/networking/interfaces

---

### Post by yono3333 on 2010-08-08
Thanks nickrout,

After plenty of mucking around, I have got this to work, as you  suggested, by disabling the Network Manager and manually setting up the  /etc/network/interfaces file.

Thanks again

---

