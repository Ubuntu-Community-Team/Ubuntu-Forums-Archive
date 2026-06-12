---
title: "setting up a domain"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-02-11
I just finished setting up Samba. At least I can share files between my PCs and Linux box. I would like to set up a domain so that the PCs log in to it. Can i do that in Samba and if so where would the code for that be?

---

### Post by wlraider70 on 2009-02-13
Bump

---

### Post by dmizer on 2009-02-13
I'm not sure exactly what you mean by setting up a domain, but it sounds like you're talking about active directory?

If so, you're looking at a fairly complicated Samba setup. More information can be found here: [https://help.ubuntu.com/community/SettingUpSamba?highlight=(AD)|(host)#Active%20Directory%20Integrated%20File%20Server](https://help.ubuntu.com/community/SettingUpSamba?highlight=(AD)|(host)#Active%20Directory%20Integrated%20File%20Server)

Hope that helps.

---

### Post by wlraider70 on 2009-02-14
Maybe I'm confused on my terms, but what I'm thinking about is way my Business network works. The computer logs on and files are synchronized and stff like that.

I know Linux is not windows, but only my server is Linux based the rest is XP.

---

### Post by jimv on 2009-02-14
You want this:

[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)

---

