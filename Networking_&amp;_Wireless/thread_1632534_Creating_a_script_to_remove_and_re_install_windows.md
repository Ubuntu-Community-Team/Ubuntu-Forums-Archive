---
title: "Creating a script to remove and re install windows driver"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by darrenbrown507 on 2010-11-28
Hi guys, I am looking for a little help.  I am running 10.10 on a Samsung n130.  Occasionally my wifi adapter locks up, everything looks like it is connected but I cannot connect to the web.  I have worked out that removing and re-installing the windows driver brings it back to life (a restart also works). What I was wondering is could it be possible to create a script that would carry out the removal and installation of the driver with one click of a button.

Many thanks

---

### Post by mikewhatever on 2010-11-28
Have you tried reloading ndiswrapper instead?

```
sudo modprobe -r ndiswrapper && sudo modprobe ndiswrapper
```

If you really need to reinstall the driver, then a script is just a text file with commands and the executable bit.

```
#!/bin/bash

command1

command2

etc
```

---

### Post by darrenbrown507 on 2010-11-28
Thanks for that.  I have created an executable file for enabling and disabling the ndiswrapper.  I will see if that works next time I get the problem.  Is there a way to work out the commands used for removing and re installing the driver?

Thanks

---

### Post by mikewhatever on 2010-11-28
'To workout the commands?' They are the same commands you use to do it, no magic here, that is, unless someone else does it for you.

---

