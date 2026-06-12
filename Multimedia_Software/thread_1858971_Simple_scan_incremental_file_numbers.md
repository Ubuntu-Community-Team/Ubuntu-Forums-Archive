---
title: "Simple scan incremental file numbers"
date: 2011-10-13
forum: Multimedia Software
---

### Post by claven123 on 2011-10-13
I would like to be able to have simple scan choose a increasing number when I save scans.  I have searched a bit and can't seem to find this.  I have to name each one and it is a bit time consuming.  

Any ideas?

I'm using Ubuntu 10.10 and simple scan 2.32.0

Thanks,

D

---

### Post by WasMeHere on 2011-10-13
I think it does already, if you do not save between each scan, but save to file after all scans. (You can also save to a pdf file.)

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Johnb0y on 2011-10-13
do you mean you want to save them as individual or multiple files? or do you mean rename them as you go? or all at one time? basically need more info... :p

---

### Post by claven123 on 2011-10-13
Ok, I have a stack of forms I need to scan.  I put one in the scanner and hit the scan button.  It scans, then I hit the save button and the save as dialog box opens up with the title......  Scanned Document.pdf  The words Scanned Document is highlighted.

I then rename the file to....   XXX.pdf

Well, then I scan another and repeat it all over....

I would like it to say....  Scan01.pdf

Then after the next document it would say... Scan02.pdf

Then.... Scan03.pdf   etc.... 


I can only scan one document at a time, I have to manually feed it.

Does anyone know of a plug in or something?  Or, if I just need to click something within simple scan?

D

---

### Post by WasMeHere on 2011-10-14
> **claven123 said:**
> Ok, I have a stack of forms I need to scan.  I put one in the scanner and hit the scan button.  It scans, then [s]I [COLOR="Red"]hit the save button[/COLOR][/s] and the save as dialog box opens up with the title......  Scanned Document.pdf  The words Scanned Document is highlighted ...

D

Don't hit the save button until you have scanned all your documents! Then you can save it as one pdf file or jpeg files with incremental file numbers.

Have a try :-)
Olle

---

### Post by claven123 on 2011-10-14
If I do that then I will end up with one pdf with tons of documents within the one pdf (I do this when I have multiple page documents I scan).

I need each one to be separate.  Ie the bank statement for Aug is not combined with the Electric bill for June etc...


Under windows the scanner would make each scan the next number in the series... just like when you take digital pictures on a camera.

Does simple scan do this or not, if it does, does someone know how to do this?  Or point me in the direction that I can seek some assistance.

Thanks,

Dennis

---

### Post by WasMeHere on 2011-10-14
Simple Scan does what you want with pictures (saving as jpg files), but it works as you describe when saving in pdf format.

Another option might be to use the Xsane scanner. If not already installed, use ```
sudo apt-get install xsane
``` to install it. This program is more advanced. I hope it can do what you need :-)

Olle

---

