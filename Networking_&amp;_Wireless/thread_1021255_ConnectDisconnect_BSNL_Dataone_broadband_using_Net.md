---
title: "Connect/Disconnect BSNL Dataone broadband using Network Manager in Taskbar"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by shan23 on 2008-12-25
Hi,

I'm a ubuntu user for over a year...I had previously used Gutsy and switched to Hardy 3 months back...In both, i had been able to configure my PC so that i could connect/disconnect to BSNL Dataone by selecting an option from the network manager. Unfortunately, i had uninstalled the GNOME Network Manager by mistake, and when i reinstalled it, my settings were lost !

I'm able to configure my braodband connection (using pppoeconfig ), but now i have to switch it on/off from the terminal ( using pon and poff) ... I want to be able to switch it on/off from the network manager itself, as i had been doing previously ( for the life of me, i couldnt figure out what i did back then :) )

Any users who have a similar setup ( connecting to dataone without using the terminal) , please help !!

---

### Post by labinnsw on 2008-12-25
Try this update [http://ubuntuforums.org/showthread.php?t=797059]("http://ubuntuforums.org/showthread.php?t=797059"). It worked for my 3 GSM connection.

---

### Post by dineshs on 2008-12-25
You can also install gpppon.

---

### Post by shan23 on 2008-12-27
Thanks for the prompt replies. Thing is, i installed the network manager 0.7 as instructed , but after i rebooted, the network manager icon is simply GONE from the taskbar ( the area at top right besides the date menu) !! I dont know what to do...instead of the drop down menu i was used to, i now have to access it form System->Preferences->Network Connections . Is there any way to get back the network manager to display on the taskbar (as shown in the snapshots at [http://www.darrenalbers.net/blog/?p=9](http://www.darrenalbers.net/blog/?p=9) ) 

I'm really hoping for a fix, as i have to repeated;y switch between LANs at college. :)

---

### Post by labinnsw on 2008-12-28
Go Systems>>Preferences>>Network Configuration
Right click on Network Configuration and select add this launcher to panel
Then drag and drop it in the notification panel

---

### Post by shan23 on 2008-12-28
Thanks for ur suggestions, but i tried doing that. All i could manage was getting to add it to the panel on top, and not in the area besides the date and volume menu. :( I hope i'm not sounding stupid, but even if i've added it to the panel, i'm not getting a drop down menu as shown in this sceenshot
[http://www.darrenalbers.com/images/menu.gif](http://www.darrenalbers.com/images/menu.gif). 

Currently, all i'm getting when i click on Network Connections is something like this [http://www.darrenalbers.com/images/Wired.gif](http://www.darrenalbers.com/images/Wired.gif)

I know i'm sounding like a noob, but i would really appreciate it if u could clarify what i'm doing wrong, in order to get to the drop-down menu.

Much obliged for the quick responses...I've never been to a more active forum !! :)

---

### Post by labinnsw on 2008-12-28
Looks like you might need to reinstall GNOME PPP (From Synaptic)
See if that works.

In my case, I actually installed GOME PPP and later did the network manager update. Not sure if doing it in reverse order will have any effect on the result. (I did not suggest this earlier because I thought it was already done)

---

### Post by shan23 on 2008-12-29
Thanks. I've installed GNOME-ppp , but i cant test it right away, because i only get a DSL pppoe connection at home on weekends :) Will check if it works this weekend...

---

### Post by isami777 on 2010-02-05
Hi Shan,

I am too encountering the same problem. My Network Manager from the System Tray is gone after I used "pppoeconf" utility.

Thanks in advance to let me know how to bring back the same in the System Tray.

Regards,
Sam

---

