---
title: "Martian confusion"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by imaca on 2012-04-27
Hi,
I am trying to get an old lucient winmodem to run under ubuntu 11.10.
I am having a very confusing time figuring out what to do.
Firstly Martian packages are listed in Synaptic (I installed them) but all the instructions I can find (which are very old) say that the martian-full-20080625.tar.gz has to be downloaded and compiled. So I tried to do this (following instructions here [http://ubuntuforums.org/showthread.php?t=1285900&highlight=martian]("http://ubuntuforums.org/showthread.php?t=1285900&highlight=martian")) but when I try this I get the following:

:~/Martian/martian-full-20080625$ make
The martian_dev.ko driver and the complementary helper martian_helper are for use with kernels after 2.6.20. Use the martian-20080407.tar.gz for earlier kernels.
:~/Martian/martian-full-20080625$ sudo make install
make: *** No rule to make target `install'.  Stop.

Can anyone help with this or am I flogging a dead horse here?

---

### Post by gordintoronto on 2012-04-27
My opinion: you're flogging a dead horse. It appears to me that martian-modem:i386 is already compiled. The tar doesn't check the kernel version properly. (3.0.0.17 huh?)

---

### Post by alexfish on 2012-04-27
> **imaca said:**
> Hi,
I am trying to get an old lucient winmodem to run under ubuntu 11.10.
I am having a very confusing time figuring out what to do.
Firstly Martian packages are listed in Synaptic (I installed them) but all the instructions I can find (which are very old) say that the martian-full-20080625.tar.gz has to be downloaded and compiled. So I tried to do this (following instructions here [http://ubuntuforums.org/showthread.php?t=1285900&highlight=martian](http://ubuntuforums.org/showthread.php?t=1285900&highlight=martian)) but when I try this I get the following:

:~/Martian/martian-full-20080625$ make
The martian_dev.ko driver and the complementary helper martian_helper are for use with kernels after 2.6.20. Use the martian-20080407.tar.gz for earlier kernels.
:~/Martian/martian-full-20080625$ sudo make install
make: *** No rule to make target `install'.  Stop.

Can anyone help with this or am I flogging a dead horse here?
check your software centre : search martian

---

### Post by imaca on 2012-04-27
OK, I think I have the driver installed by following this:
[http://wiki.debian.org/martian_dev]("http://wiki.debian.org/martian_dev").
When I type in:
sudo invoke-rc.d martian-modem start
then I get:
* Starting martian-modem daemon...                                      [ OK ]
so I assume it is installed.??
Next, the guide says:
Your device should now be accessible via the /dev/ttySM0 character device. 
But when I look its not there.
If I start Gnome PPP and go to setup, by default it has  the Device as:
/dev/modem
This doesn't exist either so needless to say it doesn't detect a modem.
Do I need to add something into /dev/ somehow and if so how?
- also - I know martian is in the repos, but it doesn't work unless you follow the steps in the debian guide. ALL the Ubuntu documents/guides etc refer to downloading the .tar.gz

---

### Post by alexfish on 2012-04-28
can post the results of this command from the terminal
```

ls -al /dev/ttySM*
```

if the device nodes exist then use in gnome ppp or wvdial

---

