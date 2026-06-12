---
title: "How to scan direct on Gimp"
date: 2019-05-07
forum: Multimedia Software
---

### Post by satimis on 2019-05-07
Ubuntu 18.04
Gimp 2.10
XSane version 0.999
Flatbed scanner - Epson Perfection 3490 (an old scanner but still working)
Media to work - old film negatives


Hi all,

My old scanner is still working on VueScan/DigiKam/Xsane without problem.  Now I expect adding scan function to Gimp.  

I found following old document;
How to aquire scanner images in GIMP using xsane in Jaunty (November 25th, 2009)
[https://ubuntuforums.org/showthread.php?t=1337039](https://ubuntuforums.org/showthread.php?t=1337039)

It is a 10 years old document.  I wonder whether it'll work for me here?

Please advise whether there is a newer document for me to follow?

Thanks

Regards
satimis

---

### Post by Holger_Gehrke on 2019-05-07
I don't think you'll need to do anything. I didn't and there's an item 'XSane' under 'File' -> 'Create' in my GiMP 2.8 (installed from the repos on XUbuntu 18.04). The only situation where things could get ... interesting ... is if you installed the newer Gimp you're using from a snap.

Holge

---

### Post by satimis on 2019-05-07
> **Holger_Gehrke said:**
> I don't think you'll need to do anything. I didn't and there's an item 'XSane' under 'File' -> 'Create' in my GiMP 2.8 (installed from the repos on XUbuntu 18.04). The only situation where things could get ... interesting ... is if you installed the newer Gimp you're using from a snap.

Hi Holge,

Thanks for your advice.

On menu
-> File
Info
Quit

only 2 items there

On Viewer
-> File
Save Image
OCR - save as text
Clone
Close

I couldn't find the item -  'Create'

Besides, XSane can't detect the scanner occasionally. I have to rebooting Ubuntu 18.04 and switching off/on the scanner simultaneously before XSane can find the scanner.

Remark:
Both Gimp and XSane are running

Regards
satimis

---

### Post by Claus7 on 2019-05-08
Hello,

> **Holger_Gehrke said:**
> I don't think you'll need to do anything. I didn't and there's an item 'XSane' under 'File' -> 'Create' in my GiMP 2.8 (installed from the repos on XUbuntu 18.04). The only situation where things could get ... interesting ... is if you installed the newer Gimp you're using from a snap.

Holge

ditto for ubuntu 19.04, yet gimp version 2.10.

Regards!

---

### Post by satimis on 2019-05-08
> **Claus7 said:**
> Hello,

ditto for ubuntu 19.04, yet gimp version 2.10.

Regards!
Hi,

It is very strange here.

On Gimp 2.10

File -> Create
(3 items there)```

From Clipboard
From Webpage ....
Screenshot .....

```

But XSane is not there.  I wonder whether I need adding additional software?

Regards
satimis

---

### Post by Holger_Gehrke on 2019-05-08
Check the output of 'snap list' in a terminal. If it lists gimp, then you installed gimp as a snap. snap-packages are restricted in what they can access in the system, so a gimp snap might not see or call xsane, even though it is installed and available. In that case the simplest solution would be to remove the gimp snap and install the version available in deb-packages through apt, unless you need whatever is new in 2.10. There may be a way to integrate gimp in a snap with xsane, but since I only use snap for programs that are not available otherwise somebody else would have to provide that.

Holger

---

