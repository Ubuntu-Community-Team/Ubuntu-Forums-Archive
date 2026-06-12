---
title: "proftpd manage folders per user"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by Chrus on 2011-05-30
Im trying to set up an Ubuntu box as a FTP server. I followed [Frodon's guide]("http://ubuntuforums.org/showthread.php?t=79588") to set up proftpd and that works no problems. But i need a bit of help with aditional configuration.

What i need is to have 5 users (lets call them Sydney, Brisbane, Melbourne, Perth and John). I need for each user (except John) to log in and see an "Upload" folder and a "Download" folder, but they need to be unique, and each user cant see each others folders. And when John connects he should get "Syd Upload", "Syd Download", "Bri Upload", "Bri Download", "Mel Upload", Mel Download", "Per Upload" and "Per Download".

Is it possible with proftpd to have these 8 folders somewhere like /data, and then have an empty ftp root folder that will link in the appropriate folders depending on who logs in?

I've done this before with filezilla... just need to know how to do it on a linux box.

Thanks.

PS: I should also point out this is 8.04 server... so no GUI (excpet webmin)

---

### Post by Lars Noodén on 2011-05-30
Have you read up on using chroot?

---

