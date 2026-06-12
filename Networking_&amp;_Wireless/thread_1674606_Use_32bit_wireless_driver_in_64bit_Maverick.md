---
title: "Use 32bit wireless driver in 64bit Maverick?"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2011-01-24
Hi all,

Interesting one. I have been banging my head against a wall about this on and off since I got my Toshiba Satellite Pro L510 three months ago. Getting no-where. The wireless card signal strength swings between 50-100% and speed is woeful compared to Ubuntu and Windows installs on the other three machines in the house. So I eventually emailed Realtek to see if they could shed some light on the situation and here is there reply: 

> [FONT=Times New Roman][SIZE=2][COLOR=black]Could you please ... download the latest RTL8191SE Linux driver source from following URL again?[/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=black][http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)[/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=black]Description: Linux driver for kernel 2.6.X[/COLOR][/SIZE][/FONT]
  **[FONT=Times New Roman][SIZE=3][COLOR=black][B]This driver source only support PC-based x86 platform, not support embedded system.**[/COLOR][/SIZE][/FONT][/B]
  **[FONT=Times New Roman][SIZE=3][COLOR=black][B]Please refer to readme file within the package for installation and follow below steps.**[/COLOR][/SIZE][/FONT][/B]
  [FONT=Times New Roman][SIZE=2][COLOR=black]You should clear previous drive or inbox driver first after you install this driver source.[/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=black]The previous driver will be stored within /lib/modules/2.6.XXX/kernel/driver/staging.[/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=black]Please remove "r8192se_pci.ko" files by following command.[/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=black]1. sudo su (you should input you root password after it)[/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=black]2. find /lib/modules/ -name "r8192se_*.ko" -exec ls -l {} \; [/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=black]3. find /lib/modules/ -name "r8192se_*.ko" -exec rm {} \;[/COLOR][/SIZE][/FONT]
  
  [FONT=Times New Roman][SIZE=2][COLOR=black]After, You could execute "find /lib/modules/ -name "r8192se_*.ko" -exec ls -l {} \;" to confirm it&#8217;s clear properly.[/COLOR][/SIZE][/FONT]
This was all fine and killed my wireless, as expected.
[FONT=Times New Roman][SIZE=2][COLOR=black]
[/COLOR][/SIZE][/FONT]
> ... install this driver source as below steps. Don&#8217;t forget to extract this package before you install it.
  1. sudo su
  2. make
  3. make install
  4. rebootThis I'd done before but I couldn't get it to install again. Weird and TAKE NOTE: It only seems to work if you 'sudo su' and become root then perform the commands. It just wouldn't happen for me by just using 'sudo' before the commands, ie:

```
sudo make
sudo make install
```Persistently throws error two after the second command. Anyhow ...

My thinking is considering this:

> **[FONT=Times New Roman][SIZE=3][COLOR=black][B]This driver source only support PC-based x86 platform**[/COLOR][/SIZE][/FONT][/B]... there is no 64bit specific driver? Is this correct by what is here? In which case, is there any way of installing the driver with some sort of 32bit compatibilty mode? I read something about 32bit compatibility libraries, had a look in Synaptics, and there seems to be some 32bit libraries installed, I just have no ideas which ones I might need to achieve compatibility, if that is even possible.

My thinking could be skewed here but I'm figuring there must be someway of getting this to work in 64bit. I even tried unsuccessfully to install 2.6.35 32bit headers and image to see if the card would perform better but, naturally, I got the message 'Wrong Architecture i386' or something similar.

I am using a[FONT=Times New Roman][SIZE=3][COLOR=black][SIZE=2] Realtek               RTL8191SEvB Wireless card[/SIZE] with the Realtek recommended driver and firmware installed.[/COLOR][/SIZE][/FONT]

Any ideas???

---

### Post by regala on 2011-01-24
> **Bucky Ball said:**
> 
... there is no 64bit specific driver? Is this correct by what is here? In which case, is there any way of installing the driver with some sort of 32bit compatibilty mode? I read something about 32bit compatibility libraries, had a look in Synaptics, and there seems to be some 32bit libraries installed, I just have no ideas which ones I might need to achieve compatibility, if that is even possible.



My thinking could be skewed here but I'm figuring there must be someway of getting this to work in 64bit.


no, not that simple...

> 
 I even tried unsuccessfully to install 2.6.35 32bit headers and image to see if the card would perform better but, naturally, I got the message 'Wrong Architecture i386' or something similar.

I am using a[FONT=Times New Roman][SIZE=3][COLOR=black][SIZE=2] Realtek               RTL8191SEvB Wireless card[/SIZE] with the Realtek recommended driver and firmware installed.[/COLOR][/SIZE][/FONT]

Any ideas???


the 32bit compatibility mode is available for code only in userspace i.e. the kernel cannot use drivers that are not built for the same arch. you can't load 32bit kernel modules on a 64bit kernel.

the way to get this to work on 64bit x86 is to fix the code to build and run on x86_64 architecture. That's it.

---

### Post by Bucky Ball on 2011-01-24
Cheers. ;)

---

