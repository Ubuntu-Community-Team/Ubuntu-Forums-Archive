---
title: "fetchmail, behaviour in response to SMTP 552 error code"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by 5tj on 2012-10-31
Small mail server (~40 users) retrieves email from internet service provider using fetchmail.

fetchmail configuration file looks like this

poll pop.isp.example port 995 with proto pop3
  user "user1@company.example" there with password "secret" is "user1@company.example" here
  options fetchall ssl forcecr pass8bits norewrite;

and so on for all users.
fetchmail is called every few minutes like this

fetchmail --smtphost 127.0.0.1/25  --fetchmailrc /path/to/config

Mailserver on localhost is postfix, it is configured to accept these email addresses and deliver to local users.

Message size limit is set to 50 MB. 

After running for a year without problems, one user received an email larger than the postfix message size limit in the Mailbox at the ISP.

fetchmail fetched the message via pop3 and delivered via smtp. Postfix complained about the message size (code 552) to fetchmail. Fetchmail logged the 552 code, sent a delivery failure notification to the sender, and did NOT delete the large message from the inbox at the ISP.

The events from last paragraph repeated every few minutes until the sender complained about getting hundreds of delivery failure notifications.

My question is, why did fetchmail not delete the large message from the inbox at the ISP? I generally appreciate that fetchmail makes sure that emails are correctly delivered before deleting them from the source, but in this case, as stated in the fetchmail man page, fetchmail should have deleted the message from the ISP inbox. The fetchmail man page states:

SMTP/ESMTP ERROR HANDLING

[...]

       552 (message exceeds fixed maximum message size)
            Delete the message from the server.  Send bounce-mail to the orig&#8208;
            inator.


The "delete" part did not happen. fetchmail output:

2 message for [EMAIL="user22@company.exampl"]user22@company.exampl[/EMAIL]e at pop.isp.example (gazillion octets).
fetchmail: SMTP error: 552 5.4.3 Message size exceeds fixed limit
fetchmail: mail from MAILER-DAEMON@internal-hostname bounced to [EMAIL="sender@large-message.exampl"]sender@large-message.exampl[/EMAIL]e
reading message [email]user22@company.example@pop.isp.exampl[/email]e: 1 of 2 (gazillion octets) not flushed
reading message [email]user22@company.example@pop.isp.exampl[/email]e: 2 of 2 (61968 octets) flushed

(where gazillion was ~100MB)

---

### Post by 5tj on 2012-12-07
This is at least unclear documentation, if not a documentation bug.

Solution is to also specify a --nosoftbounce command line parameter to fetchmail.

---

### Post by zauny on 2012-12-28
how to have postfix send email larger than 50mb

I need some guidance. My one of Execs wants to send and 
receive emails with attachment of 100MB at least. I have 
gotten Postfix to send and receive emails with attachment 
of 50MB, however whenever I change message_size_limit to a 
size larger than 50MB Postfix stop processing emails (the 
emails stay in the queue then get rejected after awhile).   
  Any assistance will be greatly appreciated…

---

### Post by NigO on 2013-02-20
> **5tj said:**
> 
Mailserver on localhost is postfix, it is configured to accept these email addresses and deliver to local users.

Message size limit is set to 50 MB. 

After running for a year without problems, one user received an email larger than the postfix message size limit in the Mailbox at the ISP.

fetchmail fetched the message via pop3 and delivered via smtp. Postfix complained about the message size (code 552) to fetchmail. Fetchmail logged the 552 code, sent a delivery failure notification to the sender, and did NOT delete the large message from the inbox at the ISP.

The events from last paragraph repeated every few minutes until the sender complained about getting hundreds of delivery failure notifications.

My question is, why did fetchmail not delete the large message from the inbox at the ISP? I generally appreciate that fetchmail makes sure that emails are correctly delivered before deleting them from the source, but in this case, as stated in the fetchmail man page, fetchmail should have deleted the message from the ISP inbox. The fetchmail man page states:


I've just come across the same problem.  In my case, on a bandwidth-capped supply, fetchmail was repeatedly downloading and then failing to deliver a 10MB message, ramping up bandwidth pretty fast!

My solution was to set a limit in the fetchmailrc which was lower than my postfix limit - e.g. 
```
limit 100000000  # 100MB per message
```
in the fetchmailrc and
```
postconf -e "message_size_limit = 101000000"
```
to set a 101MB limit for the local SMTP delivery using postfix.

Hope that helps someone else

---

