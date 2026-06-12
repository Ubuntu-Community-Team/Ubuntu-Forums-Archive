---
title: "Jitsi not finding trusted certificate"
date: 2013-03-11
forum: Multimedia Software
---

### Post by Lars Noodén on 2013-03-11
I'm getting the following error on Jitsi on Ubuntu[1], but not Jitsi on OS X:

	Jitsi can't verify the identity of the server when 
	connecting to [sip2sip.info].  The certificate is not 
	trusted, which means that the server's identity cannot 
	be automatically verified.  Do you want to continue 
	connecting? For more information, click "Show 
	Certificate".

What's the right way to eliminate the problem?  

[1]	$ apt-cache policy jitsi
	jitsi:
	  Installed: 2.0.4506.10553-1
	  Candidate: 2.0.4506.10553-1


Edit: I just tried the nightly build of Jitsi and get the same error.  I have also tried removing the .jitsi directory to see if it was a configuration issue, that had no effect either.

---

### Post by Lars Noodén on 2013-03-12
I've tried Jitsi again on three different Linux machines, with two different architectures and two different networks.  All combinations bring up the certificate error.

---

