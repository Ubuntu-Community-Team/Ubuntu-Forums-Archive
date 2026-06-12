---
title: "Enabling wireless networks for all users"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by timbim on 2012-06-23
Hi,

Running a clean install of 12.04.  I basically need all users to be able to connect to new wireless networks without requiring authentication.  I certainly can't make all users sudoers, and would like to not have to enter any password at all for connecting to networks.  There have been previous threads about this, but none that I've found that relate to 12.04, nor any that have been fully answered.  Is there a solution to this new to 12.04?  I've not found any groups that look like they might help the cause.

Thanks,
Tim

---

### Post by timbim on 2012-06-25
Bump.

Anyone know anything or am I going to have to report this as a bug?

---

### Post by rukiaEnix on 2012-06-25
You want to select your wireless connection without administrative password?

---

### Post by timbim on 2012-06-25
I want non-sudo users to be able to connect to new (as in not seen by the computer before) wireless networks without having to have a sudoer enter their password.  Ideally, no password entry would have to take place.

Obviously I'd still need to enter the wifi network's passphrase if it's an encrypted network.

Thanks.

---

### Post by rukiaEnix on 2012-06-25
I have an idea.

Create a group and add the users.

Then add that group to sudoers but you can restrict it, just allowing to use the network manager without a password. And denying the use of sudo in anything else.

---

### Post by rukiaEnix on 2012-06-25
Don't go to the URL of that guy it looks like malware or a bot

---

### Post by timbim on 2012-06-26
That idea is the best solution I'd found anywhere else.  It really shouldn't be that hard, I'm going to file it as a wishlist on launchpad.

Thanks anyway.

---

### Post by rukiaEnix on 2012-06-26
Please tell us if it helps you my idea.

---

