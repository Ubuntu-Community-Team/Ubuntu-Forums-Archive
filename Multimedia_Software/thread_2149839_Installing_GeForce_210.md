---
title: "Installing GeForce 210"
date: 2013-05-30
forum: Multimedia Software
---

### Post by Falthon on 2013-05-30
My video card died, and I installed an EVGA GeForce 210 to replace it.  When I turned the computer on, however, it booted to a command prompt instead of loading the GUI.  How can I install the driver for the new card? 

I'm running Ubuntu 10.10.  I appreciate any help you can provide.

---

### Post by ajgreeny on 2013-05-30
What was your previous graphic card, and did its driver automatically give you an /etc/X11/xorg.conf file?
Let's see the output of ```
cat /etc/X11/xorg.conf
``` from your cli login, and if there is output from a file, simply delete it with ```
sudo rm /etc/X11/xorg.conf
``` That may be all that is needed to get you a GUI after a reboot, but if not come back again and we can try to help you more.

---

### Post by Falthon on 2013-05-30
Here's the output from cat /etc/X11/xorg.conf. 

Section &#8220;Screen&#8221; 
         Identifier       &#8220;Default Screen&#8221; 
         DefaultDepth     24 
EndSection 

Section &#8220;Module&#8221; 
        Load      &#8220;glx&#8221;
EndSection 

Section &#8220;Device&#8221; 
              Identifier      &#8220;Default Device&#8221; 
              Driver     &#8220;fglrx&#8221; 
EndSection 

I deleted xorg.conf (after making a backup copy) and rebooted.  That did get me a GUI, but it was severely distorted, to the point of being completely unusable.  I could barely manipulate the mouse well enough to shut down the computer. 

I shut down and rebooted again, and ended up with a normal GUI.  It seems to be working fine now. 

Thanks very much for the advice.

---

### Post by ajgreeny on 2013-05-30
Your old graphic card was an ATI/AMD using fglrx which totally scuppered your new nvidia card.  Removing the xorg.conf means you are now using the open source nvidia driver, obviously with success.  You may get even better performance if you look in Additional-drivers and install anything that is offered in that.

---

### Post by Falthon on 2013-06-02
I went to Additional Drivers and attempted to activate the Nvidia driver, but received the following message. 

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_amd64.deb) 404  Not Found 

I receive a similar message when I attempt to use Update Manager.  I don't know if this is because Ubuntu 10.10 is no longer supported.  I'm planning to upgrade to a newer version; I'll try again once I've done so.

---

### Post by ajgreeny on 2013-06-02
Yes, 10.10 has lost support, so no more updates nor are the repos at the same URLs.

---

