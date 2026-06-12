---
title: "WUSB11 v2.6 wireless help"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by cwa on 2010-11-15
Hello,

I am trying to get my Linksys wireless adapter (WUSB11 V2.6) to work under kubuntu /ubuntu.

I have searched the forums and found lots of help to get me where I am. But I am still not able to connect. I believe that I am overlooking or not understanding something. 

This is a walk-through of steps I have taken. I can post log files or command outputs as needed. 

lsusb shows my adapter, I checked at one point and saw the log file said it needed the firmware from at76c503a.berlios.de so I downloaded the at76_usb-firmware.tar.gz file and copied the at76c503-rmfd.bin file to /lib/firmware and ran chmod 755/ chown root:root as the instructions said.  

I then ran rmmod -f at76c50x_usb followed by at76c50x_usb. iwconfig now shows my linksys adapter as wlan1. I use ifconfig to bring the interface up and then set the essid (not hidden) with iwconfig. I then use dhclient to try and get a dhcp address, but no luck.

I have tried setting the wireless mode to managed and setting the ap with the cell address of my wireless router. Still no luck. I continue to the get dhcp no offers report. 

I have read that I need to shutdown network-manager if configuring by hand. I did this with service network-manager stop. it doesn't seem to get an address either after this.

Checking the output of messages, kern.log and syslog I get wlan1: link not ready and if I set the ap by hand. I get that it can not associate 

Here are some other things that I have noticed and wonder if it is a problem:

lshw shows my wlan1 interface, it shows a loaded driver but gives firmware = N/A (this is after copying the firmware file to /lib/firmware) (log files seem to indicate firmware version)

After setting the ap manually with iwconfig, iwconfig output still shows that the access point is not associated. I am not sure if it is supposed to show the cell address after manually setting it or only if it is connected to the router. 


I am running kubuntu 10.10 and I am trying to connect to an open router. 

Thank you for the help,

cwa

---

### Post by uncaspi on 2010-11-15
Perhaps you need to blacklist the module driver you don't to be loaded before you restart the networking service.
See the file /etc/modprobe.d/blacklist.conf

---

### Post by cwa on 2010-11-15
Thanks for your response. I am not sure what module to blacklist. 
I checked dmesg and there seems to be no conflicting modules, I also checked lsmod and I have modules listed for ath5k (which won't work), at76c50x_usb and mac8011

when checking dmesg, all I get is the at76c50x_usb driver saying it needs the firmware

Note: I was reading that the atmel driver from atmelwlandriver.sourceforge.net needs to be patched for the 2.6 series kernel. Does this apply for kubuntu 10.10 ?

thanks,
cwa

---

### Post by uncaspi on 2010-11-16
I then ran rmmod -f at76c50x_usb followed by at76c50x_usb.
What do you mean "followed by"? I mean you could blacklist this driver and put the one you want loaded in /etc/modules
If you need the patch for your new driver for the 2.6 kernels it also needed in other distros since it depends of which kernel you have.

---

### Post by cwa on 2010-11-16
Sorry, I forgot a word. I meant that I removed the module at76c50x_usb and then ran modprobe at76c50x_usb. This is what the instructions said after copying the firmware to /lib/firmware. I am guessing it reloads the driver which finds the new firmware. 

All the searching that I have done indicates the at76c50x_usb driver is the one I need for the wusb11 v2.6. If I need to blacklist a conflicting module, then I need it explained to me, because I'm not aware of which module to blacklist.

as far as the 2.6 patch. Am I correct in thinking that I would I have to patch the kernel source, and then recompile the kernel? 

The other thing that I have thought about is this: I have read that the at76c503a driver from berlios.de is better though I have a hard time getting it to compile as I keep running into missing files during compile time. 

thanks for the help.

cwa

---

### Post by uncaspi on 2010-11-16
The one to blacklist must be ath5k. 
I would not recommend a patch and recompiling the kernel due to you could ran into serious kernel problems. I would rather buy a new adapter.

---

### Post by cwa on 2010-11-16
thanks for the help. I will try to blacklist the ath5k driver. and get back to you on it. It wont be till late at night or tomorrow due to work though.

I checked the atmelwlandriver.sourceforge.net site again and it appears that I don't need to patch the later releases of the 2.6 series kernel.

---

### Post by cwa on 2010-11-16
Hello,

I should mention that while I installed Ubuntu 10.10 (server) and could not get wusb11 v 2.6 (NOTE: I know not to run a server off of wireless, but I want to learn how to configure Linux wireless manually) Lately, I have been using kubuntu 10.10 live. 

I am not able to blacklist (due to loosing it after rebooting) however, I did rmmod the ath5k driver and unloaded it. If I am not mistaken, that would produce similar results to blacklisting it. 

After unloading the module, I still could get no results.

Are the steps I am taking right?

(after copying the correct firmware and reloading the at76c50x_usb driver)

1) sudo ifconfig wlan1 up (have to do this otherwise iwlist scan says network is not up)
2) sudo iwconfig wlan1 essid "name" mode managed (I sometimes set ap, sometimes not)
3) dhclient wlan1


