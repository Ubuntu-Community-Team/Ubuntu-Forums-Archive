---
title: "Firefox doesn't function properly when viewing a video on a website (e.g. YouTube)"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by EnergyEruption on 2010-02-14
Hello everyone,

          The problem I am experiencing on my laptop (HP Pavillion zv5000) which runs UbuntuStudio 9.10 (this problem also occurred with Ubuntu 9.10, before I upgraded to Ubuntu Studio) is that whenever I view a video on Firefox, be it YouTube, Metacafe, and generally any site where you can see online videos, the video glitches a lot, and after a few seconds Firefox grays out, and is not responsive, which means I either have to Kill Firefox. 
          I am running Firefox 3.5.7 with the Ubuntu Firefox modifications 0.8 pack added. In the preferences, on the content tab the Enable Java button is not ticked. The following is the list of plugins I have on Firefox:
 
              DivX Web Player 1.4.0.233 **Enabled**

              IcedTea Java Web browser plugin 1.6.1 **Disabled**

              Java plugin 1.6.0_15 **Disabled**

              Quicktime  plugin 7.2.0 (Totem 2.28.2)[B] Enabled
[/B]
              Shockwave flash 10.0 r42 **Enabled**

              VLC Multimedia plugin (compatible Totem 2.28.2)** Enabled**

              Windows media player plugin 10 (compatible; Totem) **Enabled**

Thanks in advance for your help girls and guys, hope I didn't tire you too much.

Alex

---

### Post by cchhrriiss121212 on 2010-02-16
Try disabling Compiz desktop effects. If it is still a problem, make sure you have the correct drivers installed for your graphics device.

---

### Post by Cabs21 on 2010-02-16
do you have flash installed?  Brother had same problem until he fixed his flash issue with a script I gave him.  Now everything works fine.  You using 64bit or 32bit ubuntu?

---

### Post by EnergyEruption on 2010-02-18
Hey guys and girls, 

       Sorry it took so long to reply, I was away from home for a couple of days.

      I disabled all of the Compiz Desktop effects via the Compiz Config Settings Manager, and the problem is still evident. I am using 32bit Ubuntu. I upgraded the Shockwave Flash to the latest 10.0 r45 version, and the problem still perists. Firefox doesn't gray out that often anymore, but the videos are still played "frame by frame".

     How do I find out what graphics card driver version I'm using? My graphics card is ATI Mobility Radeon 9000/9100.

     Thanks everyone,

     Alex

---

### Post by vaniderstine on 2010-02-19
I dont' know if it will help you, but on my system HP pavilion zv5000, my graphics worked better after running the System Testing test suite.  Before I ran it, I could not get 1200x800 on my lcd, nor could i get 1280x1024 on my external monitor.  Once I ran through the test suite those resolutions are availabe and work.

---

### Post by ssulaco on 2010-02-19
I would recommend uninstalling previous versions of flash then install latest version...read this
[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1)

also, try disabling Extensions,if you are using any.

---

### Post by cchhrriiss121212 on 2010-02-20
To disable compiz effects you should switch to metacity by right clicking on the icon and using the menu. Check your graphics driver by going into System>Admin>Hardware drivers.

---

### Post by EnergyEruption on 2010-02-20
Hey everyone,

         I tried everything you said, and now YouTube works fine, although some other video streaming websites still have the exact same problem. ssulaco, that was pretty useful, thanks a lot! cchhrriiss121212, was is this metacity thing? Do I download it from Synaptic? I disabled all the Compiz effects anyhow. Hardware Drivers doesn't show anything by the way, it only displays a software modem I don't even use. I remember I was trying to find out my graphics driver ages ago, and couldn't find it anywhere. 
        Thanks for your patience everyone!

Alex

---

### Post by cchhrriiss121212 on 2010-02-21
Metacity is the default window manager in Ubuntu, it is very plain and won't cause you any trouble with flash or anything else. Compiz is another window manager which can do very fancy things but occasionally causes problems with flash and other things like remote desktop.
If you have a compiz icon top right on the taskbar, you can switch to metacity by right clicking it and going to "select window manager".
I also have trouble with flash even when all compiz effects are disabled. I don't use it any more.

---

