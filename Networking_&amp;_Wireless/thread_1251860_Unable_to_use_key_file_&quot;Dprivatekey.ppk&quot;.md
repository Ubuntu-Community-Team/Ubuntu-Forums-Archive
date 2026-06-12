---
title: "Unable to use key file &quot;D:\privatekey.ppk&quot; (OpenSSH SSH-2 private key)"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by .09. on 2009-08-28
Hi!

I have set up an ssh server on my home machine running Ubuntu and I want to connect to it from work with Putty useing public/private key authentication. I generated the key pair with PuttyGen, copied the public key to authorized_keys file but when I try to connect I get this message: Unable to use key file "D:\privatekey.ppk" (OpenSSH SSH-2 private key). What am I doing wrong?

---

### Post by dk06 on 2009-08-28
> **.09. said:**
> Hi!

I have set up an ssh server on my home machine running Ubuntu and I want to connect to it from work with Putty useing public/private key authentication. I generated the key pair with PuttyGen, copied the public key to authorized_keys file but when I try to connect I get this message: Unable to use key file "D:\privatekey.ppk" (OpenSSH SSH-2 private key). What am I doing wrong?


[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)
[http://sial.org/howto/openssh/publickey-auth/problems/](http://sial.org/howto/openssh/publickey-auth/problems/)


[http://the.earth.li/~sgtatham/putty/0.55/htmldoc/Chapter10.html](http://the.earth.li/~sgtatham/putty/0.55/htmldoc/Chapter10.html)
> 
**10.8 &#8216;Unable to use this private key file&#8217;, &#8216;Couldn't load private key&#8217;, &#8216;Key is of wrong type&#8217;**

  Various forms of this error are printed in the PuTTY window, or written to the PuTTY Event Log (see [section 3.1.3.1]("http://the.earth.li/%7Esgtatham/putty/0.55/htmldoc/Chapter3.html#S3.1.3.1")) when trying public-key authentication, or given by Pageant when trying to load a private key. 
  If you see one of these messages, it often indicates that you've tried to load a key of an inappropriate type into PuTTY, Plink, PSCP, PSFTP, or Pageant. 
 You may have specified a key that's inappropriate for the connection you're making. The SSH-1 and SSH-2 protocols require different private key formats, and a SSH-1 key can't be used for a SSH-2 connection (or vice versa). 
  Alternatively, you may have tried to load an SSH-2 key in a &#8216;foreign&#8217; format (OpenSSH or ssh.com) directly into one of the PuTTY tools, in which case you need to import it into PuTTY's native format (*.PPK) using PuTTYgen - see [section 8.2.12]("http://the.earth.li/%7Esgtatham/putty/0.55/htmldoc/Chapter8.html#S8.2.12").

---

