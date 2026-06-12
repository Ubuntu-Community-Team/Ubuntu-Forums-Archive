---
title: "Help with Evolution and Exchange Server 2007"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by tshanno on 2009-07-05
Hi,

I have an account on a hosted Exchange 2007 server.  The company's name is 4smartphone.net.  I've been having a pretty difficult time getting hooked up to Evolution (2.26.1)

I'm using the MAPI plugin installed via the evolution-mapi package.  There are no instructions for hooking things up on the company's website (of course) but there are instructions for the Mac:

How to connect Microsoft Entourage 2004 SP2 to the Exchange Server

   1. Start Microsoft Entourage. Choose Tools > Accounts from the menu on the top.
   2. Switch to the Exchange tab and click New.
   3. Click Create account manually button at the bottom of the dialog.
   4. At the Account Settings tab please fill in the following information:
          * Account name: 4SmartPhone Exchange
          * Name: Type your mailbox Display Name
          * Email address: Type your email address
          * Account ID: Type your mailbox username
          * . You can find this by navigating to “MS Exchange Server > Mailboxes”, clicking the required mailbox, and then the Advanced tab. Domain: EXCH016
          * Password: Type your mailbox password
          * Exchange server: owa016.msoutlookonline.net/exchange/Type your email address

            Also please make sure to check This DAV service requires a secure connection (SSL)
   5. At the Advanced tab please fill in the following information:
          * Public folders server: owa016.msoutlookonline.net/public
          * LDAP server: ldap16.msoutlookonline.net
          * Search base: OU=tshannon,OU=Hosting,DC=exch016,DC=msoutlookonline,DC=net

            Also please make sure to check This DAV service requires a secure connection (SSL) 

Based upon these instructions, I did the following with Evolution:

Server Type:  Exchange MAPI

Server:  owa016.msoutlookonline.net/exchange/myemail@domain.edu
Username: tshannon_tshannon
Domain: EXCH016

I put in my password when prompted.

I get the following error:

Authenication Failed:
MapiLogonProvider:MAPI_E_LOGON_FAILED

Do any of these settings look unusual?  Is there some common mistake I may be making?  Any help would be appreciated.

Thanks,
Tom S.

---

