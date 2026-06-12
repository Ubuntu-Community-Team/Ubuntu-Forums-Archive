---
title: "SSHFS write permissions?"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by hotstovejer on 2009-05-02
I heart SSHFS. I only have a couple of questions. I have 3 machines that I use SSHFS on. 2 intrepid, 1 jaunty. I have a folder in my home directory that I mount the other machine to. So, at home, when I connect to my jaunty sshfs share, I can't write to it. It tells me there is no space left, and when I do go to xfer something over to it, I get the error message ```
There is not enough space on the destination. Try to remove files to make space.
```

Now, when I am on my Jaunty machine, and I connect to a sshfs share, I CAN write to it no problem. I am only connecting to the home dirs of mine on each machine, and user name is the same. Permissions are the same as well on the dirs.

Any idea as to where I should start looking for the issue? 

Thanks!

Jeremy

---

### Post by keithweddell on 2009-05-02
I think this was a bug in Intrepid which is fixed in Jaunty: [link to launchpad]("https://bugs.launchpad.net/bugs/298628")

---

### Post by hotstovejer on 2009-05-04
Badabing! That did the trick!

Thanks alot!

Jeremy

---

