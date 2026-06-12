---
title: "downloaded pdf requires password to open on centos but not on ubuntu??"
date: 2010-01-31
forum: Multimedia Software
---

### Post by extendedping on 2010-01-31
downloaded a pdf on to both systems from the same place. on centos 5.4 trying to open it with any pdf reader says it is locked and needs a password. but on ubuntu 9.10 the download just opens. I also removed the centos downloaded pdf, and copied the pdf from ubuntu (which again ubuntu opens without a password on several pdf readers), and on centos again the pdf requires a password to open. can anyone shed light on this? thanks.

---

### Post by sports.car.guy on 2010-01-31
> **extendedping said:**
> downloaded a pdf on to both systems from the same place. on centos 5.4 trying to open it with any pdf reader says it is locked and needs a password. but on ubuntu 9.10 the download just opens. I also removed the centos downloaded pdf, and copied the pdf from ubuntu (which again ubuntu opens without a password on several pdf readers), and on centos again the pdf requires a password to open. can anyone shed light on this? thanks.


It is most likely that CentOS is strictly adhering to PDF security specifications where as the libraries for PDF's in Ubuntu don't. It can also be dependent on the reader. Adobe's will adhere to security regardless the platform. The other readers it depends if they have unrestricted libraries that don't adhere to the security.

---

### Post by extendedping on 2010-01-31
> **sports.car.guy said:**
> It is most likely that CentOS is strictly adhering to PDF security specifications where as the libraries for PDF's in Ubuntu don't. It can also be dependent on the reader. Adobe's will adhere to security regardless the platform. The other readers it depends if they have unrestricted libraries that don't adhere to the security.

so there was a password placed on the pdf but ubuntu somehow ignores it while centos does not? sounds weird or I just am not getting it. anyway its pretty annoying, I did try with several pdf viewers on both and all is ok on ubuntu and non worked with centos. so it must be the os?

---

### Post by ad_267 on 2010-01-31
> **extendedping said:**
> so there was a password placed on the pdf but ubuntu somehow ignores it while centos does not?
Yep.

> so it must be the os?
It depends on how the OS/distribution has configured the PDF reader. You can change this in Evince (the default PDF reader in Ubuntu) by pressing Alt+F2 and running "gconf-editor" (without quotes) then go to Applications -> Evince and set or unset "override_restrictions". This works in Ubuntu but might not in CentOS. Okular (the default reader in KDE) has an option to obey restrictions which is available from the preferences menu.

---

