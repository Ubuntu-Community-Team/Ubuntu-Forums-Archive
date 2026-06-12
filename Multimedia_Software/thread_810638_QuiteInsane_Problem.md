---
title: "QuiteInsane Problem"
date: 2008-05-28
forum: Multimedia Software
---

### Post by spotteddog on 2008-05-28
QuiteInsane can't see my printer. It scans and I can save the document, but there is not a printer listed on the options page. I have to save my document and the open it, then I can print it.

Also, if I install Xsane, it can _not_ copy. I get an error of broken pipe and failed to execute printer command. The other scan options in Xsane work. It's just the copy option.

I think it is a printer problem with these 2 apps, because my printer prints OK with other applications.

Would uninstalling and reinstalling the printer driver help? If so, how do I do that?

Thanks

---

### Post by madjr on 2008-05-28
have you had this problem before with another version of ubuntu or linux?

---

### Post by spotteddog on 2008-05-28
> **madjr said:**
> have you had this problem before with another version of ubuntu or linux?
Hardy is my first try at Linux. I have been using it for about 6 weeks and after reinstalling 6 times, I thought I finally had it right and was happy. Hadn't had any problems in weeks until after the new kernel update last weekend. When I went to use my printer for the first time after the update, it gave me some screwy messages about printer drivers (which I never got before). I think this is where the problems started. When the preinstalled Xsane gave me printer problems, I uninstalled it and installed quiteinsane. I still have printer problems with both tose apps, but otherwise, my printer works fine.

---

### Post by Mikeoak on 2008-06-06
Am having the same problem. My quick solution if I want to scan and print from quiteinsane is to run the live CD for Gutsy, 7.10, configure the printer and install quiteinsane.  I can then make perfect copies since quiteinsane will detect my printer even from the live CD.  

I am considering installing Gutsy and setting up the system the way I want it and then doing the long upgrade to 8.04.

---

### Post by wkulecz on 2008-07-15
Found this thread vis search.  Xsane had issues finding my Canoscan USB scanner on 7.04, but once I did the "scanbuttons" hack it found scanner and the printer and we could make copies.

On 8.04, scanner is found out of the box, and printing works in all other applications I've tied but no printers are found when I choose the scan type as copy.

I'm at a loss as to what to do other than scan to a file and then print the file which is way to clunky for my wife to deal with.

--wally.

---

### Post by Mikeoak on 2008-07-27
I just found something that works partially for me.  If you install the gimp plugin for Quiteinsane, you can fire up Gimp and under file>aquire you can manage to scan the image and from the Gimp image window you can print and it will see my printer.  However, I am back to not having a 100% reproduction.  It is reduced to about 80% with an ugly black stripe on the left side.

---

