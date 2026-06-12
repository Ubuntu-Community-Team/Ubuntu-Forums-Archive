---
title: "ATI Driver issue"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by ddrichards on 2007-05-30
Hi all,

In a quest to get one of my programs working, I thought I would try the latest driver from ATI.  I used the Envy program to install it.  After rebooting, the program still did not work and other graphics programs began to run at a slower pace than before.  So, the ultimate question I have is:

How do I go back to the Restricted drivers that were being used before?

I am running Feisty on a Dell E1505.  Let me know if there is any other info I can provide.

Thanks!

Dan

---

### Post by windows hater on 2007-05-30
were might i find this envy

---

### Post by ddrichards on 2007-05-30
Well, I've uninstalled the new drivers (using the package manager) and reinstalled the original fglrx driver from the package manager.  However, now it states that the driver is enabled but not in use when you look at it in the restrictive driver manager.

Can anyone help me???  I really need to get this working again.

Thanks!

Dan

---

### Post by ddrichards on 2007-05-30
You can find it here...

```
http://albertomilone.com/nvidia_scripts1.html
```

Dan

---

### Post by ddrichards on 2007-05-31
Well, I fixed it.  Turns out, while I was marking the packages for removal, it truly wasn't removing all of the pieces.  I should have used "Mark for complete removal".  Then I went into the Restricted Driver Manager and enabled the FGLRX driver again.

All is well now.

---

