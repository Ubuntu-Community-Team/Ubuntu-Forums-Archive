---
title: "Youtube colours all wrong."
date: 2012-09-10
forum: Multimedia Software
---

### Post by jpaulb on 2012-09-10
I have a Dell Xubunt 12.04 XPS 8300, Nvidia GForce  8500GT, Dell U2312HM resolution (1920x1080). NVidia 295.49 drivers, Flash 11.2.202.238
Pictures or videos from any source other than Youtube are correct. from Youtube colours are falsch, sky is orange brown, red taillights are incandescent blue.

This does not happen if I dual boot into windoze 7 or on my wifes' IBM T61 laptop running Ubuntu 12.04.

I tried to remove the NVidia drivers; could not get Ubuntu to recognize my monitor, highest resolution was way below 1920x1080

Anyone else having this issue????

**Edit** **Installed X.Org X server -- Nouveau display driver Have a usable display again. Youtube colours are real again.  So is this a Bug or an undocumented feature with the NVidia drivers**

---

### Post by jpaulb on 2012-10-09
looks like I am the only one that used youtube;)

---

### Post by Merrattic on 2012-10-10
The reason no-one responded is that this is such a common problem with probably thousands of posts about it, that most folks will feel a little bit of searching on your part would have turned up a solution for you, which it did. Seems the problem is a combination of nvidia drivers and flash under linux.

---

### Post by jpaulb on 2012-10-10
I did get a response, eh :grin:

FYI
Here is the answer I received from Nvidia
> Hi Paul, 

Your issue was just referred to me.

This issue has been reported to Engineering and investigated. The problem is not an NVIDIA driver problem, but is instead an Adobe Flash application problem, which has been reported to Adobe. 

Let me know if any more questions.

Best regards,

Mike
NVIDIA Customer Care

---

### Post by GeForce 9500GT on 2012-10-10
[See if this solution helps you]("http://ubuntuforums.org/showthread.php?t=2060539").

---

### Post by jpaulb on 2012-10-10
> **GeForce 9500GT said:**
> [See if this solution helps you]("http://ubuntuforums.org/showthread.php?t=2060539").

I reinstalled Nvidia 295.49 followed instructions Voila it works, the blue men are gone

Thank you:D

---

