---
title: "Lots of &quot;Failed Delivery&quot; messages with my IMAP/SMTP since I moved overseas"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-10-18
I have a website that is hosted through [www.lunarpages.com](www.lunarpages.com) and an email address to boot.  I recently moved out of the US overseas to Iraq where I purchase Internet access from a local ISP for quite a high fee but it's all that's really available out here.  Often times when I send emails out using Evolution with the same email account I've always used, I'll get return messages in my inbox hours/days after I've sent the message, saying the message I tried to send failed.  The most recent one said:

> All messages from (ip address of my website) will be permanently deferred; Retrying will NOT succeed.

This came just from sending an email to my girlfriend.

There was a link to submit a form to Yahoo's Postmaster if I felt I have received the message in error, and I have submitted it.  But in the mean time I was wondering if this has happened to anyone unexpectedly and if so, what was done to resolve the issue.

---

### Post by dmizer on 2009-10-18
Tell us more about your website. If you can post your URL, please do (Send me a PM if you're not comfortable with posting it). Is it possible you have some unauthorized software on your site? Is your website's server on a shared IP address with another site (which may have badware)?

If everything still looks good, I would open a support ticket with [lunar pages support](http://www.lunarpages.com/support/). You'll most likely be required to send the bounce message with complete header.

---

### Post by diablo75 on 2009-10-18
I contacted Lunarpages Support, and received this response:

> The issue you are experiencing with delayed emails, is due to the way that Yahoo filters incoming emails, in an attempt to control spam.
        
        When an email comes into yahoo, they compare how many emails are coming in from the same email server. If they see a large amount of emails coming in from a single email server, they then start to "defer" emails for later delivery, expecting the emails to be resent by the sending server at a later date, hence the email you receive when sending to yahoo email addresses.
        
        This practice, while good in theory, does have a couple of flaws.
        
        While a dedicated hosting account only has a single account on it using a single mail server (with a dedicated account, the issue you are experiencing rarely occurs), a shared hosting plan shares a server with multiple other accounts.
        
        Since shared hosting accounts "share" a single mail server, you may not be the only one who is sending email to yahoo email addresses, and so the mail server may be hitting the limit that yahoo has on their system (the "defer limit" which they have not revealed) resulting in emails from the mail server being deferred for later delivery.
        
        Possible solutions :
        
        1. Fill out the form at [http://help.yahoo.com/l/us/yahoo/mail/postmaster/bulk.html](http://help.yahoo.com/l/us/yahoo/mail/postmaster/bulk.html) using your site information, and advise them in the additional information field that you are hosting on a shared server. They may then whitelist your domains, allowing your emails to go through quicker.
        
        2. Get an SPF record.
        
        With SPF, only machines authorized by you will be able to send out emails that come 'from' your domain, and as such this gives more "legitimacy" to your emails. (spammers usually don't get spf records)
        
        You can create an SPF record here: [http://spf.pobox.com/](http://spf.pobox.com/) or at [http://www.microsoft.com/mscorp/safety/content/technologies/senderid/wizard/](http://www.microsoft.com/mscorp/safety/content/technologies/senderid/wizard/)
        
        Once you have done this, reply to us here, with the created entry to add to your zone file.
        
        Be sure to include the following details as well, for security purposes, to confirm you are the account holder:
        
        1. your account user name
        2. The last 4 digits of the credit card you have on file with us, for this account.
        
        This request is for security reasons only.
        
        If you can not supply the last 4 digits of the credit card, please provide the first and last digits of the password on this account along with your full postal mailing address and telephone number

I'll be creating an SPF.

---

