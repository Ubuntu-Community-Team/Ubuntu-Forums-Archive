---
title: "stop mythweb from redirecting apache"
date: 2009-11-25
forum: Mythbuntu
---

### Post by xinix on 2009-11-25
Mythweb set apache to automatically go to /mythweb on my computer.  How do I get it to stop doing this.  I have tried recofigureing the package but that didn't help.  It looks like I need to manually reconfigure an apache config file.  Which one is it?

Any ideas?

Thanks

Edit: solved this,  I originally tried editing the /var/www/index.html (it simply has a redirect), but wasn't seeing the change.  I restarted apache and not this redirects to the right link.  I'm not sure why it didn't work the first few time I tried it.

---

