---
title: "internet connection sharing between ubuntu and windows 7"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by izzie86 on 2011-02-09
Hi :)

I am completely new to linux/ubuntu and I'm having trouble connecting to the internet, I think it might be that my wireless pci card either isn't compatible or I don't have a driver for it. I have a pc using win 7 (which I'm using for the internet) and a pc running win vista and ubuntu (which is the one which I can't get to connect.

I don't have any spare cash to buy a new wireless pci card and I've used an ethernet cable (no idea whether it's regular or crossover or how to know the difference :s!!) to link the two computers, is there any way I can get the ubuntu/vista pc to use the internet connection of my windows 7 computer?

I'd really love to use ubuntu exclusively, but without the internet I'm not going to be able to :(

Please help

Thanks
Izzie

---

### Post by YesWeCan on 2011-02-09
[http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing](http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing)

I have not tried this myself, but I know it can be done.

If I understand you, you have a Win7 PC that connects to the internet by wireless card. You have another PC with Ubuntu that has no wireless. So you are trying to connect the Ubuntu PC directly to the Win7 PC using an ethernet cable?

Ok. It is possible provided at least one of the ethernet cards can automatically do the "cross-over". Some can and some cannot. If neither can then you will either need a cross-over cable or an ethernet switch or router and another cable (a switch or a router will handle the cross-over automatically).

You then need to configure the Win7 PC to share its internet connection (see link above). Ubuntu *should* automatically detect the connection once the ethernet connection is made.

So try it out and if it doesn't work come back and get help with diagnosing the problem.

---

