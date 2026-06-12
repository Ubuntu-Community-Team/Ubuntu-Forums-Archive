---
title: "HELP with Atheros Wireless Lan 802.11b/g on ASUS"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by Kella on 2010-01-12
Hi all

I am quite a naive user in Ubuntu, although I have been using it for a few years now. Every time I came across any issue in the past I always managed to solve them thanks to comments and suggestions posted on online forums (very helpful!) - but now I can't get my mind around this new issue.

I am running Ubuntu 8.10 on Asus X53K and I had no problem whatsoever until yesterday when I run the last update available (through the Update Manager). After the update I cannot connect to the Internet via wireless (Atheros Wireless Lan 802.11b/g). It is working fine via ethernet but there's no way I can get the wireless LAN working. I tried to run these commands (see below) as this procedure always solved the problem in the past:

sudo aptitude update

sudo aptitude install build-essential subversion

cd ~

wget [http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz)

tar xvf madwifi-trunk-current.tar.gz

cd madwifi-trunk-r4031-20090529

# !Check the actual file name!

make

sudo make install

gksudo gedit /etc/modules

# Now add the Atheros kernel module ath_pci to the list of modules to be automatically loaded at boot by adding

ath_pci

# to the end of the /etc/modules file. (Gedit editor automatically opens)

gksudo gedit /etc/modprobe.d/blacklist.conf

# Now add the following 3 lines at the end of the /etc/modprobe.d/blacklist.conf file:

blacklist ath5k_pci
blacklist ATL1E
blacklist ath5k

# Now you can reboot and it should work.

