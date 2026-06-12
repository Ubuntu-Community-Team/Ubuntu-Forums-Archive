---
title: "Windows Shared Printer on Jaunty"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by ieduarte73 on 2009-05-12
I have just changed to the latest Ubuntu release (Jaunty Jackalope - 9.04), everything is working just fine, however, when I configure a Windows Shared Printer, it doesn't work at all, even though the printer was added.

I checked on the Windows Box that has the printer installed on, and the print job is received (Test Page from Ubuntu in this case), and the file size grows to 44MB !!, then, it apparently starts to print, but only gets to read/process 64 KB out of the 44MB, and then it crashes the Windows spool.

On the Ubuntu box, I could see the job being sent to the server (Windows Box) with a size of 150K (that's more like it) and then it shows like the job has already been completed, no errors whatsoever, but also NO PRINTOUT AT ALL.

This same printer is shared with other Windows Boxes without having any problem at all, it is only the Ubuntu Jaunty boxes the ones with this issue.

---

### Post by enathanson on 2009-09-02
Regarding the problem connecting to a windows printer share...

9.04 (Jaunty) shipped with a beta hp driver.  Perhaps the same is true for some other brands.  When I discovered this and upgraded the driver, everything worked as expected.

URL for HP Linux drivers is: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

