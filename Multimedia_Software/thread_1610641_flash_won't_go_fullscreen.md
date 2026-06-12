---
title: "flash won't go fullscreen"
date: 2010-10-31
forum: Multimedia Software
---

### Post by efball3 on 2010-10-31
Flash works fine inside the browser, but it won't go fullscreen.  It goes fullscreen for a fraction a second, then drops back into the browser.

It's the same for any browser:  chrome, firefox, opera.  It happens on youtube and hulu.

It does not happen if I log in as a different user, just my account.
It works fine on my other computer (also ubuntu 10.04).

Shockwave Flash 10.2 d161  (64-bit).  Ubuntu Lucid 10.04.
There are no flash plugins in my home directory (.mozilla/plugins/ or similar places).  I've tried flash-aid in firefox.

Any ideas how to fix it?  
Thank you,

---

### Post by efball3 on 2010-11-03
I unchecked "unredirect fullscreen windows" in the compiz setting manager and flash works fine now.

---

### Post by khopek on 2010-11-26
This didn't work for me as I never had that option checked. Any other ideas? This issue is starting to #*$( me off so much I'm almost ready to go back to winblowz...

---

### Post by highbrow69 on 2010-11-26
I found the solution from [https://bugzilla.redhat.com/show_bug.cgi?id=608957](https://bugzilla.redhat.com/show_bug.cgi?id=608957)

sudo mkdir -p /etc/adobe
sudo nano /etc/adobe/mms.cfg

Add the following line into mms.cfg, save and exit:

OverrideGPUValidation=1

That's it! Restart all browsers and you can now play full screen flash in compiz.

---

