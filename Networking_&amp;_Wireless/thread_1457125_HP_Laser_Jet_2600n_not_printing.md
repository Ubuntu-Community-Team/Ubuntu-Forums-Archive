---
title: "HP Laser Jet 2600n not printing"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by srikris on 2010-04-18
Dear members,
I have installed ubuntu 9.10. I installed drivers for Hp laserjet 2600n which is in network following these steps.

$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar zxf foo2zjs.tar.gz
$ cd foo2zjs
$ make
$ ./getweb 2600n
# make install[FONT=monospace]
[/FONT]# make cups# [system-config-printer]("http://foo2hp.rkkda.com/fedora/")

It went on well. When i tried to print pdf file with odd pages it didnt work 
and when i gave current page it worked. 
After printing 3 such pages, i manually reversed the pages for other side printing, it didnt work.

It shows in the queue pending, processing and completed without any printout.

I gave test print later it worked perfectly.

I couldnt get where the problem cud be and What shud i do to make it work properly?
Thanx in advance 
Sri

---

### Post by wilee-nilee on 2010-04-18
Did you try the printer add in system-administration first rather then down loading drivers.

I have an older HP laserjet 4mplus, the drivers for the 4mplus don't work but the 4m do.

---

### Post by srikris on 2010-04-18
I didnt do that.
What do u suggest me to do now?
How can i proceed?

---

### Post by wilee-nilee on 2010-04-18
> **srikris said:**
> I didnt do that.
What do u suggest me to do now?
How can i proceed?

I am not certain on your course of action with driver you loaded it is hard to tell what it is. the 2nd link shows a 7.10/fedora driver. It may be that this driver works but something needs to be changed.

I would go to printing in system-admin hit add printer with your printer plugged in and a driver if available will show it should be one which names the printer accept it and try to print a page.

Now when I do this like I said earlier the driver that works for my old hp is the same in name without the m at the end. 

If when you open printing you see the the driver you originally loaded displayed as a little printer icon that is okay for the moment I would leave it in until you get the printer working.

So if the driver, Ubuntu finds for you doesn't work, open the printing program again and double click on the added Ubuntu printer. Then click change on the make and model line this will bring up a screen that will show manufacturers names click on that and look for your printer and or variations of it. This window of manufacturers and device is where I found that there was a very close in name printer, only missing the letter at the end.

In the end you will want to go to this printers setup before downloading drivers in the future, it is a learning process but after you do it a few times you will know what to do.

---

### Post by srikris on 2010-04-19
I tried printing again with odd sheets selected but it printed only one page (out of 3) and stopped printing. Later even if i give current page its doing anything....

I did as u mentioned.
System->Admin-> printing->double clicked on the printer icon (already existing)-> make and model change->chosen HP->colorjet 2600n->enabled the new settings.

Its working randomly for some pages... couldnt get possible reason.

Sri

---

### Post by wilee-nilee on 2010-04-19
> **srikris said:**
> I tried printing again with odd sheets selected but it printed only one page (out of 3) and stopped printing. Later even if i give current page its doing anything....

I did as u mentioned.
System->Admin-> printing->double clicked on the printer icon (already existing)-> make and model change->chosen HP->colorjet 2600n->enabled the new settings.

Its working randomly for some pages... couldnt get possible reason.

Sri

I think I would try and install a new driver by hitting add printer, also I would look far and try 2600 if there is one.

Adding or changing the downloaded driver is probably not a good idea, but I could be wrong. Since you have worked with the printer setup, you are now initiated, so you could also just remove the one there hit add printer and try to load a fresh driver.

So I have found some more information.
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)
This confirms that the printer can work and has some reference info.

---

### Post by srikris on 2010-04-21
but the link doent have hp laserjet 2600n corresponding to ubuntu 9.10 karmic koala!!!!!!!

---

