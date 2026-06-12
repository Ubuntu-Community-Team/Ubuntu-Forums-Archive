---
title: "Configuring gmail imap folders/labels in mutt"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2009-06-25
I set up mutt, and it downloads and sends my mail just fine, but I can't access my drafts, trash, sent folder, etc using the keyboard shortcuts. I get errors like "[Gmail]/Drafts is not a mailbox." This is the contents of my ~/.muttrc file; can anyone tell me what I'm doing wrong? Thanks in advance!

```

set from = "pythonscript@gmail.com"
set realname = "pythonscript"

set imap_user = "pythonscript@gmail.com"
set imap_pass = "*my_password*"

set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed = "+[Gmail]/Drafts"
set trash = "imaps://imap.gmail.com/[Gmail]/Trash"

set header_cache =~/.mutt/cache/headers
set message_cachedir =~/.mutt/cache/bodies
set certificate_file =~/.mutt/certificates

set smtp_url = "smtp://pythonscript@smtp.gmail.com:587/"
set smtp_pass = "*my_password*"

bind editor <space> noop
macro index gi "<change-folder> =INBOX<enter>" "Go to inbox"
macro index ga "<change-folder> =[Gmail]/All Mail<enter>" "Go to all mail"
macro index gs "<change-folder> =[Gmail]/Sent Mail<enter>" "Go to Sent Mail"
macro index gd "<change-folder> =[Gmail]/Drafts<enter>" "Go to drafts"

set move = no  #Stop asking to "move read messages to mbox"!
set imap_keepalive = 900
```

---

### Post by AlexTheMad on 2009-06-26
Coincidentally, I configuring mutt atm and having sort of the same problem.

Trash/drafts works for me with
macro index gs "<change-folder> =[Gmail]/Trash<enter>" "Go to trash"

what doesn't work however is All Mail, and I'm guessing this is because of the space in the name. Does anyone know how to work around that?

---

### Post by pythonscript on 2009-06-26
Could you post your ~/.muttrc file so I can see what I'm doing wrong? I don't need the passwords, obviously :) but the configuration settings would be very helpful. Thanks!

---

### Post by AlexTheMad on 2009-06-29
Sure thing. Sorry for the late reply, but hope this helps

```

set imap_user="#####@gmail.com"
set imap_pass="#####"
set smtp_url="smtp://######@smtp.gmail.com:587/"
set smtp_pass="######"
set from="#####@stud.ntnu.no"
set realname="######"

set folder ="imaps://imap.gmail.com:993"
set spoolfile="+INBOX"
set postponed="+[Gmail]/Drafts"

set header_cache="~/.mutt/cache/headers"
set message_cachedir="~/.mutt/cache/bodies"
set certificate_file="~/.mutt/certificates"

set move = no       # stop asking to move msgs to mbox
set sort = 'threads'
set sort_aux = 'last-date-received'

# How often should mutt check for new mail?
set mail_check=60
# Notify me of new mail in my mailbox this often
set timeout=15
set imap_check_subscribed

set edit_hdrs       # see headers when editing mail
set include         # quote msg when replying
set reply_to        # use adress from reply-to header when replying
set fast_reply      # do not ask for to, sbuject,.. when replying
set auto_tag        # if something is tagged run commands on all tagged msgs
set delete_untag    # untag msgs when marking them for deletion
set mark_old = no   # don't differentiate between new and old

set forward_format="Fwd: %s"

# In what order should the header fields be presented?
hdr_order From: Date: To: Cc: Reply-To: Subject:
ignore *
unignore From: Date: To: Cc: Reply-To: Subject:

# Add these header fields to every message
my_hdr Reply-To:

set tilde                   # pad bottom blank lines when in page view
set pager_index_lines=9     # 9 index mail lines on top when in page view

# Gmail have the notion of labels
# If a message has several labels, we actually need to move it to the
# trash to remove all labels (delete from all folders)
# This one requires mutt with the trash patch
set trash = "=[Gmail]/Trash"

# Take me back to the index before deleting when in page view
folder-hook . 'macro pager d "<exit><delete-message>" "Delete the message"'

set alias_file=~/.mutt/mail_aliases
source ~/.mutt/mail_aliases

set editor="vim '+:7'"  # vim for editing, and move marker to line 7

macro index gh "<change-folder> =Hovedstyret<enter>" "Go to Hovedstyret"
macro index gd "<change-folder> =dotKom<enter>" "Go to dotKom"
macro index gf "<change-folder> =Datakameratene<enter>" "Go to Datakameratene"
macro index gm "<change-folder> =[Gmail]/Drafts<enter>" "Go to drafts"
macro index gt "<change-folder> =[Gmail]/Trash<enter>" "Go to trash"
# Doesnt work cause of spaces :(
macro index gi "<change-folder> ='[Gmail]/All Mail'<enter>" "Go to inbox"

# color WHERE FOREGROUND BACKGROUND REGEXP
color index green   default ~p  # i am to/cc
color index cyan    default ~P  # from me
color index yellow  default ~N  # new
color index yellow  default ~O  # new
color index magenta default ~F  # flagged
color index blue    default ~T  # tagged
color index red     default ~D  # deleted


```

---

### Post by AlexTheMad on 2009-06-29
woohoo.. managed to work out how to access the folders with spaces in their names now, autocompletion ftw ;)

```

macro index gi "<change-folder> =[Gmail]/All<tab><enter>" "Go to inbox"
macro index gs "<change-folder> =[Gmail]/Sent<tab><enter>" "Go to sent mail"

```

---

