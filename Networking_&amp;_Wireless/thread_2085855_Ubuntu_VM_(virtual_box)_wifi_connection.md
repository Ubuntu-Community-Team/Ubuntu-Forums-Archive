---
title: "Ubuntu VM (virtual box) wifi connection"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by hajdui on 2012-11-19
Hi! All!

I installed Ubuntu as a virtual machine (virtual box). The host mechine connects to a wired LAN that is independent from the WIFI network. May the VM connect to WIFI and if it is possible how can I do that?

Regards,
Imre

---

### Post by pkadeel on 2012-11-19
> **hajdui said:**
> Hi! All!

I installed Ubuntu as a virtual machine (virtual box). The host mechine connects to a wired LAN that is independent from the WIFI network. May the VM connect to WIFI and if it is possible how can I do that?

Regards,
Imre
If the wifi card on host connects via USB then you can do that by enabling USB support in Vbox settings

---

### Post by coldraven on 2012-11-19
If you download the **VirtualBox 4.2.4 Oracle VM VirtualBox Extension Pack **and sit puzzling how to install it, just double click it!
You probably also have to add yourself to the "vboxusers" group in Ubuntus "Users and Groups" settings although I believe that has changed in the latest version. Try Googling it.

Edit: Oops! The above applies if Ubuntu is the host

---

### Post by hajdui on 2012-11-19
WIFI card is built in the notebook. 

Under host machine I meant the machine where the VM server is running. Sorry for the wrong composition.

---

### Post by pkadeel on 2012-11-19
> **hajdui said:**
> WIFI card is built in the notebook. 

Under host machine I meant the machine where the VM server is running. Sorry for the wrong composition.
If you want to use wifi adapter for checking the wifi adapter's compatibility on the guest OS then I am sorry, as per my info you will not be able to do that because guest OS can see only the hardware which is exposed to it by the Vbox. WiFi is not in that list.
 
In case you only want to access internet but just don't want to use the wired connection on the guest instead want to utilize the wifi then you can use the bridged adapter feature on the virtual machine network settings and set it to use the wifi adapter on the host. For your reference an image of that setting is attached. In this situation, the guest OS will still consider it a wired connection but on host the traffic will go to the wifi.

---

### Post by hajdui on 2012-11-19
> **pkadeel said:**
> If you want to use wifi adapter for checking the wifi adapter's compatibility on the guest OS then I am sorry, as per my info you will not be able to do that because guest OS can see only the hardware which is exposed to it by the Vbox. WiFi is not in that list.
 
In case you only want to access internet but just don't want to use the wired connection on the guest instead want to utilize the wifi then you can use the bridged adapter feature on the virtual machine network settings and set it to use the wifi adapter on the host. For your reference an image of that setting is attached. In this situation, the guest OS will still consider it a wired connection but on host the traffic will go to the wifi.

If I understand well I have to connect to 2 network on the real machine. I use the wired network for work and I would like to seperate from the wireless network. How can I ignore the wireless for the real machine and enable to the VM?

---

### Post by pkadeel on 2012-11-20
Yes you will connect to both networks simultaneously on your host machine. As your guest machine is configured via bridge setup in Vbox, it will only be able to access internet via wifi so no further setting is required there. As for the host, you need further setting to ensure that the applications on host machine prefer wired connection over the wifi. There can be multiple solutions depending on the host OS and may be even at router level which I am not aware of right now.

By default I think all OSs prefer to use wired connection over a wifi so if both are connected, your host shall prefer wired for its internet connectivity but to be sure that it does, the simplest method on windows is to make wired the preferred connection. The method is described on the following link.

[http://www.howtogeek.com/117083/how-to-make-your-laptop-choose-a-wired-connection-instead-of-wireless/](http://www.howtogeek.com/117083/how-to-make-your-laptop-choose-a-wired-connection-instead-of-wireless/)

I assumed that your host OS is windows but if I was wrong then there is an application which can do the job but you might need to install on your linux. It is named wicd. It is present in the ubuntu repositories and you can read more about it on internet.

---

### Post by hajdui on 2012-11-26
You thought well I use windows. I checked the options you were right the OS prefer the wired conncection as default. 
Thank you for the help! 

Regards,
Hajdui

---

