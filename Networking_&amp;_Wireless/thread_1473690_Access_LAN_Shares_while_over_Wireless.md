---
title: "Access LAN Shares while over Wireless"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by maverick340 on 2010-05-05
My university has a central leased line that is split into wired and wireless. While plugged into the wired network i can access all the windows shares. However when on the wireless network, i cant access the wired shares. Windows laptops can however access them, but directly entering the share name ( \\share-name)

I am using Ubuntu 10.04.

---

### Post by maverick340 on 2010-05-16
bump ? :)

---

### Post by quadraphenia on 2010-07-14
> **maverick340 said:**
> My university has a central leased line that is split into wired and wireless. While plugged into the wired network i can access all the windows shares. However when on the wireless network, i cant access the wired shares. Windows laptops can however access them, but directly entering the share name ( \\share-name)

I am using Ubuntu 10.04.
Hi,
Did you try the following? 
Under "Places" select "Connect to Server...", select "Windows Share" as Server Type. Type in the shared PC's IP address in "Server:" and the shared folders should appear.

-v$

---

### Post by maverick340 on 2010-08-19
I have tried that, does not work.

---

### Post by anubhavrocks on 2010-08-19
Can you try this command:
smbtree

This will make sure that atleast the shares are visible on your system.

---

