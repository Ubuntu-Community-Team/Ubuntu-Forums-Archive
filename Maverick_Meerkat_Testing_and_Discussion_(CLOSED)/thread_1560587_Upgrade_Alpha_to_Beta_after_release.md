---
title: "Upgrade Alpha to Beta after release?"
date: 2010-08-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-08-25
Sorry, wrong threat!!!! 



I am unable to update through update manager nor terminal. Means I can not get rid of whatever causes this when a cure becomes available.

Question: Working happily with Maverick Alpha3. Will upgrade work after the beta is released somewhen in September? Or will I have to do a complete new install?

Michel

---

### Post by ratcheer on 2010-08-25
Read the forum sticky. In short, you do not have to reinstall the new Beta release, just keep everything updated and you will be at the Beta when it is available.

Tim

---

### Post by Yumi on 2010-08-25
yes, normally it is as you describe it.

But my update manager and sudo apt-get update in terminal wont update. I now have 390 updates pending.

How can I ever catch up?

---

### Post by andrewthomas on 2010-08-25
> **Yumi said:**
> yes, normally it is as you describe it.

But my update manager and sudo apt-get update in terminal wont update. I now have 390 updates pending.

How can I ever catch up?
did you try 
```
sudo apt-get update && sudo apt-get upgrade
```
or just sudo apt-get update?

---

### Post by andrewabc on 2010-08-25
If you installed an early alpha it is suggested to reinstall at final, due to some old packages (unclutter) no longer being installed by default, and old files that might be useless, or bad defaults.

Also, if you upgrading since early alphas, and not manually removed old kernels you can have a gigabyte or more of old kernels that are useless installed.

Although if upgraded alphas work fine for you, then no need to reinstall. Although I'd still make sure to have livecd/liveusb of 10.10 in case your install explodes.

But yes you can upgrade alpha->beta->RC->final
There are no special steps required for upgrading, just make sure update-manager has latest updates installed.

---

### Post by ranch hand on 2010-08-25
> **andrewabc said:**
> If you installed an early alpha it is suggested to reinstall at final, due to some old packages (unclutter) no longer being installed by default, and old files that might be useless, or bad defaults.

Also, if you upgrading since early alphas, and not manually removed old kernels you can have a gigabyte or more of old kernels that are useless installed.

Although if upgraded alphas work fine for you, then no need to reinstall. Although I'd still make sure to have livecd/liveusb of 10.10 in case your install explodes.

But yes you can upgrade alpha->beta->RC->final
There are no special steps required for upgrading, just make sure update-manager has latest updates installed.
Another way to put this is;
READ THE STICKIES.

---

### Post by ktp on 2010-08-25
> **ranch hand said:**
> Another way to put this is;
READ THE STICKIES.

nicely put it.

---

### Post by VastOne on 2010-08-25
> **andrewthomas said:**
> did you try 
```
sudo apt-get update && sudo apt-get upgrade
```
or just sudo apt-get update?

Or even better

```
sudo apt-get dist-upgrade
```

---

### Post by Yumi on 2010-08-26
Thank you for the information. I now do not worry about my broken update-manager and apt-get update. Instead when the next milestone release comes along I try the upgrade to become up to date again.

Ranch-Hand, I can and do read. If you can tell me which "sticky" relates to my particular problem then you are welcome. Otherwise save your efforts.

Michael

---

### Post by andrewthomas on 2010-08-26
> **Yumi said:**
>  If you can tell me which "sticky" relates to my particular problem then you are welcome. **Common Problems / Frequently Asked Questions About Testing**
[http://ubuntuforums.org/showthread.php?t=1500648](http://ubuntuforums.org/showthread.php?t=1500648)

---

### Post by ezsit on 2010-08-26
> If you can tell me which "sticky" relates to my particular problem then you are welcome.

There are five stickies, some with names that would not apply. Is it that hard to find the right one?

---

### Post by VMC on 2010-08-26
> **ezsit said:**
> There are five stickies, some with names that would not apply. Is it that hard to find the right one?

I was thinking the same thing but didn't know how to word it. They are after all, self explanatory.

---

### Post by Yumi on 2010-08-26
The stickies indeed cover the subject like "Do I have to reinstall the latest alpha / beta / RC when it comes out". But, it does not mention if upgrade works with a milestone release especially when update manager is broken.

Anyhow, I got the answer I was after and thank again for it.

Michael

---

