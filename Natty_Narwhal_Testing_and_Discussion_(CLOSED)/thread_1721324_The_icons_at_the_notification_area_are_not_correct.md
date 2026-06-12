---
title: "The icons at the notification area are not correct."
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by d0ngw on 2011-04-04
When I upgraded to Ubuntu 11.04 beta1,the icons at the notification area are not correct:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188064&stc=1&d=1301931156[/IMG]

How to recover the borken icons?

Thanks.

---

### Post by Krytarik on 2011-04-04
What icon theme is currently set?

---

### Post by d0ngw on 2011-04-04
The current icon theme is Humanity.
I try every icon theme but it's still not correct.

---

### Post by Elfy on 2011-04-04
moved to natty forum

---

### Post by Krytarik on 2011-04-04
Maybe you are using a theme that includes some icons? If so, then they override those of any icon theme.

Check "~/.xsession-errors" for related error messages.

---

### Post by Mblackwell on 2011-04-04
It's probably this:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385)

---

### Post by Harry33 on 2011-04-04
> **Mblackwell said:**
> It's probably this:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385)

That is true. This issue was also looket at in the bug #741387 (ubuntu-mono).
But later it was discovered that the issue is also seen on setups where ubuntu-mono is not even installed.

---

### Post by d0ngw on 2011-04-05
> **Harry33 said:**
> That is true. This issue was also looket at in the bug #741387 (ubuntu-mono).
But later it was discovered that the issue is also seen on setups where ubuntu-mono is not even installed.

I looked the bug #741387 and the problem with me,now only waiting for the bug fixes.
Thanks.

---

### Post by Harry33 on 2011-04-05
> **d0ngw said:**
> I looked the bug #741387 and the problem with me,now only waiting for the bug fixes.
Thanks.

If you want you icons back, you can simply downgrade the package
libappindicator1_0.3.0-0ubuntu1
to the previous version 0.2.99-0ubuntu1

From here (select the architecture first):
[https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1](https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1)

Then go to the directory (from terminal) where you downloaded it.
Then run (for 64-bit):
```
sudo dpkg -i libappindicator_0.2.99-0ubuntu1_amd64.deb
```

Then reboot.

---

