---
title: "Wireless slows down when on battery"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by Ctulhu on 2011-05-31
I have Ubuntu 10.10 running on a Dell Latitude E6500 notebook and am using the Broadcom STA wireless driver (just in passing, same happens on Mint 10). My problem is this:

- when the computer is plugged into a power outlet, wireless works fine, but
- when the computer is running on battery, it hardly works at all: The network strength indicator item still shows the same connection strength but data are not transmitted anymore or only extremely slowly (google.com might 2 minutes to load).

The drop in performance literally happens 1 sec after unplugging it, and once the notebook is plugged into external power again, it resumes after a few seconds. (I have tested this with big downloads where you can see Firefox's or the Update Manager's download speeds.) The BIOS doesn't seem to have power saving settings that make that happen, and I haven't found any in Ubuntu -- any clues??

---

### Post by Ctulhu on 2011-05-31
Ok, this was a re-posting of a 4-week old posting here. Now, after an hour or so I got a helpful reply in the Mint forums: It IS a power-saving feature:

sudo iwconfig eth1 power off

Only thing missing now, how to make this permament ...

---

### Post by joonpy on 2012-01-25
> **Ctulhu said:**
> 
sudo iwconfig eth1 power off

Only thing missing now, how to make this permament ...

Thanks for the info. I suspect that you already know this, but 
[http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67) says you can put the following in /etc/pm/power.d/wireless file:

```
#!/bin/sh

/sbin/iwconfig eth1 power off

```

and it should work without intervention.

-Joon

---

### Post by Redflea on 2012-01-26
I've been having this issue of really slow wifi, and tried to create the file but am getting told by the OS that I don't have rights to create a file in that directory (power.d).

I tried saving it to the folder, and copying it from another folder, and it failed either way. 

What do I need to do to allow myself that option?  

When I check permissions it says I'm not the owner so I can't change them.  It's my laptop - I am TO the owner!  ;-) 

P.S.  I'm sure this is obvious, but I'm Linux noob.

Nvm...DOH.  sudo cp...

---

### Post by rodrigogp on 2012-04-08
did you use use sudo to create the file? you would need root permissions...

---

