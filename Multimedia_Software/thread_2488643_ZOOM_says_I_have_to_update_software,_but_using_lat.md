---
title: "ZOOM says I have to update software, but using latest version"
date: 2023-07-11
forum: Multimedia Software
---

### Post by cigtoxdoc on 2023-07-11
I am using ZOOM version 5.15.3.4838 running under 23.04.  When I log into ZOOM, it says I need to get an updated version of the software.  Current version is only one available from ZOOM.

Are there any other sources for the update?

Thank you,

John

---

### Post by #&amp;thj^% on 2023-07-11
you say your on 23.04 but your version isn't the same as mine:
```
apt policy zoom
zoom:
  Installed: (none)
  Candidate: 5.15.0.4063
  Version table:
     5.15.0.4063 500
        500 http://repo.linuxliteos.com/linuxlite fluorite/main amd64 Packages
```
And after the update i find the same version as you:
```
apt policy zoom
zoom:
  Installed: 5.15.3.4839
  Candidate: 5.15.3.4839
  Version table:
 *** 5.15.3.4839 100
        100 /var/lib/dpkg/status
     5.15.0.4063 500

```

Types of Zoom updates

There are 3 types of updates: web-only, mandatory and optional.
[list]
    [*]Web-only: These updates are available for download from the web portal for new fixes that are being tested. 
    [*]Mandatory: These updates will start once you click on update. You cannot proceed further until you update.
    [*]Optional: These updates will start once you click on update. You can proceed should you decide to postpone the update till a later time and update manually. [/list]

Note: If you choose to postpone your optional update, you will only be prompted to update the next time you login.
But I'm not prompted to update as of now on  Installed: 5.15.3.4839

---

### Post by iamjiwjr on 2023-10-17
5.16.04. is current. Present Snap is significantly out of date, as it has been since day 1. Virtual desktops are not active. Webcam stability is shaky at best. The deb from Zoom is solid but it will no longer install in 23.10 due to dependency conflicts. And who knows when Zoom will get around to updating that on their end. I recommend the flatpak version. It's not great but at least it stays current and it has been reliably stable for me.

---

