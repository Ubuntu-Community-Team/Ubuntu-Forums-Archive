---
title: "ATI Radeon x1950 issues"
date: 2010-06-28
forum: Multimedia Software
---

### Post by Nibblit on 2010-06-28
Hello! First time poster and Linux newbie!

I've been installing things to get my gaming back together and I run into this problem while installing the drivers from ATI, copied from the commandprompt

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.34bHO7
janne@PCNibblitPC:~/Hämtningar$ 


trying to use --iscurrentdistro did nothing to help, and the drivers I was trying to install are 
ati-driver-installer-8-10-x86.x86_64.run

Would love if someone has had any experience with it and can help!

---

### Post by Yellow Pasque on 2010-06-29
Your card is no longer supported by the ATI Catlayst drivers. Use the open-source drivers or use an older distro like Ubuntu Hardy/Debian Lenny

---

### Post by Nibblit on 2010-06-29
Ah I see, what version is Ubuntu Hardy (in numericals that is :) )

Also would you know were I can find the open-source drivers?

And most important, thank you so very much for your help, its really apprechiated!

---

### Post by urbanus on 2010-06-29
If you install Ubuntu 10.04, the open source drivers are used by default :-)

This is also true for distros based on ubuntu and other ones like Fedora 13.

---

### Post by Mark Phelps on 2010-06-29
> **Nibblit said:**
> Ah I see, what version is Ubuntu Hardy (in numericals that is :) )
Version 8.04.

> Also would you know were I can find the open-source drivers?

These are installed by default. IF you have the fglrx drivers installed and remove them, Ubuntu will install the open source drivers automatically.  If you do NOT have the fglrx drivers installed, you already have the open source drivers installed; otherwise, you would not be seeing a graphical desktop.

---

