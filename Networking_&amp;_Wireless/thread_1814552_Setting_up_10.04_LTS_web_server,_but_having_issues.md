---
title: "Setting up 10.04 LTS web server, but having issues."
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by Terwax1 on 2011-07-29
I was with hostgator before that provided cPanel and i "believe" they used CentOS. 

Now that i have moved to a different host, unmanaged, i installed copy of ubuntu 10.04 LTS 32 bit.

the website is [www.terwax.com](www.terwax.com).

Now I set up the link in /srv/www/terwax.com and under their, I moved files to public_html - no luck

Then i did google search and saw that i have to put files under /var/www. So i put all the files there, including index.html, no luck.

I get different errors such as 500.

My question is, where do i put my files? I am bringing emails, data bases and joomla site.

---

### Post by hakermania on 2011-07-29
I am not sure that I got the problem but you should place your files at
/var/www/
as it was
[http://www.terwax.com/](http://www.terwax.com/)
for example the file
/var/www/index.html
is the
[http://www.terwax.com/index.html](http://www.terwax.com/index.html)

---

### Post by Terwax1 on 2011-07-30
Is this the right section for this question?

---