But still no joy :-(

As I said I am quite inexpert and unskilled, so I can't really think of any reason why it is not working. I suspect it's something to do with the update I run of course (just before the update everything was working fine), but I have no idea what to do next.

Any idea guys?? Any help would be very appreciated!

Many thanks

---

### Post by chili555 on 2010-01-12
I just ran this now:> wget [http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz)The file I got when I extracted the .tar.gz was [COLOR="Red"]madwifi-trunk-r4104-20100112[/COLOR] and not [COLOR="Blue"]madwifi-trunk-r4031-20090529[/COLOR]. Did you cd into the wrong directory and make an older version?

---

### Post by Kella on 2010-01-12
Thanks chili555 for your reply. In fact I did cd into the right directory (ie [COLOR=Red]madwifi-trunk-r4104-20100112[COLOR=Black]). There must be something else which occurred after the update. It is like my wireless card is not installed or not being recognised or something.

Not sure if I am doing anything wrong when setting up the wireless network. In the past I had to do nothing apart from installing the wireless LAN, and everything was working fine as if by magic! :D

Don't know if that help but attached there is the screenshot of the network setting window... any idea about which settings I should choose? The cripted info is obviously the name of the network. It is an unprotected network so I never had to use the password, and the network name was the only info I had to provide in order to get connected to the Internet.

Sorry I cannot be very clear about the problem but I cannot really understand what is going on!

Any further suggestion?
[/COLOR][/COLOR][IMG]file:///home/fru/Desktop/Screenshot.jpg[/IMG]

---

### Post by chili555 on 2010-01-12
Let's troubleshoot step-by-step. First, did the module get loaded.```
lsmod | grep ath
```If *ath_pci* is there, we're good. Next, did an interface, wlan0 perhaps, get created:```
iwconfig
```Is a wirless interface there, maybe similar to this from my computer?> eth1      IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 99:24:56:2A:D7:99   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-44 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3If so, can you click on the Network Manager icon and see networks, especially yours? Please see attached.

If not. let's see what the kernel has to say:```
dmesg | grep ath
dmesg | grep wlan0
```Substitute your wireless interface, if it's not wlan0.

Last, please try again with one additional command:```
[COLOR="Red"]make clean[/COLOR]

make 

sudo make install
```Did make complete with *NO* errors? Post back and, hopefully, report your success!

---

### Post by Kella on 2010-01-12
> **chili555 said:**
> Let's troubleshoot step-by-step. First, did the module get loaded.```
lsmod | grep ath
```If *ath_pci* is there, we're good.

Sorry, don't really know what you mean here... this is the terminal output so far

```
fru@fru-laptop:~$ lsmod | grep ath
fru@fru-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```Where am I supposed to see *ath_pci*?

> **chili555 said:**
> Next, did an interface, wlan0 perhaps, get created:```
iwconfig
```

Again, sorry I cannot see what you mean by saying 'did an interface' :-(

> **chili555 said:**
> Is a wirless interface there, maybe similar to this from my computer?If so, can you click on the Network Manager icon and see networks, especially yours? Please see attached.

That's the thing: no wireless interface at all. In the network manager window all I can see is the wired network - no wireless at all.

> **chili555 said:**
> If not. let's see what the kernel has to say:```
dmesg | grep ath
dmesg | grep wlan0
```Substitute your wireless interface, if it's not wlan0.

Tried this in the terminal but no output whatsoever. (But I'm sure I'm doing something wrong here)

> **chili555 said:**
> Last, please try again with one additional command:```
[COLOR=Red]make clean[/COLOR]

make 

sudo make install
```Did make complete with *NO* errors? Post back and, hopefully, report your success!

There you go, this is the output:

```
fru@fru-laptop:~$ make clean
make: *** No rule to make target `clean'. Stop.
fru@fru-laptop:~$ 
fru@fru-laptop:~$
```Doesn't seem to work, but then again I think I'm missing the 'did an interface' step! Thanks a lot for your help tho, very appreciated.

---

### Post by chili555 on 2010-01-12
> fru@fru-laptop:~$ lsmod | grep athAh ha!!! We asked /etc/modules...remember this:> # Now add the Atheros kernel module ath_pci to the list of modules to be automatically loaded at boot by adding

ath_pci

# to the end of the /etc/modules file. (Gedit editor automatically opens)We asked that ath_pci automatically get loaded. However, when you asked for a listing of the modules loaded by any name like ath (lsmod | grep ath), it was not there! Let's load it explicitly and see what errors, warnings, laughter, etc. happen:```
sudo modprobe ath_pci
```Please let us know what happens.

Naturally, since the module didn't load, a wireless interface did not get created.> fru@fru-laptop:~$ make clean
make: *** No rule to make target `clean'. Stop.
fru@fru-laptop:~$ First, you have to cd to the correct directory, in your case, madwifi-trunk-r4104-20100112/. Sorry I omitted that. You might try those steps before you try modprobbing ath_pci:```
cd madwifi-trunk-r4104-20100112/
make clean
make
sudo make install
sudo modprobe ath_pci
iwconfig
```Please post back and let us know your progress.

---

### Post by Kella on 2010-01-12
You are a true GENIUS!! Thanks a million mate... I utterly ignore the reason why all this has just happened and still don't know what the hell you've just made me do, but I've finally managed to get my wireless connection back!!!!! Feeling like a stupid monkey, just pressing buttons and watching things happening but hey ho, it's FUN and I'm lovin' it! Hooray! :D

Thank you once again... you've solved my problem and just spared me a lot of stress!

Anyway, should you find it extremely amusing again, there you go the output of my wild coding! :P

PS You might find it quite hilarious but I thought to encrypt the name of the network for security reasons... well, they always do that inspy films and I felt very clever for a few seconds!! Ha ha ha!

 fru@fru-laptop:~$ cd madwifi-trunk-r4104-20100112/
fru@fru-laptop:~/madwifi-trunk-r4104-20100112$ make clean
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
        make -C $i clean; \
    done
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath'
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_hal'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -f ar*/*~ ar*/*.o ar*/.*.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_hal'
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
        make -C $i clean; \
    done
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr'
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe'
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample'
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel'
rm -f modules.order
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate'
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/net80211'
make -C ./tools clean
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey core a.out
for d in ath_info; do \
        make -C $d clean; \
    done
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
rm -f *.o ath_info
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
rm -rf .tmp_versions
rm -f modules.order *.symvers Module.markers svnversion.h
fru@fru-laptop:~/madwifi-trunk-r4104-20100112$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-16-generic/build SUBDIRS=/home/fru/madwifi-trunk-r4104-20100112 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-16-generic'
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath/if_ath.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath/if_ath_radar.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath/if_ath_hal_extensions.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath/if_ath_pci.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath/ath_pci.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ah.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ah_eeprom_v1.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ah_eeprom_v14.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ah_eeprom_v3.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ah_os.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ah_regdomain.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_attach.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_beacon.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_interrupts.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_keycache.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_misc.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_phy.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_power.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_recv.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_reset.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5210/ar5210_xmit.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_attach.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_beacon.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_interrupts.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_keycache.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_misc.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_phy.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_power.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_recv.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_reset.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5211/ar5211_xmit.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar2316.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar2317.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar2413.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar2425.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5111.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5112.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_ani.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_attach.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_beacon.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_eeprom.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_gpio.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_interrupts.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_keycache.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_misc.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_phy.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_power.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_recv.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_reset.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_rfgain.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5212_xmit.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5212/ar5413.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar2133.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_ani.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_attach.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_beacon.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_cal.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_cal_adcdc.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_cal_adcgain.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_cal_iq.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_eeprom.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_gpio.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_interrupts.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_keycache.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_misc.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_phy.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_power.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_recv.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_reset.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar5416_xmit.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ar5416/ar9160_attach.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ath_hal.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr/amrr.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel/minstrel.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe/onoe.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample/sample.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/if_media.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_skb.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_beacon.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_crypto.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_crypto_none.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_input.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_node.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_output.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_power.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_proto.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_scan.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_wireless.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_linux.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_monitor.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_rate.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_acl.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_scan_ap.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_scan_sta.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/ieee80211_xauth.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_wep.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_tkip.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_ccmp.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_acl.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_xauth.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_scan_sta.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/fru/madwifi-trunk-r4104-20100112/ath/ath_pci.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath/ath_pci.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ath_hal.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_hal/ath_hal.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample/ath_rate_sample.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_acl.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_acl.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_ccmp.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_ccmp.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_scan_ap.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_scan_sta.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_tkip.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_tkip.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_wep.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_wep.ko
  CC      /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_xauth.mod.o
  LD [M]  /home/fru/madwifi-trunk-r4104-20100112/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-16-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
for d in ath_info; do \
        make -C $d || exit 1; \
    done
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
gcc -g -O2 -W -Wall -D_FILE_OFFSET_BITS=64 -c ath_info.c
ath_info.c: In function 'main':
ath_info.c:2824: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../ath_hal -I.. -I../ath  athstats.c
athstats.c: In function 'main':
athstats.c:288: warning: format not a string literal and no format arguments
athstats.c:290: warning: format not a string literal and no format arguments
athstats.c:310: warning: format not a string literal and no format arguments
athstats.c:312: warning: format not a string literal and no format arguments
athstats.c:347: warning: format not a string literal and no format arguments
gcc -o 80211stats -g -O2 -Wall -I. -I../ath_hal -I..  80211stats.c
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
gcc -o athkey -g -O2 -Wall -I. -I../ath_hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../ath_hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../ath_hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../ath_hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../ath_hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../ath_hal -I..  wlanconfig.c
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
gcc -o wpakey -g -O2 -Wall -I. -I../ath_hal -I..  wpakey.c
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
fru@fru-laptop:~/madwifi-trunk-r4104-20100112$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-16-generic/build SUBDIRS=/home/fru/madwifi-trunk-r4104-20100112 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-16-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-16-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.27-16-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
        make -C $i install || exit 1; \
    done
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath'
test -d //lib/modules/2.6.27-16-generic/net || mkdir -p //lib/modules/2.6.27-16-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.27-16-generic/net
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath'
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_hal'
test -d //lib/modules/2.6.27-16-generic/net || mkdir -p //lib/modules/2.6.27-16-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.27-16-generic/net
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_hal'
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
        make -C $i install || exit 1; \
    done
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr'
test -d //lib/modules/2.6.27-16-generic/net || mkdir -p //lib/modules/2.6.27-16-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.27-16-generic/net
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/amrr'
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe'
test -d //lib/modules/2.6.27-16-generic/net || mkdir -p //lib/modules/2.6.27-16-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.27-16-generic/net
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/onoe'
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample'
test -d //lib/modules/2.6.27-16-generic/net || mkdir -p //lib/modules/2.6.27-16-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.27-16-generic/net
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/sample'
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel'
test -d //lib/modules/2.6.27-16-generic/net || mkdir -p //lib/modules/2.6.27-16-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.27-16-generic/net
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate/minstrel'
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/ath_rate'
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/net80211'
test -d //lib/modules/2.6.27-16-generic/net || mkdir -p //lib/modules/2.6.27-16-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
        f=`basename $i .o`; \
        install -m 0644  $f.ko //lib/modules/2.6.27-16-generic/net; \
    done
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/net80211'
(export KMODPATH=/lib/modules/2.6.27-16-generic/net; /sbin/depmod -ae 2.6.27-16-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
for d in ath_info; do \
        make -C $d || exit 1; \
    done
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
for d in ath_info; do \
        make -C $d || exit 1; \
    done
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
        install $i /usr/local/bin/$i; \
        strip /usr/local/bin/$i; \
    done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
        make -C $d install || exit 1; \
    done
make[2]: Entering directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools/ath_info'
make[1]: Leaving directory `/home/fru/madwifi-trunk-r4104-20100112/tools'
fru@fru-laptop:~/madwifi-trunk-r4104-20100112$ sudo modprobe ath_pci
fru@fru-laptop:~/madwifi-trunk-r4104-20100112$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"XXXXXXXXXXXXXXXXXXXX"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:90:96:FB:D6:81   
          Bit Rate:48 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-66 dBm  Noise level=-96 dBm
          Rx invalid nwid:16  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

fru@fru-laptop:~/madwifi-trunk-r4104-20100112$

---

### Post by chili555 on 2010-01-12
Great!!! I'm glad it's working for you. You have learned a little bit and I have put another notch in the handle of my old .44. Bad joke, there.

Enjoy!

---

