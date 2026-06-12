---
title: "[SOLVED] Dual Monitor Resolutions"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by myst1c on 2007-12-25
so i have 2 monitors, one 17" and one 19", and they're both hooked up to my system... i'm trying to set up an extended desktop, which i have done, but no matter what combinations of resolutions i try at least one of the desktops pans... does anybody know how to remedy this?

---

### Post by myst1c on 2007-12-26
bump...

anyone one at all?

---

### Post by myst1c on 2007-12-27
please? somebody? anybody? it's important that i get this fixed

---

### Post by chewearn on 2007-12-27
What video card do you have?

---

### Post by myst1c on 2007-12-27
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2148789&CatId=319](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2148789&CatId=319)

that one

---

### Post by chewearn on 2007-12-27
Ok, you have nvidia graphics.  Let me start off by asking basic questions, since I'm do not know about your experiences using ubuntu or linux.

1. Have you installed nvidia restricted driver (via ubuntu repositories), or latest driver from nvidia website?
2. What do you use to set-up the resolution?

---

### Post by myst1c on 2007-12-27
1. yes i have, and i am using it now
2. the screen and graphics tool in ubuntu

---

### Post by chewearn on 2007-12-27
1. Have you try using nvidia-settings (run the command in terminal).

2. Can you post your xorg.conf?

---

### Post by myst1c on 2007-12-28
thanks for your help, i was able to configure my dual monitors properly using nvidia-settings, but now i have another problem... i'm not able to move windows from one monitor to another... how do i go about doing this?

---

### Post by chewearn on 2007-12-28
> **myst1c said:**
> thanks for your help, i was able to configure my dual monitors properly using nvidia-settings, but now i have another problem... i'm not able to move windows from one monitor to another... how do i go about doing this?

When you cannot move window from one screen to another, you have set-up the graphics as "separate X screens".  There are some advantages to this set-up, but if moving windows from one screen to another is important, you should use "twinview" set-up instead.

---

### Post by myst1c on 2007-12-28
again, thank you for your help, i am now properly running dual monitors, and it's very nice having a bigger workspace!

---

### Post by chewearn on 2007-12-28
No problem glad to be of help.  If your issue is resolved please mark this thread as solved (in thread tools drop down).

---

