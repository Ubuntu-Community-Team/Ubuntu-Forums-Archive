---
title: "Anyone else lose Guest Additions after latest .36 kernel release?"
date: 2011-03-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by grubdude on 2011-03-20
Hi,
 
Everything was working fine until .36 release. I re-installed guest additions sucessfully but the screen will not re-size to full screen. I do have mouse integration, so I know Guest Additions are working.
 
Any ideas?

---

### Post by DougieFresh4U on 2011-03-20
> **grubdude said:**
> Hi,
 
Everything was working fine until .36 release. 
 
Any ideas?

I believe were up to [2.6.38]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/")

---

### Post by Harry33 on 2011-03-20
> **DougieFresh4U said:**
> I believe were up to [2.6.38]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/")

Yeah you are right about that.
Grubdude means the 36th Canonical's amendment of it: 2.6.38-7.36.

---

### Post by patrickaupperle on 2011-03-20
Install from repos.

Edit:
If you install package virtualbox-ose-guest-x11 from the repository, then restart everything works great.

Edit2: 
To answer your actual question, I installed today from a daily image and they wouldn't work. A quick google search suggested the above package.

---

### Post by grubdude on 2011-03-20
Great and it worked after that fine? Thanks guys!
 
Tried it...Works! Thanks. :-)

---

### Post by Merk42 on 2011-03-20
> **grubdude said:**
> Great and it worked after that fine? Thanks guys!
 
Tried it...Works! Thanks. :-)I tried and it gave me a completely black screen.

---

### Post by patrickaupperle on 2011-03-30
> **Merk42 said:**
> I tried and it gave me a completely black screen.

Are you using the most updated virtualbox? Also, you intalled it in the guest, right?

---

