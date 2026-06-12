---
title: "bcm43xx-fwcutter and Broadcom"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by Dr Von Bon Bon on 2006-06-05
Hi,

I have a broadcom wireless card, I'm not sure of the exact make, built into my laptop and have been following a guide about how to get wireless to work using bcm43xx-fwcutter.

The problem is my sudo apt-get cannot find it.

I can't believe that this would only happen to me so it must be a problem with my computer but all other sudo-apt get appears to work fine.

Could anyone help me please or give me another way to get wireless working?

Many thanks.

---

### Post by Slicedbread on 2006-06-05
You need to add the extra repositories. Go to synaptic package manager and go to settings>repositories and enable all of them, click ok then click the reload button.

---

### Post by Dr Von Bon Bon on 2006-06-05
I've done that but it still isn't finding this file.

What other options are there do you think?

---

### Post by Patsoe on 2006-06-05
[http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter)
You can download the package from there, dependencies should not be a problem with this one.

---

### Post by mbobak on 2006-06-05
Try:

sudo apt-get update

and then:
sudo apt-get install bcm43xx-fwcutter

-Mark

---

### Post by Dr Von Bon Bon on 2006-06-06
I've tried installing it straight from the package as updating didn't work but now this message comes up. I also tried to install all of the dependancies that it says it needs.

```
god@Callum:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
fwcutter can cut the firmware out of /home/god/Desktop/wl_apsta.o
  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
/lib/firmware/bcm43xx_microcode2.fw: No such file or directory
god@Callum:~$ sudo apt-get install debconf
Reading package lists... Done
Building dependency tree... Done
debconf is already the newest version.
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies:
  libc6: Depends: locales (>= 2.3.11)
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12.5.10.1) but 2.3.6-0ubuntu20 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.5-1ubuntu12.5.10.1) but 2.3.6-0ubuntu20 is to be installed
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).
god@Callum:~$
god@Callum:~$ sudo apt-get install 2.3.6-0ubuntu20
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 2.3.6-0ubuntu20

```

Any help please?


Thanks.

---

### Post by Patsoe on 2006-06-06
I'm a bit confused - what version of Ubuntu are you running? (you labeled the thread  "Ubuntu 6.06", but your details say 5.10?)

---

### Post by Dr Von Bon Bon on 2006-06-06
How do I check what version of Ubuntu I'm running?

---

### Post by Patsoe on 2006-06-06
I guess the quickest way is to go to the menu item System > About Ubuntu.

---

### Post by Dr Von Bon Bon on 2006-06-06
It appears to 5.10


How would I upgrade then to 6.06 please?

That could be why the file isn't being found.

Would I lose any of my files?

---

### Post by Patsoe on 2006-06-06
Yes, that would be most likely the problem - when I said there would be no dependency problems, I was assuming (because the thread is labeled 6.06) that you are running Dapper. The fwcutter-deb that I linked to is meant for Dapper.

You can upgrade following this guide: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) 
- but I must add I haven't tried that out. Can you afford to "play" with the install?

---

### Post by slakkie on 2006-06-06
[QUOTE=Patsoe]Yes, that would be most likely the problem - when I said there would be no dependency problems, I was assuming (because the thread is labeled 6.06) that you are running Dapper. The fwcutter-deb that I linked to is meant for Dapper.

You can upgrade following this guide: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) 
- but I must add I haven't tried that out. Can you afford to "play" with the install?[/QUOTE]

I did it via the Update Manager, and a co-worker did as well. Both machines came back without a problem. I would advise to use the Update Manager, its pretty foolproof.. Take appropiate actions before hand, you could always get into problems..

---

