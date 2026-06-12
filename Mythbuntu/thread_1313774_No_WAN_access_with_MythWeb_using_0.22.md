---
title: "No WAN access with MythWeb using 0.22"
date: 2009-11-04
forum: Mythbuntu
---

### Post by rothgar on 2009-11-04
Hello,
I am having a problem getting access to MythWeb from outside of my LAN. I have forwarded the port and I am even prompted for a mythweb password and forwarded to /mythweb/ folder but then I just get a 404 error that the file or folder is not found. I am guessing this has something to do with mythweb only allowing LAN access but I cannot find the configuration for it. I have checked in /etc/apache2/apache2.conf and didn't see anything relevant to only allow LAN access. I have checked the wiki and searched the forum but am at a loss for where this setting might be.
I have also tried adding a password to MythWeb using the mythbuntu-control-center and the password works just fine locally but still errors out outside of my network.

If anyone has any info on making this work or things I could maybe try please let me know.

---

### Post by rothgar on 2009-11-04
This is a bump because I have found way too many configuration files and I am trying to figure out which ones I need to change to make this work. So far I think the problem lies with the fact that my site needs an alias which I tried adding to /etc/apache2/sites-enabled/default-mythbuntu by adding 

ServerAlias mysitename.com

But that didn't work.

I restarted apache and it said it couldn't resolve the ServerName either so I added that as well, but it still didn't work.

Can someone help me at least figure out which configuration files I should be looking at?

/etc/apache2/apache2.conf
/etc/apache2/sites-enabled/default-mythbuntu
/etc/apache2/sites-enabled/mythweb.conf
/etc/apache2/sites-available/default-mythbuntu
/etc/apache2/sites-available/default
/etc/apache2/sites-available/mythweb.config

One setting that looked like it might be helpful is the RewriteBase inside of /etc/apache2/sites-anabled/mythweb.conf

I tried changing it to /var/www/mythweb/ without success still.

---

