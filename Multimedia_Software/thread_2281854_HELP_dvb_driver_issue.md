---
title: "HELP dvb driver issue"
date: 2015-06-10
forum: Multimedia Software
---

### Post by jim113 on 2015-06-10
im new to linux for about a week.

im trying to setup a ubuntu system to run kodi as a htpc.

all is good except getting the tv tuner to work.

- yes its compatible (dvbsky s960)
ive followed every guide to install the firmware and drivers.
this has become confusing as 1st'ly im new to command lines 
and 2nd'ly errors dont make sense to me.

i think the main issue is i cant get anything to load into dev/dvb (drivers)
- i believe i have the firmware files inplace
ive been following:
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

kernel: 3.16.0-38-generic

---

### Post by Bucky Ball on 2015-06-10
*Thread moved to **Multimedia**.*

Welcome. [This]("http://www.linuxtv.org/wiki/index.php/DVBSKy#Howto_build_driver_for_Debian.2FUbuntu.2FopenSUSE") any help? It is for an older release but may just work.

Also, this from [here]("http://linuxtv.org/wiki/index.php/DVBSKY_S960#Firmware_and_Driver"):

> It's supported by linuxtv as of september 2014. _Support in-kernel is expected in Linux kernel 3.18_.

Not sure if it's there yet but you could do some research and try that kernel ... :-k

Have a look [here]("http://ubuntuhandbook.org/index.php/2014/12/install-linux-kernel-3-18-ubuntu/") and [here]("https://duckduckgo.com/?q=install+3.18+kernel+ubuntu+14").

Which Ubuntu release are you using? 14.04.2? 

... and just [one last link]("http://www.dvbsky.net/Support_linux.html") that might help you along a little further. You could try the 3.18 but there is also a driver build for 3.16. Look for this entry in the table:

> media_build-bst-14-141106 (Download) 	3.14.x ~ 3.17.0    ***Previous driver: 141014(Download)

PS: Just an after thought, and you may have already been doing this. Try to get it working in Ubuntu first rather than diddling with getting it working in Kodi to start. Install MeTV from the repositories (Software Centre) for testing (it has an autoscan function which is handy for testing and along the bottom of the screen MeTV will tell you if there is an issue with the DVB device when you launch it). Once you know it's working then launch Kodi and it should work. If it doesn't start trying to nut out why Kodi-specifically (as you know it works in the desktop). 

If you are only using this machine for media serving, you might be interested in [Kodibuntu]("http://kodi.wiki/view/Kodibuntu"). :)

---

### Post by jim113 on 2015-06-10
thanks for your speedy help for a noob. much appreciated.

ill look through your links..
yes: 14.04.2 - fresh download 1 week ago.

---

### Post by Bucky Ball on 2015-06-10
All good and righto. ;)

I have a (bad) habit of editing my posts with afterthoughts so you might want to read the last bits of my last post before lift off. Good luck and let us know how you go. The device definitely works by the looks of it. Just a matter of nutting out how to get it going with your setup.

---

### Post by jim113 on 2015-06-10
hi agian. your onthe money for the right info.

i downloaded media_build-bst-14-141106 and got it to install 3-5 mins of compiling, then sudo make install.
copied the firmware files over, rebooted.
but still nothing when dev/dvb??

**does the destination where the folder containing the driver download files matter?**
i downloaded in firefox opened in archive manager and copied to a new folder in "home"
then compiled (build_x86.sh - correct) and make install

if no tips i guess i update the kernel.

a thought. if i plug the tuner into my raspberry pi2 it boots up the tuner box on start up.

thnx

---

### Post by jim113 on 2015-06-10
i noticed the paths for the drivers files were installed to 
home/(the new folder)/v4l/

can the system find these files/modules?


thnx

---

### Post by jim113 on 2015-06-10
If you are only using this machine for media serving, you might be interested in [Kodibuntu]("http://kodi.wiki/view/Kodibuntu")

im running an older x86 machine. kodibuntu only supports x64


thnx

---

### Post by Bucky Ball on 2015-06-10
Try plugging it in and booting with you computer in that case.

As for where the file is, you need to be in the same directory as the file in the terminal, but seeing as you've gotten this far you probably know that.

The tuner box? You're saying when you plug it into the Pi it works 'out of the box'? In that case, which kernel is the Pi using or which kernel is the OS you're using on the Pi based on, if it is Debian/Ubuntu kernel ... ?

PS: You need to run 'ls /dev/dvb' to check. You're posting 'dev/dvb'. That won't find much. You are following this?

> ---Compile and install driver
1)Enter the source code directory

2)Check and choose one of the target systems, run &#8216;uname -a&#8217; to get os informaton.
./v4l/build_x86.sh if build for 32 bit system os.
./v4l/build_dvbc_x86.sh if build for 32 bit system os to support DVB-C.
./v4l/build_x64.sh if build for 64 bit system os.
./v4l/build_dvbc_x64.sh if build for 64 bit system os to support DVB-C.

3)Compile the source code:
make

4)Install driver, which need super user privilege:
sudo make install

5)Install firmware
unzip dvbsky-firmware.tar.gz file, then run bst-firmware.sh
or copy *.fw to /Lib/Firmware.

6)Reboot computer.

7)Verify the installation is successful or not:
ls /dev/dvb
If the adaptor0 is list here so the driver is installed properly.

?

Please post some terminal output of what you're doing. That will help.

---

### Post by jim113 on 2015-06-10
[QUOTE=Bucky Ball;13301314]Try plugging it in and booting with you computer in that case.
[COLOR=#ff0000]tryed - no change[/COLOR]

As for where the file is, you need to be in the same directory as the  file in the terminal, but seeing as you've gotten this far you probably  know that.
[COLOR=#ff0000]yup, looks to install correctly, [/COLOR]

The tuner box? You're saying when you plug it into the Pi it works 'out  of the box'? In that case, which kernel is the Pi using or which kernel  is the OS you're using on the Pi based on, if it is Debian/Ubuntu kernel  ... ?
[COLOR=#ff0000]ill have a look[/COLOR]

PS: You need to run 'ls /dev/dvb' to check. You're posting 'dev/dvb'. That won't find much. You are following this?
[COLOR=#ff0000]i have been, just a typo
yup - following to a tea[/COLOR]

---

### Post by jim113 on 2015-06-10
well i checked rpi and its running 13.8.10
i upgraded my ubuntu kernel and i now have dev/dvb files ! horray. 
next step, getting channels.

thanls for the great help!

---

### Post by Bucky Ball on 2015-06-10
I'm just coaxing you along, really. You're getting most of this done, so well done. :)

I have an Ezycap DVB dongle which just works out of the box in 14.04 LTS. I had to tweak like a mad man getting it running on 10.04 LTS, install a newer kernel in 12.04 LTS, then the driver was finally included in one of the 12.04 LTS point releases, so I know what a hair-pulling run-around it can be getting one of these to work. 

As I say, you can double check by installing MeTV in Ubuntu first and that will let you know the state of the dongle when you launch it. Then you know for sure when you launch into Kodi and setting up tvheadends etc., if that is still necessary (I run Kodi on an Odroid as the home media server. Works great, but have never used the Ezycap with it or the RPi before it, though I read up on it a early last year thinking I might try it).

If the DVB dongle is up and working and your original support request is satisfactorily dealt with, please mark the thread as solved using the second link in my signature and post a new thread for any further problems, i.e. getting it to work with Kodi. That will increase your chances of support. :)

Sounds like you're enjoying the learning curve so that is a good start.

---

