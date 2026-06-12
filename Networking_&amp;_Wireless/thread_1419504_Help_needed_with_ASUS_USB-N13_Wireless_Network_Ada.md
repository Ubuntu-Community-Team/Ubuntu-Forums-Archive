---
title: "Help needed with ASUS USB-N13 Wireless Network Adapter"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by redsultan on 2010-03-01
Hi there,
I've been searching the Internet for some help with this wireless gadget I recently bought.
I bought this specific model because there was a nice 'logo' printed on its box saying the magic words 'linux support'...:P
[COLOR=Blue]**[http://www.asus.com/product.aspx?P_ID=UI3ejenXyxqQTIcJ&templete=2](http://www.asus.com/product.aspx?P_ID=UI3ejenXyxqQTIcJ&templete=2)**[/COLOR]
However I'm having a real hardship to make it work (it does work under XP...).

There is a compressed file on the disk provided (it can be downloaded from ASUS, too), but I'm not really into programming as I'm kinda new to the whole linux thing ;)

Normally I'm able to work out some solution after having an extensive research done, like I managed to bring my laptop pcimca wireless card to life, also my Dell/Lexmark printer is working nicely. Well done, me :lolflag:

But this baby is out of my league. So if you are out there for helping others, please gimmme some advice...

I try to attach the compressed file, it has a readme, with installation guide, but for my knowledge in linux it's not detailed enough, though.

Thanks for your help, you are awesome :-)

---

### Post by chili555 on 2010-03-02
Please insert the device and open Applications -> Accessories -> Terminal and do:```
lsmod | grep -e rt2 -e rt3
lsusb
```Post the result and we'll proceed.

Here is a preview of a possible solution: [http://ubuntuforums.org/showpost.php?p=8903985&postcount=16](http://ubuntuforums.org/showpost.php?p=8903985&postcount=16)

---

### Post by redsultan on 2010-03-02
Hi, thanks for the quick reply.
So after lsmod and lsusb, here is what I got:

redsultan@redsultan-desktop:~$ lsmod | grep -e rt2 -e rt3
redsultan@redsultan-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Blue]Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I hope it helps...

---

### Post by chili555 on 2010-03-02
It helps!```
$ modinfo rt3070sta | grep 1784
alias:          usb:v[COLOR="Blue"]0B05[/COLOR]p[COLOR="Blue"]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Please open a terminal and do:```
sudo modprobe rt3070sta
iwconfig
```Do you now have a wireless interface, ra0 or wlan0, perhaps? Can you click the Network Manager icon at the top right of your desktop, see your network and connect?

---

### Post by redsultan on 2010-03-02
Here's what I got:

redsultan@redsultan-desktop:~$ sudo modprobe rt3070sta
[sudo] password for redsultan: 
redsultan@redsultan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2010-03-02
Let's take a look at:```
dmesg | grep rt3
ls /etc/Wireless/RT3070STA
```We'll get to the bottom of this!

---

### Post by redsultan on 2010-03-02
redsultan@redsultan-desktop:~$ dmesg | grep rt3
redsultan@redsultan-desktop:~$ ls /etc/Wireless/RT3070STA
RT2870STA.dat
redsultan@redsultan-desktop:~$

---

### Post by chili555 on 2010-03-03
Let's try a fix:```
sudo cp /etc/Wireless/RT2870STA.dat /etc/Wireless/RT3070STA.dat
sudo modprobe rt3070sta
dmesg | grep rt3
iwconfig
```Thanks.

---

### Post by redsultan on 2010-03-03
There you go:
redsultan@redsultan-desktop:~$ sudo cp /etc/Wireless/RT2870STA.dat /etc/Wireless/RT3070STA.dat
cp: cannot stat `/etc/Wireless/RT2870STA.dat': No such file or directory
redsultan@redsultan-desktop:~$

---

### Post by chili555 on 2010-03-03
Oops! I missed a directory. Sorry about that. Please try:```
cd /etc/Wireless/RT3070STA 
sudo cp RT2870STA.dat RT3070STA.dat
sudo modprobe rt3070sta
dmesg | grep rt3
iwconfig
```

---

### Post by redsultan on 2010-03-03
Hey,
I still have nothing...

redsultan@redsultan-desktop:~$ cd /etc/Wireless/RT3070STA/
redsultan@redsultan-desktop:/etc/Wireless/RT3070STA$ sudo cp RT2870STA.dat RT3070STA.dat
[sudo] password for redsultan: 
redsultan@redsultan-desktop:/etc/Wireless/RT3070STA$ sudo modprobe rt3070sta
redsultan@redsultan-desktop:/etc/Wireless/RT3070STA$ dmesg | grep rt3
redsultan@redsultan-desktop:/etc/Wireless/RT3070STA$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

redsultan@redsultan-desktop:/etc/Wireless/RT3070STA$ 


Have you actually checked the content of that zip file yet to see if you can figure something out...?

---

### Post by chili555 on 2010-03-03
I have checked the file; it's version 2.1.1 of the driver. Version 2.3.0 is available and we're going to build it and install it tomorrow. In the meantime, be sure you have an ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
```Download the attached file and we'll proceed tomorrow.

---

### Post by redsultan on 2010-03-04
OK. Can't wait :-)

---

### Post by chili555 on 2010-03-04
You might want to put on your welding gloves; today you become a Linux freeky geek!

By default, downloads go to your desktop, so I assume you have downloaded the file I attached and can see it, the .tar.bz2 file, sitting on your desktop. Right click it and select 'Extract Here.' A folder will be created called RT3070_LinuxSTA_V2.3.0.1_20100208.

I am assuming you have the text editor, gedit. If not, in the following commands, substitute kate, nano or your favorite text editor. Open a terminal and do:```
cd Desktop/RT3070
```Press the Tab key; the terminal will fill in the details for you, assuming you have only one RT3070etc. file on your desktop. Now do:```
cp RT2870STA.dat RT3070STA.dat
cp RT2870STACard.dat RT3070STACard.dat
sudo su
make
make install
modprobe rt3070sta
iwconfig
```*Now* do you have a wireless interface? Can you click Network Manager, see networks and connect?

I don't have the device to insert, so I got an error when I modprobed the driver module. Please insert the device before you do the modprobe step. Please let me know your result.

---

### Post by redsultan on 2010-03-04
After I had done everything you instructed:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting rt3070sta (/lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by chili555 on 2010-03-04
> Unknown symbol in module, or unknown parameter (see dmesg)I was afraid of that. Keep those gloves handy as Plan B is coming right up.

---

### Post by chili555 on 2010-03-04
Plan B:```
cd Desktop/RT3070
```Tab.```
sudo su
make uninstall
depmod -a
```Now trash the first file and download the attached file to your desktop. Right-click and select 'Extract Here.'```
cd ~/Desktop/2009
```Tab.```
gedit os/linux/config.mk
```Find these lines:> HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=nChange them to =y

Proofread carefully, save and close gedit.```
gedit os/linux/usb_main_dev.c
```At or near line 45, you will find a listing of PCI IDs. Add a new line:> {USB_DEVICE(0x0B05,0x1784)}, /* Asus 3070 */Make doubly sure that the indentation and spacing exactly matches the existing lines. I did my change at the top. Please see attached. Proofread carefully, save and close gedit.```
make
make install
modprobe rt3070sta
iwconfig
```Please report your progress.

---

### Post by JoZ3 on 2010-03-04
hey chili555 tnx you help me to solve my problem ->[http://ubuntuforums.org/showpost.php?p=8915685&postcount=20]("http://ubuntuforums.org/showpost.php?p=8915685&postcount=20")

---

### Post by chili555 on 2010-03-04
> **JoZ3 said:**
> hey chili555 tnx you help me to solve my problem ->[http://ubuntuforums.org/showpost.php?p=8915685&postcount=20]("http://ubuntuforums.org/showpost.php?p=8915685&postcount=20")I think the 2010 version of the driver is defective. Please try the version I attached just above. As well, you probably won't have to make the change to usb_main_dev.c. If you post your experience back at the thread you linked, I will be glad to help.

---

### Post by redsultan on 2010-03-04
That's what I got this time :-) I guess it's half a success?

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
root@redsultan-laptop:/home/redsultan# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:Off   Fragment thr: Off
          Encryption key: Off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-03-04
> I guess it's half a success?How much more could you want!?!? Did you click the Network Manager icon and try to connect?

I think you are moments from [SOLVED].

---

### Post by redsultan on 2010-03-04
It gets really interesting:
I've got two distros on my old laptop, Ubuntu 9.10 and Linux Mint 8.0
I did exactly the same thing with both OS.
I manage to get connected with Mint, but only after
> 
sudo su
modprobe rt3070sta

(before "modprobe" I had to remove the usb stick and re-plug it. However after restart it wouldn't reconnect, had to do the "modprobe" plug-out, plug in thing. then it'd connect again.)

With Ubuntu, if I leave the stick plugged and "modprobe" the device becomes visible in Network Manager buy it says "device not ready"... No connection, though, whatsoever. Strange.

---

### Post by redsultan on 2010-03-04
Moments away? Sounds great!

---

### Post by chili555 on 2010-03-04
> "device not ready"May we please see:```
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by redsultan on 2010-03-04
root@redsultan-laptop:/home/redsultan# dmesg | grep -e rt2 -e rt3
[   21.113318] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   21.114235] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   52.855161] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   52.857215] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   85.653611] usbcore: registered new interface driver rt2870
[   86.352235] !!! rt28xx Initialized fail !!!
[   86.947331] !!! rt28xx Initialized fail !!!
[  156.924372] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[  156.927615] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[  157.548132] !!! rt28xx Initialized fail !!!
[  158.136547] !!! rt28xx Initialized fail !!!
[  194.609024] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[  194.611860] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[  195.271819] !!! rt28xx Initialized fail !!!
[  195.900183] !!! rt28xx Initialized fail !!!
[  272.823991] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[  272.825489] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[  273.447625] !!! rt28xx Initialized fail !!!
[  274.040733] !!! rt28xx Initialized fail !!!
root@redsultan-laptop:/home/redsultan# 

I'm thinking, I might have messed up the system a little bit while trying... Maybe I reinstall Ubuntu and try that all over again...

---

### Post by chili555 on 2010-03-04
> Maybe I reinstall Ubuntu and try that all over again...First, try removing ndiswrapper via Synaptic, and then reboot.

---

### Post by redsultan on 2010-03-04
After I removed ndiswrapper and rebooted...

