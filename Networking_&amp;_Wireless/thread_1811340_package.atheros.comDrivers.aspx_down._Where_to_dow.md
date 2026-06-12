---
title: "package.atheros.com/Drivers.aspx down. Where to download?"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by Oodles on 2011-07-24
Hi everyone. I'm trying to follow the instructions at ubuntu website to solve my unusable ethernet card, but I can't get the AR81Family-linux-v1.0.0.10.tar.gz package because the site (on title) is down and it doesn't look like there are any mirrors for what I need. Is there any other way to get this, or would it be alright for anyone who's managed to download this before whilst the site is up to share it with me? Pleeeeaaase? =]

---

### Post by chili555 on 2011-07-24
I'd try the compat-wireless package instead. Do you know which driver you need, atl1c or atl1e? You'll need this for the driver-select step.

[http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

If you need more help, post back.

---

### Post by Oodles on 2011-07-24
Nope, I don't know which package I need. But my wireless is working, though. I'm just trying to fix my ethernet so that I could plug directly to the internet source since the connection through wifi is soooooo depressingly slow. =[

---

### Post by chili555 on 2011-07-24
I understand. However compat-wireless contains the atl1xx ethernet drivers as well.

You wouldn't care to troubleshoot the wireless, would you? Please post:```
lspci -nn | grep -e 0200 -e 0280
```Thanks.

---

### Post by Oodles on 2011-07-24
> **chili555 said:**
> I understand. However compat-wireless contains the atl1xx ethernet drivers as well.

You wouldn't care to troubleshoot the wireless, would you? Please post:```
lspci -nn | grep -e 0200 -e 0280
```Thanks.
Here you go:


01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)


=]

---

### Post by chili555 on 2011-07-24
Would you please try an experiment for me? Please do:```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```Is your wireless improved? If so, we can write one short file and make it permanent.> Atheros Communications AR8152 v1.1 Fast Ethernet [[COLOR="Red"]1969:2060[/COLOR]] (rev c1)If we need to build the driver, we'll want *atl1c*.

---

### Post by Oodles on 2011-07-24
**_UPDATE_**

Okay, so someone gave me the file I was looking for (see first post), but after following the steps in the [ubuntu help site]("https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250#Installing wired network drivers"), I ended up with this when I got to the "make" command:


```
make -C /lib/modules/2.6.32-33-generic/build SUBDIRS=/home/denisse/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CC [M]  /home/denisse/src/atl1e_main.o
/home/denisse/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/denisse/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:122: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
/home/denisse/src/atl1e_main.c: In function ‘atl1e_probe’:
/home/denisse/src/atl1e_main.c:287: error: ‘struct net_device’ has no member named ‘open’
/home/denisse/src/atl1e_main.c:288: error: ‘struct net_device’ has no member named ‘stop’
/home/denisse/src/atl1e_main.c:289: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/denisse/src/atl1e_main.c:290: error: ‘struct net_device’ has no member named ‘get_stats’
/home/denisse/src/atl1e_main.c:291: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/denisse/src/atl1e_main.c:292: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/denisse/src/atl1e_main.c:293: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/denisse/src/atl1e_main.c:294: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/denisse/src/atl1e_main.c:305: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/denisse/src/atl1e_main.c:313: error: ‘struct net_device’ has no member named ‘vlan_rx_register’
/home/denisse/src/atl1e_main.c:316: error: ‘struct net_device’ has no member named ‘poll_controller’
make[2]: *** [/home/denisse/src/atl1e_main.o] Error 1
make[1]: *** [_module_/home/denisse/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make: *** [default] Error 2
```


And that didn't look right, but I still proceeded anyway, and I still saw errors on what it gave me (sorry, I've already closed terminal and I didn't get to copy). =[

I hope chili555 can help me. T____T

---

### Post by Oodles on 2011-07-24
> **chili555 said:**
> Would you please try an experiment for me? Please do:```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```Is your wireless improved? If so, we can write one short file and make it permanent.If we need to build the driver, we'll want *atl1c*.
OMG, sorry, your reply wasn't there yet when I posted. Sure thing, I'd experiment. =]

Hang on.

---

### Post by Oodles on 2011-07-24
> **chili555 said:**
> Would you please try an experiment for me? Please do:```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```Is your wireless improved? If so, we can write one short file and make it permanent.If we need to build the driver, we'll want *atl1c*.

Err, I don't know how to tell if it's improved or not. But based on my system monitor, I'm getting 100-150kb/s at average. I've never seen go anywhere higher than that, honestly. =[

Oh, and it's still slow, I suppose. I'm currently downloading package files through Ubuntu Tweak, and it doesn't look like there's a change in speed. It's still listed at B/s. ="[

---

### Post by chili555 on 2011-07-24
> make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
[COLOR="Red"]make: *** [default] Error 2[/COLOR]When you get to this point, you know two things. First, that once you get an error, there is no use in proceeding further; it will only lead to even more errors and certainly won't build a working driver.

Second, you know why I recommend compat-wireless. Please go to the site I linked and download the file at the very top. Please see attached. Download the file to your desktop. Right-click it and select Extract Here.

Please go to System > Administration > Synaptic and verify that you have installed *build-essential*. Do so if not.

Now open a terminal and do:```
cd Desktop/compat
```Press Tab and the remainder of the file name will fill in. Press Enter.```
./scripts/driver-select atl1c
```That's lower case for ATLoneC.```
make
sudo make install
sudo modprobe atl1c
```Your wired ethernet should now be working.

---

### Post by Oodles on 2011-07-24
Okay, will do. Yeah, I know, I was being an idiot to even proceed. I'm a bit worried now, too, that I might have to make a fresh install again because of my dumminess. =/

Will update in a while after doing your suggestion. =]

---

### Post by Oodles on 2011-07-24
> **chili555 said:**
> When you get to this point, you know two things. First, that once you get an error, there is no use in proceeding further; it will only lead to even more errors and certainly won't build a working driver.

Second, you know why I recommend compat-wireless. Please go to the site I linked and download the file at the very top. Please see attached. Download the file to your desktop. Right-click it and select Extract Here.

Please go to System > Administration > Synaptic and verify that you have installed *build-essential*. Do so if not.

Now open a terminal and do:```
cd Desktop/compat
```Press Tab and the remainder of the file name will fill in. Press Enter.```
./scripts/driver-select atl1c
```That's lower case for ATLoneC.```
make
sudo make install
sudo modprobe atl1c
```Your wired ethernet should now be working.

OMG YEYEYEYEYEYEYEYYYYYYYY~ <3<3<3
THANKS CHILIIIIIII!!! =D
Whee~! *hug*

But, how did it fix the wireless lan to go faster too? Oh yeah, I had to reboot my netbook, but it's woooooorrrkkkiiinnggg!

---

### Post by chili555 on 2011-07-24
I wasn't aware it *would* fix the wireless, but, hey, I never fight momentum. I'm glad it's all fixed.

Would you please use thread tools at the top and Mark Solved?

---

### Post by Oodles on 2011-07-24
Done. And ima give you a HUG.

*HUG*

Thanks again! =D

---

### Post by chili555 on 2011-08-10
Mithadon, for security reasons the password is not echoed back, not even ****. Just type it in and press Enter. It will be accepted.

Just for reference purposes:> alright, ethernet: atheros communicatio AR8152 V2.0 fast ethernet [1969:2062] (rev c1), network: realtek semiconductor co., ltd. device [10ec:8176] (rev 01)

---

### Post by Mithadon on 2011-08-10
Hello,
I'm a brand new Ubuntu user so as of today a lot of this is over my head. I had to install 10.04 because I couldn't get the 11.04 setup started without crash or lost keyboard/mouse support. I am having trouble initially connecting to the internet; the ethernet is not detected (nor is the wireless).
Here's some detailed info:

Ethernet controller: Atheros AR8152 V2.0 Fast Ethernet
Network controller: Realtek, [10ec:8176]

As I said I'm trying to learn but it's best to assume I know nothing of terminal commands right now! 
Thank you for any help you can give me.

EDIT: If it's any help, I'm on a Toshiba Satellite C650D-007 laptop.

---

### Post by chili555 on 2011-08-10
Drop the Ubuntu install CD in the tray and do in a terminal:```
sudo apt-cdrom add
sudo apt-get install build-essential linux-headers-generic
```Download the file here to your desktop: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

Right-click it and select Extract Here. Now back to the terminal:```
cd Desktop/compat
```

Press Tab and the remainder of the file name will fill in. Press Enter.```
./scripts/driver-select atl1c
```

That's lower case for ATLoneC.
```
make
sudo make install
sudo modprobe atl1c
```

Your wired ethernet should now be working. Post back if you hit a snag or get stuck. I am here to help you.

---

### Post by Mithadon on 2011-08-10
Alright, after the first part I get: E: unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I've downloaded compat-wireless-2.6.tar.bz2 and transferred it to the laptop via USB.

---

### Post by chili555 on 2011-08-10
Go ahead and try that:```
sudo apt-cdrom add
[COLOR="Red"]sudo apt-get update[/COLOR]
sudo apt-get install build-essential linux-headers-generic
```and continue.

---

### Post by Mithadon on 2011-08-10
I still get a long list of failed downloads and eventually the same error... Initially, after doing sudo apt-cdrom add, I notice W: skipping nonexistent file /media/apt/dists/lucid/main/binary-i386/packages and lucid/restricted/binary-i386/packages. Does this have anything to do with it?

---

### Post by chili555 on 2011-08-10
Try to open System > Admin > Synaptic and look in Settings > Repositories and be sure CD-ROM is added as a source. Press Reload. Then search for the packages build-essential and linux-headers-generic. Install them if they are not already.

---

### Post by Mithadon on 2011-08-10
Wonderful. After adding build-essential from synaptic, the install went worked fine and the internet connection turned on like magic. How should I proceed for the wireless?

---

### Post by chili555 on 2011-08-10
Wonderful indeed! Great work.

Your wireless works with the driver rtl8192ce that we can build also with compat-wireless:
```
cd Desktop/compat
```

Press Tab and the remainder of the file name will fill in. Press Enter.
```
./scripts/driver-select restore
./scripts/driver-select rtlwifi
make
sudo make install
sudo modprobe rtl8192ce
```
The driver sometimes has a firmware issue; let's see what happens after install.

---

### Post by Mithadon on 2011-08-10
The install went smoothly, just like with atl1c, but it seems to have made no difference. At least I can't see any wireless connections?

---

### Post by chili555 on 2011-08-10
Let's have a look at:```
dmesg | grep 819
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Mithadon on 2011-08-10
It seems I had to reinstall the atl1c driver after rtl one in order for ethernet connection to work again. Here is what I get in terminal:

> mithadon@mithubuntulaptop:~$ dmesg | grep 819
[    0.358199] pcieport 0000:00:15.1: setting latency timer to 64
[   12.275655] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.275671] rtl8192ce 0000:02:00.0: setting latency timer to 64
[   12.588504] rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware!
[   12.588618] rtl8192ce 0000:02:00.0: PCI INT A disabled
[  472.450830] JFS: nTxBlock = 8192, nTxLock = 65536


---

### Post by chili555 on 2011-08-10
I believe the module looks for the firmware in /lib/firmwware/rtlwifi. Is that folder on your system?```
ls -al /lib/firmwware/rtlwifi
```Is the firmware anywhere on your system?```
sudo updatedb
locate rtl8192cfw.bin
```updatedb will take a few moments; please be patient.

---

### Post by Mithadon on 2011-08-10
No such file or directory :( no /firmware/ either, in case that was a typo. The updatedb and locate didn't appear to do anything/find anything.

---

### Post by chili555 on 2011-08-11
Attached is a file. Download it to your desktop. Right-click it and select Extract Here. In a terminal, please do:```
sudo cp Desktop/rtlwifi /lib/firmware
sudo chown root:root /lib/firmware/rtlwifi/*
```Detach the ethernet cable, reboot and give me your report.

It is quite late here; I'll have to check in tomorrow.

---

### Post by Mithadon on 2011-08-11
Thank you so much for you help, I really appreciate it.
Unfortunately I have to say that failed too. I got the file and extracted it on desktop; the first line of code seemed to replace a folder for another; and the second line failed because there was nothing at the destination. I will try to paste the specifics in the morning.

---

### Post by chili555 on 2011-08-11
Before you post the latest readings, please try it another way:```
sudo mkdir /lib/firmware/rtlwifi
sudo cp Desktop/rtlwifi/* /lib/firmware/rtlwifi
sudo chown root:root /lib/firmware/rtlwifi/*
```I knew I had been up way past bedtime last night when I typed: sudo chown root:beer /lib/firmware/rtlwif

It was past midnight here...

---

