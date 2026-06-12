---
title: "fwcutter broken after kernel update"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by adramalech on 2009-02-02
okay so i have been keeping up with the kernel updates....i have  2.6.26-7-generic, 2.6.27-9, 2.6.27-11, 2.6.28-2-ultimate...

i found out today that all my different kernels wireless driver(i use b43 fwcutter) has broken...it will show the different options for me to connect to wireless but will not connect...it will just acquire then says it failed....

so i went and un-activated the wireless b43 driver than restarted then went to reinstall it....and it will now error!!! and won't reactivate!! 

what is up with this???

do others have to same problem???

all i did was went into menu.lst to comment out different kernel versions that i won't use like 2.6.27-2..and 2.6.27-9 and 2.6.27-7...i was trying to only use 2.6.27-11 and 2.6.28-2

what should i do??? just get rid of all versions of the kernel less than 9???

---

### Post by Ayuthia on 2009-02-02
What is the error message?  From what it sounds like, it might be an issue with Network Manager.

---

### Post by sedawk on 2009-02-02
Check the output of dmesg. Are there any errors or problems related
to your b43 firmware?.
(If you are familiar with lsmod/rmmod/modprobe/insmod you can
 remove the bw43 modules from the kernel with rmmod,
 clear the message buffer  with "dmesg -c" and then insmod/modprobe
 the b43 stuff again and have a look at the new output with "dmesg".)

---

### Post by adramalech on 2009-02-02
okay thanks guys...i will have to wait till i get a hard line at home to be able to reactivate thre restrictive driver...

then i will check dmesg after i restart...and go through and rmmod and dmesg -c and then modprobe b43...

---

### Post by adramalech on 2009-02-02
okay so i downloaded on windows and installed it...then activated it....and this is what i got on dmesg now

i am using b43-fwcutter version 1-11-4 for i386 intrepid...

```
adramalech@adramalech:/etc$ dmesg | grep b43
[    3.346818] b43-pci-bridge 0000:03:07.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   16.661708] b43-phy0: Broadcom 4318 WLAN found
[   31.251252] input: b43-phy0 as /devices/virtual/input/input8
[   31.340068] firmware: requesting b43/ucode5.fw
[   31.413546] firmware: requesting b43/pcm5.fw
[   31.435740] firmware: requesting b43/b0g0initvals5.fw
[   31.477506] firmware: requesting b43/b0g0bsinitvals5.fw
[   31.788042] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   31.908434] Registered led device: b43-phy0::tx
[   31.908656] Registered led device: b43-phy0::rx
[   31.908813] Registered led device: b43-phy0::radio
adramalech@adramalech:/etc$ 

 
```

the dmesg seems okay i didn't see any errors in loading...i even rmmod b43 then modprobe b43 and it shows its installed but nothing worked...now i don't even see the active wireless broadcast on my school campus.. (this is all in 2.6.27-11)

---

### Post by Ayuthia on 2009-02-02
Can you try the following:
```
sudo modprobe -r b43 ssb
sudo modprobe b43 btcoex=0
sudo /etc/init.d/networking restart
sudo iwlist scan
```

It was something suggested in the b43 mailing list for the 4318 cards so I am not for sure what btcoex does but it won't hurt your computer.

---

### Post by adramalech on 2009-02-04
this is what i get...don't think this is working...

but i did get it at first to try and automatically acquire a ssid but it didn't connect.

```
adramalech@adramalech:~$ sudo modprobe -r b43 ssb
[sudo] password for adramalech: 
adramalech@adramalech:~$ sudo modprobe b43 btcoex=0
adramalech@adramalech:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
adramalech@adramalech:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

adramalech@adramalech:~$ 

```

---

