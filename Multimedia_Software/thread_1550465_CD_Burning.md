---
title: "CD Burning"
date: 2010-08-11
forum: Multimedia Software
---

### Post by nicknefarious on 2010-08-11
To anyone who can help,

I have had for a number of Ubuntu releases now a problem in trying to burn disks CD's, DVD's etc. of all flavours. The problem is I CAN'T.

I have read various posts about this and there seem to be many different solutions floating around out there but none of them seem to have helped my situation, and it doesn't seem to be getting fixed.

I have tried various different burning programs but they all fail.

I have attached a log from Brasero after a failed write.

Maybe someone can interpret this for me and tell me how to fix it, or what the exact problem is and that it can't be fixed now but someone is working on it.

As always... any help, guidance or info is GREATLY APPRECIATED.

Thanks,

Nick

---

### Post by nicknefarious on 2010-08-14
Anyone got any ideas?

Thanks,

Nick

---

### Post by cchhrriiss121212 on 2010-08-14
Seems to be similar to [this old bug]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076"). The solution on there seems to be to install cdrecord in place of wodim.

---

### Post by sidzen on 2010-08-14
At the Terminal or console:
[PHP]sudo apt-get update[/PHP][PHP]sudo apt-get check[/PHP][PHP]sudo apt-get purge brasero[/PHP][PHP]sudo apt-get build-dep k3b && sudo apt-get install -f k3b[/PHP][PHP]sudo apt-get autoremove[/PHP] Reboot with [PHP]init 6[/PHP]login and burn

---

### Post by nicknefarious on 2010-08-14
thanks for your replies guys. cchhrriiss121212 - From what I've read there seems to be a problem with totally removing it (wodim) due to dependencies though which I do not know. I have read that there is some workaround that involves a bit of fudging but ends up with wodim and cdrecord installed side-by-side.

sidzen - appreciate your suggestion and am going to try it. Can you explain a bit further why though.

Sorry to be a why person but I hate blindly ploughing through terminal commands installing this uninstalling that...

Cheers for the help,

Nick

---

### Post by nicknefarious on 2010-12-23
For anyone who is interested... none of the solutions here removed any of my problems. I have also moved on to Ubuntu Maverick and both Brasero and k3b again fail in many and varied ways to burn CD's or DVD's and I have been unable to find any useful help in the Ubuntu forums or elsewhere about this. 

I have been able to find many frustrated users disappointed with the fact that the Ubuntu community seems unable or unwilling to help them and that these issues have existed for such a long time and no-one has fixed them.

I did have minimal success burning one DVD with GnomeBaker. But this again failed on the second attempt. 

Ironic thing is most of the problems I have had have been while trying to burn new releases of Ubuntu onto disks to share Ubuntu with friends. They have been impressed by the OS that I can't even use to burn an install disk to CD or DVD...

As you can imagine they were blown away (by nothing) as I was unable to give them Ubuntu...

---

