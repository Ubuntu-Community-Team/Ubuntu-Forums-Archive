---
title: "Startup"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by thep8ntballfreak on 2009-01-18
when i start my computer i have to open up a terminal and type the following

sudo modprobe -r b43
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

how do i make the computer automatically do this on every startup
im new to the whole linux thing and do not know much about the OS yet. what i do know is that you have to make everything work yourself.

---

### Post by doas777 on 2009-01-18
ok, create a document, and name it whatever you like.

the first line of the gfile should be
 ```
#! /bin/bash
```

this is called a "bangline" and is the first step for any script.

then add the your commands below you bangline. save your file whereever you like.
```

#! /bin/bash
sudo modprobe -r b43
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```

then Rclick on the file and go to permissions. check the box giving the owner (you) execute permissions.

now go to System -> Preferences -> Sessions. click Add.
```

Name: wifi driver load
Command: <path to script file>
comment: Kewl! now I can get online!

```

reboot and test.

if it gives you any trouble, try switching 'sudo' out for 'gksu' since your now loading it through the gui shell.

thats all there is to it.
good luck,
franklin

---

### Post by Ayuthia on 2009-01-18
Another way to do it so that you don't have to enter the sudo password every time you start it:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b43legacy ssb wl; modprobe --ignore-install ndiswrapper' | sudo tee -a /etc/modprobe.d/ndiswrapper
```
/etc/modprobe.d/ndiswrapper is a file that contains instructions on what the ndiswrapper module needs to do when certain commands are applied to it.  In this case, when ndiswrapper is loaded, it must remove the b43, b43legacy, ssb, and wl modules before it loads ndiswrapper.  

Since the loading of the ndiswrapper module occurs before you log in, you don't need to add the sudo command.  This command also gets called when you do sudo modprobe ndiswrapper.

You should also make sure that ndiswrapper has been added to /etc/modules:
```
cat /etc/modules|grep ndiswrapper
```
If ndiswrapper is not returned:
```
echo ndiswrapper | sudo tee -a /etc/modules
```will add it for you.

---

### Post by vanadium on 2009-01-18
You can also add the commands to /etc/rc.local (without sudo) to have them run automatically at boot time.

---

