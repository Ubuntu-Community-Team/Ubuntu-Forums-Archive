---
title: "Wireless stopped working after update."
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by KaiJordanDay on 2010-02-21
To get my wireless working I followed this guide: 
[http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt](http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt)


Now, after running a recent update (kernal headers I think) the wireless has stopped working and I have to use a USB (which is pretty damn annoying)

Any ideas?

Kai

---

### Post by chili555 on 2010-02-21
The *acerhk* module was built against a previous kernel version. Now that you have a newer kernel, and every time you get a newer kernel, or linux-image as we call it here in Ubuntu-land, you will need to rebuild it against the newer one.

There are a couple of methods listed in the file you linked and we have no way to know which you used. If you built from source, then:```
cd acerhk-0.5.35/

[COLOR="Red"]make clean[/COLOR]

make

sudo make install

```

---

### Post by KaiJordanDay on 2010-02-21
> kai@kai-laptop:~/acerhk-0.5.35$ sudo make
[sudo] password for kai: 
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:105: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:307: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [acerhk.ko] Error 2
kai@kai-laptop:~/acerhk-0.5.35$ sudo make install
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [acerhk.ko] Error 2
kai@kai-laptop:~/acerhk-0.5.35$ 


All sorts of errors chucked up there.

---

### Post by chili555 on 2010-02-21
It made for me with one warning and no errors. Did you do step #0?> 0) Install pre-requirements
$ sudo apt-get install build-essential linux-headers-$(uname -r)

---

### Post by KaiJordanDay on 2010-02-21
I know what errors I did. Now Its all installed, reboot PC and still no luck! LED comes on, but no wireless.

---

### Post by chili555 on 2010-02-21
By chance, are both acerhk and acer-wmi loaded?```
lsmod | grep acer
```You might try with one or the other, but not  both:```
sudo rmmod -f acer-wmi
```Any change? If not:```
sudo modprobe acer-wmi
sudo rmmod -f acerhk
```How about now?

Whatever works we can make permanent.

---

### Post by KaiJordanDay on 2010-02-21
> My Outputs:

kai@kai-laptop:~$ lsmod | grep acer
acerhk                 30296  0 
kai@kai-laptop:~$ sudo rmmod -f acer-wmi
[sudo] password for kai: 
ERROR: Removing 'acer_wmi': No such file or directory
kai@kai-laptop:~$ sudo modprobe acer-wmi
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting acer_wmi (/lib/modules/2.6.31-19-generic/kernel/drivers/platform/x86/acer-wmi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
kai@kai-laptop:~$ sudo rmmod -f acerhk




Seems acer-wmi isnt there?

---

### Post by chili555 on 2010-02-21
It is there, it just doesn't like some aspect of your kernel:> Unknown symbol in module, or unknown parameter (see dmesg)We might just check *dmesg* as suggested:```
dmesg | grep acer
```I also suggest, if you did not already do so:```
sudo rmmod -f acerhk
sudo modprobe acerhk autowlan=1
```Did a wireless interface get created?```
iwconfig
```

---

### Post by KaiJordanDay on 2010-02-21
> kai@kai-laptop:~$ dmesg | grep acer
[ 1512.557580] acer_wmi: Unknown parameter `autowlan'
[ 1520.544460] acerhk: removed.
kai@kai-laptop:~$ 


> kai@kai-laptop:~$ sudo rmmod -f acerhk
[sudo] password for kai: 
ERROR: Removing 'acerhk': No such file or directory


> kai@kai-laptop:~$ sudo modprobe acerhk autowlan=1
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

> kai@kai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:F3:A7:D6   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


All reports from what u said to do in order.

---

### Post by chili555 on 2010-02-21
> wlan1 IEEE 802.11g ESSID:"NETGEAR"
Mode:Managed Frequency:2.462 GHz Access Point: 00:1B:2F:F3:A76
Bit Rate=108 Mb/s
Power Managementff
Link Quality:76/100 Signal level:-47 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0That appears to be your USB; associated with your access point and working nicely.> wlan0 IEEE 802.11bg Mode:Managed Access Point: Not-Associated
Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power ManagementffThis appears to be your built-in, ready to rock. Please try unplugging the USB and see if the built-in will connect.

Case solved?

---

### Post by chili555 on 2010-02-21
> WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
We probably need to clean this up at some point. These are more irritants, not errors

---

### Post by KaiJordanDay on 2010-02-21
AH yes working now. Thanks a lot :)

Can you explain to me what made it work, so I know in future? (Don't worry if you don't have time too)

---

### Post by chili555 on 2010-02-21
> **KaiJordanDay said:**
> AH yes working now. Thanks a lot :)

