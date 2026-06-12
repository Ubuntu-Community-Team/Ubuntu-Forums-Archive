---
title: "What is CA cert"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by miggys on 2012-09-17
On my campus, I connect to the wireless with PEAP with TKIP/MSCHAPv2.  I can connect to this without specifying any ca certificate but am curious if maybe I should supply one.  I don't really know what this ca certificate thing is and when I try to google it, I get very technical results that are beyond me.  Can someone try to explain what ca certificate is and why it's useful?  Also, if I decide to supply one, do I need to download a certificate from somewhere or is there already one lying around my file system somewhere?

Thanks!

---

### Post by Kirk Schnable on 2012-09-17
CA is certificate authority.  It is a third-party used to verify that an SSL certificate is genuine\valid.

My best guess is that your campus doesn't have a valid CA certificate.  It would be an added yearly expense for them to do so.  It's easier, in most cases, to just have your users ignore the invalid SSL certificate.

Just because an SSL certificate is "invalid" or not verified by a certificate authority does not mean it's insecure.  On the contrary, all your data will still be encrypted and secure.  However, the CA helps you verify that the certificate you're accepting really belongs to the party you're connecting to.  (prevents spoofing attacks, etc)

If you still have questions about this, please feel free to inquire further!

Kirk

---

### Post by hawkmage on 2012-09-17
You canthink of a Certificate Authority like a Notery Public.  Just like the Notery Public is trusted to validate that your signature is actually yours on a document a  Certificate Authoritydigitally signs an SSL certificate to verify that info in your certificate is accurate.  


As Kirk said just because the CA is not seen as valid doesn't alwayse mean that it is not correct.  Many orginizations either use self signed certificates or create their own  Certificate Authority that is not included in the standard set of CA in an OS or browser.  In your case it sounds like your school has created their own CA.

For a certificate from one of the major internet certificate authorities like VeriSign or GTE Cyber Trust that allows a company to sign their own certificates can be 10's of throusands of dollars which can be cost prohibitive.

---

### Post by Kirk Schnable on 2012-09-17
> **hawkmage said:**
> You canthink of a Certificate Authority like a Notery Public.  Just like the Notery Public is trusted to validate that your signature is actually yours on a document a  Certificate Authoritydigitally signs an SSL certificate to verify that info in your certificate is accurate. 
Great explanation.  I never thought of it as a notery public, that's a good analogy I'll have to remember for next time.


> **hawkmage said:**
> As Kirk said just because the CA is not seen as valid doesn't alwayse mean that it is not correct.  Many orginizations either use self signed certificates or create their own  Certificate Authority that is not included in the standard set of CA in an OS or browser.  In your case it sounds like your school has created their own CA.
Not necessarily.  My work has a similar PEAP MSCHAPv2 WiFi setup on our Cisco controller.  Ubuntu does ask if I want to install a CA certificate, and we do not have one set up.  I think it's a standard question when configuring that type of connection authentication.

Nevertheless, I wouldn't be concerned about it, miggys.

Kirk

---

### Post by jrog on 2012-09-17
> **miggys said:**
> Also, if I decide to supply one, do I need to download a certificate from somewhere or is there already one lying around my file system somewhere?
I don't think I saw anyone answer this part of your question (sorry if I missed it). For Ubuntu, many of the common certificates are available in the ca-certificates package, available on the Ubuntu repos. If they are installed on your system, they are available under /etc/ssl/certs.

---

### Post by miggys on 2012-09-19
Thanks everybody.  So this certificate validates that the network I am connecting to is the one I want rather than some other network that has the same SSID?  The validation is either self-signed (equivalent to them promising me they are for real) or it is verified by a some trusted third party (at an expense to the network owners)?

So I guess my follow up questions may be more technical...does my computer download the network's certificate and check it against some database?  If so, what prevents a mal-network from downloading that certificate and using it for their fake network? 

I have no reason to believe that I am being fooled, I am just curious at this point.  Thanks!

---

### Post by Kirk Schnable on 2012-09-20
Well, SSL is SSL, so here's a great little video explaining how it works for websites:
[http://www.commoncraft.com/video/secure-websites](http://www.commoncraft.com/video/secure-websites)

The short answer, is your computer has a list of trusted certificate authorities. If the connection has no CA certificate or the CA isn't a known trusted CA, your SSL will show as invalid.  This is also true for websites.

Kirk

---

