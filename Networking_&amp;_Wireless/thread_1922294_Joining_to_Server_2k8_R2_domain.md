---
title: "Joining to Server 2k8 R2 domain"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by myth1914 on 2012-02-08
I can't figure out if this is an issue with Linux or the lovely implementation of kerberos on MS...


After MANY MANY searches, I have been unable to find a solution to this issue.  Here's the setup:


 Windows Server 2008 R2
 Linux Samba client version 3.2.4-0.22
 

When attempting to join AD, originally I was getting 'KDC - No support for encryption type'  I then added:
 [COLOR=#ff0000]default_tkt_enctypes = rc4-hmac des-cbc-md5[/COLOR]
 [COLOR=#ff0000][/COLOR] [COLOR=#FF0000]default_tgs_enctypes = rc4-hmac des-cbc-md5[/COLOR]
[COLOR=#FF0000][/COLOR]
to my krb5.conf  This was after the suggestions of using DES for the  domain admin user.  In this case, DES was turned off and that issue was  resolved.  



From there, I can run kinit [email]user@DOMAIN.COM[/email] and pull a ticket  noted by klist.  kdestroy  removes the ticket.  When I attempt to join in my lab, all is well.  



In  the field however, I am now getting: "kinit client credentials have  been revoked"  After setting the DNS to the DC and syncing the time with  the DC, I have attempted the  following:
 1. Reset the domain admin account password - No change
 2. Delete the computer account - The computer account is created when  attempting to join; however, the same error is thrown with the box not  being joined.
 3. Delete the computer account and manually create it - No change
 4. Add computer account to domain admin group - no change


 I'm sure i'm forgetting some things as I've been working on this off  and on for weeks.  I should note:  I am NOT getting "client credentials  have been revoked while getting initial credentials"  I am getting  "kerberos_kinit_password [email]COMPUTER@DOMAIN.COM[/email]  failed: Clients credentials have been revoked"
 This machine was previously joined to the domain.  In my lab  environment, this is fully functional and works with the same PC.  I'm  hoping someone has some experience with this issue or some direction.

---