I am out of ideas.

Thanks,
cwa

---

### Post by uncaspi on 2010-11-17
You must shut down network-manager before you connect manually.
sudo service network-manager stop

If you want at76c50x_usb to be loaded at boot put it /etc/modules

sudo echo "at76c50x_usb" > /etc/modules   If you get permission denied log in as root and skip sudo.

And in /etc/rc.local you put rmmod ath5k 
Reboot.

---

### Post by cwa on 2010-11-18
Hello,

 I just wanted to update you in this process. I booted Ubuntu 7 something. I was able to get on the internet with my wusb11 v2.6. I did some snooping around and found that it was using the at7_usb driver which got replaced by the at76c50x_usb driver in later 2.6 kernel releases. I found some websites that talked about older Ubuntu's running this and people got them to work out of the box. I also noticed that the ath5k module was not loaded as well. 

A few days ago, I downloaded at7_usb and at7_usb-firmware from at76c503.berlios.de I also download the cvs tarball and some other firmware as well. 

I want to try the blacklist suggestion, but if that doesn't work,
I will decide to try and get the at7_usb driver working. However, I was having problems to get it to compile. I was wondering if you would be able to answer some questions about error messages I was getting. I appreciate the time you have taken to help out.

---

### Post by uncaspi on 2010-11-18
Yes you run into compiling problems because at7_usb is intended to use another kernel version and another gcc compiler. So I'm afraid I can't solve your compiling problems.

---

### Post by uncaspi on 2010-11-18
I have compiled with no errors the at76c503.ko driver with a 7 years old compiler version. See the attachment.

Put it in /lib/modules/2.6.32.....generic/kernel/drivers/net/wireless

and try sudo modprobe at76c503 and see if it lods with no errors.
If it does place the firmware bin files in /lib/firmware
if the directory don't exist make it. sudo mkdir /lib/firmware
and sudo chown root /lib/firmware

Let me know if it works.

---

### Post by cwa on 2010-11-18
thanks for all your help. I guess that is why it is balking at no gcc compiler installed when it appears that I have one installed. (At least, according to package management - I didn't verify manually)

Right now, I am dual booting. This is a lot better situation then trying to boot off of live cd all the time for this work. 

 I have the /lib/firmware directory. I will give this a try and get back to you tomorrow.

cwa

---

### Post by cwa on 2010-11-19
Hello, 

I copied the file over, I copied it over to the wireless modules directory, ran modprobe and it said no module existed, I ran depmod and then tried again and it brings up the following error:


FATAL: Error inserting at76c503 (/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/at76c503.ko): Invalid module format

I know there is a solution, it might be faster to buy a different card, but I know there is a solution, just haven't found it.

---

### Post by uncaspi on 2010-11-19
Yes you could buy a new card or try other drivers;)

---

### Post by cwa on 2010-11-19
ok, ran modinfo on the driver you gave me, it was compiled for a 2.4 series kernel, I looked up that error and it mentioned that the cause was compiling for a different kernel.

is there any way to compile the at76c503a from berlios for the 2.6 series kernel? I would think so, I would probably have to have kernel source/headers and gcc installed?

---

