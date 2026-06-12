---
title: "Securing Servers with SSL"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2013-06-16
What exactly does one need to do to properly secure a server with SSL?

Say I just installed a linux distribution on a machine that is meant to act as a simple, home router, and it has an https web interface that I will be logging into from the internet.

Does leaving the default pregenerated ssl certificate that it came with pose a security threat, because everyone else that downloads the same distribution has the private key?
What are the disadvantages of having a self-signed certificate? Is it significantly less secure than having it signed by a CA? I don't really have thousands of users using my servers so I don't care that I need to confirm with firefox on clients that I want to proceed, as long as it still guarantees that no one can listen in on the communication.

I basically just followed the instructions found here:
[http://www.akadia.com/services/ssh_test_certificate.html]("http://www.akadia.com/services/ssh_test_certificate.html")
for generating a self-signed certificate. Is there anything else I must do to ensure no one can intercept the communication and decode it?

---

### Post by linuxtechguy on 2013-06-17
> **terminator14 said:**
> 

Does leaving the default pregenerated ssl certificate that it came with pose a security threat, because everyone else that downloads the same distribution has the private key?


ahahah no they dont

> 
[COLOR=#000000]What are the disadvantages of having a self-signed certificate? Is it significantly less secure than having it signed by a CA?


There are none except of a warning before you connect. NO it is not less secure not having a purchased ssl certificate.[/COLOR]

---

### Post by terminator14 on 2013-06-17
> **linuxtechguy said:**
> ahahah no they dont

Are you sure. Because, for example when you download NoMachine from their website, it specifically says:

> The NoMachine Web tools can be run by pointing your browser at the following URL: [https://serverHost:4080](https://serverHost:4080) where serverHost is either the IP or hostname of the machine where you have installed the NoMachine or NoMachine Virtual Desktop package. Please note that the installation comes with a self-signed SSL certificate intended to be a sample. **This doesn't grant a secure connection. In order to secure your web application, please replace the SSL Certificate File, namely /usr/NX/etc/httpd.crt and the SSL Certificate Key File /usr/NX/etc/httpd.key with your own.**

Which seems to imply that all web servers with HTTPS need to have their default SSL certificates replaced in order to be secure.

> **linuxtechguy said:**
> There are none except of a warning before you connect. NO it is not less secure not having a purchased ssl certificate.

Cool - I was hoping that was the case.

---

### Post by terminator14 on 2013-06-17
Anyone know? With SSL being so widespread, I would think that tons of people would know how to use it.

---

### Post by Cheesemill on 2013-06-18
Continuing to use the default self-signed SSL certificate opens the possibility of a man-in-the-middle attack.

Because the servers certificate is public knowledge it is possible for an attacker to intercept communications and pretend to be the server you think you are connected to. All traffic is still encrypted but there is no way of knowing if the server you are connected to is the one you think it is.

[http://en.wikipedia.org/wiki/Man-in-the-middle_attack](http://en.wikipedia.org/wiki/Man-in-the-middle_attack)

---

### Post by terminator14 on 2013-06-18
> **Cheesemill said:**
> Continuing to use the default self-signed SSL certificate opens the possibility of a man-in-the-middle attack.

Because the servers certificate is public knowledge it is possible for an attacker to intercept communications and pretend to be the server you think you are connected to. All traffic is still encrypted but there is no way of knowing if the server you are connected to is the one you think it is.

[http://en.wikipedia.org/wiki/Man-in-the-middle_attack](http://en.wikipedia.org/wiki/Man-in-the-middle_attack)

Thanks. I was actually aware of man in the middle attacks, but could not understand how one might be possible in this situation until I read this: [http://www.clintharris.net/2009/self-signed-certificates/]("http://www.clintharris.net/2009/self-signed-certificates/"). SSL was always a mystery to me until I read that article, which explains in very simple terms how SSL works, and how to create self-signed certificates. I recommend that anyone who is wondering the same thing as I was in my original post reads the wiki on man in the middle attacks, and this article. Here's a short version of what I found out though:

Like cheesemill said, default certificates of any web server are susceptible to man-in-the-middle attacks, and must be changed if you plan to connect over any unsecure network (eg. over the internet).
If this is the case for you, generating your own, self-signed certificate is not enough. If you simply connect to your https web server over the internet, ignore the browser warning, and proceed, you are basically assuming that no one has intercepted that message and changed the public key in the certificate for their own public key (which is something that certificate authorities guarantee). If you want true security, you would need to transfer the self-signed certificate to your clients in a secure way (eg. by using a public, SSL-secured website like dropbox or google drive, or an already secure SSH connection, since the initial SSH connections also suffer from this vulnerability).

---

