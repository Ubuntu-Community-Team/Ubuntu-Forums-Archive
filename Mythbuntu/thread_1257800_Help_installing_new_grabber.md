---
title: "Help installing new grabber"
date: 2009-09-04
forum: Mythbuntu
---

### Post by KriZo on 2009-09-04
I have some trouble with the DK grabber that was already in mythbuntu. So therefore I wanted another, I have then downloaded the other grabber that i wanted, but running tv_find_grabbers it doesn't find my new grabber, which I have installed in /usr/bin. The new grabber is written in python.

How do I get mythtv to use the new grabber?

---

### Post by joshoekstra on 2009-09-04
I moved the old grabber to bla.old then symlinked the new grabber to the old name.
make it executable:
chmod ugo+x bla.new

This is with tv_grab_nl_py which also is a python grabber
Maybe your grabber has it's own help page?

---

### Post by KriZo on 2009-09-04
> **joshoekstra said:**
> I moved the old grabber to bla.old then symlinked the new grabber to the old name.
make it executable:
chmod ugo+x bla.new

This is with tv_grab_nl_py which also is a python grabber
Maybe your grabber has it's own help page?


My grabber has a help page, but I havn't been able to use it for much. My main problem is that mythtv can't find the grabber. 
I'm not really sure what it is you want me to do, could you make a quick step by step?

---

### Post by joshoekstra on 2009-09-04
Well it depends on the new grabber, but mine has an compat option to use the configfile and settings of the previous grabber(not supported any more in XMLTV) which made configuration in mythtv easier.
In short:
use the help option of your grabber, you are probably better of using a --configure option of your grabber and then later on use mythfilldatabase via cron to grab data.

You might even want to split it into the grabber writing data to an xml-file and then a couple of hours later or in the same job let mythfilldatabase use that xml-data to get guide-info.

I can only help you partially because I don't know the grabber concerned and I used the ln -s method to let mythtv use it, but I configured it with the old grabber.

---

### Post by SiHa on 2009-09-05
Now I'm not 100%, but IIRC there is a problem with MythTV setup, where it doesn't wait long enough to populate the list of grabbers, so if there's lots, some get missed off. I think the fix is to remove the ones you don't want so that setup can find the one you do.

Now, as I say, I'm not 100% on this, so probably best to just move them, rather than delete!

---