### Post by uncaspi on 2010-11-19
I think the problem is the compiler version. The compiler I used is 7 years old and probably gcc-2.96 or gcc-3.1. Thats the main problem when compiling source codes. You could try to use git and download the old gcc if you find and old respitory housing ubuntu 7. Currently installed gcc I have now is version 4.4.3. And I tried apt-get install gcc-3.1 ,but it didn't find it.

---

### Post by cwa on 2010-11-19
Yeah, from my understanding when reading forums of others getting their wusb11 v2.6 to work. I tried to follow suit, but nothing. I seem to be missing something or having compiler issues. 

I tried compiling the driver from berlios, but it kept complaining about missing linux/config.h 

I checked in the headers/include directory for that file, but didn't see it. I saw a configfs.h edited the complaining c file, it moved on but dumped out too many errors that are above my head to fix. 

at this point, at least looking to see which card works the best, not sure about buying anything yet. I *hate* giving up, especially when others seem to get it to work. 

Do you think Prism2 chipsets work the best? Do you have any recommendations?

---

### Post by cwa on 2010-11-20
Hi,

Thanks for all your effort, but I got rid the wusb11v2.6

With all of the forum posts that I have read, it seems the wusb11v2.6 series worked the best with the at76_usb and at76c503a drivers in the 2.4 and maybe early 2.6 series kernels. All the howto's that I have read and forums where people got it to work were earlier versions of the linux kernel/distro's and years ago. Once they ditched at76_usb for at76c50x_usb, The one site I found with Ubuntu 10.04 or 10.10 ..the thread was unsolved and it appeared that the user had the card set up right. Also read about this driver being flaky and not working well. Though I would imagine it has to work otherwise why keep it? I did download the atmelwlandriver - which hasn't been updated it seems for a while. I also downloaded the 2.6 series patch and the most recent kernel. I had thoughts of trying to compile my own kernel and use the last release of the atmel driver from sourceforge. 

But no need now, got rid of the adapter :) I also not sure if my above speculation is correct! I may very well overlooked a problem with configuration.  If I ever get a wireless adapter again, I am thinking prism2/etc based that can be used with HostAP. 

Thanks again for the help. If I need help with things in the future, I will post in the appropriate forums.

cwa

---

### Post by uncaspi on 2010-11-20
Your thoughts are right. I have tried several days to compile the at76c503 driver for your kernel version with no luck. I would search the threads for Prism, to locate eventually problems related to your
linux distro. Good luck :D

---

### Post by cwa on 2010-11-24
Although this thread is not 'solved', I am going to mark it as such to close it. I mentioned in the above post that I am thinking about prism2/etc cards, but now thinking ath9k chipsets. There were a few ideas I had about getting the wusb11 v2.6 to work in 2.6.36 or newer. But I didn't get it figured out.

cwa

---

### Post by theiron on 2011-05-20
My issue is similar,  I'm attempting to wrest a Dell Dimension 4600C from a bad Windows XP installation (keeps asking for authentication and won't allow login) and have installed Ubuntu 10.10 alongside, booting into Ubuntu and then mounting the Windows filesystem to get at the data.  The wireless adapter is a Linksys WUSB11 v2.8, and I've been thru all of the suggestions about downloading and making the driver.  I got the firmware installed with an "sudo apt-get install atmel-firmware" (with the desktop on the wired network, and it worked without a hitch.

Doing the MAKE of the driver ran into a hitch looking for "ieee60211.h" when it was compiling, and I can't find that file ANYWHERE.  The error in the MAKE is this:  

"fatal error: net/ieee80211.h: No such file or directory"

Full text of the MAKE:
> make -C /usr/src/linux-headers-2.6.35-28-generic M=/media/9402-7555/WUSB_Drivers/Driver/at76_usb-0.17 KERNELRELEASE= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /media/9402-7555/WUSB_Drivers/Driver/at76_usb-0.17/at76_usb.o
/media/9402-7555/WUSB_Drivers/Driver/at76_usb-0.17/at76_usb.c:39: fatal error: net/ieee80211.h: No such file or directory
compilation terminated.
m

Any help circumventing this issue would be appreciated.  The firmware is installed and online, but I don't know if the DRIVER is up and installed, or if it is the correct one!  I haven't been successful building the driver, so I've not gotten to the MAKE INSTALL.

---

