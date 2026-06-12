---
title: "can not successfully respond to certain e-mails"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2012-04-10
Why is it that when attempting to reply to certain e-mails (not all) which I receive, I get the following - is this a problem with Ubuntu or Evolution or is there something else afoot here - My Internet service provider (Verizon) is too dumb to help me with this problem ???

Thanks.

This report relates to a message you sent with the following header fields:

  Message-id: <1334077393.1380.3.camel@XXX-natty-1.myhome.westell.com>
  Date: Tue, 10 Apr 2012 13:03:13 -0400
  From: "XXXXXXXXXXX" <XXXXXXXXXXX@verizon.net>
  To: Me <gunbleur@embarqmail.com>
  Subject: Re: Blue Ridge Bluing Website: Contact Form

Your message cannot be delivered to the following recipients:

  Recipient address: [email]gunbleur@embarqmail.com[/email]
  Reason: Remote SMTP server has rejected address
  Diagnostic code: smtp;550 5.1.1 [R2] Recipient [email]gunbleur@embarqmail.com[/email] does not exist here.
  Remote system: dns;smtp.embarq.synacor.com (TCP|206.46.173.21|21052|208.47.184.2|25) (smtp.embarq.synacor.com ESMTP ecelerity 2.2.3.47 r[39797/39798] Tue, 10 Apr 2012 13:03:28 -0400)

---

### Post by SeijiSensei on 2012-04-10
> Diagnostic code: smtp;550 5.1.1 [R2] Recipient [email]gunbleur@embarqmail.com[/email] does not exist here.
Remote system: dns;smtp.embarq.synacor.com 

The server handling mail for embarqmail.com doesn't recognized gunbleur as a valid user.  I checked the MX record for embarqmail.com, and that is the right server.

I then made a connection directly to the server's port 25 and simulated an SMTP transaction attempting to send mail to [email]gunbleur@embarqmail.com[/email].  I get the same "does not exist here" error.

I see that the subject line refers to a contact form.  Maybe it's configured only as an outbound address and doesn't accept replies.

---

### Post by wpshooter on 2012-04-10
> **SeijiSensei said:**
> The server handling mail for embarqmail.com doesn't recognized gunbleur as a valid user.  I checked the MX record for embarqmail.com, and that is the right server.

I then made a connection directly to the server's port 25 and simulated an SMTP transaction attempting to send mail to [email]gunbleur@embarqmail.com[/email].  I get the same "does not exist here" error.

I see that the subject line refers to a contact form.  Maybe it's configured only as an outbound address and doesn't accept replies.

It is from a "contact form" type of communications setup on his website.  I can SEND him e-mails from that "form" and his response comes back to me in my Evolution client.  BUT I can not successfully make a reply to his response which was delivered to my Evolution program.  

Is it possible for his e-mail account be setup to receive ONLY from that form which is on his website and not from any other means ?  If so, that does not seem like a very good idea to me !!!

Thanks.

---

### Post by SeijiSensei on 2012-04-11
Sure.  The form might even be sending to an entirely different address.

---

