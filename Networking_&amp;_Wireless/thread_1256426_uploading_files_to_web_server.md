---
title: "uploading files to web server"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by philcamlin on 2009-09-02
hey guys, 
i was wondering if i could have an option on how to upload files to a directory on my web page 
is that possible??

please keep it as simple as possible cause im new to the web page developing :)

---

### Post by cybergalvez on 2009-09-02
> **philcamlin said:**
> hey guys, 
i was wondering if i could have an option on how to upload files to a directory on my web page 
is that possible??

please keep it as simple as possible cause im new to the web page developing :)

lots to consider but mostly security. If this is strictly intranet then you've got nothing to worry about and there is a very simple javascript solution that will fit what you need nicely.  If you want to do this over the internet then you are going to have to take authentication into consideration, and there are lots of solutions.

In any event take a look at uploadify ([http://www.uploadify.com/]("http://www.uploadify.com/")) that will give you the basic tools you need to set it up.  I used that recently with Turbogears to make the user authentication simple. They give you a nice PHP example on how to use the script.  Good luck

---

### Post by koperry on 2009-09-02
I use filezilla to upload to both of my web servers, pretty straight forward and basic. You can find filezilla using the package manager.

---

### Post by philcamlin on 2009-09-02
> **koperry said:**
> I use filezilla to upload to both of my web servers, pretty straight forward and basic. You can find filezilla using the package manager.

thanks!!

---

### Post by gordintoronto on 2009-09-02
> **philcamlin said:**
> hey guys, 
i was wondering if i could have an option on how to upload files to a directory on my web page 
is that possible??

please keep it as simple as possible cause im new to the web page developing :)

Where is your web page?  If it is on a commercial shared hosting site such as Go Daddy, they will have a tutorial which gives you most of the information.  Sadly, there is no standard for the exact location of your files.  I've seen ftp.mysite.com and [ftp://mysite.com](ftp://mysite.com), and others.

I use gFTP.  Once you get connected to the site, you bookmark it, and you never have to type things in again.

---

