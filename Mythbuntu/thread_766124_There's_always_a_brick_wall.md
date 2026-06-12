---
title: "There's always a brick wall"
date: 2008-04-25
forum: Mythbuntu
---

### Post by GuiGuy on 2008-04-25
I was really pleased to get Mythbuntu running. It's the best success I've have had with MythTV.

But, there's always that eventual brickwall. 

I want to use wireless networking. That's sorted. But everytime I reboot mythbuntu, this stupid dialog pops up wanting a "keyring" password. 

Given that Mythbuntu is supposed to be able to boot straight into MythTV, how can I get rid of the keyring password dialog? Please note that a [supposed fix posted here]("http://klamstwo.org/evad/archives/54") didn't work for me. 

Thanks

---

### Post by superm1 on 2008-04-25
You've got to install libpam-gnome-keyring.  Also see the README that comes with the package.  It explains how to activate it on Ubuntu.

---

### Post by GuiGuy on 2008-04-25
> **superm1 said:**
> You've got to install libpam-gnome-keyring.  Also see the README that comes with the package.  It explains how to activate it on Ubuntu.

I did that (linked in my OP). No good. Have decided to go cable and remove the wireless. 

Thanks

---

### Post by laga on 2008-04-25
It doesn't work if the keyring password is the same as your login password. Just set the password to the empty string instead and it should work.

---

### Post by GuiGuy on 2008-04-25
> **laga said:**
> It doesn't work if the keyring password is the same as your login password. Just set the password to the empty string instead and it should work.

No, the passwords were the same. I've given up and pulled a wire through the ceiling. It's better that way, anyway. 

But many thanks for the reply.

---

