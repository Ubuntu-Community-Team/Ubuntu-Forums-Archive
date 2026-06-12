---
title: "installing adobe flash"
date: 2009-08-07
forum: Multimedia Software
---

### Post by On Boards on 2009-08-07
i tried to uninstall adobe flash player again (broken package)

in synaptic manger i get this 
```

E: adobe-flashplugin: cannot remove `/.'

```then in terminal


 ```


 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 44 files and directories currently installed.)
Removing adobe-flashplugin ...
dpkg: error processing adobe-flashplugin (--remove):
 cannot remove `/.': Invalid argument
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
are there any pobssible way to make it work ? thanks

---

### Post by Metaljaz on 2009-08-07
Does the following work from the terminal window:

sudo apt-get remove adobe-flashplugin

sudo apt-get --purge remove adobe-flashplugin

---