root@redsultan-laptop:/home/redsultan# modprobe rt3070sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
root@redsultan-laptop:/home/redsultan# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@redsultan-laptop:/home/redsultan# dmesg | grep -e rt2 -e rt3
[  101.684620] usbcore: registered new interface driver rt2870
[  102.342984] !!! rt28xx Initialized fail !!!
[  102.930872] !!! rt28xx Initialized fail !!!

---

### Post by chili555 on 2010-03-04
Please try:```
sudo cp /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat
sudo rmmod -f rt3070sta
sudo modprobe rt3070sta
dmesg | grep -e rt2 -e rt3
```Any improvement after [ 102.93ish]?

---

### Post by poohstickz on 2010-03-04
Here's another approach. The downside is that you'll get the message in your log about loading a module from the staging area, the upside is it survives across a kernel update. Clearly, the "right" answer is for a supported update to the module but this method is, for me, nice, clean and portable.

[LIST=1]
[*]Copy and configure the /etc/Wireless/RT2870STA file as described in the driver README. You really do need to read this file to understand the configuration.
[*]Add a UDEV rule to load RT3070STA
[*]Bind the driver to the device (can be combined with the above)
[/LIST]

/etc/udev/rules.d/network_drivers.rules
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
```/etc/modprobe.d/network_drivers.conf
```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Now the driver will "just" work. Obviously, you'll still need to configure your network but the above will automatically load the module when/if the device is plugged in. Also, no need for ndiswrapper, compiling kernel modules, etc.

You can do the same for other drivers and devices. Multiple new devices can be added in this way.

---

### Post by redsultan on 2010-03-06
I'm sorry I haven't been in touch. I'm working cr*ppy split shifts right now, so no time for computers:-)
So, I got fed up, reinstalled Ubuntu, with the latest updates.
I did all the steps we've been through but I think it just got worse.

After editing the config files, make, make install and modprobe, here' what I have:

> redsultan@redsultan-laptop:~/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0$ sudo modprobe rt3070sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
redsultan@redsultan-laptop:~/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0$ dmesg | grep -e rt2 -e rt3
[  929.589749] usbcore: deregistering interface driver rt2870
[  935.604653] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[  935.619157] usbcore: registered new interface driver rt2870
redsultan@redsultan-laptop:~/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


---

### Post by redsultan on 2010-03-06
Hey, I tried and got this for the first code:
root@redsultan-laptop:/etc/udev/rules.d# ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
ATTR{idVendor}==0b05,: command not found

