---
title: "SOLVED - Ekiga gconf schema error"
date: 2008-11-25
forum: Multimedia Software
---

### Post by WhiteHorse on 2008-11-25
I was getting the following error message from Ekiga after upgrading from 8.04 to 8.10:
Ekiga got an invalid value for the GConf key "/apps/ekiga/general/gconf_test_age"

Here's the solution:

sudo cp /usr/share/gconf/schemas/ekiga.schemas /etc/gconf/schemas/
sudo ekiga-config-tool --install-schemas

Then I started Ekiga with no problem. Note: I also ran the clean, clean schemas, and fix permissions before doing the above solution. Here is it's usage:

ekiga-config-tool
Usage:  ekiga-config-tool OPTION
Fixes problems with the Ekiga settings

  --clean                remove all user settings
  --install-schemas      install schemas with default settings (run as root)
  --clean-schemas        remove schemas with default settings (run as root)
  --fix-permissions      fix permissions of GConf repository (run as root)

---

### Post by jvin248 on 2009-08-12
I used your solution with success, Ekiga on my 8.04 Xubuntu wasn't starting up and now it is.  Thanks!  I did have to create the schemas directory as it seemed to be missing on my setup.  So check with the ls command and mkdir if it's not there.

Here are the correctly ordered steps
for the next recipe user:

=================================

ls -l /etc/gconf/schemas/
sudo mkdir /etc/gconf/schemas/
sudo cp /usr/share/gconf/schemas/ekiga.schemas /etc/gconf/schemas/ekiga.schemas

sudo ekiga-config-tool --clean
sudo ekiga-config-tool --clean-schemas
sudo ekiga-config-tool --fix-permissions
sudo ekiga-config-tool --install-schemas

ekiga

================================

---

