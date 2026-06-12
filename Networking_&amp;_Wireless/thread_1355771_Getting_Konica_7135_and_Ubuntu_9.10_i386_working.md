---
title: "Getting Konica 7135 and Ubuntu 9.10 i386 working?"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by shultzjr on 2009-12-15
hi all,

I am trying to get an Ubuntu 9.10 box working with a network printer, Konica 7135 that is postscript compatible.  The address of the printer is 192.168.1.201 port 10001 and it works with Windows XP just fine.  I downloaded all the appropriate files from konica's website including the ppd file, went through the installation instructions and set up cups in gnome.  When the icon appears in the printing manager it has a green checkmark in the upper left hand corner of it and it has a triangle with an exclamation point in it in the lower right part of the icon.  When I try to print a test page, I get "stopping job because the scheduler could not excecute a filter."  From what I gather this means that it can't find the driver (ppd).  I unarchived it and copied it to the /etc/lp/ppd directory and point directly to it in the install process.  What am I missing?

Ubuntu needs a printing subcategory for help questions.  Since this is over the network I posted here.  If there is a better place for this question, please let me know.

thanks,
charles......

---

