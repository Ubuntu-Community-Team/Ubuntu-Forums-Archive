---
title: "mytharchive permissions"
date: 2010-01-02
forum: Mythbuntu
---

### Post by pinacate on 2010-01-02
I'm running mythbuntu 9.10 and having what looks like permissions problems when attempting to burn a dvd using mytharchive.

I've set permissions in /var/lib/mytharchive/temp to 777 and owner to mythtv:mythtv.

Any help would be appreciated.

Here's the tail of the mytharchive log:

chmod: changing permissions of `/var/lib/mytharchive/temp/': Operation not permitted
chmod: changing permissions of `/var/lib/mytharchive/temp/work': Operation not permitted
chmod: changing permissions of `/var/lib/mytharchive/temp/logs': Operation not permitted
chmod: changing permissions of `/var/lib/mytharchive/temp/logs/mythburn.log': Operation not permitted
chmod: changing permissions of `/var/lib/mytharchive/temp/config': Operation not permitted
chmod: changing permissions of `/var/lib/mytharchive/temp/config/xxm': Operation not permitted

---

### Post by NightStorm on 2010-01-03
I had the same issue.  To fix it I did this:
  sudo bash
  cd /var/lib/mytharchive
  rm -rf temp
  mkdir temp
  chown <myAccount>.mythtv temp
  chmod 777 temp

Replace "<myAccount>" with whatever account name your mythfrontend runs under.  I am doing this from memory, but hopefully I've got that correct.  I also recall that I had issued the same "chown" command on /var/lib/mytharchive at one point (but I doubt that it is necessary).

I hope that works for you.

        - Bruce

---