For the second code:
root@redsultan-laptop:/etc/udev/rules.d# install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
install: unrecognized option '--ignore-install'
Try `install --help' for more information.

But oddly enough the wireless come to life!!! However it shows in network manager it wouldn't connect to the router, even if I type the password in.
After the restart it it doesn't work, again.

Any idea, guys?

iwconfig:
root@redsultan-laptop:/etc/udev/rules.d# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.417 GHz  Access Point: 00:24:01:29:8C:AB   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-19 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by poohstickz on 2010-03-06
The intent of my post was to tell you to create two new files. The names of the files really don't matter, the directory you place them in does. 

So, you create **/etc/udev/rules.d/network_drivers.rules **and in it you place the following that I have type in [COLOR=RoyalBlue]**blue**[/COLOR]. Note, put this all on one line and you must copy it exactly. Case and all, quotes and all:

[COLOR=RoyalBlue]**ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"**[/COLOR]

Next, you create a file** /etc/modprobe.d/network_drivers.conf** and in it you place the following, again, all on one line.

**[COLOR=RoyalBlue]install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id[/COLOR]**

Then you plug in your USB adapter. As long as you haven't tried to force any other drivers to load (updated modules.conf, for example), and you've removed ndiswrapper (you have to chose one method) and friends, this will absolutely work for you.

The only thing you type in on the console is whatever command you use to bring up your editor. No other commands, you simple create two files then plug in your adapter.

I hope this is a little clearer this time around.

---

### Post by redsultan on 2010-03-08
Hi there, eventually I had a day off, so I could spend some time on the whole wireless thing.
IT'S WORKING!
After a fresh install with the latest updates, I installed the driver (make, make install), then created the two files you instructed me to. Plugged the USB in and MAGIC! :-)
Thanks a lot. This topic is now SOLVED :-D

---

### Post by oioi on 2010-03-12
Hi I'm a newbie who's having the same problem with this adapter as well.
Could you please outline the steps you've taken to get the adapter working?

Like what updates (build-essential?) you've downloaded, and which driver you've used? 

I have tried drivers v2.1.1.0 and v2.1.2.0, using Plan B described by chilli555, but to no avail. 

When I do a "modprobe rt3070sta", there's no response from the system at all.

Any help is appreciated, thanks!

---

### Post by redsultan on 2010-03-13
Hi there,
I'm a newbie, too.
After I installed Ubuntu 9.10 I also installed the latest upgrades using LAN cable to connect the Internet.

1.) Download the driver from #17 by chili555  (2009_1110_RT3070_Linux_STA_v2.1.2.0)
2.) Extract it to your Desktop (or anywhere, but I used that one)
Basically if you double-click on it the Archive Manager will start and you need to choose where to Extract.
3.) Go to the folder
code:
> cd /home/redsultan/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.04.) code:
> sudo make (obviously it will ask for your sudo/administrator password)
5.) code:
> make install
6.) Create two files in the next steps:
code:
> gedit /etc/udev/rules.d/network_drivers.rulesthen when the text editor opens up
copy and paste the followings exactly as it is. case and all, quotes and all:
> [COLOR=RoyalBlue]**ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"**[/COLOR]save and close the text editor.
>  gedit /etc/modprobe.d/network_drivers.conf 
the copy and paste as above:
>  **[COLOR=RoyalBlue]install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id[/COLOR]**
save and close text editor.
7.) plug the USB device in (mine wasn't recognized until I restarted...)
8.) exit terminal window
9.) restart system
10.) configure your wireless
11.) enjoy. :-D

I hope I didn't miss anything... Good luck.

PS: it's worth to mention that I had to fiddle with the router, too because for some reason it just didn't let the USB to connect, I ran the router's connection wizard and that solved my last problem.

---

### Post by oioi on 2010-03-13
Thank you so much.

I'll work on this tonight and see how it goes. 

Will report the outcome of it tomorrow. 

Cheers!:)

---

### Post by oioi on 2010-03-14
For some reason, this method didn't work for me :(

But the adapter somehow came to life after I modified the config.mk and usb_main_dev.c files as described by chili555 and then rebooted. 
(Provided that I firstly disable the default rt2870sta.ko and rt3070sta.ko files that came with Karmic.) 

It took me the whole day, but at least it's working now! :D

---

### Post by redsultan on 2010-03-14
Congratulations!
It doesn't matter which method, if you finally managed to get it working. :-)

---

### Post by oioi on 2010-03-15
Cheers!

We'll become experts in no time if we keep doing this...;)

---

### Post by pepoweb on 2010-03-20
I have followed this thread by the letter, but no luck :-(

I do see a 'connection' in the network manager, but no information in the details (wel all zero's).

Here is the output off dmesg:
```
flip@desktop:~/install/v2.1.2.0$ dmesg | grep -e rt2 -e rt3
[   37.055822] usbcore: registered new interface driver rt2870
[   50.990417] !!! rt28xx Initialized fail !!!
```

iwconfig:
```
flip@desktop:~/install/v2.1.2.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"test"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The ESSID:"test" appeared after I selected "Connect to a diffenten Wireless network" in the networkmanager and entered test. After that I did the same thing with the real network (manually, is the card doesn't see any networks) but this didn't change anything. I have tried the network without encryption, with WEP and with WPA2.

I am starting to get fed up with this situation and the lack of support of hardware vendors :-(

Any suggestions? (A fresh install is not an option)

---

### Post by chili555 on 2010-03-20
> !!! rt28xx Initialized fail !!!That's surely a clue! Let's widen the search. Please post:```
lsusb
lsmod | grep -e rt2 -e rt3
dmesg | grep -i rt2
```I noticed you built a newer version of rt2870sta. In my opinion, very few cases actually need the newer version; some other factor is at work preventing the built-in version from working properly. We shall soon see.

---

### Post by pepoweb on 2010-03-23
With a friend I spend another evening playing around with the driver. We found a little error. Which after we solved that resulted in a working driver (from the 2.1.2.0 version):

dmesg | grep -e rt2 -e rt3

```

[ 3079.616362] usbcore: registered new interface driver rt2870

```

but nothing in iwconfig and no device in the network manager:

```

flip@desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Here are the other commands you requested:

```

flip@desktop:~$ lsusb
Bus 005 Device 003: ID 059f:0651 LaCie, Ltd 
Bus 005 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
flip@desktop:~$ lsmod | grep -e rt2 -e rt3
rt3070sta             547672  0 
usbcore               170288  6 rt3070sta,usb_storage,libusual,ehci_hcd,uhci_hcd
flip@desktop:~$ dmesg | grep -i rt2
[   38.212607] usbcore: registered new interface driver rt2870

```

Hope this helps.

TIA!

Peter

---

### Post by chili555 on 2010-03-23
> flip@desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""Is this not something in *iwconfig*? Let's also see:```
dmesg | grep -e rt3 -e ra0
```Thanks.

---

### Post by poohstickz on 2010-03-23
Earlier in this thread, I posted a very simple way to get this device to work. However, it seems that everyone keeps doing MORE than is necessary and that's why a large part of why these problems persist. 

So, to be clear. Unless you KNOW that you have a different conflict, then you do NOT need to blacklist anything; you do NOT need to compile or update any modules; you do NOT need to install ndiswrapper, you do NOT need to install wicd; and so on. You can make many devices work with just a "modprobe" and an "echo" command. 

Not that those others things are "wrong" in and of themselves, it's just that by the time most folks have gone down that route than way too much has been changed and luck takes over. Pick one method and stick with it. Mix and match rarely works.

Guys, if you make a change and it doesn't work, BACK IT OUT. Don't continue with some other recipe for some other card and some other driver. It's just making things worse. Honestly it is.

In terms of this thread. Regarding the logs and grep. If you eyeball the log and look around the time of the error you'll probably see the CAUSE of the error. "Firmware load failed", perhaps? The error is in there, you need to find it.

None of this, by the way, is meant to sound mean. I share the frustrations of so many in this thread, but I share it from the perspective of seeing so many people accidentally going around in circles.

The iwconfig questions,  confusing... they show ra0, it's there. Not sure of the question.

---

### Post by pepoweb on 2010-03-25
Output of dmesg | grep -e rt3 -e ra0
```

flip@desktop:~$ grep -e rt3 -e ra0


```
(So no output, neither with -e rt**2**)



@poohstickz
Thanks for your input. Let me explain my case:
This ASUS USB-N13 is a stick I got after I tried an unsupported Netgear stick. I followed the instructions of this treat to the letter. After this didn't work I found out I reverted all changes I made to get the Netgear stick running except for 1 symlink. That caused the problem with the "Initialized fail" because the driver was build wrong. When I corrected the symlink the driver build correct. I now just have an additional problem that I am trying to solve.

---

### Post by kook44 on 2010-04-02
Hello-
I'd just like to add some addt'l input.  I was able to successfully install this device by following exactly the instructions in [post #35]("http://ubuntuforums.org/showpost.php?p=8958958&postcount=35") of this thread.  I was NOT able to compile the manufacturer's drivers.  My make output is as follows:

```
user@user-desktop:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ sudo make
make -C tools
make[1]: Entering directory `/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools/bin2h
cp -f os/linux/Makefile.6 /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/Makefile
make  -C  /lib/modules/2.6.31-20-generic-pae/build SUBDIRS=/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic-pae'
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_md5.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.o
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:4406: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wep.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/action.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_data.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.o
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/include/rtmp.h:5687: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.o
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_sync.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/eeprom.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_info.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/dfs.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/spectrum.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rt_channel.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_profile.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_asic.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/assoc.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/auth.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.o
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:651: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:1429: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:929: warning: the frame size of 1260 bytes is larger than 1024 bytes
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sync.c:525: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/sanity.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.o
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/connect.c:343: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../sta/wpa.o
  CC [M]  /home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/user/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic-pae'
make: *** [LINUX] Error 2
user@user-desktop:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ 

```

And here is the diff between the mfr driver and what was downloaded from this thread.
```
user@user-desktop:~/Desktop$ diff 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/ 2009_1110_RT3070_Linux_STA_v2.1.2.0/
Common subdirectories: 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/chips and 2009_1110_RT3070_Linux_STA_v2.1.2.0/chips
Common subdirectories: 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/common and 2009_1110_RT3070_Linux_STA_v2.1.2.0/common
Common subdirectories: 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/include and 2009_1110_RT3070_Linux_STA_v2.1.2.0/include
Common subdirectories: 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os and 2009_1110_RT3070_Linux_STA_v2.1.2.0/os
diff 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/README_STA_usb 2009_1110_RT3070_Linux_STA_v2.1.2.0/README_STA_usb
11c11
< RT3070 Wireless Lan Linux Driver
---
> RT2870 Wireless Lan Linux Driver
17c17
< rt3070.o/rt3070.ko
---
> rt2870.o/rt2870.ko
36c36
< This is a linux device driver for Ralink RT3070 USB ABGN WLAN Card.
---
> This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.
59,60c59,60
< 1> $tar -xvzf DPB_RT3070_Linux_STA_x.x.x.x.tgz
<     go to "./DPB_RT3070_Linux_STA_x.x.x.x" directory.
---
> 1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
>     go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
89c89
<     #    $/sbin/insmod rt3070sta.o
---
>     #    $/sbin/insmod rt2870sta.o
93c93
<     #    $/sbin/insmod rt3070sta.ko
---
>     #    $/sbin/insmod rt2870sta.ko
98c98
< 	$/sbin/rmmod rt3070sta
---
> 	$/sbin/rmmod rt2870sta
103c103
< RT3070 driver can be configured via following interfaces, 
---
> RT2870 driver can be configured via following interfaces, 
491,492c491,492
< If you want for rt3070 driver to auto-load at boot time:
< A) choose ra0 for first RT3070 WLAN card, ra1 for second RT3070 WLAN card, etc.
---
> If you want for rt2870 driver to auto-load at boot time:
> A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
496c496
<        alias ra0 rt3070sta
---
>        alias ra0 rt2870sta
diff 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/RT2870STA.dat 2009_1110_RT3070_Linux_STA_v2.1.2.0/RT2870STA.dat
7c7
< SSID=208-thomson
---
> SSID=11n-AP
72c72
< WapiAsCertPath=
---
> WapiAsCertPath=
\ No newline at end of file
Common subdirectories: 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/sta and 2009_1110_RT3070_Linux_STA_v2.1.2.0/sta
Common subdirectories: 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools and 2009_1110_RT3070_Linux_STA_v2.1.2.0/tools
user@user-desktop:~/Desktop$ 

```

Maybe those referenced object files were compiled against an older version of the shared objects???

Anyway, I hope maybe someone may find this useful.

Thanks!

---

### Post by Mambo2 on 2010-04-17
I had a similar problem where the network adapter would show up in iwconfig but I was unable to configure it.

The module would show up in lsmod as well but with no hardware listed as using it.

After reviewing the errors in /var/log/messages I discovered it was looking for the module configuration in the wrong location.

All I had to do was rename the /etc/Wireless/RT3070STA/ directory to /etc/Wireless/RT2870STA/

Works great now.

---

### Post by masacote on 2010-06-07
Thank you "Red Sultan" I got a same wireless adapter on my computer and using yours step # 35 make it work my adapter, I'm newbie on ubuntu and linux I came from Windows and this is awesome experience.:guitar::)

---

### Post by I got worms. on 2010-06-08
Thanks gang!

Great thread with great results.  Post #35 was a success after doing the reading and a little research. =D>

---

### Post by razkal on 2010-06-10
I have been searching the forums for days trying to get netcards working for ubuntu on 1 of my machines, my other one worked straight after install but this one has been giving me a headache, resorted to using ASUS USB N13 I had but no luck so far...I followed the instructions on post 35 I think it was and got upto here

[COLOR=RoyalBlue][B]ACTION=="add", SUBSYSTEM=="usb",  ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe  -qba rt3070sta"

pasted that in and keep getting an error when I try to save it saying in red :


could not save the file /etc/udev/rules.d/netowrk_drivers.rules.

you do not have the permission necessary to save the file.
Please checked you have typed in the location correctly and try again.

btw I'm a Linux noob...thanks for the tips, but yeah stumped at the moment.

oh and I'm using Ubuntu Lucid v10.04
[/B][/COLOR]

---

### Post by b k on 2010-06-10
> **razkal said:**
> I have been searching the forums for days trying to get netcards working for ubuntu on 1 of my machines, my other one worked straight after install but this one has been giving me a headache, resorted to using ASUS USB N13 I had but no luck so far...I followed the instructions on post 35 I think it was and got upto here

[COLOR=RoyalBlue][B]ACTION=="add", SUBSYSTEM=="usb",  ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe  -qba rt3070sta"

pasted that in and keep getting an error when I try to save it saying in red :


could not save the file /etc/udev/rules.d/netowrk_drivers.rules.

you do not have the permission necessary to save the file.
Please checked you have typed in the location correctly and try again.

[/B][/COLOR]

Hi there, with reference to post #35 Step 6, precede the code with [COLOR=Red]sudo[/COLOR] and try again:

[COLOR=Red]sudo[/COLOR] gedit /etc/udev/rules.d/network_drivers.rules                      

Hope the info is helpful

Good luck

---

### Post by razkal on 2010-06-10
OK so I reinstalled ubuntu and tried again and couldnt get past step 1, so I used the GUI to copy the driver folder to the /tmp folder and not sure it worked properly but it seemed to I guess (not really sure what I'm doing) got to that step I couldnt pass and "sudo" got it working (thanks for that!) now at the next step

Quote:
 	 	 		 			 				 gedit /etc/modprobe.d/network_drivers.conf 			 		

the error it's giving me now is:

No such file or directory

I tired doing it exactly as typed and with sudo in front, either way it wouldnt work.

---

### Post by b k on 2010-06-10
> **razkal said:**
> OK so I reinstalled ubuntu and tried again and couldnt get past step 1, so I used the GUI to copy the driver folder to the /tmp folder and not sure it worked properly but it seemed to I guess (not really sure what I'm doing) got to that step I couldnt pass and "sudo" got it working (thanks for that!) now at the next step

Quote:
                                                  gedit /etc/modprobe.d/network_drivers.conf                      

the error it's giving me now is:

No such file or directory

I tired doing it exactly as typed and with sudo in front, either way it wouldnt work.

Hi there, (still with reference to post #35) try this from a Terminal window:

Code:
[COLOR=Red]sudo gedit[/COLOR]

In the blank opened file copy and paste :

[B][COLOR=RoyalBlue]install rt3070sta /sbin/modprobe  --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" >  /sys/bus/usb/drivers/rt2870/new_id

[/COLOR][/B][COLOR=RoyalBlue][COLOR=Black]then click* File*, *Save a*s, change the Name: Unsaved Document 1 to [/COLOR][/COLOR][COLOR=Red]network_drivers.conf [/COLOR][COLOR=RoyalBlue]

[COLOR=Black]then left click on **File System**, double left click** etc** folder, double left click **modprobe.d** folder, and then at the bottom right click [COLOR=Red][B]Save

[/B][/COLOR][/COLOR][/COLOR]All the stuff in blue above should be in the [COLOR=Red]network_drivers.conf[/COLOR] file (of the /etc/modprobe.d directory) now.

Hope that the info above helps you to progress further with post #35.

Good luck and post back hopefully with success.

---

### Post by razkal on 2010-06-10
Ok thanks that worked, did steps 7-11 after that but no go...no wireless device showing up in connection manager still, not sure what to try next as I don't want to mess things up and have to reinstall.

OK I tried sudo modprobe rt3070sta
The result was FATAL: Module rt3070sta not found.
sh: cannont create /sys/bus/usb/drivers/rt2870/new_id: directory nonexistent
FATAL: Error running install command for rt3070sta

and with iwconfig

lo no wireless extensions

Maybe it's because I used the /tmp folder to do the install and it wipes it after reboot?
Also I thought I had success because after I did the unplug and re plug in wireless step the green light on the network adaptor lit up and was flashing a bit I think before I rebooted...now there is no green light on it :/

---

### Post by chili555 on 2010-06-10
@b k --

I don't believe rt3070sta exists any longer; I think it is being merged into rt2870sta:```
$ modinfo rt2870sta
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
[COLOR="Red"]alias:          rt3070sta[/COLOR]
version:        2.0.1.0
license:        GPL
description:    RTxx70 Wireless LAN Linux Driver
```I think the process you've outlined will work if he changes *every* instance of rt3070sta to rt2870sta in the files he created.

---

### Post by razkal on 2010-06-11
Hi chilli555 Is that an ideal solution?  If so, how do I go about doing that?

Also found my sound card isn't working so I was hoping to get the updates once my network was sorted and that may fix it...btw is there a way to download the 170meg updates without using download manager, ie. from another pc and put on a cd or flash drive to update this machine which has no ethernet working?

---

### Post by rljames@psualum.com on 2010-06-11
I also have the ASUStek USB-N13 and following this thread.

However nothing suggested seems to work in my situation. So I'm wondering, keep in mind that I'm a relative novice, would the Linux "flavor" and target machine be possible issues? Specifically Xubuntu 9.10 on an IBM T22.

In the interest of time and anticipating questions, here is this mornings boot as per;
sudo cat /var/log/syslog | grep -i network

```

Jun 11 06:30:39 xubuntu NetworkManager: <info>  starting...
Jun 11 06:30:39 xubuntu NetworkManager: <info>  Trying to start the modem-manager...
Jun 11 06:30:39 xubuntu kernel: [    3.663149] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
Jun 11 06:30:39 xubuntu kernel: [    6.398426] type=1505 audit(1276237824.413:3): operation="profile_load" pid=325 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun 11 06:30:40 xubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.0/net/eth0, iface: eth0)
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun 11 06:30:40 xubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 11 06:30:40 xubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 11 06:30:40 xubuntu NetworkManager: <info>  Wireless now enabled by radio killswitch
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: (165083888) ... get_connections.
Jun 11 06:30:40 xubuntu NetworkManager:    SCPlugin-Ifupdown: (165083888) ... get_connections (managed=false): return empty list.
Jun 11 06:30:40 xubuntu avahi-daemon[661]: Network interface enumeration completed.
Jun 11 06:30:40 xubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): carrier is OFF
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e100')
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): now managed
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): bringing up device.
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): preparing device.
Jun 11 06:30:40 xubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun 11 06:30:40 xubuntu kernel: [   22.358904] type=1505 audit(1276252240.373:12): operation="profile_replace" pid=764 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Jun 11 06:30:40 xubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:03.0/net/eth0
Jun 11 06:30:40 xubuntu NetworkManager: <info>  modem-manager is now available
Jun 11 06:30:40 xubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 11 06:30:40 xubuntu NetworkManager: <info>  Trying to start the supplicant...
bob@xubuntu:~$ 

