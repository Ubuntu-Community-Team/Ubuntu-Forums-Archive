---
title: "CALIBRE not working in Natty"
date: 2011-04-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CoolJohnB on 2011-04-27
I installed Calibre from Software center it worked fine and collated a number of .pdf files I have, but when I click open to view it logs out and back in again!  This happens with both Unity and Classic.

Is there a solution to this?  Has it happened to anyone else?

Thanks in advance for any advice.

---

### Post by dino99 on 2011-04-27
you should find usefull errors logged: watch into /var/log (system admin logviewer) and into .xsession-errors (/home, ctrl+h to unhide it)

---

### Post by stoneguy on 2011-04-27
The PDF conversion engine calibre uses doesn't work so well. If your starting documents are multi-column or have embedded graphics, don't get your hopes up. 

If you want PDF output, use calibre to convert to RTF and then LibreOffice to PDF. But regard it as a one-way trip and preserve the RTF to base further conversions on.

---

### Post by CoolJohnB on 2011-04-27
OK Thanks for that, guess I might as well uninstall Calibre as I wanted it mainly for .pdf files.  Is there an alternative?

---

