---
title: "Hugin Panorama tool  not working in Digikam since upgrade to Ubuntu 22.04"
date: 2023-01-22
forum: Multimedia Software
---

### Post by colliers-barci-westnet on 2023-01-22
I have recently made a clean install of Ubuntu 22.04 LTS.  After reinstalling Digikam I find that the panorama creator tool (Hugin) is demanding additional files and refuses to run without them.  I have no idea where those files are supposed to go.  I need help with understanding the process to get Hugin working again.  Any help would be much appreciated . . .

---

### Post by mIk3_08 on 2023-01-22
> **colliers-barci-westnet said:**
> I have recently made a clean install of Ubuntu 22.04 LTS.  After reinstalling Digikam I find that the panorama creator tool (Hugin) is demanding additional files and refuses to run without them.  I have no idea where those files are supposed to go.  I need help with understanding the process to get Hugin working again.  Any help would be much appreciated . . . 
Try to run the command below in your terminal: 
```
apt search packagename
example: 
apt search panorama
```
Regards and cheers.

---

### Post by colliers-barci-westnet on 2023-01-23
Thank you for your quick response mlk3_08.
I tried the apt search command you suggested.
The response was
 "Sorting. . . Done
Full Text Search. . . Done"
then return to the prompt.  Apparently nothing found..
I still need help.

---

### Post by monkeybrain20122 on 2023-01-23
Is digikam a snap?

---

### Post by ajgreeny on 2023-01-23
And what are these packages or files that digikam needs for it to run?

---

### Post by mIk3_08 on 2023-01-23
> **colliers-barci-westnet said:**
> 
 "Sorting. . . Done
Full Text Search. . . Done"
then return to the prompt.  Apparently nothing found..
I still need help.
As what ajgreeny says what are you trying to look for? Regards and cheers.
> **ajgreeny said:**
> And what are these packages or files that digital needs for it to run?

---

### Post by neilbacon on 2023-03-26
The problem is that Ubuntu installs digikam as a snap package, which runs in a sandbox that can only access parts of the system configured by the package creator. A nice security measure and a pain in the butt. Digikam needs to be able to kick off external tools like hugin, gimp & darktable, but the snap package won't let it do this. A snap expert might be able to make it work somehow, but for the rest of us, we're just left cursing snap.

---

