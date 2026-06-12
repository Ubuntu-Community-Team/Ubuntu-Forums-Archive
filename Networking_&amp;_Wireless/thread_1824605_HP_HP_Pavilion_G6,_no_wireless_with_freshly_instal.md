---
title: "HP HP Pavilion G6, no wireless with freshly installed 11.04"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by bicyclelifestyle on 2011-08-14
Installed 11.04 (64bit) on my HP Pavilion G6, in place of windows. ethernet works, however i cannot connect wirelessly. i have done much google searching but to no avail. these are the things i have found but have not helped.
][http://ubuntuforums.org/showthread.php?t=1740963&page=3](http://ubuntuforums.org/showthread.php?t=1740963&page=3)
[http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/](http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/)
[http://ubuntuforums.org/showthread.php?t=1780954](http://ubuntuforums.org/showthread.php?t=1780954)
[http://ubuntuforums.org/showthread.php?t=1740963&page=3](http://ubuntuforums.org/showthread.php?t=1740963&page=3)

I need help to get this running!
thank you in advance

(long time ubuntu user, first post)

---

### Post by bicyclelifestyle on 2011-08-14
the version of the linux driver on the ralink website is different from the one in the forums, v2.5.0.3, instead of v.2.4.0.4. how do i adapt what ive found to work for this? 


[LIST=1]
[*] Download the driver from ralinktech.com &#8211;> Software &#8211;> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory.  **(THE ONE I DOWNLOADED WAS 2011_xxxx, the 2010_xxxx was updated to this)**
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n &#8212; this was the only thing I modified) **DOES NOT EXSIST in the version i downloaded.**
[*]Go back to the 2010_xx directory
[*]run command &#8216;make&#8217; **(i instead went this route: **> **chili555 said:**
> I found this: [http://ubuntuforums.org/showpost.php?p=10669120&postcount=70](http://ubuntuforums.org/showpost.php?p=10669120&postcount=70)

I tried it, albeit a bit modified, and it got me, on my Natty system,  from errored out to warnings but installs and modprobes without error. I  don't have the device, so I don't know if it works properly. Let's try  it. Go here: [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless]("https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless")

Download all the patches except the x64_86 patch (I assume you have  installed a 32-bit system). Move them to your  2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder. Now, in a  terminal, do:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```Post back any errors or if you get stuck. 

Fingers crossed! 
[B]this is as far i was able to get, with nothing happening. even changing the terminal code from 2.4.0.4, to the newer 2.5.0.3, which matches the newer ralink software.
[/B]
[/LIST]

[LIST=1]
[*]Make sure &#8216;make compile&#8217; exists without errors. I got an error &#8220;too  many arguments to format&#8221; towards the end of the compile but it did  compile successfully eventually. And so I ignored the errors. You would  see ***errors*** if the compile is not successful. In which, something  went wrong and you may need to tweak the makefile or config.mk files  before compile is successful.
If you get compile error (*** Error 2) when doing &#8216;make&#8217;, then add this  change to the change recommended in step 5 (edit the config.mk file):
HAS_CFG80211_SUPPORT=n (was &#8216;y&#8217; originally);
then type: &#8216;make clean&#8217; and proceed with &#8216;make&#8217;.
I found this tip in: [atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/]("http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/");
[*]run command &#8216;sudo make install&#8217;. This is not listed in the  README_STA_pci file that comes with downloaded driver zip file. This  takes of copying the file to  /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko.  running depmod, creating /etc/Wireless/&#8230; folder.
[*]Edit the /etc/modules and add the line at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it&#8230;
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command &#8216;ifconfig&#8217;
You may have to run &#8216;/etc/init.d/network-manager restart&#8217; command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing
[/LIST]
**so basically, none of this that ive found workas anymore, now that ralink has updated their wireless download. how can i make it work with this updated version?**

bump.
thank you in advance.

---

### Post by chili555 on 2011-08-14
I don't believe the patches are required in the 2.5.0.3 version. First, let's make sure you have the correct driver. Please run and post:```
lspci -nn | grep 0280
```Next, if you still have the bz2 file, I'd move the folder that was created when you extracted the bz2 to trash:```
cd Downloads
rm -rf 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
rm -rf 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL
```Now we re-extract the bz2:```
tar -xvf 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL.bz2

```Now, open os/linux/config.mk and change:```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```To read:```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```Proofread carefully, save and close the text editor. Now, back to the terminal:```
cd 2011
```Press Tab and let the remainder of the file name fill in automatically. Press Enter.```
sudo su
make
make install
modprobe rt5390sta
exit
```Any improvement?

---

### Post by bicyclelifestyle on 2011-08-14
here is what i got
~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]

i went ahead with the rest. i restarted, and still, nothing. :(

thank you for your response. i will attempt a second run.

---

### Post by bicyclelifestyle on 2011-08-14
this look right?
```

[sudo] password for jerika: 
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# sudo su
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make
make -C tools
make[1]: Entering directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:481:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type
include/linux/pci.h:736:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:487:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:487:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:500:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type
include/linux/pci.h:736:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:509:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:509:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217;
  LD [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
see include/linux/module.h for more information
  LD [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
cp -f /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make install
make -C /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-8-generic
make[1]: Leaving directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# modprobe rt5390sta
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# exit
```

---

### Post by bicyclelifestyle on 2011-08-15
i updated, and redid it.

```

[sudo] password for jerika: 
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# sudo su
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make
make -C tools
make[1]: Entering directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Wrap&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.c:1459:6: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Unwrap&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.c:1554:6: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:1053:3: warning: cast from pointer to integer of different size
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:1053:3: warning: cast from pointer to integer of different size
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c: In function &#8216;MlmePeriodicExec&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:1291:4: warning: cast from pointer to integer of different size
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:1291:4: warning: cast from pointer to integer of different size
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/action.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/dfs.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.c:1857:3: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffset&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:882:10: warning: unused variable &#8216;bTempSuccess&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:881:6: warning: unused variable &#8216;LookupTableIndex&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:880:6: warning: unused variable &#8216;CurrentTemp&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:879:8: warning: unused variable &#8216;BbpValue&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:878:32: warning: unused variable &#8216;pTxPowerTuningEntry2&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:875:8: warning: unused variable &#8216;RFValue&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:874:32: warning: unused variable &#8216;pTxPowerTuningEntry&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicAdjustTxPower&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1575:16: warning: unused variable &#8216;flags&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1562:20: warning: unused variable &#8216;pFinalTxPwr&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1560:11: warning: unused variable &#8216;bAutoTxAgc&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.c: In function &#8216;STA_MonPktSend&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.c:411:9: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sync.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.c: In function &#8216;LinkUp&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.c:1446:35: warning: unused variable &#8216;pCurrEntry&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.c:1445:28: warning: unused variable &#8216;HashIdx&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:498:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:500:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:652:20: warning: assignment makes integer from pointer without a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:671:2: warning: assignment makes integer from pointer without a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:698:15: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.c:1577:2: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_led.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function &#8216;RTMPrt3xSetPCIePowerLinkCtrl&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.c:1793:8: warning: unused variable &#8216;offset&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.c:1792:8: warning: unused variable &#8216;Vendor&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibration&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:202:18: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:215:18: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:230:18: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:252:18: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:265:18: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:136:10: warning: unused variable &#8216;bUpdateRFR&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:481:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type
include/linux/pci.h:736:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:487:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:487:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:500:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type
include/linux/pci.h:736:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:509:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:509:4: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3090.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.c: In function &#8216;NICInitRT3390RFRegisters&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.c:42:7: warning: unused variable &#8216;bbpreg&#8217;
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_Init&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:490:25: warning: assignment makes integer from pointer without a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390LoadRFSleepModeSetup&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:910:8: warning: unused variable &#8216;RFValue&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390ReverseRFSleepModeSetup&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:986:8: warning: unused variable &#8216;RFValue&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ChipSwitchChannel&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1631:17: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1642:17: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1656:16: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1526:17: warning: unused variable &#8216;BbpR110&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:1525:23: warning: unused variable &#8216;BbpR109&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;GetDesiredTssiAndCurrentTssi&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3120:2: warning: missing braces around initializer
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3120:2: warning: (near initialization for &#8216;htTssiInfo.PartA.field&#8217;)
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ATETssiCalibration&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3391:2: warning: ISO C90 forbids mixed declarations and code
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3480:4: warning: passing argument 3 of &#8216;eFuseWrite&#8217; from incompatible pointer type
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp.h:5742:10: note: expected &#8216;PUSHORT&#8217; but argument is of type &#8216;UCHAR *&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3392:42: warning: unused variable &#8216;ChannelPower&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;GetPowerDeltaFromTssiRatio&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3622:2: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;LONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3651:2: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;LONG&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_AsicResetBbpAgent&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3929:8: warning: unused variable &#8216;BBPValue&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3928:8: warning: unused variable &#8216;loop&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ATETssiCalibration&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:3392:9: warning: &#8216;BbpData&#8217; may be used uninitialized in this function
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c: In function &#8216;rt2860_probe&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c:326:13: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.o
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DefaultATEAsicSwitchChannel&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:1248:16: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:1034:21: warning: unused variable &#8216;RFValue2&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function &#8216;ATETxPwrHandler&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:5162:45: warning: unused variable &#8216;CfgOfTxPwrCtrlOverMAC&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TX_FREQOFFSET_Proc&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:7623:13: warning: comparison of distinct pointer types lacks a cast
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_EX_Proc&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9373:9: warning: unused variable &#8216;CurrentChannel&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9372:9: warning: unused variable &#8216;BSSID_ADDR&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9371:10: warning: unused variable &#8216;ChannelPower&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9370:10: warning: unused variable &#8216;EEPData&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9369:31: warning: unused variable &#8216;TssiDeltaPerChannel&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9369:8: warning: unused variable &#8216;TssiRefPerChannel&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:53: warning: unused variable &#8216;BBP49Value&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:42: warning: unused variable &#8216;RF28Value&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:31: warning: unused variable &#8216;RF27Value&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:22: warning: unused variable &#8216;RFValue&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368:9: warning: unused variable &#8216;BbpData&#8217;
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9376:1: warning: control reaches end of non-void function
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_Proc&#8217;:
/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9360:1: warning: control reaches end of non-void function
  LD [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
see include/linux/module.h for more information
  CC      /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.mod.o
  LD [M]  /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
cp -f /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# make install
make -C /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-10-generic
make[1]: Leaving directory `/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# modprobe rt5390sta
root@Lillith:/home/jerika/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO# exit

```

SO after that, my wireless appears like it should be working, but will not find a wireless network. so i now have the option to "enable wireless". got me much further along this time though!

thank you, but i still need help, unfortunatly :(

---

### Post by bicyclelifestyle on 2011-08-15
is this relevant?

```

jerika@Lillith:~$ sudo ifconfig
[sudo] password for jerika: 
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:55:12:fc  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae3:b5ff:fe55:12fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2174859 (2.1 MB)  TX bytes:383852 (383.8 KB)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

ra0       Link encap:Ethernet  HWaddr cc:af:78:14:cc:b3  
          inet6 addr: fe80::ceaf:78ff:fe14:ccb3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

```

---

### Post by chili555 on 2011-08-15
It is relevant in the sense that you have a wired ethernet connection. Network Manager will disallow a wireless connection if you have wired. Do you see networks with the cable detached and a pause for a few moments for NM to notice a change in state? Are there any interesting clues here?```
dmesg | grep -e rt5 -e rt2
```

---

### Post by bicyclelifestyle on 2011-08-15
the ifconfig was run without the ethernet plugged in. WIthout the ethernet plugged in, same problem presists. does this give up any clues?
```

  [FONT=DejaVu Sans Mono, monospace]jerika@Lillith:~$ dmesg | grep -e rt5 -e rt2[/FONT]
 [FONT=DejaVu Sans Mono, monospace][   15.624813] register rt2860[/FONT]
 [FONT=DejaVu Sans Mono, monospace][   15.624997] rt2860 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17[/FONT]
 [FONT=DejaVu Sans Mono, monospace][   15.625156] rt2860 0000:06:00.0: setting latency timer to 64[/FONT]
 [FONT=DejaVu Sans Mono, monospace][   16.383880] <==== rt28xx_init, Status=0[/FONT]
 [FONT=DejaVu Sans Mono, monospace][   16.449410] <==== rt28xx_init, Status=0[/FONT]
 [FONT=DejaVu Sans Mono, monospace][   17.095318] Modules linked in: parport_pc ppdev vesafb snd_hda_codec_idt snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hwdep hp_wmi joydev snd_pcm sparse_keymap binfmt_misc snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer rt5390sta(P) uvcvideo snd_seq_device videodev snd v4l2_compat_ioctl32 fglrx(P) sp5100_tco rts_pstor(C) k10temp i2c_piix4 psmouse soundcore snd_page_alloc serio_raw video lp parport r8169 ahci libahci[/FONT]
```


[FONT=DejaVu Sans Mono, monospace]thank you so much for your help
[/FONT]

---

### Post by chili555 on 2011-08-15
It gives an interesting hunch. Please post:```
lsmod | grep -e rt2 -e rt5
```Thanks.

---

