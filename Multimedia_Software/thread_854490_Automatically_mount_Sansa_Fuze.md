---
title: "Automatically mount Sansa Fuze"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Daswebmastri on 2008-07-09
Okay, I've looked at all the other Sansa posts, and found items of little interest.
 Ever since installing vmware on ubuntu 8.04, my Sansa 2gb Fuze will not mount unless I do one of several things:

1.) Run my WinXP virtual machine
2.) run lsusb
3.) turn and walk away.

Anyway, I have a shortcut that runs lsusb, and that works, but is there a way that ubuntu can run that command every time a usb device connects?

---

### Post by jaygo on 2008-09-04
I'm troubleshooting the same fuze for a friend, with the same issue.

Thanks for the lsusb fix. It's nice that it doesn't require root and doesn't duplicate previously mounted USB drives. I've posted it in the few other threads here.

I don't know of any way to auto-run a script when the fuze is not being detected at the hardware level but perhaps there is another service that *is* detecting it. I did read that many people found connecting it through a hub worked perfectly.

Would there be any harm in a script that ran lsusb every X seconds all day?

---

