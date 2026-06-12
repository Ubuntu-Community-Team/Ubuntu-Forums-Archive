---
title: "Can't read packing lists"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Briguy9 on 2011-04-20
After requesting => sudo apt-get update
I get this error message=>
...
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 13.3 MB in 50s (261 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by plucky on 2011-04-21
> **Briguy9 said:**
> After requesting => sudo apt-get update
I get this error message=>
...
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 13.3 MB in 50s (261 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

You could try removing the list with ```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
``` then run ```
sudo apt-get update
``` so it has to download the list again.

Good Luck

---

### Post by Briguy9 on 2011-04-21
Here's what happened ->

brian@brian-Mr:~$ sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
rm: cannot remove `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en': No such file or directory

Happy Easter!

---

### Post by drs305 on 2011-04-21
You can open Synaptic (gksu synaptic): Settings > Repositories. Untick the Universe selection, then reselect it. That should refresh the entry if there was a problem with it and 'Reload' should work.

If it doesn't 'Reload', check the 'Other Software' tab and see if you have another entry for universe which is in the incorrect format.

If it still isn't working, post /etc/apt/sources.list and also take a look in /etc/apt/sources.list.d for any other files which may contain an erroneous entry.

---

### Post by Briguy9 on 2011-04-21
Thanks for your help BTW!!

  	 	 	 	 	 	  When I try to open Synaptic, get this rut-ro:
 

 An error occurred 
  The following details are provided:
 E: Encountered a section with no Package: header 
 E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fUS 
 E: The package lists or status file could not be parsed or opened. 
 E: _cache->open() failed, please report.

---

### Post by drs305 on 2011-04-21
How about trying to move the offending file. It uses a wild card but we aren't deleting, only moving:
```
sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main* /root/Desktop/
sudo apt-get update

```

If the command runs without error but your system still won't update, try changing servers in Synaptic. If it still doesn't work, I suspect you have something in your /etc/apt/sources.list file or /etc/apt/sources.list.d folder which is creating the problem.

---

### Post by Briguy9 on 2011-04-22
When I ran sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main* /root/Desktop/


 this error => mv: target `/root/Desktop/' is not a directory

---

### Post by drs305 on 2011-04-22
> **Briguy9 said:**
> When I ran sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main* /root/Desktop/


 this error => mv: target `/root/Desktop/' is not a directory

The target is not important as long as you know where you put it. I am not sure why you don't have a /root/Desktop/ folder, but you can move it anywhere you wish.

---

