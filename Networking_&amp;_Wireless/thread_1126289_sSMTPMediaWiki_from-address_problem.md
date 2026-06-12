---
title: "sSMTP/MediaWiki from-address problem"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by CR34M3 CR4CK3R on 2009-04-15
Hi, I've got a server set up running a wiki (MediaWiki powered) and a project tracker (Redmine). Both are configured to send notification emails to users using sSMTP. The problem is that email sent by MediaWiki appears to come from www-data@myserver.

I have Redmine configured to send mail from redmine@myserver, but I can't seem to find such an option in MediaWiki.

The most likely cause is that it is using the Apache username (www-data), but I do not have the MediaWiki/sSMTP/Apache knowledge to rectify this.

[Running an Apache2 webserver on Ubuntu 8.10 with MediaWiki and Redmine]

Any help would be greatly appreciated.

---

### Post by Mr. Brownstone on 2009-04-29
Check this option in your ssmtp.conf:

```
# Set this to never rewrite the "From:" line (unless not given) and to
# use that address in the "from line" of the envelope.
FromLineOverride=YES
```

Enabling this allows you to specify a From: address in your mail headers.

---

