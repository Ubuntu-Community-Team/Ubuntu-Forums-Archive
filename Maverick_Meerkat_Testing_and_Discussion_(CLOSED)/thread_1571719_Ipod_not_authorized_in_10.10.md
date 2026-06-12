---
title: "Ipod not authorized in 10.10"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dunc12 on 2010-09-10
When I plug my Ipod classic into my laptop, it gives me an error message saying "Unable to mount <ipod name>. Not authorized" It's really bugging me, is there something glaringly obvious I'm missing, or could it be a bug with 10.10? I didn't have this issue with 10.04

---

### Post by uRock on 2010-09-10
Have you searched launchpad to see if there is a bug report for this issue already? That feature might not be in the 10.10 image yet. Has a month left until release.

---

### Post by dunc12 on 2010-09-10
thanks for the help =] I think I may have found a solution on launchpad

---

### Post by caryb on 2010-09-10
> **dunc12 said:**
> thanks for the help =] I think I may have found a solution on launchpad

Link???

---

### Post by dunc12 on 2010-09-10
Alright, one problem to the solution I found, which is:

"Please open System&#8594;Administration &#8594; Users and group

Select your user push the "Advanced settings" button

goto the "User Privileges" tab and

check "Mount user-space filesystems (FUSE)".

Log out, log in, try connecting the drive again."

Only problem is that nothing happens when I click "advanced settings". Same for "properties" "add" "delete" etc.

edit: here's the link [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/113018](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/113018)

---

### Post by imiksu on 2010-09-20
I'm having exacly the same problem. In my other desktop user I got same warning message.

And besides that, I tried to add more privileges to that user, nothing happens when I click "Advanced settings".

I'm using Ubuntu 10.04.

Any tips doing that on command line?

---

### Post by cariboo on 2010-09-20
You can add yourself to the fuse group using the following command:

```
gpasswd -a USER fuse
```

Where USER is your user. You'll have to log out and log back in again for the changes to take affect.

---

### Post by dunc12 on 2010-09-20
I actually just updated 10.10 and it fixed the problem =] I just pulled up the update manager and installed everything available, works like charm now

---

