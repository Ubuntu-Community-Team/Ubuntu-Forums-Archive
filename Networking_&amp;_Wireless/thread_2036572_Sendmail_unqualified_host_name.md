---
title: "Sendmail unqualified host name"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by JimLS on 2012-08-02
I am installing sendmail and got an unqualified host name message.  I did some checking and found it has to do with my /etc/hosts file.  I looked at the file and was surprised to see TWO lines with ip addresses - expected only one...
 
/etc/hosts
-----------
127.0.0.1 localhost.localdomain
127.0.1.1 Netvista
 
Should I have both lines?  What is the recommended solution?  I don't think I care what the host name actually is...

---

### Post by TheFu on 2012-08-02
Both those lines are fine, but you probably need to add the FQDN to it for your static IP.
Something like netvista.{domain}.{TLD}.  Email on the internet needs to come from a known domain.  If you don't have a domain (did you pay someone like GoDaddy?), then you probably want to use the domain from your ISP.

Are you really using sendmail?  That is an expert-level tool. I've been running mail servers since around 1995 and only used sendmail once in all this time for an extremely complex requirement.

Postfix is an easier to use and more secure tool. It is 100% API compatible with sendmail. Other system tools trying to email stuff don't know the difference.

Sending email on the internet has become more of a challenge the last 10 yrs. Most email servers will block email from hosts that aren't registered as email servers at the DNS level through an MX record.  Most residential ISPs block outbound and inbound SMTP traffic to hold down the amount of internet spam caused by their uninformed clients. They require an SMTP-gateway be used to send email.

Postfix is easy to setup as a leaf node that will always forward all outbound email through an ISP's email gateways.  During installation, you'll be asked the main questions.  [http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html) should explain. It will ask which domain your server is part of and you'll not see that *unqualified host name* message anymore.

Getting inbound email from external email servers is usually best through IMAP, POP or by running an IMAP server on your Linux machine and using **fetchmail  **to pull email into your machine a 6-24 times daily from those external accounts.  If you do this, you become responsible to backup the email, but you also gain tremendous flexibility. There's no need to store email inside an specific client program again when you run your own IMAP server and searches are FAST from any platform.

Sorry if I rambled. I love email and email systems.

---

### Post by JimLS on 2012-08-02
Thanks for the reply.  I could use postfix - Not stuck on sendmail.  I have found some information on setting up both for sbcglobal/att but hard to tell if these are completly up to date.  Very inexperienced so didn't understand much of what you said.
 
This isn't really a server.  Just a PC on a home network with some programs that need to send and get email and relay it through a local program like postfix, and possibly through stunnel for smtps (have read that sendmail and postfix don't support smtps but that may be old info).  Some of the programs can directly interact with pop3 and smtp servers but don't have all the options needed for the increased complexity you mentioned being put in place in the last 10 years.
 
my email would be something like:  [EMAIL="someone@sbcglobal.net"]someone@sbcglobal.net[/EMAIL]
 
I don't have a static ip.  I don't have a domain name of my own.  Just a residential DSL line with dynamic ip.
 
The "Netvista" name is just something I entered when installing ubuntu for a machine name.  It isn't tied to anything - just something to make it easy for me to know what box it is.
 
I am lost on FQDN, TLD, etc....

---

### Post by TheFu on 2012-08-02
[http://www.easy-ubuntu-linux.com/email-configure-1.html](http://www.easy-ubuntu-linux.com/email-configure-1.html) looks like an easy to follow tutor that might be just what you are seeking.

Or I can continue with ....  your "server" needs a static IP - at least on your internal LAN, but not necessarily a public static IP. Without a static IP on your LAN, how will other devices like PCs, wifi smartphones and tablets find your internal email server?

Email from an end-user perspective email is 2 different things - they are very different.
1) sending email.
2) receiving email.

**Sending Email**
To send email you have 2 choices on Linux.  Setup every client application to talk directly with your ISP's email servers or setup an **MTA** - that is what sendmail, qmail, exim, and postfix are call - MTAs - to handle all output email sending.  It is much easier to setup postfix as the MTA.  Outbound MTA will be setup using 1 account to send all emails through SBC's email gateways.  Port 25 is used for SMTP.  I'm pretty certain all of the current MTAs support SMTPS, so you don't need a tunnel, however, SMTPS is controlled by the MTAs involved.  They negotiate the connection and if one doesn't support it, then you get plain SMTP, not the encrypted version.  You can force SMTPS from your server, but the SBC gateway can refuse that and when they forward the messages to the final email destination, they may not use SMTPS at all.

**Receiving Email**
With a residential internet connection, you can't easily use an MTA to receive email. It can be done, but you'll need an outside provider who receives your email and forwards it to you on a non-standard port.  DynDNS will do this for you for $50/yr ... receive only. Sending is different.

Ok, back to receiving email.  SMTP has nothing to do with reading email in a client. For that, you probably use either POP3 or IMAP clients.  Again, there are many different ways to configure this ... per client settings directly to the ISP servers or you could setup an IMAP server on your Linux machine and periodically pull all email to your box using an automatic tool like **fetchmail.**  Fetchmail rocks.

