---
title: "Huawei E220 3g modem + UbuSTU 8.10"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by paulera on 2009-01-28
I need to install and configure my Huawei modem in Ubuntu Studio 8.10 ](*,), and i do not have internet on that machine (posting from work, now).

First, I did not found the network item to configure my modem settings in Administration menu, in this distro. Where is it? :sad:

Second, i have only USB 1.0 ports :(, and this modem has a cable that allows to use 2 ports at the same time :o. It is automatic and works fine in Windows. How do I use this feature in Linux, instead of configuring my modem only at /dev/ttyUSB0 or only at /dev/ttyUSB1? :-k

Thanks a lot! \\:D/

(First post!!!)

---

### Post by nightmare0 on 2009-01-28
Hi there, congrats on your first post  :) have you tried looking up your modem model on the manufacturer's website to see if the modem is supported? And what model is it?

---

### Post by paulera on 2009-01-29
> **nightmare0 said:**
> Hi there, congrats on your first post  :) have you tried looking up your modem model on the manufacturer's website to see if the modem is supported? And what model is it?

Hi friends, thanks for your reply... My issue goes a little down under: I do not know where is the screen to configure any kind of connection (modem, wireless or lan)!

I tried to reinstall the OS, thinking that I could removed it accidentally, but this wasn't the problem.

---

### Post by nightmare0 on 2009-01-29
Ok, here's a link to an installer for what I would hope to be your model. [http://www.brothersoft.com/huawei-e220-rc-2-installer-for-linux-72997.html](http://www.brothersoft.com/huawei-e220-rc-2-installer-for-linux-72997.html) 
You should also see if you can google a GUI for your model that is your _exact_ model. 
Let me know if you need additional assistance!
(the install instructions are towards the bottom of the download page)

---

### Post by royston on 2009-01-31
I have a same problem with my Huawei 220 I have downloaded this file    [http://www.brothersoft.com/huawei-e2...nux-72997.html](http://www.brothersoft.com/huawei-e2...nux-72997.html) 
my problem now is where  in the Ubuntu  system would  you put this file ..?

---

### Post by Rhubarb on 2009-01-31
While I don't have a Huawei E220 3G modem, I do have a Huawei E160 3G modem.
And it works very well in Ubuntu 8.10.

System --> Preferences --> Network Configuration
Click on the "Mobile Broadband" tab
Press the Add button, and follow the prompts.
That's all you have to do really.


If your service provider isn't there, then things could be a bit more tricky for you;

3G modems are usually picked up essentially as high speed dial up modems.
So with a bit of playing around with pon / KPPP it's possible to get it working that way.
- But really, if you can, use the network configuration manager, it's much easier to use.

If that doesn't work, I'm afraid you may have to do more searching on net for a solution.

Best of luck.

---

### Post by nightmare0 on 2009-01-31
> **royston said:**
> I have a same problem with my Huawei 220 I have downloaded this file    [http://www.brothersoft.com/huawei-e2...nux-72997.html](http://www.brothersoft.com/huawei-e2...nux-72997.html) 
my problem now is where  in the Ubuntu  system would  you put this file ..?

You have to open the Terminal and do a 'make' install file on that download page in the comments it has an explanation of how to do the make install.

---

