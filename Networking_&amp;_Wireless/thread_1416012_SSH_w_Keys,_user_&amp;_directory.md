---
title: "SSH w/ Keys, user &amp; directory"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by bertmanphx on 2010-02-25
Hello all,
I have a family member that lives a great distance away.  Their current install of SUSE 11.0 just recently had a problem with starting gnome-session, so the machine is being shipped back to me for repair, and a fresh install of Ubuntu :)
I had used RDP to remotely work on the machine, but due to the distance, and their relatively slow DSL connection, it was rather painful.
In the couple years since setting this machine up, I realized that RDP, even with a strong password is really not a good solution.  I use SSH on my local lan, and was considering setting up with a key, so I could admin their machine remotely, perhaps better.

I've read the how-to.  but am not sure of where I'll be when I log in?  In their /home, or /root, or, /home/mine? (if I set myself up on the machine).

Any thoughts would be appreciated.

bertmaphx

---

### Post by lewisforlife on 2010-02-25
You will be in the home directory of the user that you log in with.  Say you log in under "bob".  Look in the /etc/passwd file if you are not sure of the home directory of the user is.  You would log in like:

```
ssh bob@ip-address
```

Of course you would not get asked for a password if you were using key authentication.

---

### Post by bertmanphx on 2010-02-26
lewisforlife,
Ok, that's good information.  I'll have the opportunity to set it up and test here at home before shipping it back.

Thank you!

bertmanphx

Kubuntu 10.04

---

### Post by lewisforlife on 2010-02-26
One more thing, you will be using the external IP address of the router, not the internal IP address of the individual computer.  You will also have to forward the SSH port (TCP 22) in the router to the computer running the SSH server.

---