### Post by pythonscript on 2009-07-04
Thank you so much for the help! In hindsight, configuring mutt to give me access to All Mail was somewhat stupid, since I  have around 25000 messages in that folder, it takes a while to update... but the tip about spaces worked great. Now I don't have to leave my virtual terminals to check e-mail!

---

### Post by retrovertigo on 2009-11-16
You can also put the following line before your "gi", "gs", etc. macros and not have to worry about putting in the **<tab>**.

```
bind editor <space> noop
```

---

### Post by karthick87 on 2010-10-04
But the shortcut not working for me..This is the script.,


```
# Gmail-style keyboard shortcuts
macro index,pager y "<enter-command>unset trash\n <delete-message>" "Gmail archive message"
macro index,pager d "<enter-command>set trash=\"imaps://imap.googlemail.com/[GMail]/Bin\"\n <delete-message>" "Gmail delete message"
macro index,pager gi "<change-folder>=INBOX<enter>" "Go to inbox"
macro index,pager ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
macro index,pager gs "<change-folder>=[Gmail]/Starred<enter>" "Go to starred messages"
macro index,pager gd "<change-folder> =[Gmail]/Drafts<enter>" "Go to drafts"

```

---

### Post by retrovertigo on 2010-10-04
> **getyourkarthick said:**
> But the shortcut not working for me..This is the script.,


```
# Gmail-style keyboard shortcuts
macro index,pager y "<enter-command>unset trash\n <delete-message>" "Gmail archive message"
macro index,pager d "<enter-command>set trash=\"imaps://imap.googlemail.com/[GMail]/Bin\"\n <delete-message>" "Gmail delete message"
macro index,pager gi "<change-folder>=INBOX<enter>" "Go to inbox"
macro index,pager ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
macro index,pager gs "<change-folder>=[Gmail]/Starred<enter>" "Go to starred messages"
macro index,pager gd "<change-folder> =[Gmail]/Drafts<enter>" "Go to drafts"

```

Which ones don't work? Those look fine, except for the one for "drafts", which should not have that space after "<change-folder>".

---

### Post by karthick87 on 2010-10-04
I changed it to the following

```
macro index,pager gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"
```

but when i enter gd in mutt it says "[COLOR=Red]Unknown Mailbox: [GMAIL]/Drafts (failure)[/COLOR]"
when i enter gs it says "[COLOR=Red]Unknown Mailbox: [GMAIL]/Starred (failure)[COLOR=Black]"[/COLOR]
[COLOR=Black]when i enter ga it says "[/COLOR][/COLOR][COLOR=Red]Unknown Mailbox: [GMAIL]/All Mail (failure)[COLOR=Black]"[/COLOR][/COLOR][COLOR=Red]
[/COLOR]

---

### Post by karthick87 on 2010-10-05
Bump....!

---

### Post by retrovertigo on 2010-11-17
> **karthick87 said:**
> I changed it to the following

```
macro index,pager gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"
```

but when i enter gd in mutt it says "[COLOR=Red]Unknown Mailbox: [GMAIL]/Drafts (failure)[/COLOR]"
when i enter gs it says "[COLOR=Red]Unknown Mailbox: [GMAIL]/Starred (failure)[COLOR=Black]"[/COLOR]
[COLOR=Black]when i enter ga it says "[/COLOR][/COLOR][COLOR=Red]Unknown Mailbox: [GMAIL]/All Mail (failure)[COLOR=Black]"[/COLOR][/COLOR][COLOR=Red]
[/COLOR]

It looks like the "=" sign is missing from the beginning of the folder name in the error messages you're seeing. I wonder if the order in which you define your IMAP settings and macros has anything to do with it. Can you post your .muttrc?

---

### Post by daithib8 on 2011-01-01
Use [Google Mail] instead of [GMail]. in mutt press c followed by ? to bring up a list of available folders. Sent and Bin are under GMail but other folders are under GoogleMail. At least in my case
Also don't forget to update set postponed and set record in muttrc.

---

### Post by retrovertigo on 2011-01-02
> **daithib8 said:**
> Use [Google Mail] instead of [GMail]. in mutt press c followed by ? to bring up a list of available folders. Sent and Bin are under GMail but other folders are under GoogleMail. At least in my case
Also don't forget to update set postponed and set record in muttrc.

That might not be the case for everyone though. One way to check the names of the IMAP folders is to hit "c" from within mutt, then hit "?". This will take you to a list of the IMAP folders.

---

### Post by epikvision on 2013-01-06
> **karthick87 said:**
> I changed it to the following

```
macro index,pager gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"
```but when i enter gd in mutt it says "[COLOR=Red]Unknown Mailbox: [GMAIL]/Drafts (failure)[/COLOR]"
when i enter gs it says "[COLOR=Red]Unknown Mailbox: [GMAIL]/Starred (failure)[COLOR=Black]"[/COLOR]
[COLOR=Black]when i enter ga it says "[/COLOR][/COLOR][COLOR=Red]Unknown Mailbox: [GMAIL]/All Mail (failure)[COLOR=Black]"[/COLOR][/COLOR][COLOR=Red]
[/COLOR]

Right now, I am on a quest to configure my mutt, and I luckily found this post. 

I was having the same problem earlier, until I tried c and ?, as most of the following replies suggested.  I realized the name for "Starred" was actually "&#48324;&#54364;&#54200;&#51648;&#54632;" (starred mails).  *Because I set my gmail localization to Korean, I had to use the korean names for the folders.*

I got the same error message for gs, until I configured as...
```
macro index,pager gd "<change-folder>=[Gmail]/**&#48324;&#54364;&#54200;&#51648;&#54632;** 
```.  Then it was solved!

It so happens I had to make the same changes to drafts and all mail as well.  Strangely, INBOX wasn't affected.

---

