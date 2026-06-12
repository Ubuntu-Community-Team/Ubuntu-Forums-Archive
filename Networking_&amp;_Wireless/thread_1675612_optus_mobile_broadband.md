---
title: "optus mobile broadband"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by jalalee on 2011-01-25
have huawei model E1762 dongle and have followed new connection procedure which seems ok but still will not connect. have tried forum suggestions with no success. works on windows and 3 mobile broadband works ok on ubuntu. help appreciated   thankyou

---

### Post by Rhubarb on 2011-01-25
Try installing **usb-modeswitch** from the ubuntu repositories.
I've found that has helped getting a newer vodafone dongle working (I can't be sure what model dongle it is, most likely a huawei one).
I don't have access to any optus sim cards with 3G access, so I can't test out that much for you.

Once usb-modeswitch is installed, try setting up a new 3G connection via the Network Manager, then with any luck it should work for you.

---

### Post by jalalee on 2011-01-25
thankyou for that will try it regards

---

### Post by jalalee on 2011-01-26
solved by selecting cant find provider then typed yesoptus then typed in plan apn (got this from tech support by calling optus ) which in my case is connectcap then completed installation and it connected straight away.  Please how do i mark this thread solved

---

### Post by manoftao on 2011-06-15
> **jalalee said:**
> solved by selecting cant find provider then typed yesoptus then typed in plan apn (got this from tech support by calling optus ) which in my case is connectcap then completed installation and it connected straight away.  Please how do i mark this thread solved

Thank you so much for your humble but essential bit of info that got me connected via this damn huawei e1762 using ubuntu 11.04. This is after reading some real daunting threads.. Cheers mate!

---

