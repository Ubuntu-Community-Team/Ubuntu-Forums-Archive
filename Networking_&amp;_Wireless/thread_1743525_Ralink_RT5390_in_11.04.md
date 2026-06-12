---
title: "Ralink RT5390 in 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by port86 on 2011-04-29
Hi there,

This is my first post here, so hello everyone :)

I'll go through some background info first - I have recently installed Ubuntu 11.04 on my HP G62 laptop. The wireless card in this laptop is a Ralink RT5390 (I have confirmed this through lspci and via Windows). I'm a total linux noob, but I have researched the problem and tried following several instructions on the web for this particular wireless card (such as [http://ubuntuforums.org/showpost.php?p=10452987&postcount=42](http://ubuntuforums.org/showpost.php?p=10452987&postcount=42)), but I seem to be failing at the first hurdle every time.

I have gotten as far as downloading the source code for the driver and attempting to compile it, but I can't seem to get it to compile. I seem to get the following result every time:

make[2]: *** [/home/donald/Downloads/wireless/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/donald/Downloads/wireless/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2

I have read on some pages that I should attempt to modify the config.mk and Makefile files, but being a noob I have no idea what to look out for or what to edit. 

I am aware that 11.04 is a new release of Ubuntu, could my issues be due to this being so recent and the driver requires an update from the vendor?

Any assistance would be appreciated. Thanks.

---

### Post by chili555 on 2011-04-29
Please start with post #9 here. If you have a question, post back. This is a fairly advanced process, but if you follow each step carefully, you should be successful. I have subscribed to the thread, so, if you get stuck, shout and I'll help you.

[http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390)

---

### Post by port86 on 2011-04-29
> **chili555 said:**
> Please start with post #9 here. If you have a question, post back. This is a fairly advanced process, but if you follow each step carefully, you should be successful. I have subscribed to the thread, so, if you get stuck, shout and I'll help you.

[http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390)

For any searchers, this thread solved my problem.

---

### Post by seebs on 2011-04-29
For what it's worth, it didn't for me (at least yet); I can build the driver, and I see a wlan0, but NetworkManager doesn't see it, I can't create connections on it, and so on.

---

### Post by dr.s on 2011-05-07
> **port86 said:**
> Hi there,

This is my first post here, so hello everyone :)

I'll go through some background info first - I have recently installed Ubuntu 11.04 on my HP G62 laptop. The wireless card in this laptop is a Ralink RT5390 (I have confirmed this through lspci and via Windows). I'm a total linux noob, but I have researched the problem and tried following several instructions on the web for this particular wireless card (such as [http://ubuntuforums.org/showpost.php?p=10452987&postcount=42](http://ubuntuforums.org/showpost.php?p=10452987&postcount=42)), but I seem to be failing at the first hurdle every time.

I have gotten as far as downloading the source code for the driver and attempting to compile it, but I can't seem to get it to compile. I seem to get the following result every time:

make[2]: *** [/home/donald/Downloads/wireless/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/donald/Downloads/wireless/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2

I have read on some pages that I should attempt to modify the config.mk and Makefile files, but being a noob I have no idea what to look out for or what to edit. 

I am aware that 11.04 is a new release of Ubuntu, could my issues be due to this being so recent and the driver requires an update from the vendor?

Any assistance would be appreciated. Thanks.

Try this, it worked for me:
-edit config.mk ( should be under ..../os/linux )
-look for this line:
 HAS_CFG80211_SUPPORT=y
-change "y" to "n" then recompile and run make install.

---

### Post by xenagi on 2011-05-12
> **dr.s said:**
> Try this, it worked for me:
-edit config.mk ( should be under ..../os/linux )
-look for this line:
 HAS_CFG80211_SUPPORT=y
-change "y" to "n" then recompile and run make install.

This worked for me! Thank you!! :D

---

### Post by chareen on 2011-06-03
Hi,
 
I am having the same problem too. The following error message is displayed.
 
cp:cannot create regular file '/tftpboot': Permission denied.
 
Any ways to resolve this?

---

### Post by chili555 on 2011-06-03
> **chareen said:**
> Hi,
 
I am having the same problem too. The following error message is displayed.
 
cp:cannot create regular file '/tftpboot': Permission denied.
 
Any ways to resolve this?Sure. Instead of make and sudo make install, etc., instead, do:```
sudo su
make clean
make
make install
etc., etc.
```

---

### Post by Mguel on 2011-07-21
Hi, thanks a lot for all the people who contributed (specially chili and akshay)!!! Now I can use ubuntu! (using lubuntu really, on a HP Pavilion dm1 3060la).

I wanted to put on one place all the steps necessary to config Ralink RT5390 in 11.04, so here is what I made and it worked (I only followed the steps mentioned here and on the referred threads and sub threads):

```
sudo apt-get install linux-headers-generic build-essential

[COLOR="DarkSlateGray"]*download RT5390PCIe from*[/COLOR]  [COLOR="Navy"]http://www.ralinktech.com/support.php?s=2[/COLOR]
cd [COLOR="DarkSlateGray"]to the[/COLOR] 2010_xxx [COLOR="DarkSlateGray"]extracted directory[/COLOR]
cd os/linux/
[COLOR="DarkSlateGray"]*Edit the config.mk file as below:*[/COLOR]
HAS_ATE=y *[COLOR="DarkSlateGray"](no change, it was originally as is)[/COLOR]*
HAS_WPA_SUPPLICANT=y *[COLOR="DarkSlateGray"](no change, it was originally as is)[/COLOR]*
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y *[COLOR="DarkSlateGray"](no change, it was originally as is)[/COLOR]*
HAS_ANTENNA_DIVERSITY_SUPPORT=y *[COLOR="DarkSlateGray"]originally was n -- **this was the only thing I modified**)[/COLOR]*

[COLOR="DarkSlateGray"]*Download patches (except x86_64, if you are on a x86_64 read Note below) from:*[/COLOR]
[COLOR="Navy"]https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless[/COLOR]

patch -p0 < rt5390sta-2.4.0.4-config.patch 
[COLOR="DarkSlateGray"]*(applied patch detected -> enter -> apply anyway? -> y)*[/COLOR]
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
```**[COLOR="DarkRed"]Note[/COLOR]**: If you are using a x86_64 system, then obviously they need to also download and apply the 64-bit patch

Please point out any errors... I'm a noob so only followed what I found.

Cheers,
Mguel

---

### Post by chili555 on 2011-07-21
> download patches (except 86_64) from:
[https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)
I think your steps are accurate and excellent. I shall myself link to them in the future. I might just add that if a user is working on a x86_64 system, then obviously they need to also download and apply the 64-bit patch.

Thank you for your compilation.

---

### Post by Mguel on 2011-07-21
> **chili555 said:**
> I think your steps are accurate and excellent. I shall myself link to them in the future. I might just add that if a user is working on a x86_64 system, then obviously they need to also download and apply the 64-bit patch.

Added a note for x86_64 systems ;)

thanks!

---

### Post by Mguel on 2011-07-21
Just realized I'm using a x86_64 system!!! (I got confused on all the usb drive installation process and I didn't remember quite well which iso I used :P)

So the above instructions work on x86_64 also, even if you don't do the x86_64 patch... should I repeat the steps doing that patch also... but if it is working and it ain't broken... don't fix it (my guts say)

cheers!

---

### Post by chili555 on 2011-07-21
> **Mguel said:**
> but if it is working and it ain't broken... don't fix it (my guts say)

cheers!I completely agree. If a new user comes along with a 64-bit system, I suggest the x86_64 patch. If you have a perfectly working system, don't touch a thing.

---

### Post by pturmel on 2011-08-06
> **chili555 said:**
> Please start with post #9 here. If you have a question, post back. This is a fairly advanced process, but if you follow each step carefully, you should be successful. I have subscribed to the thread, so, if you get stuck, shout and I'll help you.

[http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390)
Now that support for this device is in kernel 3.0, using the kernel PPA is a simpler solution.  See my comment #14 on [launchpad]("https://bugs.launchpad.net/bugs/815064").  And, from the bug details there, its clear that 11.10 will have support out-of-the-box.

---

### Post by saintkepha on 2011-08-10
Thanks for the post, it helped me get my wifi working on my HP dv6-6135dx laptop.

FYI, ralink has published a new driver (as of 7-29-2011) version 2.5.0.3.  Fortunately, Axel has committed an updated patch at the opensuse.org site as of 8-2-2011 which now works against the new ralink version 2.5.0.3.  In turn, the patch commands are now a bit different (need to substitute for the new version), but other than that, it worked like a charm.

One more note, it appears that with the new ralink driver, the kernel config option HAS_ANTENNA_DIVERSITY_SUPPORT is no longer present in the config.

---

### Post by palimmo on 2011-08-12
> **pturmel said:**
> Now that support for this device is in kernel 3.0, using the kernel PPA is a simpler solution.  See my comment #14 on [launchpad]("https://bugs.launchpad.net/bugs/815064").  And, from the bug details there, its clear that 11.10 will have support out-of-the-box.

I'm sorry pturmel.. but I followed your instructions and I'm not able to see the card work properly.
Could you help me, guys?:(

---

### Post by palimmo on 2011-08-12
> **palimmo said:**
> I'm sorry pturmel.. but I followed your instructions and I'm not able to see the card work properly.
Could you help me, guys?:(

Now it works!

But.. the led changes continuously and very fast the colour, from white to orange and so on!

Could it be dangerous???:confused:

---

### Post by palimmo on 2011-08-12
> **palimmo said:**
> Now it works!

But.. the led changes continuously and very fast the colour, from white to orange and so on!

Could it be dangerous???:confused:

Mh... 
I've also tried to delete both
echo 1814 5390 >/sys/bus/pci/drivers/rt2800pci/new_id
in 
/etc/rc.local

and

rt5390sta
rt2800pci
in
/etc/modules

And it works as well!

....but it flashes continuously! So worrying!

---

### Post by chili555 on 2011-08-12
I don't think you want both rt5390sta and rt2800pci to load. They conflict. Please remove rt2800pci from /etc/modules and reboot.

---

### Post by palimmo on 2011-08-12
> **chili555 said:**
> I don't think you want both rt5390sta and rt2800pci to load. They conflict. Please remove rt2800pci from /etc/modules and reboot.


I have already removed **both** of them. But the problem persists.

---

### Post by chili555 on 2011-08-12
Sorry, I have no more ideas.

---

### Post by MiracleCat on 2011-08-22
[QUOTE=chili555][QUOTE=MiracleCat]Hi, I'm very very new to Linux.

I did everything as said in post n°9, still not working. I copied and pasted some commands you put inthis post earlier in the terminal. Here is what i got:

```
dmesg | grep 539
[    0.305390] pci 0000:00:05.0: PME# disabled
[    0.324229] pci 0000:02:00.0: [1814:539f] type 0 class 0x000280
[    1.065392] tun: Universal TUN/TAP device driver, 1.6
[    1.065396] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   10.529779] rt5390 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.529858] rt5390 0000:02:00.0: setting latency timer to 64
sudo modprobe rt5390sta
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

I own a HP DM1-3060la netbook.[/QUOTE]Please add to the thread. Include:> lspci -nn | grep 0280
rfkill list all
modinfo rt5390staAlso confirm that you made the changes in os/linux/config.mk. Thanks.

chili555[/QUOTE]


Here are the commands:

```

**lspci -nn | grep 0280**
02:00.0 Network controller [0280]: Ralink corp. Device [1814:539f]
**rfkill list all**
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
**modinfo rt5390sta**
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5390sta.ko
description:    RT539X Wireless Lan Linux Driver
license:        GPL
version:        2.5.0.3
srcversion:     E50A87101587A949CF35F45
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
```

About the changes in os/linux/config.mk I did exactly as said in the post n°9, **BUT** my config.mk file did not have the "HAS_ANTENNA_DIVERSITY_SUPPORT", so I wrote it down manually.

Hope you can Help me.

---

### Post by chili555 on 2011-08-22
Did you do all the patches here? [http://ubuntuforums.org/showpost.php?p=10731708&postcount=24](http://ubuntuforums.org/showpost.php?p=10731708&postcount=24)

I believe if you have the latest version of the driver, 2.5.0.3, and the latest kernel, 2.6.38-xx, the patches are *not* required.

---

### Post by MiracleCat on 2011-08-22
Update made on post.

---

### Post by MiracleCat on 2011-08-22
Yes I did all the patches.

---

### Post by chili555 on 2011-08-22
Do you have the .bz2 file you downloaded on your desktop? Let's start fresh. Right-click your desktop and create a folder; let's call it *test*. Drag and drop the .bz2 into test. Open test and right-click the .bz2 and select Extract Here. Open os/linux/config.mk and only make these changes:> Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.Then do:```
cd Desktop/test/2010_1216_RT5390_LinuxSTA_V2.5.0.3_WiFiBTCombo_DPO
sudo su
cp RT2860STA.dat RT5390STA.dat
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```Now is your wireless working?

---

### Post by MiracleCat on 2011-08-22
I'd like to point out that my file from Ralink is called: 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL.bz2

I'll do the sae procedure with this file and i'll let you know.

---

### Post by MiracleCat on 2011-08-22
Yes sir, wireless is working and im posting through it.

Thank you so much, I don't know much about linux.

I really appreciate your help.

---

### Post by chili555 on 2011-08-23
Glad it's working! Have fun.

---

### Post by shurin on 2011-08-26
Hi. I bought a HP g4 Pavilion at the end of July and had success in getting my wireless to work in 11.04 through these forums.  However, I used Update Manager to update my software earlier this evening, which I believe caused my wireless to stop working after I restarted it. I think it is because there is a conflict with one of the updates.  Is there way to check for this and eliminate the conflict?

---

### Post by chili555 on 2011-08-26
> **shurin said:**
> Hi. I bought a HP g4 Pavilion at the end of July and had success in getting my wireless to work in 11.04 through these forums.  However, I used Update Manager to update my software earlier this evening, which I believe caused my wireless to stop working after I restarted it. I think it is because there is a conflict with one of the updates.  Is there way to check for this and eliminate the conflict?Did you compile the file from a bz2 or similar? A recent update was a newer kernel version. You therefor need to build again for the new kernel:```
cd Desktop/test/2010_1216_RT5390_LinuxSTA_V2.5.0.3_WiFiBTCombo_DPO
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5390sta
exit
```Of course, substitute the location of your driver file if it's not Desktop, etc.

---

### Post by shurin on 2011-08-26
Thanks Chili!  It worked! This and your other posts have been a tremendous help!

---

### Post by linuxdweeb on 2011-09-07
Has anyone been successful in getting the rt5390 to work with WPA2 Enterprise? I haven't been able to get it to work.

I see the following errors in /var/log/syslog:

Sep  7 12:13:43 kiosk wpa_supplicant[972]: Authentication with 00:00:00:00:00:00 timed out.
Sep  7 12:13:43 kiosk wpa_supplicant[972]: Trying to associate with SSID 'MYWIFINETWORK'
Sep  7 12:13:43 kiosk NetworkManager[707]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep  7 12:13:43 kiosk NetworkManager[707]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep  7 12:13:43 kiosk NetworkManager[707]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep  7 12:13:43 kiosk wpa_supplicant[972]: Association request to the driver failed
Sep  7 12:13:46 kiosk kernel: [ 8389.869317] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1130
Sep  7 12:13:46 kiosk kernel: [ 8389.869662] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1130
Sep  7 12:13:48 kiosk kernel: [ 8391.869318] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1369
Sep  7 12:13:48 kiosk kernel: [ 8391.869917] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1369

---

### Post by DanielSon2055 on 2011-10-20
> **saintkepha said:**
> Thanks for the post, it helped me get my wifi working on my HP dv6-6135dx laptop.

FYI, ralink has published a new driver (as of 7-29-2011) version 2.5.0.3.  Fortunately, Axel has committed an updated patch at the opensuse.org site as of 8-2-2011 which now works against the new ralink version 2.5.0.3.  In turn, the patch commands are now a bit different (need to substitute for the new version), but other than that, it worked like a charm.

One more note, it appears that with the new ralink driver, the kernel config option HAS_ANTENNA_DIVERSITY_SUPPORT is no longer present in the config.



I have the same laptop and I am having the problem with the wireless switch/no wireless driver.  I am new to Ubuntu and this is the first thing i have ever dealt with when it comes to this OS. I am lost....I downloaded the new drivers, extracted them to a folder, but now what? I dont know how to "Make file" or anything like that. Any help is appreciated, i am super eager to learn about Linux. Thanks dudes

---

### Post by chili555 on 2011-10-21
> **DanielSon2055 said:**
> I have the same laptop and I am having the problem with the wireless switch/no wireless driver.  I am new to Ubuntu and this is the first thing i have ever dealt with when it comes to this OS. I am lost....I downloaded the new drivers, extracted them to a folder, but now what? I dont know how to "Make file" or anything like that. Any help is appreciated, i am super eager to learn about Linux. Thanks dudesPlease check private messages at the top.

---

### Post by DanielSon2055 on 2011-10-21
> **chili555 said:**
> Please check private messages at the top.


Checked and Responded, Thanks!

---

### Post by Scorpiodbk on 2012-03-06
hello all!
i have a general question

im the bigest noob and lame with linux, backtrack ...
all i want is to get a wireless key, through the aircrack-ng, using Backtrack5
but im using it through the virtual box
so, is it possible to see and do all this kind of stuff, through the Virtualbox, where i installed the Windows 7, and Parralel the Backtrack5 ?
or im just losing time doing it with Virtualbox ?

because i tried to install it on my notebook, paralel with my windows 7, from the USB flash, but it just doesnt start, when i write startx and enter, it does something, black screen, and my Capslock is flashing, nothing happens, and here im stuck

i also have the Ralink RT5390 802.11b/g/n WiFi Adapter
but it doesnt display anything, when i write the first stept of cracking the wireless, "airmong-ng" its just shows
[http://s003.radikal.ru/i202/1203/9d/4cd3a89d5b3c.png](http://s003.radikal.ru/i202/1203/9d/4cd3a89d5b3c.png)

please help :oops:

---

### Post by chili555 on 2012-03-06
You might have better luck posting your own new thread. I am not a Virtualbox guy nor an aircrack guy. They only let me fiddle with easy stuff around here!

---

### Post by columb on 2012-11-15
hi! I use ubuntu 12.04. And I have the same problems. My labtop is HP 650 and chip rt539a. Somebody can help me?

P.S. I apologize for my bad English.

---

### Post by chili555 on 2012-11-15
> **columb said:**
> hi! I use ubuntu 12.04. And I have the same problems. My labtop is HP 650 and chip rt539a. Somebody can help me?

P.S. I apologize for my bad English.I suggest you follow the steps in post #9, but for 12.04, omit the patches.

---

### Post by columb on 2012-11-16
> **chili555 said:**
> I suggest you follow the steps in post #9, but for 12.04, omit the patches.

Thanks! But which patches to miss? In post number 9?

---

### Post by chili555 on 2012-11-16
Yes. This right here is post #42 in the thread. Go back to page 1 of this thread and scroll down to post #9. There's the exact procedure!

Wherever it says to download and apply patches, you should skip as I am fairly sure they are not required in 12.04.

---

### Post by columb on 2012-11-16
I have some problems. I executed this command  "make install" from post #9 and show next massage
```

root@hp650-HP-650-Notebook-PC:/home/hp650/RT5390# make install
make -C /home/hp650/RT5390/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/hp650/RT5390/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/hp650/RT5390/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `rt5390sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/hp650/RT5390/os/linux'
make: *** [install] Error 2

``` 

After that I executed next command

```
root@hp650-HP-650-Notebook-PC:/home/hp650/RT5390# modprobe rt5390sta
FATAL: Module rt5390sta not found.

```  

What happed? I did all from post #9

---

### Post by chili555 on 2012-11-16
> **columb said:**
> 

What happed? I did all from post #9Please back up to 'make' and show us the whole sequence.

---

### Post by columb on 2012-11-16
Dear friend! I added some comments cause my ubuntu language is russian. I do everything as it was written in the message #9. i am full loh(nerd) in ubuntu. =) But i want to know this OS and work with it.
command make clear

```
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]:_&#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;_ `/home/hp650/RT5390/os/linux' // **This in russian, mean Enter into dir**
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../ate/common/*.o
rm -f ../../ate/common/.*.{cmd,flags,d}
rm -f ../../ate/chips/*.o
rm -f ../../ate/chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]:_&#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;_ `/home/hp650/RT5390/os/linux' **// Exit from dir**
rm -rf os/linux/Makefile
```command make

```
root@hp650-HP-650-Notebook-PC:/home/hp650/RT5390# make
make -C tools
make[1]: _&#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;_&#1075; `/home/hp650/RT5390/tools'  **// Enter into  dir**
gcc -g bin2h.c -o bin2h
make[1]:_ &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;_ `/home/hp650/RT5390/tools'  **// Exit from dir**
/home/hp650/RT5390/tools/bin2h
cp -f os/linux/Makefile.6 /home/hp650/RT5390/os/linux/Makefile
make -C /lib/modules/3.2.0-29-generic-pae/build SUBDIRS=/home/hp650/RT5390/os/linux modules
make[1]: _&#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;_ `/usr/src/linux-headers-3.2.0-29-generic-pae' **// Enter into dir**
  CC [M]  /home/hp650/RT5390/os/linux/../../common/crypt_md5.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/crypt_aes.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/mlme.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/drs_grp.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_wep.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/action.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_data.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/rtmp_init.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_aes.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_sync.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/eeprom.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_info.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_radar.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/spectrum.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/rt_channel.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_profile.o
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_asic.o
/home/hp650/RT5390/os/linux/../../common/cmm_asic.c: _&#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080;_(**in a function**)   «AsicGetAutoAgcOffsetForTemperatureSensor»:
/home/hp650/RT5390/os/linux/../../common/cmm_asic.c:1233:28: _&#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;_(**warning**): assignment discards «const» qualifier from pointer target type [_&#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; &#1074;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1072;_](**by default on**)
/home/hp650/RT5390/os/linux/../../common/cmm_asic.c:1246:28: _&#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;_(**warning**): assignment discards «const» qualifier from pointer target type [_&#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102; &#1074;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1072;_](**by default on**)
  CC [M]  /home/hp650/RT5390/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/hp650/RT5390/os/linux/../../chips/rtmp_chip.o
/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.c: _&#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080;_ (**in a function**)  «HWAntennaDiversityEnable»:
/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.c:2010:2: _&#1086;&#1096;&#1080;&#1073;&#1082;&#1072;_(**error**): «regs» undeclared (first use in this function)
/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.c:2010:2: _&#1079;&#1072;&#1084;&#1077;&#1095;&#1072;&#1085;&#1080;&#1077;_(**admonition**
): each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.o] _&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1_ (**error 1**)
make[1]: *** [_module_/home/hp650/RT5390/os/linux] _&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2_(**error 2**)
make[1]: _&#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;_(**exit from dir**) `/usr/src/linux-headers-3.2.0-29-generic-pae' 
make: *** [LINUX] _&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2_(**error 2**)

```thanks for the help!

---

### Post by chili555 on 2012-11-16
> I added some comments cause my ubuntu language is russian. Thank you; it helps me.> /home/hp650/RT5390/os/linux/../../chips/rtmp_chip.c:2010:2: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;(error): «regs» undeclared (first use in this function)
/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.c:2010:2: &#1079;&#1072;&#1084;&#1077;&#1095;&#1072;&#1085;&#1080;&#1077;(admonition
): each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1 (error 1)
make[1]: *** [_module_/home/hp650/RT5390/os/linux] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2(error 2)
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;(exit from dir) `/usr/src/linux-headers-3.2.0-29-generic-pae' 
make: *** [LINUX] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2(error 2)Whenever you see '&#1054;&#1096;&#1080;&#1073;&#1082;&#1072;' at the 'make' part, you may as well stop. Nothing afterwards is going to work, as you've seen.

Which version of the driver did you build? I went here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501) and downloaded RT539x PCIe which is version 2.5.0.3 and it makes with many warnings but no errors (&#1054;&#1096;&#1080;&#1073;&#1082;&#1072;, correct?) on a 12.04 live CD running kernel 3.2.0-23-generic-pae. I suggest you download it and try it.

---

### Post by columb on 2012-11-16
1. I downloaded that driver from official site, where you were. 
2. I installed OS from flash, not from CD. ISO downloaded from official site ubuntu desktop 12.04
3. &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; = it means only error, but is not warning. 

```

/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.c:2010:2: **&#1086;&#1096;&#1080;&#1073;&#1082;&#1072;(It's error!**): «regs» undeclared (first use in this function)
/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.c:2010:2: **&#1079;&#1072;&#1084;&#1077;&#1095;&#1072;&#1085;&#1080;&#1077;(maybe it warning! )**: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/hp650/RT5390/os/linux/../../chips/rtmp_chip.o] **&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1 (It's error!)**
make[1]: *** [_module_/home/hp650/RT5390/os/linux]** &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2(It's error!)**
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;(exit from dir) `/usr/src/linux-headers-3.2.0-29-generic-pae' 
make: *** [LINUX] **&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2(It's error!)**

```

---

### Post by chili555 on 2012-11-16
I don't understand at all. It even makes on my 12.10 system with warnings and no errors. Is yours a 64-bit system?```
arch
```I'm not sure this will build on 64-bit.

Are the prerequisites installed correctly?```
sudo  dpkg -s build-essential | head -n3
sudo  dpkg -s linux-headers-generic | head -n3
```Did the built-in rt2800pci not work for you?

---

### Post by columb on 2012-11-16
I repeat all from post #9. But that errors repeat too. =( 
But in config.mk
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n <- was, I change on "y"

upd 

command arch return i686

command sudo  dpkg -s build-essential | head -n3 return

Package: build-essential
Status: install ok installed
Priority: optional

command sudo  dpkg -s linux-headers-generic | head -n3

Package: linux-headers-generic
Status: install ok installed
Priority: optional

---

### Post by chili555 on 2012-11-16
I'm sorry; I still think you have an older version. Do you still have the bz2 you extracted? What version is it? Please try this: [https://dl.dropbox.com/u/58267392/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip](https://dl.dropbox.com/u/58267392/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip)

Notice it is a zip; you can right-click it and select Extract Here. Please be sure to make the change in os/linux/config.mk.

---

### Post by columb on 2012-11-16
I downloaded file for Your link, but all the same errors. 
How You think, if i will reinstall system, it maybe help?


command [COLOR=#000000][FONT=Ubuntu Beta]lspci  return [/FONT][/COLOR]
```

[COLOR=#000000][FONT=Ubuntu Beta]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]02:00.0 Network controller: Ralink corp. Device 539a[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01[/FONT][/COLOR]

```command [COLOR=#000000][FONT=Ubuntu Beta]ifconfig  return 

[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Beta]eth0      Link encap:Ethernet  HWaddr b4:b5:2f:29:bb:b1  [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          inet6 addr: fe80::b6b5:2fff:fe29:bbb1/64 Scope:Link[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          RX packets:41456 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          TX packets:23002 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          collisions:0 txqueuelen:1000 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          RX bytes:61745539 (61.7 MB)  TX bytes:1734354 (1.7 MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          Interrupt:41 Base address:0xa000 [/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          RX packets:157 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          collisions:0 txqueuelen:0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          RX bytes:17447 (17.4 KB)  TX bytes:17447 (17.4 KB)[/FONT][/COLOR]
```
command iwconfig return
```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.
[COLOR=#000000][FONT=Ubuntu Beta][/FONT][/COLOR]
```

---

### Post by columb on 2012-11-17
I reinstalled OS, but no change. What calls errors where i do command "make"?

---

### Post by chili555 on 2012-11-19
It will be very helpful for you to post the exact wording of the errors.

---

### Post by columb on 2012-11-19
> **chili555 said:**
> It will be very helpful for you to post the exact wording of the errors.

I think I found a bug, but I do not know how to fix it.
If I change value in the file HAS_ANTENNA_DIVERSITY_SUPPORT=n on HAS_ANTENNA_DIVERSITY_SUPPORT=y errors appear. but if I leave the value HAS_ANTENNA_DIVERSITY_SUPPORT=n no errors.

CC [M]  /home/hp650/rt/os/linux/../../chips/rtmp_chip.o
**/home/hp650/rt/os/linux/../../chips/rtmp_chip.c: In function ‘HWAntennaDiversityEnable’:**
**/home/hp650/rt/os/linux/../../chips/rtmp_chip.c:2010:2: error: ‘regs’ undeclared (first use in this function)**
/home/hp650/rt/os/linux/../../chips/rtmp_chip.c:2010:2: note: each undeclared identifier is reported only once for each function it appears in
**make[2]: *** [/home/hp650/rt/os/linux/../../chips/rtmp_chip.o] Error 1**
**make[1]: *** [_module_/home/hp650/rt/os/linux] Error 2**
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [LINUX] Error 2

I found a file with an error.
This is the part where the error occurs

```


VOID HWAntennaDiversityEnable(
	IN PRTMP_ADAPTER		pAd)
{
	UINT8 BBPValue = 0, RFValue = 0;

	/* RF_R29 bit[7:6] = b'11 */
	RT30xxReadRFRegister(pAd, RF_R29, &RFValue);
	RFValue |= 0xC0; /* rssi_gain */
	RT30xxWriteRFRegister(pAd, RF_R29, RFValue);

	/* BBP_R47 bit7=1 */
	RTMP_BBP_IO_READ8_BY_REG_ID(pAd, BBP_R47, &BBPValue);
	BBPValue |= 0x80; /* ADC6 on */
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R47, BBPValue);
	
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R150, **regs[0]**); /* ENABLE_ANTSW_OFDM and RSSI_ANTSWT */
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R151, **regs[1]**); /* ENABLE_ANTSW_CCK and RSSI_LNASWTH_HM */
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R152, **regs[2]**); /* RSSI_LNASWTH_HL */
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R153, **regs[3]**); /* RSSI_ANALOG_LOWTH */
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R154, **regs[4]**); /* ANTSW_PWROFFSET, ANTSW_DELAYOFFSET and auto-control BBP R152[7] (RX_DEFAULT_ANT) */
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R155, **regs[5]**); /* RSSI_OFFSET */
	RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R253, **regs[6]**); /* MEASURE_RSSI_OFFSET */

	DBGPRINT(RT_DEBUG_OFF, ("HwAnDiv --> Enable!\n"));
}


```



**/home/hp650/rt/os/linux/../../chips/rtmp_chip.c: In function ‘HWAntennaDiversityEnable’:**
**/home/hp650/rt/os/linux/../../chips/rtmp_chip.c:2010:2: error: ‘regs’ undeclared (first use in this function)**

---

### Post by columb on 2012-11-19
But I also found driver for openSUSE. I converted to .deb and installed it. But no changed. Maybe some things wrong in a driver PCIe 2860sta?

---

### Post by chili555 on 2012-11-19
Ah, ha! Now I see why it errored out for you but not me. Igenerally don't make all those changes before I compile. I assume, I see now incorrectly, that it will compile.

I don't see HAS_ANTENNA_DIVERSITY_SUPPORT=y mentioned in the README. I wonder if it's really needed. Did you try compiling and installing the driver without the change?

Did you also blacklist rt2800pci?

---

### Post by columb on 2012-11-20
> **chili555 said:**
> Did you try compiling and installing the driver without the change?
Yes, no change. How can i do blacklist rt2800pci?

---

### Post by chili555 on 2012-11-20
> **columb said:**
> Yes, no change. How can i do blacklist rt2800pci?Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
echo rt5390sta >> /etc/modules
exit
```Reboot and tell us how it's working.

---

### Post by columb on 2012-11-21
> **chili555 said:**
> Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
echo rt5390sta >> /etc/modules
exit
```Reboot and tell us how it's working.

No change and when i executed command iwconfig  it showed

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.
```

how do you see it's gone

```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


```

In my laptop Wi fi enabled through a combination of Fn +12. When he was off the amber light, and when it is on white. Previously, the system saw the device, I still could not turn the key combination Wi fi.
Now I can not see even the device, and it has seen before.
I have now is two systems: Ubuntu and windows 7. On win7 wifi works very well. I do not understand the reason in ubuntu.

---

### Post by chili555 on 2012-11-21
> I still could not turn the key combination Wi fi.Let's see:```
rfkill list all
```

---

### Post by columb on 2012-11-21
> **chili555 said:**
> Let's see:```
rfkill list all
```

0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

---

### Post by chili555 on 2012-11-21
Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement?

---

### Post by columb on 2012-11-21
> **chili555 said:**
> Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement?

I'm sorry, but no change.

---

### Post by chili555 on 2012-11-21
With hp-wmi still removed, does anything change as you press the wireless key combination?```
sudo rfkill unblock all
```Press key combination...```
rfkill list all
```Press key combination...```
rfkill list all
```Any change? What does rfkill report?

---

### Post by columb on 2012-11-21
no change
command does not display anything

---

### Post by chili555 on 2012-11-21
If there is no longer any indication of rfkill, then is the wireless now enabled?```
sudo iwlist wlan0 scan
```If you boot into Windows and turn the wireless on, is it still on in Ubuntu?

I am very low on ideas.

---

### Post by columb on 2012-11-21
command return 

```
Interface doesn't support scanning.
```

> If you boot into Windows and turn the wireless on, is it still on in Ubuntu?

No, wi fi works only windows, and when system boot wifi default turn off. And i have to turn on. On BIOS I can't change it. 
But wifi worked on openSUSE. I bought a laptop with already established openSUSE. But this system does not suit me. So I decided to install ubuntu.

---

### Post by columb on 2012-11-24
sudo rfkill list all

```

0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```sudo modprobe -r hp-wmi
sudo rfkill unblock all
sudo rfkill list all

```

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```sudo iwlist wlan0 scan
```


wlan0     Interface doesn't support scanning : Network is down
```

iwconfig

```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```



And system detected wi fi, but I can't turn on it with combination buttons Fn+F12.  See image.

[IMG]http://imageshack.us/photo/my-images/833/screenshotfrom201211241.png[/IMG][IMG]http://img833.imageshack.us/img833/6686/screenshotfrom201211241.png[/IMG]
[IMG]http://postimage.org/image/8qknm1kth/[/IMG]

---

### Post by chili555 on 2012-11-24
I'm sorry, but no combination of key presses, removing or adding hp-wmi or anything else gets rid of *hard blocked: yes*. Until the system thinks the wireless switch is switched to ON, it isn't going to work.

Are you still running 11.04? I'd certainly download 12.10 and try the live CD. Otherwise, I have no further suggestions.

I assume you downloaded and compiled rt5390sta because the native in-kernel driver didn't work for you. The real reason it won't work is rfkill, not the driver.

---

### Post by columb on 2012-11-24
I installed 12.04. before I installed 12.10 but no change. The result was the same.

---

### Post by columb on 2012-11-27
How can I remove the hard block?

---

### Post by chili555 on 2012-11-27
> **columb said:**
> How can I remove the hard block?I'm very sorry, I have no further suggestions.

---

### Post by BodyKount on 2013-02-25
Okay so it looks like this topic has been dead for awhile but I hope there is somebody that can still help me solve this issue. So I downloaded Ubuntu 11.04 a while back using Wubi and it is a partition on my hard drive. I tried to use Ubuntu because I love the way it is setup but when I tried using the internet it did not work. I read everything that everyone has said to do except I get stuck at the beginning because realtech has merged with another site now and I cannot find the rt5390 driver download anywhere else. I also have another problem as I have not used Ubuntu much so I do not know how to open the terminal (another type of command prompt im assuming). So Im probably going to have alot of trouble with this since im only experienced with windows and its commands. I would like to use Ubuntu as a partition along with my windows so I dont want to get the disk and just overwrite everything. is there a newer version that automatically finds drivers or something or can somebody help me with the version I have now?

here is some of my pc info if it helps

Compaq Hewlett-Packard Presario CQ56 Notebook Pc

Processor: Intel Celeron

64bit

the version on the Ralink RT5390 is 3.1.11.0 and the date for it is 9/10/2010

I will be checking this often but I check my email more often so if is there an awesome person out there that would help me through email it is [email]JoshMurphy0@Gmail.com[/email]

---

### Post by chili555 on 2013-02-25
[https://dl.dropbox.com/u/58267392/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip](https://dl.dropbox.com/u/58267392/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip)

Open the terminal with Ctrl + Alt + t.

The instructions are all there above, but post back if you get stuck. Are you subscribed to the thread using Thread Tools at the top?

---

### Post by BodyKount on 2013-02-25
yes im subscribed, Im going to try this and ill let you know how it goes

---

### Post by chili555 on 2013-02-25
> **BodyKount said:**
> yes im subscribed, Im going to try this and ill let you know how it goesExcellent! Post back if you get stuck.

---

### Post by BodyKount on 2013-02-25
okay so im stuck pretty quickly lol, I downloaded that file and I have it opened in Jzip, Im using my windows 7 now (because I have no access to the internet on Ubuntu) so I read the beginning part of Post #9 and im confused because I cannot see a config file to edit. after i find this and im finished editing it how do i get this driver to ubuntu?

---

### Post by BodyKount on 2013-02-25
> **BodyKount said:**
> okay so im stuck pretty quickly lol, I downloaded that file and I have it opened in Jzip, Im using my windows 7 now (because I have no access to the internet on Ubuntu) so I read the beginning part of Post #9 and im confused because I cannot see a config file to edit. after i find this and im finished editing it how do i get this driver to ubuntu?


Ubuntu is a partition im not using any type of virtual machine

---

### Post by chili555 on 2013-02-25
> **BodyKount said:**
> okay so im stuck pretty quickly lol, I downloaded that file and I have it opened in Jzip, Im using my windows 7 now (because I have no access to the internet on Ubuntu) so I read the beginning part of Post #9 and im confused because I cannot see a config file to edit. after i find this and im finished editing it how do i get this driver to ubuntu?Probably with a USB key. Drag and drop it to your Ubuntu desktop. Right-click it and select Extract Here.

---

