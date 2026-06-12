---
title: "N00b here - NVidia Twin View"
date: 2009-01-30
forum: Multimedia Software
---

### Post by dbansal1 on 2009-01-30
Hello,

I am trying to enable my second monitor. I am using Ubuntu 8.10. I see the Nvida X Server Settings console through System >> Administration.

Now it shows my other monitor as disabled.

Now I click on configure for my disabled monitor.

Subsequently, I choose separate X screen and click on apply.

Then, I choose save to x configuration file to /etc/X11/xorg.conf.

When I do that I get a message saying: 

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

Can somebody please help!

THANKS!!!

---

### Post by overdrank on 2009-01-30
Hi and welcome, you may try the command with the alt, F2 keys and enter ```
gksu nvidia-settings
``` this will allow you to save your settings.

---

### Post by dbansal1 on 2009-01-31
So I was able to get the configuration file to save with your command. However, my second monitor just looks horrible. It has this red hue over it. I don't understand where it is coming from. I have checked my connections twice now.

Please help!

Thank you!!!!!!!!!!!!!!!!!

---

