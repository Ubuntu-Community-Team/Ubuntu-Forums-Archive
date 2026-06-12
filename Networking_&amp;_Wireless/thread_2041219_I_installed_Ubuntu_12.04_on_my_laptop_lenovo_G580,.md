---
title: "I installed Ubuntu 12.04 on my laptop lenovo G580, wired connection is not working."
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by shravankumar531 on 2012-08-12
I found solution in [http://www.zyxware.com/articles/2680/solved-wired-connection-eth0-not-detected-in-ubuntu-12-04](http://www.zyxware.com/articles/2680/solved-wired-connection-eth0-not-detected-in-ubuntu-12-04)

I downloaded compact-wireless-2012-07-03-p.tar.bz2

Here the steps i followed along with output

1. shravankumar@shravankumar-Lenovo-G580:~/Desktop/compat-wireless-2012-07-03-p$ scripts/driver-select alx

Output:
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
Backup exists: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk

2.shravankumar@shravankumar-Lenovo-G580:~/Desktop/compat-wireless-2012-07-03-p$ make

output:
make -C /lib/modules/3.2.0-23-generic/build M=/home/shravankumar/Desktop/compat-wireless-2012-07-03-p modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
scripts/Makefile.build:44: /home/shravankumar/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros/alx/Makefile: No such file or directory
make[4]: *** No rule to make target `/home/shravankumar/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros/alx/Makefile'.  Stop.
make[3]: *** [/home/shravankumar/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros/alx] Error 2
make[2]: *** [/home/shravankumar/Desktop/compat-wireless-2012-07-03-p/drivers/net/ethernet/atheros] Error 2
make[1]: *** [_module_/home/shravankumar/Desktop/compat-wireless-2012-07-03-p] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [modules] Error 2

3. hravankumar@shravankumar-Lenovo-G580:~/Desktop/compat-wireless-2012-07-03-p$ make install

output:
FATAL: Could not open /lib/modules/3.2.0-23-generic/modules.dep.temp for writing: Permission denied
make: *** [uninstall] Error 1

4. shravankumar@shravankumar-Lenovo-G580:~/Desktop/compat-wireless-2012-07-03-p$ modeprobe alx

output:
No command 'modeprobe' found, did you mean:
 Command 'modprobe' from package 'module-init-tools' (main)
modeprobe: command not found


I am new to Ubuntu ,Please help me.

Thanks in advance

---

### Post by sanderj on 2012-08-12
Can you do this without errors:

```
cd compact-wireless-2012-07-03-p
make clean
scripts/driver-select ath9k
make
```

---

### Post by Puma1x on 2012-12-02
OK, managed to fix the problem. I downloaded and installed **compat-wireless-2012-02-28-p.tar.bz2** from **[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)** .

[B]tar -xvf compat-wireless-2012-02-28-p.tar
cd compat-wireless-2012-02-28-p
scripts/driver-select alx
make
make install
modprobe alx[/B]
Note: This fix will NOT work with newer versions of compat-wireless-2012-02-28-p.tar.bz2. Alx was removed from newer versions. Use the exact file described here.

Got it from here 
[http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162](http://askubuntu.com/questions/157223/12-04-does-not-detect-eth0atheros-ar8162)

---

### Post by diegocarrera on 2012-12-11
i just upgrade to kernel 3.5.0-19-generic on ubuntu 12.10 64bits and it works.

---

### Post by Rifester on 2012-12-24
Diego,

I was considering ordering this laptop but was holding off, as I was reading about issues with the wired connection.  Regarding your last post, is everything working good on this laptop under 12.04?
I would appreciate it!

Rifester

---

### Post by diegocarrera on 2013-01-16
> **Rifester said:**
> Diego,

I was considering ordering this laptop but was holding off, as I was reading about issues with the wired connection.  Regarding your last post, is everything working good on this laptop under 12.04?
I would appreciate it!

Rifester


Today i installed ubuntu 12.04 x64, 
+ After i updated it, 
+ The last step is to install compat-wireless-2012-05-09-p.tar.bz2 from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

After these steps the wifi and ethernet connection is working.

Diego

---

### Post by zwets on 2013-02-20
> **diegocarrera said:**
> today i installed ubuntu 12.04 x64, 
+ after i updated it, 
+ the last step is to install compat-wireless-2012-05-09-p.tar.bz2 from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

after these steps the wifi and ethernet connection is working.

Diego

Same here on Ubuntu 12.04 Server 64-bit, using compat-wireless-3.6.8-1-snpc.tar.bz2 from [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/)

Reminder to those still struggling: don't forget the -a when looking for eth0 with ifconfig. Without it, interfaces which are down will not be listed. Also, verify that /etc/network/interfaces has an 'auto eth0' stanza, or your eth0 will happily stay down. (Forehead, meet hand.)

---

### Post by zwets on 2013-02-22
Since the latest Ubuntu 12.04 point release (12.04.2) on 14 Feb, there is a very simple and supported solution to the AR8162 driver problem. [I]No more module-compiling hassles! 
[/I] 
The 12.04.2 point release introduced the [LTS Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") which keeps the kernel and X stack up to date with the versions from Quantal (or later). Quantal's kernel (3.5.0) has built-in support for the alx driver.

If you currently are on 12.04, apt-get updating your system to 12.04.2 will not enable the LTS Enablement Stack by default. You need to explicitly install the packages **linux-generic-lts-quantal**  (and/or **xserver-xorg-lts-quantal **if you want the X stack):

[FONT=Courier New]    apt-get update
    apt-get install linux-generic-lts-quantal 

[/FONT]... is all it took in my case to get the network card working.
[FONT=Courier New]
[/FONT]

---

