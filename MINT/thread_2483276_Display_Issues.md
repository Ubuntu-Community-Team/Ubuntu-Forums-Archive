---
title: "Display Issues"
date: 2023-01-25
forum: MINT
---

### Post by j-new on 2023-01-25
I installed Mint on a brand new build, the latest version as of this writing. 

I moved to a 43" television for my computer monitor, but when I booted  up with it for the first time I got the "out of memory" error message and the OS wouldn't load.  After searching for more info, it appears it has to do with the default  display settings which are unable to deal with the large monitor. 

My question is how do I set Mint so it can handle my new display?

---

### Post by ajgreeny on 2023-01-26
We need a lot more information to be able to help you properly so please run command ```
inxi -Fzx
```and show us the output that you see.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. 
See my signature below for a **How-to**

---

### Post by j-new on 2023-01-29
Problem solved. I adjusted the grub file to my resolution and updated. Works fine now. 


More info here: [https://ubuntuhandbook.org/index.php/2021/05/screen-resolution-grub-boot-menu-ubuntu/ ]("https://ubuntuhandbook.org/index.php/2021/05/screen-resolution-grub-boot-menu-ubuntu/")

---

### Post by mIk3_08 on 2023-01-30
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by j-new on 2023-01-30
Done. Thanks.

---

