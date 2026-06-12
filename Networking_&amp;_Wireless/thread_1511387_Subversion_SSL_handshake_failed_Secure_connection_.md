---
title: "Subversion: SSL handshake failed: Secure connection truncated"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by rybu on 2010-06-16
Hi all, 

I'm having a problem with Subversion.  When I try an "svn up" it gives me this error message:

 SSL handshake failed: Secure connection truncated

I'm running Ubuntu 10/4 but I also had this problem with 9/10.  Does anyone know what this error message means?   It appears to be an SSL problem but it's not clear to me what exactly the problem is.  

I do not have this problem with svn on my other office computer, nor my home computer.

FYI, I'm running subversion on the Regina project.  The full error message is this:

```
svn up
svn: OPTIONS of 'https://regina.svn.sourceforge.net/svnroot/regina/branches/4-manifolds': SSL handshake failed: Secure connection truncated (https://regina.svn.sourceforge.net)

```

Although I don't think there's anything specific to Regina about this svn problem, as I mentioned, I can "svn up" from home, or from my other office computer.

---

### Post by rybu on 2010-06-17
Is there a more appropriate forum for this question?

thanks

---

### Post by toby.batch on 2010-06-23
+1

I have the same problem following and upgrade from 8.04 lts to 10.04 lts

---

### Post by rybu on 2010-06-24
Interesting.  It appears to be an intermittent problem.  I'm still not sure what the source of the problem is.  Does anyone know how to get additional information on what might or might not be going on?

Last week the SSL problem went away (for no reason I can discern).  I had not updated any software.  Nothing had changed as far as I can tell.  

My svn connections to the same Regina project work fine from home, and from my other office computer.  It just doesn't work consistently from my "main" office computer.  svn isn't working today on my main office computer. It worked fine sometime last week, but it also wasn't working earlier last week. 

I'm not sure how to determine what the bug is.

---

### Post by rybu on 2010-08-03
It no longer seems intermittent.  I haven't been able to do a successful svn up in over a month.

---

### Post by StrikerNL on 2010-11-26
Same exact problem here after updating from 8.10 to 10.04. Will post answer here if I find it.

---

### Post by StrikerNL on 2010-11-26
> **StrikerNL said:**
> Same exact problem here after updating from 8.10 to 10.04. Will post answer here if I find it.

Well that was fairly easy. Turns out I had to change any **custom** (I think the defaults are fine) VirtualHost entries in /etc/apache2/sites-available/default from <VirtualHost *> to <VirtualHost *:80> (if you have them in any other config files, you'll probably have to do it there too). Otherwise apache just sends plain unencrypted data over the 443 port. I guess that changed in apache somewhere down the line between 8.10 and 10.04.

Hope this helps someone.

P.S. I didn't come up with this myself, this answered it for me: [http://stackoverflow.com/questions/119336/ssl-error-rx-record-too-long-and-apache-ssl/887350#887350](http://stackoverflow.com/questions/119336/ssl-error-rx-record-too-long-and-apache-ssl/887350#887350))

---

### Post by rybu on 2010-11-26
Hi there, 

The problem seems to have dissappeared over one of the last system updates.  So I'm unable to recreate the problem now.  But thanks for pointing out what it very likely. 

I just noticed this, so it must have been a very recent system update.

---

### Post by tekrei on 2010-12-06
Hello,

I am having this problem when using Subversion (tried with Eclipse, rapidsvn and command line tool): "SSL handshake failed: Secure connection truncated"

I don't have apache, and server I'm trying to connect is not under my administration. Is there anybody who knows how to solve this problem? Do I need to update or upgrade my SSL or Subversion or anything else?

Regards.

System information:
- Ubuntu 10.10
- Subversion 1.6.12

---

### Post by quicknisip on 2011-08-23
I got the "SSL handshake failed" issue on Ubuntu 10.04. I resolved by renaming both ~/.ssh and ~/.subversion (don't know which one fixed the problem because I renamed both on the same time).
Then at the next connection I was asked again to accept the server certificate.

---

### Post by macronom on 2012-10-04
Renaming/deleting ~/.subversion worked for me.

---

