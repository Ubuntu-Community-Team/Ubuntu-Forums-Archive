---
title: "No GUI after video driver upgrade"
date: 2009-01-06
forum: Multimedia Software
---

### Post by RickSmith on 2009-01-06
I attempted to install the ATI update and now my Xubuntu will only boot into text mode. GUI not working. Warning when gnome starting says cant find video. I found some info on here and tried it it did not work. What is the proceedure for activating the genaric vidio drive from the Xubantu install. I guess it amounts, to what is the driver name.

---

### Post by ubuntu-freak on 2009-01-06
Reboot into recovery mode and use the "xfix" command.

---

### Post by RickSmith on 2009-01-06
Ok tried the xfix. Still not going into GUI. Iget the splash screen then it goes into text mode. prints kinit: no resume image, doing normal reboot then it prints Xubuntu 8.10 Patriot(this is the name of my computer} tty1
Patriot login. I log in and the promt is ricky@patriot:~$. Hopefully this shows you were its taking me. Anouther question. If I have to reinstall. can I skip the reformat and not reload grub, just xubuntu. will it screw up the boot loader.

---

### Post by ubuntu-freak on 2009-01-06
> **RickSmith said:**
> Ok tried the xfix. Still not going into GUI. Iget the splash screen then it goes into text mode. prints kinit: no resume image, doing normal reboot then it prints Xubuntu 8.10 Patriot(this is the name of my computer} tty1
Patriot login. I log in and the promt is ricky@patriot:~$. Hopefully this shows you were its taking me. Anouther question. If I have to reinstall. can I skip the reformat and not reload grub, just xubuntu. will it screw up the boot loader.

 
Have you tried booting with another kernel? I presume you have at least two installed. I always have two, just incase some bug comes along. 
 
I'm not sure what you mean regarding your grub and reformatting etc.

---

### Post by RickSmith on 2009-01-06
No only one linux kernal. I am running a duel boot system with XP as the other OS. As far as the reinstall. the Xubuntu install will format and partition your drive if you don't tell it not to. You can also install or not install GRUB. My question was if I don't reformat the drive and don't reinstall Grub, just reinstalling Xubantu will it still boot with the exising Grub?

---

### Post by ubuntu-freak on 2009-01-06
> **RickSmith said:**
> No only one linux kernal. I am running a duel boot system with XP as the other OS. As far as the reinstall. the Xubuntu install will format and partition your drive if you don't tell it not to. You can also install or not install GRUB. My question was if I don't reformat the drive and don't reinstall Grub, just reinstalling Xubantu will it still boot with the exising Grub?

 
Why don't you want to install Grub again? There's been a kernel update since Intrepid was released (which is why I'm surprised you only have one kernel), so it's best to install Grub. It will detect XP and add a menu entry. And yeah, if you want to reinstall, just select the manual method and use the same root partition as your installation path.

---

