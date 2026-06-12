---
title: "Vista MCE Remote .10"
date: 2007-12-26
forum: Mythbuntu
---

### Post by tj71587 on 2007-12-26
I used the preloaded configuration and while it is functional, the buttons dont work perfectly.  Does anyone have a .conf file that works perfect and tell me where it goes, or does anyone know where the conf file is located and can give me a quick explanation on how to program it?

---

### Post by foxbuntu on 2007-12-26
> **tj71587 said:**
> I used the preloaded configuration and while it is functional, the buttons dont work perfectly.  Does anyone have a .conf file that works perfect and tell me where it goes, or does anyone know where the conf file is located and can give me a quick explanation on how to program it?

There are two pertinent files you need know about however:

/etc/lirc/lircd.conf (Do not change this)
~/.lircrc

You can edit the second following the format. Basically you take the button name from the first and add it to the function in the second.

However as the maintainer of the mythbuntu-lircrc-generator, please provide more details to what is or is not working on your remote. I am in the middle of a upgrade to this application and need good user input to help me along.

Thanks!

---

### Post by tj71587 on 2007-12-26
I dont see the second file there.  There is no .lircrc in there.  The numbers work well, however the volume and channel up and down dont work.  Pause doesnt work either and the rewind and fast forward buttons skip to the beginning and end.  Stop or record do not work either.  Here is the remote.  [http://www.pcconnection.com/ProductDetail?sku=8129757&oext=1038A&ci_src=14110944&ci_sku=8129757](http://www.pcconnection.com/ProductDetail?sku=8129757&oext=1038A&ci_src=14110944&ci_sku=8129757)

Also, once I click one of the colored buttons on top, the remote stops working until I unplug or reboot.  

Thanks for the help.

---

