---
title: "messed up iwlagn with modprobe command - how to undo?"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by eskararriba on 2012-04-10
I'm having trouble with the intel centrino n-1000 card, as wifi-connection is terribly slow. while trying to fix this, I messed something up in the kernel, I guess, and now the wifi-function seems to have gone completely. even if you don't know how to fix the bug with the wifi-card, I'd be glad to at least get back to where I was before I tried to repair this....


following [this thread]("http://ubuntuforums.org/showpost.php?p=11425909&postcount=2"), the commands I ran are: 

> 
echo "options iwlagn lln_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn

as wireless disappeared completely, I tried 
> sudo update-initramfs -u
sudo modprobe -r iwlagn && sudo modprobe iwlagn

without any success. the output I get now is: 


> ...@miles:~$ sudo modprobe -v iwlagn
insmod /lib/modules/3.0.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko lln_disable=1
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

...@miles:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic

...@miles:~$ sudo modprobe -r iwlagn && sudo modprobe iwlagn
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)


well ... what do I do now? thanks a lot for your help!

---

### Post by ridetheteapot on 2012-04-10
in a terminal : sudo nano /etc/modprobe.d/iwlagn.conf

change those "l"'s to ones. (El's aka L's) i dunno what font you use but sometimes its really hard to see the difference.


___EDIT
hey i see what your doing, and I can just guess why. my laptop is using a bleeding edge kernel and my wireless N (i'm also using the iwlwifi driver) goes from working to f'd up like every other update! so crazy! (have been following the bug, and it seems like some people's HW is working on some updates, but others aren't --- then they switch it up and boom same thing but visevera)

---

### Post by kevdog on 2012-04-10
Couple of things:

options iwlagn lln_disable=1

should be  iwlagn 11n_disable=1

Second, if you are really in a jam, just remove the /etc/modprobe.d/iwlagn.conf file.  What going on here is that /etc/modprode.d is just a folder the modprobe utility looks at whenever modprobe is executed.  Within this modprobe.d folder you can put the name of files that would be executed with specific modprobe commands.

For example with,
sudo modprobe iwlagn
The modprobe utility would look in /etc/modprobe.d for a folder named iwlagn.conf.  If it finds the folders it would pass the options listed in this folder to the kernel driver its trying to load.  Specifically in this case it would try to set the 11_disable Flag to 1 or TRUE so 11n would be disabled. If no iwlagn.conf file exists, than the module would be loaded with the default options the developer set in the kernel module code itself.

---

### Post by praseodym on 2012-04-10
Just like this:

```
sudo rm /etc/modprobe.d/iwlagn.conf
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe iwlagn
```

---

### Post by ridetheteapot on 2012-04-10
all i have to say to the two of you is :P

some reason this isn't the same thing?
> in a terminal : sudo nano /etc/modprobe.d/iwlagn.conf

change those "l"'s to ones. (El's aka L's) i dunno what font you use but sometimes its really hard to see the difference.

but to kevdog - i think he's trying to disable wireless N because iwlagn aka iwlwifi (as it's part of in newer kernels) because it doesn't work :P

---

### Post by eskararriba on 2012-04-10
all of you, thanks a lot!
the error was indeed the "l"/"1"-confusion, with this being fixed I could disable wireless N, and for now, I've got a working internet connection (5MB instead of 200Kb, which makes quite a difference). 
hope this bug will be fixed with the new distro... 
cheers all, 
eska

---