```

Thanks.

---

### Post by chili555 on 2010-06-11
> **razkal said:**
> Hi chilli555 Is that an ideal solution?  If so, how do I go about doing that?

Also found my sound card isn't working so I was hoping to get the updates once my network was sorted and that may fix it...btw is there a way to download the 170meg updates without using download manager, ie. from another pc and put on a cd or flash drive to update this machine which has no ethernet working?Please do:```
lsusb
```Do you have the very same device?> 0b05:1784If so, please do:```
gedit /etc/udev/rules.d/network_drivers.rules 
```If you have created the file previously, change every instance of rt3070sta to rt2870sta. Proofread, save and close.

If you have not created the file previously and gedit opens an empty file, put in one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread carefully, save and close gedit.

Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf 
```If you have created the file previously, change every instance of rt3070sta to rt2870sta. Proofread, save and close.

If you have not created the file previously and gedit opens an empty file, put in one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Now reboot and tell me if the wireless card is working.

If you do not have the same device, start a new thread and start by posting:```
lsusb
```

---

### Post by chili555 on 2010-06-11
> **rljames@psualum.com said:**
> I also have the ASUStek USB-N13 and following this thread.

However nothing suggested seems to work in my situation. So I'm wondering, keep in mind that I'm a relative novice, would the Linux "flavor" and target machine be possible issues? Specifically Xubuntu 9.10 on an IBM T22.

In the interest of time and anticipating questions, here is this mornings boot as per;
Thanks.
Please try the steps in my post #58 above and post back.

I love those old IBMs! I have had about four Ts over the years.

---

### Post by razkal on 2010-06-12
[FONT=monospace]Hi and thanks for the help.

I tried following your steps but after

[/FONT]ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"
I got an error saying it couldn't save in gedit because it couldnt find the file at that location.

Ahhh damnit I just looked for the file and there is on there but I made a typo when saving the name I guess and can't seem to rename it...quite annoying that I can't seem to do a simple thing like rename it :/

So somehow I have to rename this file them struggle through the rest of the instructions, why is Linux so awkward.  I really prefer a GUI for this sort of thing, it's doing my head in, I haven't done any coding/commands stuff since DOS hehe

---

### Post by chili555 on 2010-06-12
Rename any file in Linux by moving it:```
sudo mv mispellt.txt spelled.txt
```

---

### Post by rljames@psualum.com on 2010-06-15
Chili,

> **chili555 said:**
> Please try the steps in my post #58 above and post back.


Tried most of the suggestions in this thread including step #58. However, it would seem I originally included a "/" after the "/bin/echo" path in the "install" statement. Corrected that mistake and all seems to work.

Thanks for the help.

A couple of follow-on questions;
[LIST=1]
[*]Given that I've experimented quite abit in trying to solve this problem, do I need to "reverse" any of the other changes to the system? For instance, the "makes" and "make install" etc?

[*]Also could you perhaps explain what your solution actually does?
[/LIST]

Thanks again,
Bob

---

### Post by AnothrNmbr on 2010-06-15
fwiw, i followed #35 (prepending 'sudo' to everything) and then followed the fixes in #58 and everything is working perfectly now.  thanks for your help guys.

ji

---

### Post by chili555 on 2010-06-15
> **rljames@psualum.com said:**
> Chili,



Tried most of the suggestions in this thread including step #58. However, it would seem I originally included a "/" after the "/bin/echo" path in the "install" statement. Corrected that mistake and all seems to work.

Thanks for the help.

A couple of follow-on questions;
[LIST=1]
[*]Given that I've experimented quite abit in trying to solve this problem, do I need to "reverse" any of the other changes to the system? For instance, the "makes" and "make install" etc?

[*]Also could you perhaps explain what your solution actually does?
[/LIST]

Thanks again,
BobIf your card is working as expected, I wouldn't change anything. All we did is get the rt2870sta driver to recognize the usb.id of your card.> 0b05:1784 It was actually stolen from another wireless guru on the forum. I make no apologies; if it works, I use it!

---

### Post by rljames@psualum.com on 2010-06-21
OK, I just couldn’t leave well enough alone. Xubuntu 9.10 install on IBM T22 was working great with the ASUS N13 as per the help from this thread *but* after an “Update Manager” move to version 10.4 LTS the system stopped recognizing the USB stick when inserted…

Something I heed to “redo” for the N13 wireless networking setup?

Thanks.

---

### Post by redsultan on 2010-06-27
As far as I know the steps described in #35 not working under the 10.04... that's why I still run 9.10... (I don't remember now, but shortly after the new release I found that info on some forum...maybe here?)
I'm a newbie too, so no idea on how to do the 'redo' :-)

---

### Post by mchlor on 2010-07-01
worked like a charm in lucid.  thanks.  Followed everything to a tee and finally worked when I reached page 6.  even the network manager gtk is working.

---

### Post by blackhawkover on 2010-07-15
> **Mambo2 said:**
> I had a similar problem where the network adapter would show up in iwconfig but I was unable to configure it.

...

All I had to do was rename the /etc/Wireless/RT3070STA/ directory to /etc/Wireless/RT2870STA/

Works great now.


This solved my problems too. number 35 is the quickest and easiest help here. 
READ MY LIPS - Use number 35 to fix this problem if you are stuck. 

Thanks so much guys. My wife would kill me if I bought this adapter (because it said linux supported) and it was a flop like the other ones I've bought and don't have time to do a lot of command editing. I am really looking forward to a day of true plug and play with hardware for linux. 
Thanks again, and thanks sultan for starting us off with a good question.

---

### Post by Xonnie316 on 2010-07-18
I'm another Asus N-13 USB Owner which is trying to install it on Ubuntu 10.4.

I'm experiencing the same issues installing it...

I followed post #35.

After typing in **make install** this error shows up about file & folder permissions

> make -C /home/shaun/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': Permission denied
make[1]: Entering directory `/home/shaun/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
mkdir: cannot create directory `/etc/Wireless/RT3070STA': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/shaun/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
make: *** [install] Error 2


Any suggestions people??


And when I tried to add the code to the 2 following files, it doesn't allow me to save regarding permissions aswell:

gedit /etc/udev/rules.d/network_drivers.rules
gedit /etc/modprobe.d/network_drivers.conf


I had a look at my account and it seems like its admin, coz this is the user I installed Ubuntu with...

---

### Post by blackhawkover on 2010-07-28
> **Xonnie316 said:**
> I'm another Asus N-13 USB Owner which is trying to install it on Ubuntu 10.4.

I'm experiencing the same issues installing it...

I followed post #35.

After typing in **make install** this error shows up about file & folder permissions



Any suggestions people??


And when I tried to add the code to the 2 following files, it doesn't allow me to save regarding permissions aswell:

gedit /etc/udev/rules.d/network_drivers.rules
gedit /etc/modprobe.d/network_drivers.conf


I had a look at my account and it seems like its admin, coz this is the user I installed Ubuntu with...

Are you still root? make sure you type "sudo make install" "sudo gedit ..."
Does that help?

Keep trying, don't give up. I am finding setbacks as I am setting this device on other computers, so it's giving me a headache too, but I finding it eventually working.

---

### Post by blackhawkover on 2010-08-01
Boy has it been a long week for me. 
I followed many rabbit trails this last week and a half trying to get this device working in 10.04 (even had to go back to 9.10 to try because I lost my network manager by installing wicd). 

But I'm happy to say that I am posting this from a wireless access. 

So, long story short, I have installed this on three computers now, each needing a different workaround, but essentially, to anyone that has read this far, don't give up. 

Use the instructions on number 35 of this thread, and for me, what finally made it work right was the renaming of things in #58. 

Thanks so much to chilli555, pooshtick(sp?) and redsultan for trailblaizing here guys. I lookforward to more Ubuntu. 

blackhawkover - over, out, and very satisfied.

---

### Post by koanhead on 2010-08-18
After struggling with this for a few days, I am posting this from my wireless connection.
I used the steps from post #35 and the copying-over of the .dat files mentioned in post #14:
```


cp RT2870STA.dat RT3070STA.dat

cp RT2870STACard.dat RT3070STACard.dat

```