### Post by adramalech on 2009-02-05
```

adramalech@adramalech:/etc$ b43-fwcutter -v
b43-fwcutter version 011
adramalech@adramalech:/etc$ b43-fwcutter -l
b43-fwcutter version 011

Extracting firmware is possible from these binary driver files.
The <ID> column shows the unique identifier string for your firmware.
You must select the firmware with the same ID as printed by the kernel driver on modprobe.
Note that only recent drivers print such a message on modprobe.
Please read http://linuxwireless.org/en/users/Drivers/b43#devicefirmware

<driver>	<filename>		<microcode>	<ID>	<MD5 checksum>

b43legacy	wl_apsta.o		295.14		FW10	e08665c5c5b66beb9c3b2dd54aa80cb3
b43		wl_apsta.o		351.126		FW11	9207bc565c2fc9fa1591f6c7911d3fc0
b43		wl_apsta_mimo.o		351.126		FW11	722e2e0d8cc04b8f118bb5afe6829ff9
b43		wl_apsta_mimo.o		410.2160	FW13	cb8d70972b885b1f8883b943c0261a3c

adramalech@adramalech:/etc$ 

```


okay this is what i get when listing the support drivers for the b43-fwcutter installed....

could it be that i have an unsupported older version of the firmware?? should i just go threough and redownload the newest version of the .object files and then reput them back into /lib/firmware/b43???

also shouldn't b44 and ssb be blacklisted??? could it be conflicting between b43 and ssb???

---

### Post by Ayuthia on 2009-02-05
> **adramalech said:**
> ```

adramalech@adramalech:/etc$ b43-fwcutter -v
b43-fwcutter version 011
adramalech@adramalech:/etc$ b43-fwcutter -l
b43-fwcutter version 011

Extracting firmware is possible from these binary driver files.
The <ID> column shows the unique identifier string for your firmware.
You must select the firmware with the same ID as printed by the kernel driver on modprobe.
Note that only recent drivers print such a message on modprobe.
Please read http://linuxwireless.org/en/users/Drivers/b43#devicefirmware

<driver>	<filename>		<microcode>	<ID>	<MD5 checksum>

b43legacy	wl_apsta.o		295.14		FW10	e08665c5c5b66beb9c3b2dd54aa80cb3
b43		wl_apsta.o		351.126		FW11	9207bc565c2fc9fa1591f6c7911d3fc0
b43		wl_apsta_mimo.o		351.126		FW11	722e2e0d8cc04b8f118bb5afe6829ff9
b43		wl_apsta_mimo.o		410.2160	FW13	cb8d70972b885b1f8883b943c0261a3c

adramalech@adramalech:/etc$ 

```


okay this is what i get when listing the support drivers for the b43-fwcutter installed....

could it be that i have an unsupported older version of the firmware?? should i just go threough and redownload the newest version of the .object files and then reput them back into /lib/firmware/b43???

also shouldn't b44 and ssb be blacklisted??? could it be conflicting between b43 and ssb???

