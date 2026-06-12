---
title: "WUSB54g V4 -- I have to use ndiswrapper to get it to work"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by willz06jw on 2010-06-01
Hi,

I have a Linksys WUSB54G V4 wireless adapter and the only way it will successfully connect to the internet in through ndiswrapper.  It *says *that it connects to the router, but it doesn't connect to the web.  I have tried all types of static settings.  With ndiswrapper it works perfectly.

Any ideas?
Will

---

### Post by leofenix on 2010-06-02
I have the same device WUSB54G external wifi. Using Lucid I can connect to my router, I can use the web but only for a while, after a period of time it gets disconnected and the only way to re-connect is to disable networking and enable it again and sometimes I have to reboot. With ndiswrapper this disconnection problem can be solved? Is there any other workaround?

---

### Post by willz06jw on 2010-06-02
With ndiswrapper all problems are solved with this adapter.   Let me know if you need help setting it up.  In theory you shouldn't have to use it; it should work out of the box.

---

### Post by leofenix on 2010-06-10
I have downloaded and installed the ndiswrapper package and rebooted the machine. The problem persist, after a while I got disconnected. I should do something else, change some configuration? Please, let me know if you can help me out to configure the device. Thanks!

---

### Post by willz06jw on 2010-06-10
Use the "Using Windows Drivers" part of this official help file: [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

Note: Remember to open the .exe you download from Linksys with the Archive Manager

Let me know if you have any questions.

Will

---

### Post by leofenix on 2010-06-17
[COLOR=Black][]("http://ubuntuforums.org/member.php?u=143294")[/COLOR]I followed willz06jw's instructions and now is working fine without any disconnection or packets lost. Thanks for the help!

---

### Post by cantormath on 2010-09-25
I installed the linux-fireware-nonfree package.  After that the hardware was recognized after boot.

---

### Post by Fernando Negro on 2011-12-29
There's no need to use "ndiswrapper" and follow all those complicated instructions.

You can easily solve the problem, simply by [switching to a different kernel]("http://ubuntuforums.org/showthread.php?p=11572146#post11572146").

---

