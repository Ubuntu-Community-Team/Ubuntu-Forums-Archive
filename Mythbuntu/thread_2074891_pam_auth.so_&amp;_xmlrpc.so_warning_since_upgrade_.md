---
title: "pam_auth.so &amp; xmlrpc.so warning since upgrade to 12.04 &amp; .26"
date: 2012-10-22
forum: Mythbuntu
---

### Post by dheianevans on 2012-10-22
Upgraded to 12.04 *and* 0.26 yesterday and since then my root email's been getting a ton of these warning messages from cron every 30 minutes on the half-hour.

Any idea? I've never had this with previous mythbuntu versions.


PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/pam_auth.so' - /usr/lib/php5/20090626/pam_auth.so: cannot open shared object file: No such file or directory in Unknown on line 0 PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/xmlrpc.so' - /usr/lib/php5/20090626/xmlrpc.so: cannot open shared object file: No such file or directory in Unknown on line 0 

This is what cron appears to be trying to do that causes the message if that helps nail it down:

[ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete

---

### Post by shissncg on 2012-11-05
bump

---