Including this step appears to render the addition of udev rules as in post #58 unnecessary, although the next kernel update may well hose the driver. I'm working on this.

I made a launchpad question about this issue.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/121473](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/121473)
If anyone thinks this should be escalated to a bug report, let me know and I will do it. Or, of course, you can always DIY.

---

### Post by koanhead on 2010-08-25
Bug #624339 created.

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-nettool/+bug/624339](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-nettool/+bug/624339)

---

### Post by dishantlangayan on 2010-08-28
I followed all the steps mentioned. the driver installed correctly, BUT there is no light on the device nor is it detecting any wireless networks. any idea what the problem might be?

Also when i click on the network manager icon i see the following options:
Connect to Other Wireless Network...
Create New Wireless Network...
Manual Configuration...

When i use the 1st option and enter the network ssid and password, it tries to connect but nothing happens. I think once the adapter light come on it should work. SO anyone know how to get the adapter working? (this same adapter work in Windows). please help. i'm using Ubuntu 8.04 hardy heron updated with latest patches.

---

### Post by zelibobla on 2010-09-08
Chili, thank you very much. Can't imagine what could I do without of your posts. Much more useful than instruction given to me with my new Asus USB N10.

---

### Post by koanhead on 2010-09-08
In post #55 Chili555 says:
> I don't believe rt3070sta exists any longer; I think it is being merged into rt2870sta

Yes, according to this:

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.32.y.git&a=search&h=HEAD&st=commit&s=rt307](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.32.y.git&a=search&h=HEAD&st=commit&s=rt307)

This would seem to indicate that the rt2870sta module is the correct one to use, but I don't have it working yet. I'm testing the latest devel release and will report back.

The problem as I see it is that rt2870sta will not recognize device id 0b05:1784 as configured. I fixed this by using the approach in post #19, changing all references to rt3070sta to rt2870sta. Now the device works in client mode only, which is the same result I obtained using the rt3070sta 2.1.2.0 driver. That one quit working after the most recent kernel update, as expected.

---

### Post by zelibobla on 2010-09-09
Ooops. It looks like it work but it doesn't.

So. I've got Asus USB N10 and followed all the steps in this thread. In result I've got next:
```
zeliboba@zeliboba:~$ dmesg | grep -e rt2 -e rt3
[   28.786790] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   28.829056] usbcore: registered new interface driver rt2870
[24172.929717] rt2870 1-5:1.0: no reset_resume for driver rt2870?

```
```
zeliboba@zeliboba:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1786 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
zeliboba@zeliboba:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"11n-AP"  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
/etc/modprobe.d/network_drivers.conf
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1786" > /sys/bus/usb/drivers/rt2870/new_id
```
/etc/udev/rules.d/network_drivers.rules 
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1786", RUN+="/sbin/modprobe -qba rt2870sta"
```

So, Network Manager see wlan but doesn't see any networks. I've installed Wifi radar and it don't see any networks too, but I'm sure there is wifi here. I've called for help one guy who looked on my Ubuntu and told that drivers set incorrectly. He don't know how to fix it.

Can anybody look on quoted info and tell me if my wireless adapter works properly? And if it's not - how to fix?

---

### Post by chili555 on 2010-09-11
> RTxx70 Wireless  ESSID:"11n-AP"  Nickname:"RT3070STA"This has the earmarks of a compile from a file downloaded from Ralink. Did you? If so, please do:```
cd directory/you/downloaded
sudo su
make uninstall
exit
```Now reboot and run your tests above again and let us hear your report.

---

### Post by zelibobla on 2010-09-11
Hello Chili555! Thanks for reply!

This was driver I've downloaded from one of your posts:
[http://ubuntuforums.org/showpost.php?p=8916939&postcount=17](http://ubuntuforums.org/showpost.php?p=8916939&postcount=17)

I guess this file originally from Ralink, but not sure. Anyway I've uninstalled it. Here is report:

```
zeliboba@zeliboba:~$ dmesg | grep -e rt2 -e rt3
[    9.371940] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.383477] usbcore: registered new interface driver rt2870

```

```
zeliboba@zeliboba:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1786 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```
zeliboba@zeliboba:~$ iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

/etc/modprobe.d/network_drivers.conf
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1786" > /sys/bus/usb/drivers/rt2870/new_id

```

/etc/udev/rules.d/network_drivers.rules
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1786", RUN+="/sbin/modprobe -qba rt2870sta"

```

---

### Post by chili555 on 2010-09-11
Now can you click the Network Manager icon and connect? How about:```
sudo iwlist wlan0 scan
```

---

### Post by zelibobla on 2010-09-11
```
zeliboba@zeliboba:~$ sudo iwlist wlan0 scan
[sudo] password for zeliboba: 
wlan0     No scan results

```

I haven't got network manager (uninstalled it in cause of bad behaviour and set eth1 manually). But especially for this expirement I've installed it back. It does see an wireless ineterface but doesn't recognize any wireless network.

I'm sure there are wireless networks here cause in my HTC mobile, that lies on the table close to plugged in my laptop ASUS N10, I can see 4 wireless networks.

---

### Post by chili555 on 2010-09-11
Let's try:```
sudo iwconfig wlan0 rate auto
sudo iwconfig wlan0 txpower 20
sudo iwlist wlan0 scan
```If *txpower 20* causes an error, try 18, 16, etc. until it works with no error.

Any scan results?

---

### Post by zelibobla on 2010-09-11
```
zeliboba@zeliboba:~$ sudo iwconfig wlan0 rate auto
[sudo] password for zeliboba: 
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 20
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 18
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 16
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 14
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 12
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 10
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 8
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 6
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 4
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwconfig wlan0 txpower 2
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.
zeliboba@zeliboba:~$ sudo iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by chili555 on 2010-09-11
May I see:```
cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf
sudo cat /var/log/syslog | grep rt2
```The last command will produce many dozens of lines of output; we only need the last 20 or so. I am a bit mystified (so far) as to why this doesn't spring to life.

---

### Post by zelibobla on 2010-09-11
```
zeliboba@zeliboba:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

```

```
zeliboba@zeliboba:~$ cat /etc/NetworkManager/nm-system-settings.conf 
[main]
plugins=ifupdown,keyfile

no-auto-default=00:15:c5:6a:8a:c7,

[ifupdown]
managed=false

```

```
zeliboba@zeliboba:~$ sudo cat /var/log/syslog | grep rt2
[sudo] password for zeliboba: 
Sep 11 17:56:43 zeliboba kernel: [    9.371940] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Sep 11 17:56:43 zeliboba kernel: [    9.383477] usbcore: registered new interface driver rt2870
Sep 11 18:36:28 zeliboba kernel: [    8.965228] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Sep 11 18:36:28 zeliboba kernel: [    8.993147] usbcore: registered new interface driver rt2870

```

I've killed some comments in first two quotes and the third one didn't contain dozen info. I've put here all output.

---

### Post by chili555 on 2010-09-11
I believe we have the wrong driver. I don't believe this is an rt2870sta device at all. Just so we don't confuse the searchers, please start a new thread and PM me the link.

Please see:> Hello Chili555! Thanks for reply!

This was driver I've downloaded from one of your posts:
[http://ubuntuforums.org/showpost.php...9&postcount=17](http://ubuntuforums.org/showpost.php...9&postcount=17)
The post you linked says:> {USB_DEVICE(0x0B05,0x[COLOR="Blue"]1784[/COLOR])}, /* Asus 3070 */ However, you said you have:> Bus 001 Device 002: ID 0b05:[COLOR="Red"]1786[/COLOR] ASUSTek Computer, Inc. 
Close, but not close enough.

I believe we need to adapt r8192s_usb for your device.

I'm sorry I didn't catch this sooner.

---

### Post by koanhead on 2010-09-16
Hello all, I have filed a bug on this issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624339](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624339)

Following that link, there's a link on the page labeled "This bug affects me". Please consider clicking on this link if you are affected by this issue. Please **only** click the link if your device has USB ID **0b05:1784**.

Since the fix seems to be known, it shouldn't be too hard to get this ironed out so that these devices work out of the box.

---

### Post by dgpe on 2010-09-21
I have been battling with the Asus USB-N13 adapter for a few days.  Got it to work on one machine after digging through lots of stuff and finally applying the approach given in Message #35.  Trouble was I wasn't sure if it was that final approach that did the whole thing or some combination of that with the earlier things I tried.

Tried it on a second machine just applying the method in Message #35, with no success.  Eventually found another message elsewhere saying that they had found that their /etc/Wireless/ directory did not include an RT2870STA folder and creating one (by copying the RT3070STA folder) had fixed the problem.  I found the same thing, and it also solved the problem for me.

Still not sure if blacklisting rt2800usb was necessary or not (as indicated in another thread) but I did it as part of the whole procedure and it all works so I don't intend to mess around with it.

Not sure what the lesson from this is - thrashing around until something works isn't a great approach to problem solving but that seems to be what I do every time!

---

### Post by ario on 2010-10-02
> ```
gedit os/linux/usb_main_dev.c
```At or near line 45, you will find a listing of PCI IDs. Add a new line:Make doubly sure that the indentation and spacing exactly matches the existing lines. I did my change at the top. Please see attached. Proofread carefully, save and close gedit.```
make
make install
modprobe rt3070sta
iwconfig
```Please report your progress.

I saw the file. There was no such a list. There is one in common folder named rtusb_dev_id.c with the mentioned list in it. But adding the line in this on top of the list will not change any thing and the unknown symbol in module error is still exists.
Any Idea?
Thanks.

---

### Post by chili555 on 2010-10-02
> Any Idea?
Thanks.You are asking in at least four threads that I know of. Do you mind if we try to get your wireless sorted in one place only?

