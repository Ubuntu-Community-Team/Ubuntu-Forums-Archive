---
title: "Help! Postfix+DSPAM Mail Loops"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by Soda Ant on 2009-04-17
I have Postfix set up to deliver email to virtual users (without accounts on the system), and this works fine.

I'm trying to add DSPAM to filter spam, but run into problems with mail loops when trying to get it to work.

I have DSPAM configured as a transport in Postfix with the following line in master.cf:

dspam unix - n n - 10 pipe
flags=Ru user=dspam argv=/usr/bin/dspam --deliver=innocent,spam --user $user -i -f $sender -- recipient

and the following in main.cf:

virtual_transport = dspam
dspam_destination_recipient_limit = 1

smtpd_client_restrictions =
permit_mynetworks,
check_client_access pcre:/etc/postfix/dspam_filter_access

In dspam.conf I have:

TrustedDeliveryAgent "/usr/sbin/sendmail"

When an email arrives, Postfix passes it off to dspam for filtering, and dspam passes it back to Postfix for final delivery. Instead of putting the mail in the virtual user's mailbox, it immediately passes it back to dspam. Eventually it detects this as a mail loop and gives up.

How do I get Postfix to recognize that the message as already been through dspam once already and deliver it to the user's mailbox rather than giving it back to dspam?

It seems I'm almost there with this configuration, but am missing a crucial step that prevents the loop...

---

### Post by jwiggs on 2010-05-08
I'm having the exact same problem.  I've followed the documentation at [https://help.ubuntu.com/community/Postfix/Dspam](https://help.ubuntu.com/community/Postfix/Dspam) absolutely to the letter, and I get a loop as well.  Running lucid lynx with all updates as of May 5th, 2010.

---