All the stuff about MX records do not apply to you at this point. Also you don't need a domain.  Generally people trying to run sendmail want a full email server on the internet. You'll need a few months to get their if that is your desire. The learning curve is pretty steep for someone completely new to Linux.  Email is one of the hardest parts of the internet to do securely and without too much spam.  

I'm a bit fan of IMAP and IMAPS over POP3.  I like to leave all my mail on a central server connect from any client and read it, search it, have attachments available to me from anywhere in the world and I love that my single server can merge email accounts from many other addresses using fetchmail.  Reading email on my server from gmail or yahoo or my ISP is great, but I know that I can't send email outbound except from my ISP by default.  It is possible to have postfix recognize the "from" address and use the correct email service directly, provided the ISP doesn't block the ports being used.

[http://answers.yahoo.com/question/index?qid=1006050811067](http://answers.yahoo.com/question/index?qid=1006050811067) seems to have what look like reasonable answers for the server settings.  SMTP and POP3.

If you see a reference that you don't understand, try to google it. Linux is a team sport, but YOU need to do your homework too.
* [https://en.wikipedia.org/wiki/FQDN](https://en.wikipedia.org/wiki/FQDN)
* [https://en.wikipedia.org/wiki/TLD](https://en.wikipedia.org/wiki/TLD)

Machine names on the internet are arbitrarily named.  Netvista is just as good as "www" or "ftp" ... actually most [www.domain.com]("http://www.domain.com") machines actually aren't named "www", but that is an alias for the real name.  A web server can run on any computer, it is just often called www, but that name isn't even a standard.  Public SMTP servers can be named anything too, except they need to have DNS records and MX DNS records and a domainname.

So, your homework now is to 
* **apt-get purge sendmail**
* apt-get install postfix fetchmail ; set it up as a satellite system and enter all your data for sbcglobal.net
* apt-get install {some imap server}  ; courier-imap or uw-imapd
* Setup an email client to use your SMTP/MTA and IMAP servers, not the public ones.
* Setup **fetchmail**  to poll your external ISP, gmail, and other email accounts every 10 to 60 minutes automatically

Simple?

---

### Post by SeijiSensei on 2012-08-02
> **JimLS said:**
> I am installing sendmail and got an unqualified host name message.  I did some checking and found it has to do with my /etc/hosts file.  I looked at the file and was surprised to see TWO lines with ip addresses - expected only one...
 
/etc/hosts
-----------
127.0.0.1 localhost.localdomain
127.0.1.1 Netvista
 
Should I have both lines?  What is the recommended solution?  I don't think I care what the host name actually is...

First, there's absolutely nothing wrong with using sendmail.  I've used it for fifteen years or so and continue to do so today.

Now as for the error, could you post the actual error as it appears in /var/log/mail.log?

Have you told sendmail the name of your computer?  If it only has one name, and will only be accepting mail addressed to user@hostname, then you can put it in the line that begins with Cw in sendmail.cf.  If that file has an entry for the Fw macro that points to a file of local host names, put the name in that file instead.  On my CentOS servers, that file is called /etc/mail/local-host-names.  The name on your computer will be associated with the Fw entry in sendmail.cf like this:

```
Fw/etc/mail/local-host-names
```

Mail sent to any of the names in that list will be delivered locally.  All other messages will be sent to the servers for the target domains referenced in their DNS MC records.

You will still need to deal with fully-qualified names unless you're intending simply to send mail among accounts on your server.  If you send mail outside your network, you'll need to be using a real domain.

---

### Post by JimLS on 2012-08-03
I got postfix installed and went through the setup.  But I am getting several errors.  One is:
CLIENT wrappermode (port smtps/465) is unimplemented

My version of postfix is 2.8.5 (the packaged version for Ubuntu 11.10).
The solution I found for this used stunnel but I thought that wasn't needed...

The log also shows:  from=<jim@sbcglobal.net>
jim is the login on the local machine but not the name of the account on sbcglobal.net
The substitution in /etc/postfix/generic doesn't seem to be happening.  I did it as shown about halfway down the page here:
[http://fonality.com/trixbox/wiki/howto-voicemail-email-postfix-and-sbc-att-your-isp](http://fonality.com/trixbox/wiki/howto-voicemail-email-postfix-and-sbc-att-your-isp)

I have done a bunch of searching but haven't found much that helps...

---

### Post by JimLS on 2012-08-05
Athough postfix seems to have at least some of the options needed for att/sbc/yahoo smtp on port 465 apparently it isn't possible to do it directly.  The postfix site shows using stunnel which is what I plan to do:

[http://www.postfix.org/TLS_README.html#client_smtps](http://www.postfix.org/TLS_README.html#client_smtps)

Since this has gotten far from the original issue I have started a new topic on postfix configuration:

[http://ubuntuforums.org/showthread.php?t=2037477](http://ubuntuforums.org/showthread.php?t=2037477)

---

