---
title: "Freecom DVB-T USB-Stick with Lucid"
date: 2010-04-20
forum: Multimedia Software
---

### Post by xadm on 2010-04-20
Hi,

Did anyone try to use the Freecom DVB-T USB-Stick in Lucid (10.04)? It seems that the kernel still does not have a driver included for this DVB-T USB-Stick. So I tried to compile a driver (also found here at ubuntuforums.org) that was modified (based on a driver for hardy, written by the community) for intrepid (8.10), but as expected, compiling failed.

So does anyone have an idea how to make the Freecom DVB-T Stick useable in Lucid or did anyone already solve this problem?

Thanks a lot!

---

### Post by jbrice on 2010-04-28
Yes, it looks as if the Freecom DVB stick firmware is no longer in Lucid in its present version. However Ryan Lothian is your man here - this works for me:
[http://ryan.nfshost.com/projects/linux/freecom-dvb-t-stick](http://ryan.nfshost.com/projects/linux/freecom-dvb-t-stick)

Also - in case you choose to use this player - there seem to be some demux stuff missing from Kaffeine for Lucid which is solved by doing:
```
sudo apt-get install kaffeine libxine1 libxine1-all-plugins phonon-backend-xine
```
(See also:
[https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/563803](https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/563803) etc.)

Pity, as it's easily fixed if you are Linux person but a real show-stopper if you are a refugee from Windows-land!

PS - I also see that an option to load DVB card hardware drivers appears (in System/Administration/Hardware Drivers) when the DVB card is plugged into the PC.

---

### Post by xadm on 2010-05-04
Thanks for reply, but unfortunately this does not work for me. I followed the instructions, but when I plugged my DVB-T stick in, the light did not turn orange. So I even restarted  my computer, but it did not change anything.

With Intrepid when the Stick worked with a driver modified by the community, the light was green when the stick was active. So it seems that there are different versions (with different chipsets?) of Freecom's DVB-T usb-stick...

But I don't know which version I have - how can I find it out?

If you need more information please let me know, I'll try to provide them.

---

### Post by ianc on 2010-05-04
Yes - there is more than more version. They are described here:

[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#WideView.2FYakumo.2FHama.2FTyphoon.2FYuan_Boxes_and_Pens](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#WideView.2FYakumo.2FHama.2FTyphoon.2FYuan_Boxes_and_Pens)

From memory, to get mine working (in Karmic) *all* (it took a while to find it!) I had to do was track down a copy of the correct file & put it into /lib/firmware.

---

### Post by Shabba on 2010-05-04
The above guide posted by jbrice also works with the ultra cheap ezcap DVB-T stick. All I had to do was alter the kernel revision and it now works like a charm (except for the remote that is).

Just thought I'd add this comment for the search engine to help others with the same stick as me.

---

### Post by jbrice on 2010-05-06
xadm,
Looks as if you now have some information from people who know more about the subject than I do. 
Did you try the procedure in the PS at the end of may last post above (i.e. try System/Administration/Hardware Drivers) I think that should find the correct driver irrespective of the chipset in your DVB stick, if that driver is included with with the distro.

Yes, you are right about the LED on the DVB stick - with mine it comes on yellow when the driver is loaded, and then green when tuned to a broadcast multiplex.

---

### Post by xadm on 2010-05-07
I followed the links to linuxtv.org and there i read (or remembered) that I have the rev4 of Freecom's DVB-T usb-stick, and it is still listed under the unsupported devices. I followed the link and tried [http://www.linuxtv.org/wiki/index.php/Realtek_RTL2831U](http://www.linuxtv.org/wiki/index.php/Realtek_RTL2831U) - but however errors occurred while compiling, so it did not work.

I also tried System --> Administration --> Hardware drivers, but the system didn't find any available drivers, so it seems that the driver is not shipped with ubuntu lucid.

---

### Post by xadm on 2010-05-09
In an other thread on ubuntuforums.org, I found the solution:

[http://ubuntuforums.org/showpost.php?p=9258544&postcount=58](http://ubuntuforums.org/showpost.php?p=9258544&postcount=58)

For my rev4 stick it works fine :-)

Thanks a lot to all of you helping me to find the solution! :-)

---

