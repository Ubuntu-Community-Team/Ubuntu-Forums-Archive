---
title: "Issue with mythweb program listing [SOLVED]"
date: 2008-11-24
forum: Mythbuntu
---

### Post by jasonsjunk on 2008-11-24
I was having an issue with the program guide on mythweb exceeding the memory allocated for php scripts.  I adjusted my memory allocation in my php.ini /etc/php5/apache2/php.ini but that did not work.  

There is another php memory allocation in /etc/apache2/sites-available/mythweb.conf I changed this to 64M and the guide works perfectly now.  

Just wanted to share in case somebody else has the same issue.  I am running mythbuntu 8.10

---

### Post by damirabal on 2008-12-01
> **jasonsjunk said:**
> I was having an issue with the program guide on mythweb exceeding the memory allocated for php scripts.  I adjusted my memory allocation in my php.ini /etc/php5/apache2/php.ini but that did not work.  

There is another php memory allocation in /etc/apache2/sites-available/mythweb.conf I changed this to 64M and the guide works perfectly now.  

Just wanted to share in case somebody else has the same issue.  I am running mythbuntu 8.10

Same thing here. Although the changed solved the Listings, please test the searches. It still has problems.

Any ideas?

Dennis

---

