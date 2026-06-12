---
title: "PHP DNS fails"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by fela on 2011-04-30
DNS is working fine with things like ping, ie. I can ping any address from my server and it gets resolved. However PHP always fails with things like file_get_contents("http://www.google.com"), or simply php_network_getaddresses.

Any idea what's at fault?

Cheers

---

### Post by fela on 2011-04-30
OK, PHP can see hostnames while running from the command line, and running a test script that echoes [http://www.google.com](http://www.google.com) with file_get_contents works like that. I also tested running that script as www-data, the apache user. That works aswell, so I don't think it can be a permissions issue.

Any ideas?

---

### Post by fela on 2011-04-30
Update:

DNS resolution does actually work, however ```
<?php
file_get_contents("http://www.google.com");
?>
``` doesn't.

Also, drupal gives the error 'HTTP REQUEST STATUS failure' - ie it can't do DNS resolution.

EDIT: fixed the drupal error, but file_get_contents() still doesn't work.

---

