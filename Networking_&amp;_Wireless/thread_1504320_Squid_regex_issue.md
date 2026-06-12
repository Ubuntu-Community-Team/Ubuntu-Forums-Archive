---
title: "Squid regex issue"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by hardwarehank on 2010-06-07
Why won't the following rules work properly in squid?

```

# Facebook Like Button Denial 
acl facebook dstdomain .facebook.com 
acl facebook_like urlpath_regex [-i] ^\/plugins\/like\.php 
deny_info error-facebook-like facebook_like 
http_access deny facebook facebook_like http_access allow facebook

```

It blocks [http://developers.facebook.com/plugins](http://developers.facebook.com/plugins) as well as [http://facebook.com/plugins/like.php](http://facebook.com/plugins/like.php)

---

### Post by hardwarehank on 2010-06-07
The problem is that I had a typo that Squid didn't fix.  Here's the working version with the change in bold:

```
# Facebook Like Button Denial
acl facebook dstdomain .facebook.com
acl facebook_like urlpath_regex **-i** ^\/plugins\/like\.php
deny_info error-facebook-like facebook_like
http_access deny facebook facebook_like
```

**Squid should not run with the following line in the config file:**

```
acl facebook_like urlpath_regex [-i] ^\/plugins\/like\.php
```

This makes it match very strangely.  I'm not really sure why it was matching like it was.  If you're a squid developer, please fix this.  I'll be posting a bug.

---

