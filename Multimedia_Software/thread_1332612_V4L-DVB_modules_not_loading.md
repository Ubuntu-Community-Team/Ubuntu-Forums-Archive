---
title: "V4L-DVB modules not loading"
date: 2009-11-20
forum: Multimedia Software
---

### Post by Cardcaptor Stacey on 2009-11-20
Don't know where else to get help for this. :(

I followed this very helpful tutorial perfectly: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) but it hasn't quite worked.

I've built the module okay. It installed correctly and copied the files into /lib/modules/2.6.31-14-generic/kernel/drivers/media/dvb/dvb-usb. After that I rebooted (since it was easier for me). Then I got to the "If the Modules load correctly" section to find that nothing has worked at all.

I've checked my system log and it's recognising the USB device when I enter it but it isn't doing anything with it. The tutorial says you should be able to see the modules in /proc/modules but the modules folder doesn't even exist. The /dev/dvb/ folder has not been created either.

---

### Post by wkulecz on 2009-12-31
Bummer, I was searching to find the answer to basically the same question, no answer in over a month :(

I was expecting to find the drivers in synaptic, but searching v4l-dvb ot V4L-DVB comes up empty.

--wally.

---

### Post by jimmers on 2009-12-31
What device are you using???
Please give enough information so that we can help you more effectively

---

