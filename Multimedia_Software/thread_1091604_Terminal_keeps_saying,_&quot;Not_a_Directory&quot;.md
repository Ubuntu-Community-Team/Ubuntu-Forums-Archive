---
title: "Terminal keeps saying, &quot;Not a Directory&quot;........."
date: 2009-03-09
forum: Multimedia Software
---

### Post by wbee on 2009-03-09
Hello,

The operating system recognizes my tv tuner card but needs something else. Someone on this forum sent me the information I need,for which I thank him. But I can not make it "stick",which is,of course,my fault.

((Deep breath)) Here goes:

Type into terminal:

sudo lshw -C multimedia  
(enter password the card shows up)

Put into a text editor and copy:

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17

Then I saved it as saa7134,to my home folder. Is that the right place to save it?

((Edit)) Or should I have saved it to the file system,and if so,to which file therein?((Close edit)

Then enter:

sudo cp saa7134 /etc/modprobe.d/

******My question,what do I add after   .d/  above to get it to work?


my root is /root
my name is /wbee
my home is /home
file is saa7134  saved in /home

---------------

Thank you.

---

### Post by cariboo on 2009-03-09
You don't have to do anything:

```
sudo cp saa7134 /etc/modprobe.d/
```

means superuser do copy saa7134 to /etc/modprobe.d

to check if the file was copied correctly cd to /etc/modprobe.d

```
cd /etc/modprobe.d
``` 

then:

```
ls -l
```

then the result should look something like this:

```
jim@jack:~$ cd /etc/modprobe.d
jim@jack:/etc/modprobe.d$ ls -l
total 36
-rw-r--r-- 1 root root 2387 2009-03-09 10:18 alsa-base.conf
-rw-r--r-- 1 root root 1783 2009-03-09 10:25 blacklist.conf
-rw-r--r-- 1 root root  213 2009-03-09 10:25 blacklist-firewire.conf
-rw-r--r-- 1 root root  662 2009-03-09 10:25 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2009-03-09 10:18 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2009-03-09 13:18 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  838 2009-03-09 10:25 blacklist-watchdog.conf
-rw-r--r-- 1 root root   45 2009-03-05 05:59 dkms.conf
-rw-r--r-- 1 root root   16 2009-03-05 15:22 libpisock9.conf
-rw-r--r-- 1 root root   84 2009-02-13 13:32 **saa7134**
jim@jack:/etc/modprobe.d$
```

After you have made the change reboot.

Jim

---

### Post by lovinglinux on 2009-03-09
I think I have a similar card, since they both use saa7134.

Here is what I did to make it work:

In the terminal run:

```
sudo gedit /etc/modprobe.d/options

```

The command above will open the **/etc/modprobe.d/options** file. Then, 
add the following line at the end of the file and save it.

```
options saa7134 card=17
```

then run this command:

```
sudo modprobe saa7134 card=17
```

Then open TVTime and do a channel scan

I f this doesn't work, then you might need to add not only "card=17" in the /etc/modprobe.d/options, but also the turner number and alsa, like this:

```
options saa7134 card=**[COLOR="Red"]26[/COLOR]** tuner=[COLOR="Red"]**33**[/COLOR] alsa=1
```

Please note that the tuner number for you card will not be the one above.

---

### Post by lamadredelsapo on 2010-10-16
How do I check what's the number of my card and tuner?

---

### Post by lamadredelsapo on 2010-10-22
?????? No one nows?

---

