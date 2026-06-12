---
title: "cant install/run java"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by 565Customz on 2008-03-31
bash: alisas: command not found
slider@ButT3R:~$ sudo apt-get install -f
[sudo] password for slider:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
slider@ButT3R:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin



so how do i get to the bin....?

ps is there a way to completely reinstall ubuntu without losing all my stuff? i have a /home partition on my drive and i think thats where eveything is supposed to get saved...im not real sure.

---

### Post by ubuntu27 on 2008-04-01
Try the following command:

```
sudo apt-get update && apt-get dist-upgrade
```


```
sudo apt-get install ubuntu-restricted-extras
```

---

