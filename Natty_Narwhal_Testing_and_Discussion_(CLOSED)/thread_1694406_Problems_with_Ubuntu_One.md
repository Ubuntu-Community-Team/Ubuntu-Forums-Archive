---
title: "Problems with Ubuntu One"
date: 2011-02-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by clivejo on 2011-02-24
I have never used Ubuntu One before but ever since my last update, a process called ubuntuone-syncdaemon is hogging my CPU's.  Every time I kill it it restarts!  How do I get rid of this?

---

### Post by dino99 on 2011-02-24
open synaptic and remove/purge every installed ubuntuone packages (you might need to uninstall the ubuntu-desktop metapackage too)

---

### Post by sgage on 2011-02-24
> **dino99 said:**
> open synaptic and remove/purge every installed ubuntuone packages (you might need to uninstall the ubuntu-desktop metapackage too)

Or, more simply, you can just go into Preferences/Startup Apps and uncheck Ubuntu One - after a logout/in or reboot your problem will be solved.

---

### Post by clivejo on 2011-02-24
> **sgage said:**
> Or, more simply, you can just go into Preferences/Startup Apps and uncheck Ubuntu One - after a logout/in or reboot your problem will be solved.


Thanks, thats fixed it, any idea why it was doing that?

---

