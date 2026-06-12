---
title: "Rebuilding and activating kernels problem"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by mym2f on 2011-10-06
Hi there .....

I have used my ath9k_htc drive very well on a gnome VM image of linux with a kernel 2.6.39.4, but I needed more disk space and it seems like expanding it does not work on the VM image.

I have downloaded an iso image of the same linux OS (kernel 2.6.39.4) and the disk space was solved but I can't get my drive to work as on the previous OS !!!

When I run (make) for compat-wireless the following appears :

/root/Desktop/compat-wireless-2011-08-27/config.mk:213: "WARNING:
CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was
compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig
will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make -C /lib/modules/2.6.39.4/build M=/root/Desktop/compat-wireless-2011-08-27
modules
make: *** /lib/modules/2.6.39.4/build: No such file or directory.  Stop.
make: *** [modules] Error 2

I have searched the forum and Terminal said that he solved it but didn't mention how !!!

I have reinstalled linux-headers-2.6.39.4 build-essential but nothing changed

Please respond as soon as possible

---

### Post by AskTell on 2011-10-06
[http://ubuntuforums.org/showthread.php?t=1598930&page=4](http://ubuntuforums.org/showthread.php?t=1598930&page=4)

found a similar problem in above thread

> "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working  because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext  interface like iwconfig will not work. To activate it build your kernel  e.g. with CONFIG_LIBIPW=m."

---

### Post by mym2f on 2011-10-06
Thanks for your reply AskTell ......

However, I have tried the solution mentioned in the that thread to the letter and it does not work with me ...:(

I have also tried that with my newer compat-wireless package and the error still appearing it the same manner preventing me to run (make) command ...

(I wounder what modules are and how to install them for my kernel).:confused:

---

### Post by mym2f on 2011-10-06
I have solved the problem by entering (/usr/src/linux) and creating a link to it (Link to linux)

Then I renamed the link to (build) and move it to (/lib/modules/2.6.39.4/)

Now (make) command works just fine :)

I hope this thread will help other people as it seems that the current BT5R1 Gnome 32-bit iso image has this defect which is easy to repair but may be difficult to detect .......

Thanks to Ubuntu Forums and AskTell :D

---

### Post by AskTell on 2011-10-07
all i did was use Google's wonderful search engine and some of your error ;)

---

