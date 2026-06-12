---
title: "help with compiling driver"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by abnobuntu on 2010-03-30
Hi guys.. i'm trying to compile the driver for my wireless adapter but am running into some trouble..  the source came with a Makefile... and the readme file indicate that i just need to run 'make' to start the compile.  However, when i ran the make command, i'm getting the following error message:

> 
8188_8191_8192SU_usb_linux_v2.6.0006.20100226$ make -f Makefile 

make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-3-686/build M=/home/hywong/downloads/rtl8191SU_usb_linux_v2.6.0006.20100226/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-3-686'
/home/hywong/downloads/rtl8191SU_usb_linux_v2.6.0006.20100226/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/Makefile:11: /usr/src/linux-headers-2.6.32-3-common/config: No such file or directory
make[4]: *** No rule to make target `/usr/src/linux-headers-2.6.32-3-common/config'.  Stop.
make[3]: *** [_module_/home/hywong/downloads/rtl8191SU_usb_linux_v2.6.0006.20100226/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-3-686'
make: *** [modules] Error 2


now, i did noticed that there is a 'config' file in the source directory that i'm compiliing in.  i'm suspecting that's the file it's looking for.. but why in the world would it be looking for it in the linux header directory instead?  am i doing something wrong?  do i need the extract the source in some specific directory before i can compile the driver??   any help would be greatly great as i'm not sure how to procceed from here.

thanks in advance!!

---

### Post by chili555 on 2010-03-30
Are *build-essential* and *linux-headers-generic* installed on your system? Do things improve if you start with:```
sudo su
make
```

---

### Post by abnobuntu on 2010-03-30
i have build essential and linux header installed.. i tried compiling with root.. but endedup with the same error message.

---

### Post by chili555 on 2010-03-30
May I have a link to the file you downloaded?

---

### Post by abnobuntu on 2010-03-30
here you go...

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)


Thanks for in advance!

---

### Post by chili555 on 2010-03-30
It built perfectly for me with no errors or warnings.

I'm confused:> No rule to make target `/usr/src/linux-headers-2.6.32-3-[COLOR="Red"]common[/COLOR]> Leaving directory `/usr/src/linux-headers-2.6.32-3-[COLOR="Red"]686[/COLOR]'Is it possible that your headers version does not match your running kernel version? I checked in Ubuntu package search and did not find a '-common.'

---

### Post by abnobuntu on 2010-03-30
i'm actually running crunchbang 10..  i ran 'uname -r' to get the linux kernel version and just apt-get the linux-header for the version..  is that the wrong way to go about this?  sorry if i'm asking something silly.. kinda new to this..


> 
hywong@crunch:~$ uname -r
2.6.32-3-686
hywong@crunch:~$ apt-cache search headers-2.6.32-3-686
linux-headers-2.6.32-3-686 - Header files for Linux 2.6.32-3-686
linux-headers-2.6.32-3-686-bigmem - Header files for Linux 2.6.32-3-686-bigmem
hywong@crunch:~$ sudo apt-get install linux-headers-2.6.32-3-686


---

### Post by chili555 on 2010-03-30
I know nothing about crunchbang, except it sounds painful. The Ubuntu way is exactly as I described: linux-headers-generic. If that doesn't help, I'm not sure I can offer anything further.

---

### Post by guysoft on 2010-06-07
Same problem here, with that same driver, but on Debian.

---

