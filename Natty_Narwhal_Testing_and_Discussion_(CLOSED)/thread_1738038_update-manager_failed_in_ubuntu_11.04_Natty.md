---
title: "update-manager failed in ubuntu 11.04 Natty"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zigorati on 2011-04-24
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by tlcstat on 2011-04-24
Greetings,
Open /var/lib/apt/lists and delete the contents. If you feel hesitant to do this you can compress the lists dir first so that it can be restored. 
You may need to have super user rights to delete the contents, sudo nautilus. The update manager will update the lists dir. 
If you are comfortable with Ubuntu you can use sudo rm /var/lib/apt/lists/*.*
tlcstat

---

### Post by KegHead on 2011-04-24
Hi!

Then upgrade:

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

KegHead

---

