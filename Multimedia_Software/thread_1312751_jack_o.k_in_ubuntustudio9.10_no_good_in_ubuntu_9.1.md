---
title: "jack o.k in ubuntustudio9.10 no good in ubuntu 9.10"
date: 2009-11-03
forum: Multimedia Software
---

### Post by supapete on 2009-11-03
So what ? My wireless only works in ubuntu 9.10 and not in ubuntustudio 9.10. Jack only runs in studio9.10 but not in ubuntu9.10. I've posted in the "wireless" forum as well. regards and thanks for you genius answers in advance. P

---

### Post by angelsguitar on 2009-11-03
Ubuntu Studio's kernel and general configuration is optimized for multimedia, but mainstream Ubuntu is not.  So it is natural that jack's performance would be better in Ubuntu Studio than in Ubuntu.  To get it properly running you'll need to install the realtime kernel and modify some settings (like the /etc/security/limits.conf file).

I will advice to just use Ubuntu Studio for multimedia work and leave Ubuntu as it is, using it for mainstream work.  Ubuntu Studio is already optimized for multimedia work; it may save you time and effort.

---

### Post by supapete on 2009-11-03
Thanks angelsguitar. All received and understood. My problem is that wireless won't work in ubuntustudio but does in ubuntu. The fact that jack's no good in ubuntu muddied the waters. I'm ubuntustudio's number one fan, but I can't get the3945abg wireless to fly. I've posted similarly in the network forum. Thanks again. best regards P

---

