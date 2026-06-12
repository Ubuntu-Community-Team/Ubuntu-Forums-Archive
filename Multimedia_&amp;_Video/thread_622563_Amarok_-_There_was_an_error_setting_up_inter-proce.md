---
title: "Amarok - There was an error setting up inter-process...."
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by xcusmwah on 2007-11-24
When I start Amarok I get the following error...

There was an error setting up inter-process communications for KDE.  The message returned by the system was:

Could not read network connection list.
/home/jeremy/.DCOPserver_Jeremy Ubuntu_0

Please check that the "dcopserver" program is running!

Amarok is still able to open and function correctly but I'd like to get rid of the error message if possible.  I am also noticing a small icon in the top right hand corner of my screen (see screenshot).  Any help you could provide would be greatly appreciated.  Thank you

---

### Post by Jeffrey Magder on 2008-02-12
What was the result of:

```
ls ~/.kde -altrh
```

On my system the "root" account was the owner of that directory.   Running:

```
sudo chown -R myusername:myusername ~/.kde
```

Changed my account to the owner, and the problem disappeared after that.

---

### Post by rksingh54 on 2008-06-04
Thank you Jeffrey,

The command line "sudo chown -R myusername:myusername ~/.kde" seems to have done the trick. Thanks a million!

RKS

---