Here is what you are using:
```
b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```which is the latest version.  You might try to go back to the previous version to see if it works.  You can get it at:
[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

As for b44 and ssb, they should not be blacklisted.  The b43 module needs to have the ssb module.  The b44 module is used for some Broadcom wired ethernet cards.  So if you disable them, you could end up without having a working internet connection.

There was someone in the forum that went back to the previous firmware and get their card working.

---

### Post by adramalech on 2009-02-05
i think that kernel 2.6.28-2-ultimate screwed up my internet connection....because i go to recover any broken packages in 2.6.28 and it comes up with this....

```

Examining /etc/kernel/postinst.d

Run-parts: executing /etc/kernel/postinst.d/dkms

Run-parts: executing /etc/kernel/postinst.d/dkms/nvidia-common

Run-parts: executing /etc/kernel/postinst.d/dkms/nvidia-common exited with return code 20

Failed to process etc/kernel/postinit.d at /var/lib/dpkg/info/linux-image-2.6.28.2-ultimate postinst line 1181.

dpkg: error processing linux-image-2.6.28.2-ultimate(--configure)

Subprocess installation script returned error exit status 2

Errors were encountered while processing linux-image-2.6.28.2-ultimate

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i think that kernel version is broken so how do i remove the  2.6.28.2-ultimate kernel completely from my system or you think i should just clean install and reinstall back to kernel version 2.6.27.11-generic

---

### Post by odium1 on 2009-02-07
My boot setup isn't showing 2.6.28-2 as the latest, but 2.6.27-11 instead and I'm still having the wired ethernet problem. When i boot with 2.6.27-9 I can use my broadcom card but the connection is super slow. I'm going to do a clean re-install and update all the way up to 2.6.27-9 and stop there until the development team works the bug out of the latest kernel(s).

---

### Post by adramalech on 2009-02-08
i am actually going to find a fix for this...i am going to search launchpad for stuff and come up with a fix or something!!!

---

### Post by odium1 on 2009-02-09
please do! haha.. i reinstalled and i didn't install the 2.6.27-11 i just kept 2.6.27-7 and my wired networking worked FINE until i came home and it stopped working lol. i fixed it at work and i probably restarted 5 times because i was just installing and doing crap and right when i get home it stopped working. i just read somewhere that the 2.6.26 kernal works fine AND that the new jaunty jackalope alpha didn't have the problem.. I guess i'm going to go ahead and install JJ.

---

### Post by adramalech on 2009-02-09
i wouldn't do that unless u are a dev guy or alpha bug tester and will actually report stuff...no use getting something installed that you won't use for the purpose it was need for..

it is only in alpha-2

i used kernelcheck to get 2.6.28-2 which should be good...it comes with some good bug fixes over 2.6.27 stuff

maybe just try ubuntu 8.10 with 2.6.28-2!!!

so far the graphic drivers like nvidia and ati don't want to work well at all and i bet there are alot of bugs ur better off with either researching a way to fix it....figuring it out...or just reinstalling ubuntu 8.10 with 2.6.28-2

---

### Post by odium1 on 2009-02-11
well i followed your advice and just used kernel checker to download and install the newest kernel (2.6.28-*). I had re-installed 8.10 but didn't update to the 2.6.27-11 kernel but i was still having the issue. so, after i booted up last night, i unplugged the power cord on my cable modem and gave it about 120 seconds and plugged it back in. after it restarted itself i was able to connect and run kernel check. I will check this evening when i get home from work and see if running the new kernel fixes the problem.

---

### Post by adramalech on 2009-02-11
okay...well keep me informed i am going to try it too...

---

### Post by odium1 on 2009-02-11
ah ha! success! i just got in from work, rebooted and checked to see which kernel loaded automatically and it is 2.6.28-4 ultimate. got booted up and it connected right to the wired network.

---

### Post by adramalech on 2009-02-12
wow they are already on to version 4 that is good....sooo did the wireless work??? or did just the eth0 (your hardline connection)???

i actually uninstalled my hdd and reinstalled ubuntu 8.10 and re updated with using any unrecommended updates and it is sooo screwed up...i cannot installed the restricted driver for flgrx i do have the b43-fwcutter installed with the newest firmware but no success in having it acquire any ssid's!!!  checked lspci -v command and lsmod | grep b43 and everything looked good even checked the dmesg and everything looked as it should i really think it is something wrong with 2.6.27.11-generic..

u seeing any better results on 2.6.28.4-ultimate???:confused:

u know that 2.6.28.4-ultimate is the kernel version for jaunty jackalope alpha version 4!!! it said that it fixed some issues that where plagueing the 2.6.27 kernels...i hope it works i was just going on a hunch that the newest kernel will go good...i love kernelcheck because of the ability to use a gui to change options into make a custom kernel install...:)

it has ext4 filesystem format stable and the new gem(better graphics interface to get rid of glitchy videos off of the internet) but i don't believe u can use any of the new stuff with intrepid ibex i believe u will have to wait to update your distro to jaunty in april 2009:(

---

### Post by odium1 on 2009-02-12
yeah wired and wireless work just fine now :D yeah, from the minute i updated to the 2.6.27-11 kernel i had problems.. after two weeks of trying everything i could find i thought it was going to be pretty hopeless until the development team fixed the bug but after you mentioned using kernelcheck i figured i'd give it a try.. i'm glad it worked, i was slowly losing my sanity haha.

---

### Post by adramalech on 2009-02-12
lol kewl!!!

KERNELCHECK FTW!!!!:P


i know need to reinstall back to 2.6.28.4 because i updated back to 2.6.27.11 and have used everything from the b43 restricted driver, the compat-wireless-2009-02-10, all the way to the ndiswrapper which even that doesn't work....so 2.6.28.4-ultimate here i come!!!! weeeee:lolflag:

---

### Post by odium1 on 2009-02-13
haha.. i'm still battling with my ibook g4 trying to get the wireless card working. it has the airport extreme (broadcom chipset) but i couldn't get ndiswrapper installed/configured correctly. the ethernet connection works though.. so i'm thankful for that. when this computer went down i was still able to get online lol. i have dapper drake on the ibook because i hated yellow dog and i couldn't get 8.10 to even boot.. i've since found a work around but i'm just being lazy.

---

### Post by Anti-Me on 2009-02-13
Hello all,

I'm having a similar problem. When i boot the 2.6.27-11-generic kernel in Ibex, my wireless networking card is not detected. A message is displayed stating the critical error. I was previously using the 2.6.27-9-generic kernel, and if i boot with this kernel everything works fine.

So, what should i do now? I mean, if i can just use 9-generic, i suppose i should, correct? If so, should i get rid of 11-generic, and how do i do that? OR, should i try to fix 11-generic to detect my wireless card? It shouldn't be that hard, right? I mean, i had to go trough a couple hours of "work" to get the ralink 2500 module to work properly for Ibex in the first place, so i imagine getting the module to work for 11-generic is, what, a matter of blacklisting and mod commands, maybe?

Anyway, i know there are some things you need to know in order to give me some help, which is very appreciated, let me say in advance. But, unfortunately, i don't know what those things/commands are. But in any event, any help is deserving of many thanks.

BTW, i don't remember actively updating my kernel, unless it's updated through the update manager, which is what, i'm guessing, notifies me automatically when updates are called for/available.

---

### Post by adramalech on 2009-02-13
no no....use kernelcheck it will get u the best newest and cleanest kernel this side of the universe!!!

go to google and search for kernelcheck...

download the newest version from the webpage...i suggest getting the .deb file so it is easier to install than the .tar file

okay once u done that u will not see it in any of the applications or in system but u can run this command

sudo kernelcheck

it will then pop up with kernel check's gui and then you can choose between different options of what kind of kernel to check for...

i would usually suggest stay with the stable version like i am just now compiling 2.6.28.rc5 

and then go to program on the top left of the gui and then click on build latest kernel and then let it work its magic

i would suggest that you first clean install your system meaning get the cd out and partition and formate your drive, then using update manager unclick any update to 2.6.27.11 and update everything else...

also install all of the wireless b43-fwcutter if you have the3 broadcom restrictive driver and any other restrictive driver....

when you restart then just run

sudo kernelcheck 

you will have to go through and save the .config file which is a file that popups up during building the kernel that will allow you to change the settings of what to build aka make a custom kernel easy with a gui!!! unless you know what you are doing or want any experimental stuff in your custom kernel then don't change any settings in the .config file or check any experimental stuff!!  just save it in the kernel directory of whatever kernel version you are installing then it will just compile taking 2-4 hours

then just do as i say above and then after that you might have to reinstall your graphics and some restrictive driver....

then walla...you got it made in the shade!!

---

### Post by adramalech on 2009-02-13
```

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.5-ultimate.postinst line 1181.
dpkg: error processing linux-image-2.6.28.5-ultimate (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28.5-ultimate
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i think there are still some errors and i might say it is a big bug...now i went from having to deal with 2.6.27.11 to having to deal with dpkg and /etc/kernel/postinst.d  

should i install repo's for jaunty???


edit: also found this to be of what i just posted here with issues with broken installations

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305794/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305794/+viewstatus)

---

### Post by adramalech on 2009-02-13
okay so i figured it all out...

the man pages are our friends:lolflag:

okay so here is what you do...run this command in your terminal

sudo dpkg-reconfigure -a

and then you will have to reinstall some stuff don't worry it is easy and straight forward...

this is thought not for the feint of hearts!! like you will need to know if you are running gnome, kde, or something else...along with some other basic stuff 

consult manpages or guides...sorry i don't have any to link but just take my word for it....it is pretty easy to do

furthermore u will see certain parts that blue screens will pop up with options you will need to select like how debian use to be during installs!!:guitar:

EDIT:
okay so i have found out that for defaults just press ENTER but on certain things...like on some cups settings like what kind of connection is default for your printer usually switch it to usb...etc..

---

### Post by odium1 on 2009-02-15
hmm.. did you start having those problems with 2.6.28-5? see, i compiled and installed 2.6.28-4 ultimate and i haven't had the first problem. my system is actually running more smoothly than it ever has lol.

---

### Post by adramalech on 2009-02-15
mannnnn grrrrrrrrrrrrrrr](*,):twisted::confused::mad:

