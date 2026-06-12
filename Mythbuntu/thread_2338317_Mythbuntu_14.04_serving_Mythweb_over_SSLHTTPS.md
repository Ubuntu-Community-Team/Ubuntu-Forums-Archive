---
title: "Mythbuntu 14.04 serving Mythweb over SSL/HTTPS?"
date: 2016-09-26
forum: Mythbuntu
---

### Post by Nate B. on 2016-09-26
I've been poking all over the Web including searching this forum but I've not hit the magic configuration yet.

I have enabled SSL per [FONT=Courier New]/usr/share/doc/apache2/README.Debian.gz[/FONT] and the default page under [FONT=Courier New]/var/www/html[/FONT] is served via HTTPS.  So far so good.

I have also enabled userdirs to have their [FONT=Courier New]public_html[/FONT] content served via HTTPS.  So far so good.

Mythweb is the last ornery holdout and I am guessing that since the mythweb directory is under [FONT=Courier New]/var/www/[/FONT] as [FONT=Courier New]/var/www/mythweb[/FONT] instead of [FONT=Courier New]/var/www/html[/FONT], that this is somehow the issue.  My question is that since this is apparently the default location from the mythweb package install script that it should be reasonably straight forward to serve this directory via SSL. So far I have not found any documentation that talks about this.  Has anyone gotten this to work?

---

