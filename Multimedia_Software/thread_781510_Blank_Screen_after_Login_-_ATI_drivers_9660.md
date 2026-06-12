---
title: "Blank Screen after Login - ATI drivers 9660"
date: 2008-05-04
forum: Multimedia Software
---

### Post by [pl]ice on 2008-05-04
Hi guys,
  Got problem here, the 7.10 had the same problem. After I played around with compiz, i had a blank screen after login. In safemode I had no frame etc

In Hardy, i just did a fresh install, and installed as well compiz-configuration tool. Installed the restriced drivers and got the blank screen again after login.
 Wheres the problem? I tried removing drivers manualy then installing from ATI website, but nothing helped.
 Anyone?
 Thanks
 Polish

---

### Post by sal-e on 2008-05-04
Hi [Pl]
Last night I had similar problem after I upgraded from 7.10 to 8.04.
I am not sure what version of Ubuntu you are using, but let me try to help. If there is more experience user please step in and correct me if I am wrong.
I am assuming that you have normal 'Login' screen, but the screen goes blank after you login. Is this correct?

To recover your GNOME desktop you should switch to 'Failsafe GNOME' session. To do this you should click on the 'Options' button (bottom left corner in your login display) and select 'Select Session...' I hope that you are able see your desktop now.

Next you should try to find exactly where is the problem. In my case the ATI binary driver did not load properly because the Mesa driver. To solve my problem I had to remove the old installation of ATI binary driver, fix /etc/X11/xorg.conf, disable compiz and then manually re-install the latest (8.04) driver form ATI website and then re-enable compiz. I found instruction here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method")
If you are using different version of Ubuntu check this page:
[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")
Just remember I had to use Method 2 (Manual) because for some reason the 'easy way' did not work for me.

I hope you find solution quickly. Good luck,
SAL-e

---

### Post by [pl]ice on 2008-05-04
I'm using Hardy and now i'm pretty sure its the ATI drivers. Will try the same way you did it :)
 Thanks :)

---

### Post by Kowalski_GT-R on 2008-05-04
> **'[pl]ice said:**
> I'm using Hardy and now i'm pretty sure its the ATI drivers.

not the drivers themselves, it's the drivers + compiz interaction messing about.

Not that its solving anything....

---

### Post by [pl]ice on 2008-05-04
> **Kowalski_GT-R said:**
> not the drivers themselves, it's the drivers + compiz interaction messing about.

Not that its solving anything....

well, if I still got problems from trying to install the ati manually, would it be worth it to go shopping tomorrow for an average geforce card? :) ?

---

### Post by Kowalski_GT-R on 2008-05-04
been tempted, but I'm not shopping for an AGP card anymore.

Not bothered either with rescuing an old GeForce3 series card.

Be aware! search about in the forums, I've read (without going into detail) someone's having problems with Nvidia too.

As for me, I'm going along fine with MESA drivers and no acceleration, waiting for a fix.

The trouble between ATI/fglrx/compiz has been filed in Launchpad.

Regards,

Andre

---

### Post by [pl]ice on 2008-05-04
no luck.Same error. Even gnome failsafe,fails as well :(

Well,MESA it is then... will wait untill Synaptic will give me a new compiz :) (hope that will work better...)
thanks for the help :)
Nite nite

---