[http://ubuntuforums.org/showthread.php?t=1585225](http://ubuntuforums.org/showthread.php?t=1585225)

I will be glad to help you in one place, please.

---

### Post by ario on 2010-10-03
> **chili555 said:**
> You are asking in at least four threads that I know of. Do you mind if we try to get your wireless sorted in one place only?

[http://ubuntuforums.org/showthread.php?t=1585225](http://ubuntuforums.org/showthread.php?t=1585225)

I will be glad to help you in one place, please.

Sure, Sorry. Just here I will be:
[http://ubuntuforums.org/showpost.php?p=9919355&postcount=11](http://ubuntuforums.org/showpost.php?p=9919355&postcount=11)

---

### Post by mrnuxi on 2010-10-09
Hi there,
I am a very experienced linux user, and just got Ubuntu 10.04 running on a live USB stick (with persistence). I have the Asus USB-N13 wireless usb dongle, which worked flawlessly on my MSI Wind U100 netbook. I got it because it works very well in wireless N mode (300Mbs) connecting to a Buffalo WHR-HP-G300N access point under the installed Windows XP that came on the netbook. Using the instructions here from Chili555, I easily got it working under Ubuntu (simply by editing the two files and rebooting). However I only get wireless g speed. Has anyone been able to get wireless N speed with this under Ubuntu? Note that it works perfectly at N speed under windows.

---

### Post by WarmonkeyUK on 2010-10-15
Sorry to duplicate this in several threads. Most people are having some success at getting building from source, but this no longer works on Maverick. The make crashes out with errors, and thus you are unable to install the driver. Any ideas on where to go from here?

---

### Post by BlocknBleed on 2010-10-30
Use the instructions on number 35 of this thread, and for me, what finally made it work right was the renaming of things in #58. 

Thanks so much to chilli555, pooshtick(sp?) and redsultan for trailblaizing here guys. I lookforward to more Ubuntu. 



This also worked for me.
The only difference is that in editing the files I changed everything from rt2870 to rt3070. Opposite for some reason from what chilli555 recommended in #58.

Big thanks to everyone who helped.

---

### Post by chili555 on 2010-10-30
> I changed everything from rt2870 to rt3070. Opposite for some reason from what chilli555 recommended in #58.You are evidently running 9.04 where the rt3070sta module was separate. It has now been merged with rt2870sta and does not exist stand-alone in 10.10 nor, if I remember correctly, in 10.04.```
$ modinfo rt2870sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    [COLOR="Red"]RT2870/RT3070[/COLOR] Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
```

---

### Post by d3u5 on 2010-11-01
I also had some prolems with the Asus n13 on Ubuntu 10.10.

I think for users with Ubuntu 10.* and higher, do what chili555 said in post [**#58. **]("http://ubuntuforums.org/showpost.php?p=9445731&postcount=58")

I was not able to "make" and "make install" (had an error 2) the drivers on the cd and downloaded from ralink. What helped was making the 2 files specified in post [**#58**]("http://ubuntuforums.org/showpost.php?p=9445731&postcount=58")

As said in this topic: drivers rt3070 are merged with rt2870 so using post 17 won't help anymore in Ubuntu 10.10 and higher.

---

### Post by coyote2 on 2010-11-20
Hi just an update. 

I followed the adding two files method without recompiling, the N13 works in ubuntu 10.10 but only connects at 54G speed. 

I followed adding the two files plus compiling the drivers from chili55, the N13 is detected in ubuntu 10.04 but network manager keeps prompting me to reenter the passphrase. 

Some thing is still missing...

---

### Post by coyote2 on 2010-11-21
On Ubuntu 10.04, here is how to do it.

First uninstall the faulty driver by doing

cd 'old driver directory'

sudo make uninstall

Next, goto 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Download the 2.4.0.1 version for RT2870. Untar.

gedit os/linux/config.mk

Set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'

I have no idea why default = 'n'? 

next, do 

sudo make
sudo make install 

reboot

now my iwconfig looks like this 

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"fedoragroup"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 94:0C:6D:B2:74:54   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-41 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So, connection is more normal now, but still it's stuck at rate = 54 Mb/s.

Guess I have gotten both 10.04 & 10.10 both run at 54Mb/s.
Any more configuration in the driver file I should modify before recompiling to enable 300mbps?

---

### Post by flawedexistence on 2010-11-26
THis is something I'd like to know also.  After several (6) fresh installs, I got my usb-n13 working "out of the box", but it is stuck at 54gb.  I'd love to know how get it working at 300!

---

### Post by tibug on 2010-11-28
I was having trouble with my usb-n13 adapter in 10.04.  I'm pretty inept with this command line stuff, but thanks to chili555, poohstickz, and redsultan (and others, I'm sure), I'm up and running and this old laptop has a bit more life left in it!

That's all.  Keep it up!

Thanks guys! :popcorn:

---

### Post by prayersfor.rain on 2010-12-23
Hello,
 I'm running 9.10 Karmic, super fresh install. Haven't even been able to do updates yet because I can't get the internet going.  I'm not super fresh to Ubuntu but I'm not that great at it either, I'm good at copy pasting.
 I really hope I can get this working.  If I can do it, I'm going to try and get it working on Zenwalk as well.  If not, I'll be living in WinXP land.
 

 Anyway I've got the Asus USB-N13.
 I did post 17, post 35, and then post 58 of this thread.
 Network Manager now shows Wired & Wireless networks (before it just showed Wired, or nothing), but doesn't pick up any wireless networks (there should be about 4 showing up, 0 wired)
 I've tried creating a new wireless network and it'll show up, look like it's trying to connect, not connect, and if I click Disconnect it disappears completely like it doesn't exist...the computer no longer finds it.

 

 This is what I get when I do lsusb (after changes, for some reason I didn't think to do it before):
 Bus 001 Device 002: ID 0b05:1784 AsusTek Computer, Inc.
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 002 ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 Any help would be greatly appreciated!!

---

### Post by chili555 on 2010-12-28
> **prayersfor.rain said:**
> Hello,
 I'm running 9.10 Karmic, super fresh install. Haven't even been able to do updates yet because I can't get the internet going.  I'm not super fresh to Ubuntu but I'm not that great at it either, I'm good at copy pasting.
 I really hope I can get this working.  If I can do it, I'm going to try and get it working on Zenwalk as well.  If not, I'll be living in WinXP land.
 

 Anyway I've got the Asus USB-N13.
 I did post 17, post 35, and then post 58 of this thread.
 Network Manager now shows Wired & Wireless networks (before it just showed Wired, or nothing), but doesn't pick up any wireless networks (there should be about 4 showing up, 0 wired)
 I've tried creating a new wireless network and it'll show up, look like it's trying to connect, not connect, and if I click Disconnect it disappears completely like it doesn't exist...the computer no longer finds it.

 

 This is what I get when I do lsusb (after changes, for some reason I didn't think to do it before):
 Bus 001 Device 002: ID 0b05:1784 AsusTek Computer, Inc.
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 002 ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 Any help would be greatly appreciated!!Let's take a look at:```
lsmod | grep rt2
dmesg | grep -i rt2
modinfo rt2870sta | grep -i version
```Thanks.

---

### Post by prayersfor.rain on 2010-12-29
Hi Chili, thanks for responding!
when i put in:
lsmod | grep rt2 I get: 

rt2870sta             488820  1
 

 dmesg | grep -i rt2 [    9.183455] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [    9.187175] usbcore: registered new interface driver rt2870  
 [   14.963559] --> Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat  
 

 modinfo rt2870sta | grep -i version 

 version:        1.4.0.0  
 srcversion:     E5C45807808E721690B4101 
 vermagic:       2.6.31-14-generic SMP mod_unload modversions 586
 

 

 

 Also, now when I'm in Ubuntu the icon thingy spins like it's trying to connect and asks for password, I put it in, it spins some more, and then the password screen comes up again.

---

### Post by chili555 on 2010-12-29
> Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.datLet's create a file and see if it helps. Please do:```
sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```The text editor will open, presumably with a new empty file. Type in one word:```
Default
```Proofread, save and close gedit. Reboot and give us your report.

---

### Post by prayersfor.rain on 2010-12-29
It won't let me save, a red box comes up on the editor and says “Could not find the file /etc/Wireless/RT2870STA/RT2870STA.dat”

---

### Post by chili555 on 2010-12-29
Perhaps a needed directory is missing. Let's create them and then proceed:```
sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT2870STA
```If they are already present, just continue. Then edit the file as in my post above.

---

### Post by prayersfor.rain on 2010-12-29
Ok.  The first command came back as already being there.  The second one got created I think as I was able to edit the file, rebooted.
  The icon looks like it's “thinking” still and when I click on it, my wireless network now shows up (YAY!) but it doesn't connect.  If I click on it it says “Wireless Network disconnected”
 


 I have to go for a few hours so I'm sorry if I don't get back to you for a while.  So if you've got other things to do! Don't rush :)

---

### Post by chili555 on 2010-12-29
Let's see the diagnostic again:```
dmesg | grep -i rt2
dmesg | grep wlan
```Thanks.

---

### Post by prayersfor.rain on 2010-12-30
dmesg | grep -i rt2when I put: dmesg | grep -i rt2


 I get:
[    8.258820] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [    8.262504] usbcore: registered new interface driver rt2870  
 

 when I put: dmesg | grep wlan
I get nothing.

Icon still spins, it asks for password, etc.

---

### Post by chili555 on 2010-12-30
> when I put: dmesg | grep wlan
I get nothing.That means the interface is ra0 and not wlan0. Please post:```
dmesg | grep ra0
sudo cat /var/log/syslog | grep ra0
```If the last command produces a lot of output, try to omit the repeats and post the remainder.

---

### Post by prayersfor.rain on 2010-12-30
dmesg | grep ra0 [   26.592036] ra0: no IPv6 routers present  
 [   40.178143] rtusb_disconnect: unregister_netdev(), dev->name=ra0!  
 [   54.620019] ra0: no IPv6 routers present 

 
sudo cat /var/log/syslog | grep ra0  
Dec 30 10:47:56 d00m-desktop NetworkManager: <info>  (ra0): supplicant interface state:  starting -> ready  
 Dec 30 10:47:58 d00m-desktop avahi-daemon[985]: Registering new address record for fe80::22cf:30ff:fea2:2127 on ra0.*.  
 Dec 30 10:48:07 d00m-desktop kernel: [   24.592009] ra0: no IPv6 routers present  
 Dec 30 10:48:07 d00m-desktop NetworkManager: <info>  Activation (ra0) starting connection 'nittnen'  
 Dec 30 10:48:07 d00m-desktop NetworkManager: <info>  (ra0): device state change: 3 -> 4 (reason 0)  
 

 Dec 30 10:48:07 d00m-desktop NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)  
 Dec 30 10:48:07 d00m-desktop NetworkManager: <info>  Activation (ra0/wireless): access point 'nittnen' has security, but secrets are required.  
 Dec 30 10:48:07 d00m-desktop NetworkManager: <info>  (ra0): device state change: 5 -> 6 (reason 0)  
 

 Dec 30 10:48:18 d00m-desktop NetworkManager: <info>  (ra0): device state change: 6 -> 4 (reason 0)  
 

 Configure) starting...  
 Dec 30 10:48:18 d00m-desktop NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)  
 Dec 30 10:48:18 d00m-desktop NetworkManager: <info>  Activation (ra0/wireless): connection 'nittnen' has security, and secrets exist.  No new secrets needed.  
 Dec 30 10:48:18 d00m-desktop NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete.  
 Dec 30 10:48:18 d00m-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected  
 Dec 30 10:48:18 d00m-desktop NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning  
 Dec 30 10:48:18 d00m-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating  
 Dec 30 10:48:28 d00m-desktop NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected  
 

     Dec 30 20:31:17 d00m-desktop NetworkManager: <info>  (ra0): device state change: 6 -> 9 (reason 7)  
 Dec 30 20:31:17 d00m-desktop NetworkManager: <info>  Activation (ra0) failed for access point (nittnen)  
 Dec 30 20:31:17 d00m-desktop NetworkManager: <info>  Activation (ra0) failed.  
 Dec 30 20:31:17 d00m-desktop NetworkManager: <info>  (ra0): device state change: 9 -> 3 (reason 0)  
 Dec 30 20:31:17 d00m-desktop NetworkManager: <info>  (ra0): deactivating device (reason: 0). 







Hopefully I included the correct information. I saved the entire thing just in case!

---

### Post by chili555 on 2010-12-31
I wonder if Network Manager is refusing to connect the wireless because you simultaneously have wired ethernet connected. Is there an ethernet cable attached? Please detach it and try again.

---

### Post by prayersfor.rain on 2010-12-31
That I know of I'm not connected to anything through wired ethernet.  Like I'm not connected to any of the other computers in the house, and I'm getting on the internet by dual booting winxp (the dongle works there).

---

### Post by coyote2 on 2010-12-31
With the latest ubuntu 10.10 2.6.35-24-generic-pae kernel, the Asus USB-N13 300Mbps adapter is fully plug & play. Unfortunately, I moved the N-router to my mum's place, unable to confirm the kernel allows it to connect at 300N speed. 

In the earlier kernel version for 10.10, adding the two lines allow it to connects at 54G speed to the N router only.

---

### Post by Craig_W on 2011-01-01
Hi and Happy New Year, new poster and new to Ubuntu to boot. 

I have had great success getting the Asus N13 to work manys thanks to the original poster, Chilli555 and all other contributors. 

Should anyone be kind enough to find out how to configure it to 802.11n speeds i would be most grateful

Regards Craig

---

### Post by prayersfor.rain on 2011-01-01
> **coyote2 said:**
> With the latest ubuntu 10.10 2.6.35-24-generic-pae kernel, the Asus USB-N13 300Mbps adapter is fully plug & play. Unfortunately, I moved the N-router to my mum's place, unable to confirm the kernel allows it to connect at 300N speed. 

In the earlier kernel version for 10.10, adding the two lines allow it to connects at 54G speed to the N router only.

I'm sticking with 9.10 because I know it works for me.  When 10.04 came out I tried it and got a frozen mouse that required restart.  When I tried to upgrade to 10.10 by first moving to 10.04 my mouse would freeze every time right before I had the chance to upgrade to 10.10.  I've searched forums for fixes for that problem but haven't found anything.  But no matter, because I have 9.10 and I'm not installing anything I don't know works for sure for sure.

Now to get this thing working with it.

---

### Post by hallandnash on 2011-01-07
I can't seem to get by the make stage, using either the driver in this thread or the newest one from ralink.

Here's the output:
```

~/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ sudo make

make -C tools
make[1]: Entering directory `/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/lisa/myinstalls/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2


```

```
$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

any help would be great

---

### Post by chili555 on 2011-01-07
What has been your experience with the native driver rt2870sta? Please post:```
sudo modprobe rt2870sta
lsmod | grep rt2 
dmesg | grep -i rt2
```Thanks.

---

### Post by hallandnash on 2011-01-07
> **chili555 said:**
> What has been your experience with the native driver rt2870sta? Please post:```
sudo modprobe rt2870sta
lsmod | grep rt2 
dmesg | grep -i rt2
```Thanks.

I'm assuming this was for me :) ... 

I've never gotten anything to install or work with this usb. Currently I have my internal wifi working.. but that's all

```

$ sudo modprobe rt2870sta
$ lsmod | grep rt2
rt2870sta             405890  0 
crc_ccitt               1351  1 rt2870sta
 $ dmesg | grep -i rt2
[  735.021326] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  735.039687] usbcore: registered new interface driver rt2870

```

---

### Post by chili555 on 2011-01-07
> I'm assuming this was for me Yes, indeed. Because this is getting long and confusing, please start a new thread and send me a private message if I don't catch it.

So far so good.

---

### Post by pythonX13 on 2011-01-11
I don't think I managed to read the entire thread, and this may have come up. (Sry if this is rule-breaking then.) I mangled and mashed through the above steps before updating Ubuntu at all. I just did a fresh install of 10.10 x64 the day before. 

Worked fine after I updated. This may apply to some users, idk.

---

### Post by polarbear10 on 2011-02-21
I tried Chili's bits and Post 35 here and found that when I was done I couldn't connect with "n" speeds...  I decided to look further and managed to install the latest drivers

DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

see the thread here - I have it working properly now :D

[http://ubuntuforums.org/showthread.php?p=10481486](http://ubuntuforums.org/showthread.php?p=10481486)

---

### Post by olddouane on 2011-04-05
Hi Chili555 and thanks for the help in your #58
It was my first ubuntu-project to get this dongle work in Ubuntu10.10

---

### Post by thenickrulz on 2011-04-08
Sometimes mine cuts out... is there a way to fix this?

---

### Post by thenickrulz on 2011-04-08
Actually might wait until the new Ubuntu comes out.. it should be fixed then.....! 11.04!

---

### Post by khul on 2011-06-19
Did it work in 11.04? I had it working in 10.10, after fixing a couple of
compilation errors in the ASUS-provided code and doing the installation using insmod and cp since "make install" is confused about driver/firmware names. 

But after switching to 11.04 I cannot insmod my driver, since there is a bunch of modules already loaded. I guess they ought to handle the device, but they don't seem to. The network applet says something like "no firmware available" and I cannot scan for networks.

I guess I'll try to stop the loading of some modules  (if I can figure out how and which) and put in the one I compiled as before.

---

### Post by chili555 on 2011-06-19
> **khul said:**
> Did it work in 11.04? I had it working in 10.10, after fixing a couple of
compilation errors in the ASUS-provided code and doing the installation using insmod and cp since "make install" is confused about driver/firmware names. 

But after switching to 11.04 I cannot insmod my driver, since there is a bunch of modules already loaded. I guess they ought to handle the device, but they don't seem to. The network applet says something like "no firmware available" and I cannot scan for networks.

I guess I'll try to stop the loading of some modules  (if I can figure out how and which) and put in the one I compiled as before.Please show us:```
lsmod
```Thanks.

---

### Post by Mud.Knee.Havoc on 2011-07-03
> **thenickrulz said:**
> Actually might wait until the new Ubuntu comes out.. it should be fixed then.....! 11.04!

Unfortunately, it's not fixed in 11.04. :(

---

### Post by satkins on 2011-07-14
I picked up one of these adapters a couple of weeks ago.  I was able to get it up and running using the network manager after getting the drivers from Asus.

But since I'm running a MythTV box on this machine I would like to have ra0 come up before gdm auto logs in.  A new kernel came out tonight (at least for me) on my 11.04 Mythbuntu box.  After upgrading I removed the network manager then recompiled the drivers for the n13 setting HAS_WPA_SUPPLICANT=Y and  HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=N and installed.

The drivers come up when I plug in the device.  In the /etc/Wireless/RT2870 dir I added my ssid and my key to the wpa2psk fields.  I connects to the router but won't authenticate.  I'm not sure if I have this right or not.

Thanks for any help

Stephen

---

### Post by chili555 on 2011-07-15
> I would like to have ra0 come up before gdm auto logs in.Does it run headless; that is without a monitor and no display manager such as Gnome or Unity? If so, and particularly if you've removed Network manager, the usual way to handle this is to amend /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
wpa-essid <your_router>
wpa-psk <your_key>
```If you want to easily access the MythTV machine, I'd probably use a static IP outside the range of addresses used by the DHCP server in the router:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
wpa-essid <your_router>
wpa-psk <your_key>
```

---

### Post by satkins on 2011-07-16
Thanks for the info.  I doesn't need to be with out the network manager but I've had issues with Mythtv if it does.  Basically because mythtv-backend won't run with out network and gnome hasn't logged in (automatically btw) when it tries to start mythtv-backend it fails and will only start manually.

So to fix it I have the wired network starting as static and it comes up before gnome does so the backend starts properly.  Now I wanted to move this machine to an area with no wired network so it kinda does need to start with out gnome running.

Thanks again.

---

### Post by chili555 on 2011-07-16
I don't believe Network Manager will start without Gnome and so I believe the method I proposed above is the answer.```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
wpa-essid <your_router>
wpa-psk <your_key>
```Have you tried it? Does it work?

---

### Post by satkins on 2011-07-16
Right I don't want the network manager and I've uninstalled it.

I'm currently trying your solution but it's not working and I'm not sure why.  Here is what I currently have been trying in my interfaces file:

auto ra0
iface ra0 inet dhcp
wpa-ssid VE6CPU-N
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
spa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 6676dfcaabexxxxxxxxxxxxxxxx7a020ce1e98352eb31382xxxxxxxxxxxxxxxx

In my router logs I see it connect but authentication fails.  I've blurred out some of my hex key but I've double checked and it is the full key that wpa_passphrase supplies.  Is this because I'm trying to use WPA2?  Or possibly because I'm using AES?

Stephen

---

### Post by chili555 on 2011-07-16
> full key that wpa_passphrase suppliesIn this file, you do not use a wpa_passphrase encrypted key; you use the key in plain text. Your file looks a bit busy. I suggest:```
auto ra0
iface ra0 inet dhcp
wpa-ssid VE6CPU-N
wpa-psk <your_key>
```Restart the interface:```
sudo ifdown ra0 && sudo ifup ra0
```Does it connect?

---

### Post by satkins on 2011-07-16
Changed the key to plain text.  No go with the stripped down interfaces file.

EDIT:

Okay I'm just not awake yet or something.  I decided to re-read the entire thread and even though I saw many people say "Just follow post #35" and I've read it many times, I just never created those two files.  After I did those two and rebooted, BANG!  I've got wireless.

Sorry for wasting your time Chilli555.  I do appreciate all the help you have given me.  Now to get some coffee or sleep.  Not sure which yet.

---

### Post by chili555 on 2011-07-16
I was happy to help. Glad it's working. Have some sleep and then have fun!

---

### Post by robbiebravo on 2011-07-16
Here is how I got the ASUS-N13 USB working on wireless N speed in Ubuntu 10.04 Lucid. I'm a noob, it's my first post with code and such, so go easy on the mistakes, i hope this helps someone. All these steps are outlined somewhere in this forum. Since you got to this page you may have to remove some thing you've tried  before, with a first install you could start at step 7.


[LIST=1]
[*]make sure any remains of a last install are removed, in the directory where you downloaded the drivers you installed before ```
sudo make uninstall
```
[*]you may have to remove some files manually ```
cd /lib/modules/2.6.xx-xx-generic/kernel/drivers/net/wireless 
sudo rm rt2870sta.ko
sudo rm rt3070sta.ko
``` where xx-xx stands for your kernel.
[*]and also check to see if there's nothing left in "/etc/Wireless"```
cd /etc/Wireless
sudo rm -Rf RT2870STA
sudo rm -Rf RT3070STA
```
[*]you might need to remove any already loaded modules: ```
sudo modprobe -r rt2870sta
sudo modprobe -r rt3070sta
```
[*]Also check if there are no modules automatically loading from your previous attempts and remove them from the file: ```
sudo gedit /etc/modules
```
[*]I also made sure there was nothing in:  "/etc/udev/rules.d/network_drivers.rules" and  "/etc/modprobe.d/network_drivers.conf" ie the files should be empty, before starting a new install. ```
sudo gedit /etc/udev/rules.d/network_drivers.rules
sudo gedit /etc/modprobe.d/network_drivers.conf
```
[*]Now you can start making a new installation. Downloading the 2.1.0.0 driver only gave me 'G' speeds, I used the 2.3.0.2 driver and got 'N' speeds, get it here: [http://uk.asus.com/Networks/WiFi_Networking/USBN13/#download](http://uk.asus.com/Networks/WiFi_Networking/USBN13/#download)
[*]unpack and change directory to the driver you just downloaded. Now here is the trick, **you have to rename the file "RT2870STA.dat" to RT3070STA.dat" otherwise the "sudo make install" will give you errors**
[*]In the file "/os/linux/config.mk" mark "y" under both network manager and wpa_supplicant support: ```
 sudo gedit /os/linux/config.mk
```
[*]Go back to the driver directory and run ```
sudo make
sudo make install
``` (I did not have to edit the "/os/linux/usb_main_dev.c" file in the 2.3.0.2 version)
[*]Now create/edit this file ```
sudo gedit /etc/udev/rules.d/network_drivers.rules
``` in which you paste: ```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"
```
[*]Create/edit this file: ```
sudo gedit /etc/modprobe.d/network_drivers.conf
``` paste into this file: ```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```
[*]Notice that **none of the lines says "rt3070sta" anywhere**,** change all of them to "rt2870sta"** THIS IS VERY IMPORTANT, without it i couldn't get it to work
[*]reboot
[*]check iwconfig, should give you 'N' speeds, done.
[/LIST]

---

### Post by miguelh3000 on 2011-08-04
> **AnothrNmbr said:**
> fwiw, i followed #35 (prepending 'sudo' to everything) and then followed the fixes in #58 and everything is working perfectly now.  thanks for your help guys.

ji

Hi guys,

I registered to also say that I followed #35 and then the fix on post #58 and was able to install the wireless adapter. Took me 5 hours of understanding Ubuntu and reading, and trial and error but I got it with the help from this forum. Thanks!

PS: In my case, only the newest driver, RT5370 v2.5.0.1, [from this post]("http://ubuntuforums.org/showpost.php?p=10347892&postcount=2") would install without giving me a "'LINUX' error 2". Besides that, the steps from the above two post's worked.

---

### Post by wdutcher on 2011-08-06
Hi All.  I'm looking for some help with my recently purchased USB-N13.  I'm now running 11.10 Alpha3 (which I upgraded to in desperation after failing to get wireless networking up and running on 11.04).

I've generally tried everything posted here and elsewhere, though a bit haphazardly.  With the latest drivers from Ralink, and using the firmware included with 11.10 Alpha3 this is my current state:

```

% uname -mr
3.0.0-7-generic x86_64


```

After installing the rt2870sta.ko
```

% sudo insmod rt2870sta.ko

% dmesg
...
[ 3708.551716] rtusb init --->
[ 3708.551772] usbcore: registered new interface driver rt2870


```

But, no wlan
```

% sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

```

% lsusb | grep 2870
Bus 002 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT2870]

% lsmod | grep rt2870
rt2870sta             629991  0 


```

A little bit on how I got here might be relevant...
- Tried a TP-LINK TL-WN722N with Ubuntu 11.04.  Wireless interface seemed to function and recognize available networks, but I couldn't authenticate.
- After googling a bit, I decided to return the TP-LINK and buy the Asus USB-N13, hoping it'd plug-n-play... but same result.  Started looking at all the posts on this and other forums and going down the path of installing the latest drivers.
- Latest Ralink driver:  Whether on 11.04 or 11.10, my current state (no wireless network interface) is the furthest I've been able to get with this driver.
- Latest driver on the ASUS website for USB-N13: With this older driver, I'm able to get a bit further.  The wireless network interface is available as ra0 and available wirelss networks show up in the network manager.  However, I'm not able to connect/authenticate to my home network.

Any guidance or suggestions on how to get wireless up and running with this adapter on 11.10?

---

### Post by coyote2 on 2011-08-06
I  followed the instructions at post 137 & managed to get the wireless interface working. 

However, no matter whether I use version RT5370 v2.5.0.1 or 2.3.0.2, I am still just connected at 54Mbps.

Any chance I have to do some settings on my Asus RT-N16 router? 

I have already set 

channel bandwidth to 40MHz
Tried channel = auto, 3, 4 all the same.

thing is, everything is working, but iwconfig shows 54Mbps no matter what I do.

---

### Post by chili555 on 2011-08-06
@wdutcher--

See my PM.

---

### Post by mycotropic on 2011-08-27
Hi I downloaded the newest install disk and I have no wireless using this exact same ASUS device. I can go into network Tools, select, Wireless interface (wlan0), configure with the network name and security and I have nothing. The network connection "Last Used" is "never" and nothing I can do changes it at all. Is this a problem with the USB device, the drivers or what? How can you even tell?

iwconfig shows wlan0 as IEEE 802.11bgn ECCID:off/any Mode:Managed access point: not associated tx-power=0 dbm retry long limit:7 rts thr:off fragment thr:off power management:on

any clues?

---

### Post by chili555 on 2011-08-27
> **mycotropic said:**
> Hi I downloaded the newest install disk and I have no wireless using this exact same ASUS device. I can go into network Tools, select, Wireless interface (wlan0), configure with the network name and security and I have nothing. The network connection "Last Used" is "never" and nothing I can do changes it at all. Is this a problem with the USB device, the drivers or what? How can you even tell?

iwconfig shows wlan0 as IEEE 802.11bgn ECCID:off/any Mode:Managed access point: not associated tx-power=0 dbm retry long limit:7 rts thr:off fragment thr:off power management:on

any clues?Let's have a look at:```
lsmod | grep rt2
```Thanks.

---

### Post by mycotropic on 2011-08-27
i can't cut and paste because i'm on a laptop (also ubunto, 8.04, operating perfectly fine on the same wireless network) so i have to type the output;

rt2870sta   410104 0
rt2800usb    17907 0
rt2800lib    43824 1 rt2800usb
crc-ccitt    12595  2 rt2870sta, rt2800lib
rt2x00usb  19693  1 rt2800usb
rt2x00lib  39075  3 rt2800usb, rt2800lib, rt2x00usb
mac80211  257001  3 rt2800lib, rt2x00usb, rt2x00lib
cfg80211  156212  2 rt2x00lib, mac80211

---

### Post by chili555 on 2011-08-27
Pllease see here: [https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04](https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04)

---

### Post by mycotropic on 2011-08-27
Thanks, it's trying to connect and probably hanging my router settings. Thanks very much for the help!

---

### Post by Need_your_Advice on 2011-11-17
Chili55

I need your help.  I tried to install the driver you had on your #17 (2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2) so my Wireless adapter USB-N13 would work.

I thought I had succeeded until I  typed iwconfig in a terminal window and noticed that the 'Bit Rate and the RTS' were missing.

Code:
    **** horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ iwconfig
        lo        no wireless extensions.

        eth0      no wireless extensions.

        ra0       RT2870 Wireless  ESSID:""  
                  Mode:Auto  Frequency=2.412 GHz  
        ****      Bit rate is missing    
        ****      RTS ... is missing
                  Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
                  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                  Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I typed 'dmesg | grep -e rt3 -3 ra0' in the terminal window, nothing happened.  

    lsmod | grep -e rt2 -e rt3
    dmesg | grep -e rt3 -e ra0
    modinfo rt3070sta | grep -e version -e 1784

Code:
    **** horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ lsmod | grep -e rt2 -e rt3
        rt3070sta             512239  0 
    
Code:
             horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ dmesg | grep -e rt3 -e ra0
        **** NOTHING!

Code:
         horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ modinfo rt3070sta | grep -e version -e 1784
        version:        2.1.2.0
        srcversion:     490C020EB5EF0484E8F2833
        vermagic:       2.6.32-02063235-generic SMP mod_unload modversions 586  

I think I am close, but no cigar yet. Please help me to get it working.

What I did to install the driver, from start to finish including the reference I used as a guide, is in the attached file What_I_Did.gz.

---

### Post by chili555 on 2011-11-17
This is an old, old thread. What we did in early 2010 is no longer the preferred method. Need_your_Advice, please start your own new thread and post the information above plus:```
modinfo rt2870sta
```Thanks.

TO THE SEARCHERS: This is too old. Please start a new thread and we'll use new methods.

---

### Post by j_mill on 2012-04-12
> **chili555 said:**
> How much more could you want!?!? Did you click the Network Manager icon and try to connect?

I think you are moments from [SOLVED].

You just [SOLVED] my problem, chili555. Thank you!!

---

