---
title: "vob to dvd or iso"
date: 2009-10-06
forum: Multimedia Software
---

### Post by jasonmichel on 2009-10-06
I have several dvd rips that i want to burn onto dvd, they are currently in Vob format.  How can i convert them?  i've tried using mkisofs -dvd-video  -o ybcr1.iso /home/User/DVD Movies/ybcr1, which is the path that has the movie but i get 
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - '/home/user/DVD'.

can someone point me in the right direction?

---

### Post by GrandpaLeaman on 2009-10-06
Try this instead:
 
mkisofs -dvd-video -o ybcr1.iso /home/User/DVD\ Movies/ybcr1
 
the program mkisofs doesn't like spaces.

---

### Post by jasonmichel on 2009-10-06
worked like a champ...thanks!!

---

