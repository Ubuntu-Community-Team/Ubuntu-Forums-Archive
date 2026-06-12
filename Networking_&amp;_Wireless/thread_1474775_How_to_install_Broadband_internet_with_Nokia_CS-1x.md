---
title: "How to install Broadband internet with Nokia CS-1x"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by coc_21 on 2010-05-06
I am using 10.04 and is trying to install the linux drivers for Nokia CS-10.

However when I try to install the deb file, it doesnt work. The installation process starts then its starts another process then gives me the error which state I have to close the previous installer window.

Any ideas ???


This is where I found the drivers
following[http://europe.nokia.com/EUROPE_NOKIA_COM_3/Get_Support/Product_Support/Support_for_Accessories/IMAGING/Nokia_Internet_Stick_CS-10/linux_2.10.zip]("http://europe.nokia.com/EUROPE_NOKIA_COM_3/Get_Support/Product_Support/Support_for_Accessories/IMAGING/Nokia_Internet_Stick_CS-10/linux_2.10.zip")

---

### Post by Lion's Pride on 2010-11-29
To correct the bug that you encountered follow the steps below:

- Extract the contents of the.deb archive
- Open the DEBIAN folder that was extracted
- Open & Edit the postinst file.
- Replace "***udevadm control reload_rules***" with "***udevadm control --reload-rules***"
- Save and close the file 
- Open & Edit the postrm file.
- Replace "***udevadm control reload_rules***" with "***udevadm control --reload-rules***"
- Save and close the file 


Remake the deb package by using

- dpkg -b *directory packagename.deb*; where *directory*  contains the filesystem tree with all the requisite files for your  program (the extracted files). Note, you can build the package without specifying the name of  the new package, but then it will simply place the package file under directory as ".deb" -- which might lead you to believe that the package wasn't created at all.

Or just use the .deb archive in the zip archive attached.

---

