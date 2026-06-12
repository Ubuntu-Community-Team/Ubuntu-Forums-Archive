---
title: "SSH path error"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by hughcharlesparker on 2010-04-09
I'm using lucid on both my laptop and my desktop, both fully up to date.  When I ssh from my laptop to my desktop, I get "PATH: command not found", and then a shell with no working path.  I don't know enough about how bash starts up, or how ssh works, to figure it out.  Can anyone help?

Thanks.

Update - I've found .bash_profile, and commented out the first line, and now it works.  I'd still like to sort this, though, so I don't have to keep commenting it in and out.  The line is:
export PATH=$(PATH):/usr/share/android-sdk/tools

---

### Post by DGortze380 on 2010-04-09
> **hughcharlesparker said:**
> I'm using lucid on both my laptop and my desktop, both fully up to date.  When I ssh from my laptop to my desktop, I get "PATH: command not found", and then a shell with no working path.  I don't know enough about how bash starts up, or how ssh works, to figure it out.  Can anyone help?

Thanks.

Update - I've found .bash_profile, and commented out the first line, and now it works.  I'd still like to sort this, though, so I don't have to keep commenting it in and out.  The line is:
export PATH=$(PATH):/usr/share/android-sdk/tools

export PATH=$PATH;/usr/share/android-sdk/tools

---

