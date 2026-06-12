---
title: "map an XP folder on Ubuntu?"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by masooga on 2006-05-05
Hello networking gurus!

I was wondering if someone could give me a quick run-through of how to map a student drive that's on an XP server. What programs and information will I need?

Thanks!

---

### Post by kzutter on 2006-05-05
Since you say "map", I assume you want to "mount" it.
To do that you will need to install the  smbfs package.
Then you will need to create a mount point for it. (Just an empty directory with appropriate permissions set for the user that will access it once it is mounted)

The rest will depend on whether you will want to mount it manually or automatically.

And of course, the info about the XP. UNC name, username, password, etc.

man smbmount will tell you enough to either figure it out or baffle the sh** out you.

Let me know if you get stuck.

---

