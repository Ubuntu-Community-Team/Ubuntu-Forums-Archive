---
title: "How to fix the &quot;/var/log/jockey.log&quot; wifi driver problem"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by Marinozai on 2010-10-26
If you get this message when you try to install the Broadcom wifi driver on your Apple computer, this is for you:
> Sorry, installation of this driver failed.
      Please have a look at the log file for details:/var/log/jockey.log

This happened for me and it was bugging me for days! 

First of all, I have an iMac with a Core 2 Duo processor (2.8 GHz), 2GB RAM, and I don't think this matters, but a 500GB HDD. I installed Ubuntu Maverick Meerkat 10.10 and used rEFIt as my bootloader. 

I was connected to my airport through ethernet, but wifi did not work. Whenever I tried to install the driver by going to System>Administration>Additional Drivers, I would get the error message, "Sorry, installation of this driver failed.
       Please have a look at the log file for details:/var/log/jockey.log" and though I browsed through different forum posts for hours, nothing worked, even the ones with a hundred follow-up posts from people for whom it worked.

I had all the stuff, - I had the wifi card, I had the option to install the driver, I just couldn't install it!

This may be one of those many things you tried while trying to fix this problem, but hopefully this will be the one that works for you:


[LIST=1]
[*]Go to System>Administration>>Synaptic Package Manager and in the search bar, type "bcm".
[*]Make sure "broadcom-sta-common" and "broadcom-sta-source" are installed. If not, mark them for installation, close, and reload.
[*]Make sure  "bcmwl-kernel-source" and "bcmwl-modaliases" are installed. If not install, reload, and then go back and mark them for reinstallation. Then reload.
[*]Restart your computer. It won't tell you that you need to restart, but it is necessary nonetheless.
[*]After you have restarted, click on the network icon at the top and click on "Connect to Hidden Wireless Network..."
[*]Enjoy your wifi connection...hopefully.
[/LIST]

---

### Post by pookito on 2011-05-23
What would happened if bcmwl-modaliases is no where to be found in synaptic?  And when you try to downloaded from the site, ubuntu software says that if I install it it might brake some packages?  

What would you do then?  cause that is what is happening to me.

---

### Post by Peter7K on 2011-05-25
Hello.  I have a Dell Precision M4400 which I have just upgraded for my aunt and I have the same problem, the "bcmwl-modaliases" is not in synaptic!

---

### Post by sam034 on 2012-03-11
If nothing else works try this [http://wiki.debian.org/wl](http://wiki.debian.org/wl) it worked just fine for me.

---

### Post by Admac on 2012-03-28
i had the same problem, I'm running 11.10 and wireless was working properly till the other day and it wasnt possible to see any network.for me it turned out the driver was hard blocked see this link it helped me [http://ubuntuforums.org/showthread.php?t=1745681](http://ubuntuforums.org/showthread.php?t=1745681)

but to cut a long story short i tuped this "sudo rfkill unblock all" into the terminal and straight away i had my wireless again. good luck
sudo rfkill unblock all

---

### Post by Admac on 2012-03-28
dont worry about bcmwl-modaliases being in synaptic i am using a dell laptop with the broadcom sta wireless driver and i also dont have bcmwl-modaliases in synaptic i guess you dont need it because my wireless works without it, infact it sent me on a wild goose chase for a while trying to figure out how to get it when not having it wasnt even a problem :-)

---

### Post by uRock on 2012-03-28
Necromancy

Thread Closed

---

