---
title: "Read-Only Ipod"
date: 2010-09-22
forum: Multimedia Software
---

### Post by Cerin on 2010-09-22
I just migrated from Fedora to Ubuntu. Under Fedora, I used gtkpod to manage my Ipod Nano, and it worked flawlessly. I see the Ubuntu's repos can the same program, but I was surprised to find Ubuntu only mounts Ipods as a read-only filesystem, which completely breaks all Ipod management apps. I can't even use it as a flash drive.

Am I missing something? I'm having a hard time believing this is the "correct" behavior, especially when Fedora (much less friendly then Ubuntu) never had a problem. How can I get Ubuntu to correctly mount my Ipod so I can manage it with gtkpod?

---

### Post by Chronon on 2010-09-24
I have found that damaged file systems commonly get mounted as read-only.  Try doing a fsck on your iPod to try to detect and correct possible errors.

---