Can you explain to me what made it work, so I know in future? (Don't worry if you don't have time too)Rebuilding acerhk against your current running kernel and them inserting it with the correct parameter, autowlan=1, I assume. Whenever you get a new kernel, the rebuild will need to be done, including the 'make clean' step as outlined above.

I am off for a while, but I will get back to you about the conf files as I posted above. In the meantime, please post:```
cat /etc/modprobe.d/options
```We'll work out how to fix it. The other file you can fix effectively with:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```I'll check in later. Glad it's working.

---

### Post by KaiJordanDay on 2010-02-21
> kai@kai-laptop:~$ cat /etc/modprobe.d/options
options acer-wmi force_series=6805 autowlan=1
kai@kai-laptop:~$ sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
[sudo] password for kai: 
kai@kai-laptop:~$ 


Outputs of the 2 above commands.

---

### Post by chili555 on 2010-02-21
Let's try the quick and easy way:```
sudo mv /etc/modprobe.d/options /etc/modprobe.d/options.conf
```If the acerhk module loads correctly on boot and wireless works as expected, then we're all good. If not, post back and we'll do some tweaking.

Find out, after a reboot, with:```
lsmod | grep acer
iwconfig
```If acerhk is a loaded module and if you have a wlan0 wireless interface, then we're done.

---

### Post by KaiJordanDay on 2010-02-21
> kai@kai-laptop:~$ lsmod | grep acer
acerhk                 30296  0 
kai@kai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:F3:A7:D6   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


After doing the command and reloading I get that ^

Also wireless has stopped again, and I've had to put mu USB back in.

---

### Post by chili555 on 2010-02-21
Please do:```
sudo rmmod -f acerhk
sudo modprobe acerhk autowlan=1
iwconfig
```Is wlan0 back? If not, please do:```
sudo rmmod -f acerhk
sudo modprobe acerhk force_series=6805 autowlan=1
iwconfig
```One of those is going to kick the wireless to life and we'll know how to tweak.

Moreover, the file /etc/modprobe.d/options.conf is not going to help us at all. It references acer-wmi which, as you recall, wouldn't load because of an error. 

I just, in my near-sightedness, noticed that it doesn't refer to acerhk, but to acer-wmi. We might as well remove it:```
sudo rm /etc/modprobe.d/options.conf
```Please also post:```
cat /etc/modules
```

---

### Post by KaiJordanDay on 2010-02-21
> kai@kai-laptop:~$ sudo rmmod -f acerhk
[sudo] password for kai: 
kai@kai-laptop:~$ sudo modprobe acerhk autowlan=1
kai@kai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:F3:A7:D6   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kai@kai-laptop:~$ sudo rmmod -f acerhk
kai@kai-laptop:~$ sudo modprobe acerhk force_series=6805 autowlan=1
kai@kai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:F3:A7:D6   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kai@kai-laptop:~$ sudo rm /etc/modprobe.d/options.conf


Still no wlan0 showing. Even after all the commands.

---

### Post by chili555 on 2010-02-21
I believe your built-in is an Atheros. If so, please post:```
dmesg | grep ath
rfkill list
```Thanks.

---

### Post by KaiJordanDay on 2010-02-21
Atheros A5001 Yes.

> kai@kai-laptop:~$ dmesg | grep ath
[    2.770622] device-mapper: multipath: version 1.1.0 loaded
[    2.770629] device-mapper: multipath round-robin: version 1.0.0 loaded
kai@kai-laptop:~$ rfkill list


---

### Post by chili555 on 2010-02-21
Please try:```
sudo modprobe ath5k
iwconfig
```If there is no wlan0, please do:```
dmesg | grep ath5k
```Thanks.

---

### Post by KaiJordanDay on 2010-02-21
> kai@kai-laptop:~$ sudo modprobe ath5k
[sudo] password for kai: 
kai@kai-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:F3:A7:D6   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


Its back there, but will it still be there on reboot?

Don't want to have to put sudo modprobe ath5k in every time lol.

---

### Post by chili555 on 2010-02-21
Let's just drop it into */etc/modules*:```
sudo gedit /etc/modules
```Use nano, kate or vim if you don't have gedit. Add two lines:```
ath5k
acerhk autowlan=1
```Proofread carefully, save and close gedit. Now reboot and let us know the result.

---

### Post by KaiJordanDay on 2010-02-21
Perfect, works after reboot.

Thanks a lot :)

---

### Post by macrules on 2011-05-08
> **KaiJordanDay said:**
> I know what errors I did. Now Its all installed, reboot PC and still no luck! LED comes on, but no wireless.

Hi,

Would you be so kind how you fixed that bounds error?
It is so darn irritating when one finds an error and the person reporting it says: yeah fixed!
Please share HOW!
Thank you

---

