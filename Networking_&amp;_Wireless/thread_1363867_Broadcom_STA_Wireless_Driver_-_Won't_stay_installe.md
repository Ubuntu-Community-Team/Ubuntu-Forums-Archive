---
title: "Broadcom STA Wireless Driver - Won't stay installed"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by rarach on 2009-12-25
Hello,

After many hours of sifting through posts on here regarding the 9.10 vs the broadcom sta wireless driver I was finally able to get the driver installed and working. The problem I am having now is that after each restart I need to input the last two parts from broadcom's read me file for the driver installation because it seems the driver doesn't stay fully installed. I have figured out that the minimal information that needs to be put into the terminal after restarting is:

# cd hybrid_wl
# modprobe lib80211
# insmod wl.ko

After putting this into the terminal my wireless connections will show up and I will have access to them. I am glad I have figured out a work around to getting my internet working on 9.10, but I am wondering a few things. Is it harmful to enter this into the terminal each time I'm booting up my computer? If entering this is the only way I can get my internet working each time, would it be alright to make a script file (I think that's what it is..) that will automatically run each time I boot up?

Thanks for your time! :)

---

### Post by Ayuthia on 2009-12-25
You can try the following:
```
sudo mkdir /lib/modules/$(uname -r)/kernel/hybrid
sudo cp hybrid_wl/wl.ko /lib/modules/$(uname -r)/kernel/hybrid
sudo depmod -a
echo wl | sudo tee -a /etc/modules
```
This will place the wl.ko module into the current kernel's modules library.  It will then update the module list dependencies file.  The last part will add the wl module to the list to load automatically when booting.

Hopefully that will fix it for you.

By the way, it does not hurt anything to enter the commands in the Terminal every time and it is also fine to create a script to do it.  All it is doing is loading the modules manually.

---

### Post by rarach on 2009-12-25
That did the trick! Thank you very much for your help and speedy reply! :)

---

### Post by rarach on 2010-05-01
Hello,

I am having another problem with my wireless internet. The previous advice has been working since I last posted, but now since I have done an ubuntu updates thing and no longer can get the previous work around to work. The error message I get in the terminal is:

insmod: error inserting 'wl.ko': -1 invalid module format

I have no idea what this means, and now I do not have internet. Also, I do not have a wired option at this time. 

Thanks in advance!

---

