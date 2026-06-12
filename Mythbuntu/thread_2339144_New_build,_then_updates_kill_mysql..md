---
title: "New build, then updates kill mysql."
date: 2016-10-05
forum: Mythbuntu
---

### Post by grego892 on 2016-10-05
I did a full format and install build from mythbuntu-16.04.1-desktop-amd64.iso.  Works fine until I do the updates in Control Centre.  First, it hangs at "samba-common" update.  I rebuilt without samba and now mysql won't start at all after the updates.  Does anyone have any suggestion?

Thank you

---

### Post by grego892 on 2016-10-09
(Short version)

Go to "Mythbuntu Control Center" and uncheck "Enable MySql performance tweaks" before you undate.  

[https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767)

---

