---
title: "dovecot public folder reaf only for user"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by faun77 on 2010-07-30
I have dovecot
in /etc/dovecot/dovecot-postfix.conf
and config like:
------------
umask=0007
mail_debug=yes

namespace private {
  separator=/
  location=maildir:~/Maildir
  inbox=yes
  list=yes
  subscriptions=yes
}

namespace public {
  prefix=RGW/
  separator=/
  location=maildir:/home/share_folders
  list=yes
  subscriptions=yes
  inbox=no
}

plugin {
  acl=vfile
}

mail_access_groups=userpublic
---------------------
system permision to folder
drwsrwsrwx  5 spam         userpublic 4096 2010-07-30 21:19 .SPAM

and files in this folder:
-rwxrwxrwx  1 spam          userpublic      746 2010-07-30 20:04 dovecot-acl
-rwxrwxrwx  1 spam          userpublic   756208 2010-07-30 20:25 dovecot.index
-rwxrwxrwx  1 spam          userpublic 14946304 2010-07-30 20:34 dovecot.index.cache
-rwxrwxrwx  1 spam          userpublic    13644 2010-07-30 20:34 dovecot.index.log
-rwxrwxrwx  1 spam          userpublic       13 2010-07-29 16:52 dovecot-keywords
-rwxrwxrwx  1 spam          userpublic  2150254 2010-07-30 20:34 dovecot-uidlist

and if I list mails in folder dovecot change permission to files for example:
-rw-------  1 user1        userpublic  2150254 2010-07-30 20:34 dovecot-uidlist

if user 2 list this folder take error:
permission denied

how to do this permission to default:
-rw-rw----  1 user1        userpublic  2150254 2010-07-30 20:34 dovecot-uidlist

---

### Post by marc.verwerft on 2010-07-31
> how to do this permission to default:
-rw-rw----  1 user1        userpublic  2150254 2010-07-30 20:34 dovecot-uidlist

chmod g+rwx filename ??
chmod 777 filename ??

---

### Post by faun77 on 2010-08-02
> **marc.verwerft said:**
> chmod g+rwx filename ??
chmod 777 filename ??

Yes but dovecot change this permision.
Is any methods to set dovecot.conf to set default umask 002 ?
I have umask i dovecot.conf but its not work for public folder.

---

