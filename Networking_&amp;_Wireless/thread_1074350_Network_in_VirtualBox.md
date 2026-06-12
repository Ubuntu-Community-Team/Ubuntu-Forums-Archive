---
title: "Network in VirtualBox"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by andsmi on 2009-02-19
Hi there!
I've just installed Windows 7 in VirtualBox in Ubuntu Intrepid. My problem is that Windows 7 does not recognize any wireless network card. I've tried to change the network settings in "network" in VirtualBox but it doesn't seem to work. Is there some settings I need to change or is it just that I need a driver for Windows 7? If it's because a driver problem, where can I download drivers for windows 7? My wireless network card is; Intel 4965AGN wireless.

Thanks!;)

---

### Post by yoyoned on 2009-02-19
Virtual machines will not directly access the wireless card.  If you want to get windows 7 on the net, let you ubuntu box connect via wifi and let the VM connect via NAT which is the default behaviour for virtualbox

---

### Post by andsmi on 2009-02-19
Thanks, but I still can't get any internett connections... Is there something special I need to do in Windows 7? or is it something I need to do through my ubuntu?

---

### Post by konqueror7 on 2009-02-19
use static ip inside you guest os, just copy all the information on your dhcp settings (ip, subnet, default gateway), now create a static ip config with all those details, except that your dns servers are the from your host/main os...

---

### Post by andsmi on 2009-02-19
ok. And where can I get all the information on my dhcp settings? I used to get that information trough terminal, but I can't remember how.

---

### Post by konqueror7 on 2009-02-19
in xp (windows), right click on your network trayicon and select 'Properties' or 
```
ipconfig /all
```

---

### Post by andsmi on 2009-02-19
And how do I create a static ip config?

thanks for your help! :)

---

### Post by konqueror7 on 2009-02-19
its windows 7 right? if i remember correctly (i also installed windows 7 in vbox), go to Control Panel > Network Connections...now, right click your connection and select 'Properties'(there should be one named the same as set it in the 'Network' tab in vbox, ex. PCnet-PCI II)...now there is a checkbox list, select the IPv4 and press the 'Properties' button, now a dialog will show, input it there...

---

### Post by andsmi on 2009-02-19
Its Windows 7 yes. It says "open network and sharing center" when I right click on my connection. I can't find (thats named the same as set in the "Network" tab in vbox)in Windows 7's network and sharing center. And I can't find the checkbox list.
Am I looking at the right place? :p

---

### Post by konqueror7 on 2009-02-19
i think in the sidepane of the 'network and sharing center', there is a link saying something 'Manage network connections', there... here's a similar [view]("http://www.bcpl.net/help/vista/vistaguide7.jpg")

---

### Post by andsmi on 2009-02-19
[[IMG]http://img11.imageshack.us/img11/439/99962278hm9.th.png[/IMG]](http://img11.imageshack.us/my.php?image=99962278hm9.png) This is how mine looks like... :S

---

### Post by konqueror7 on 2009-02-19
> **andsmi said:**
> [[IMG]http://img11.imageshack.us/img11/439/99962278hm9.th.png[/IMG]](http://img11.imageshack.us/my.php?image=99962278hm9.png) This is how mine looks like... :S

go to 'Adapter Settings'

---

### Post by andsmi on 2009-02-19
And that is absolutely blank. There is nothing there, it opens a new window; [[IMG]http://img22.imageshack.us/img22/5485/w7networkyt6.th.png[/IMG]](http://img22.imageshack.us/my.php?image=w7networkyt6.png)

---

### Post by konqueror7 on 2009-02-19
lol, its getting harder by every post:D

how did configure your network in vbox? did you set to 'NAT'?

---

### Post by konqueror7 on 2009-02-19
here's a guide i googled, [here]("http://forums.virtualbox.org/viewtopic.php?t=2430&highlight=network+proxy")

---

### Post by andsmi on 2009-02-19
Yup. It's set to nat. But I can choose either PCnet-FAST III or PCnet-PCI II.
[[IMG]http://img8.imageshack.us/img8/9026/natoh1.th.png[/IMG]](http://img8.imageshack.us/my.php?image=natoh1.png)

---

### Post by konqueror7 on 2009-02-19
seems strange...have you read the guide?

mmm...inside the 'Adapter Settings' is there a link 'Network Connections'?

too bad i deleted my windows 7 last week...:(

---

### Post by konqueror7 on 2009-02-19
i think i found the [solution]("http://twoguystech.com/blog/art/installing-windows-7-beta-suns-virtualbox")...

just follow the last part of the guide, mount guest additions, explore device manager (My Computer, then right click 'Properties', and 'Device Manager'), manually update the drivers of the two unrecognised devices via exploring it to the location of the guest addition...

(my windows 7 vm was actually running on winxp, maybe thats why i got less trouble)

(hopefully this will work on you, i'll sleep now, i'll check back tomorrow again) :)

---

### Post by andsmi on 2009-02-19
Got it working!:D That last link was all I needed! thanks alot! have a nice sleep;)

---

### Post by konqueror7 on 2009-02-19
glad it worked...:D

---