---

### Post by philosophia on 2009-02-20
I have the same problem.  fwcutter broken on 2.6.27-11-generic.  I tried booting to 2.6.27-7-generic and reinstalling the .deb package - this didn't work.  What's the best thing to do?  Upgrade to Jaunty?  I don't have a working network card on this laptop now, so it would be difficult to upgrade the kernel using kernelcheck.

---

### Post by adramalech on 2009-02-20
okay from what i understand you need to run the command to see if it can forcefully fix everything...

with me that command didn't work...and my problem wasn't with my wireless it was with my nvidia-common...

so i purged it out of cache and then reinstalled it...

can you show me your output when you go to install a package???


like can you hardline to a network and then try and install a package does it give you an error???? and if so can u print it out...

check your log files...and check your dmesg for errors if any it will be a great help to me helping u...

---

### Post by philosophia on 2009-02-20
> **adramalech said:**
> okay from what i understand you need to run the command to see if it can forcefully fix everything...
with me that command didn't work...and my problem wasn't with my wireless it was with my nvidia-common...

so i purged it out of cache and then reinstalled it...

can you show me your output when you go to install a package???



I'm not sure what command you're referring to.  Since I have no internet connection now, I have to install from the b43-fwcutter .deb package.

sudo dpkg -i b43-fwcutter*deb

I can't post the output since I have no internet connection on the laptop, but there are no errors when I attempt to reinstall this package.

---

### Post by adramalech on 2009-02-21
purge the b43-fwcutter....

dpkg --purge or whatever the command is....

if you still have the problem with the wireless does it show anything different like in the dmesg it doesn't show that it didn't error or didn't load correctly then it should be installed correctly

there is a command to forcefully check all your packages and if they are not correctly installed or running it will reinstall them correctly...i wish i knew what the command was ......i will hopefully find it....if i don't i will ask a friend and have him tell me the command he told me to run that way i can tell anybody that has this problem

because i even have the 2.6.27.11-generic installed without a issue...by running this command...

---

### Post by adramalech on 2009-02-21
okay here goes it...i found 3 commands that might help

sudo apt-get install -f

sudo apt-get install --fix-missing

sudo apt-get dist-upgrade

---

### Post by philosophia on 2009-02-22
I installed windows on the laptop and gave it to my wife.  Lol.  It's not worth spending hours and hours to fix non supported hardware.

---

