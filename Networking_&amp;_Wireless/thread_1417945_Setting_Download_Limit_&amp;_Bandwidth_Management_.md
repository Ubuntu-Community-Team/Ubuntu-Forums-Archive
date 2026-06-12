---
title: "Setting Download Limit &amp; Bandwidth Management Using SQUID"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by linuxrockers on 2010-02-27
How to set download limit using SQUID? I want to specify the download limit for a particular list in MB. Is it possible to limit bandwith for some group of machines in network? If so how? Please help..!!!

---

### Post by Barriehie on 2010-02-28
Having never done it you may or may not find this useful. :)  I'm running 2.6 stable 18 and straight out of the squid.conf file it says:
```

#  TAG: reply_body_max_size	bytes allow|deny acl acl...
#	This option specifies the maximum size of a reply body in bytes.
#	It can be used to prevent users from downloading very large files,
#	such as MP3's and movies. When the reply headers are received,
#	the reply_body_max_size lines are processed, and the first line with
#	a result of "allow" is used as the maximum body size for this reply.
#	This size is checked twice. First when we get the reply headers,
#	we check the content-length value.  If the content length value exists
#	and is larger than the allowed size, the request is denied and the
#	user receives an error message that says "the request or reply
#	is too large." If there is no content-length, and the reply
#	size exceeds this limit, the client's connection is just closed
#	and they will receive a partial reply.
#
#	WARNING: downstream caches probably can not detect a partial reply
#	if there is no content-length header, so they will cache
#	partial responses and give them out as hits.  You should NOT
#	use this option if you have downstream caches.
#
#	If you set this parameter to zero (the default), there will be
#	no limit imposed.
#
#Default:
# reply_body_max_size 0 allow all

```

Should be easy to implement!
HTH

---

### Post by linuxrockers on 2010-02-28
I found the line ,

# reply_body_max_size 0 allow all

in my configuration file.But value 0 means Unlimited download. I need to setup download limit to 15 MB
for an Access Control List(ACL).How can I achieve it? Please help..!!

---

### Post by Barriehie on 2010-02-28
According to the description in the comments:
```

reply_body_max_size 15000000 allow ***ACL name here***

```

---

### Post by linuxrockers on 2010-03-02
Its working now..!! Thank you so much!!

---

### Post by Barriehie on 2010-03-02
> **linuxrockers said:**
> Its working now..!! Thank you so much!!

Welcome! Perhaps mark the thread as solved for others.

---

### Post by Subhranshu on 2010-10-21
Hi all,

I would like to control bandwidth usage for specific application.

For Example:- If i have 4000kbps of bandwidth, and if some one uses **"SKYPE"** i could alot a specific bandwidth of 255kbps to it.

Is there any way out,

I tried following this,

[http://pcquest.ciol.com/content/linux/103080904.asp](http://pcquest.ciol.com/content/linux/103080904.asp)

But no Joy,

Thanks

Subhranshu Dwivedi

---

### Post by kashif_max on 2012-04-30
Changes in 3.x.x. Syntax changed to:
*reply_body_max_size [size unit] [acl]*
allow/deny no longer used.

---

