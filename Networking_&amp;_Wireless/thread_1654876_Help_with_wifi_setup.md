---
title: "Help with wifi setup"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by chenry on 2010-12-29
I am new to Ubuntu.  I am dual booting with windows xp on a dell computer I recently acquired. I am running Ubuntu 10.10.  The computer didn't have a wireless connection so I installed a wireless pci adapter from a company called ZONET.  I installed it perfectly on windows xp, however, I cannot install the driver and the "Ralink Wireless LAN" on Ubuntu.  I inserted the cd, and opened the setup.exe file with Wine Windows Program Loader (I have installed Wine 1.3 by following the instructions on [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and clicking on the link that says "click here". I am currently temporarily connected to the internet by borrowing my main computers ethernet cable).  I followed the instructions on the InstallShield Wizard only to have two windows pop up saying there is an error (see attached image).  Please remember I am a beginner with Ubuntu.  All help is greatly appreciated.  I would hate to waste 40 bucks on a wireless adapter...

P.S. I can post more pictures if needed

---

### Post by PatchesTheCaveman on 2010-12-29
Windows drivers will not work on Linux, except through an arduous process that is generally unnecessary.

To help us figure out your problem, we need to know exactly what model wireless card you have.  To do that, click Applications on your top menu, choose Accessories, and click Terminal.  Type in *lspci -v* and press Enter.  That program will spew a bunch of information about lots of devices in your computer.  Find the one that says something like *04:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe* and copy that line and the indented lines below it and paste in in a reply to this thread.  That will tell us exactly what card you have and what (if any) driver it has installed.

---

### Post by chenry on 2010-12-29
Thanks for the help.  I wont be able to check until tomorrow. However, I can give you everything on the package right now if it is of any help. It is called a Zonet ZEW1642S - 802.11n Wireless PCI Adapter. Its interface is 32-bit PCI and Chipset is Ralink Rt3062.
Again, I appreciate the help and if that information doesn't help I will follow your instructions and post that information tomorrow (most likely in the morning sometime).

---

### Post by PatchesTheCaveman on 2010-12-29
Don't worry about it.  That's what I needed to know.  :D

First, download the Ralink RT3062 Linux driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2).  Select the one labeled *RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592)*.

Second, open a terminal window by going to Applications > Accessories > Terminal.  Then, install everything you need to build the driver by entering the following command in that window and pressing Enter:
```
sudo apt-get install build-essential
```
Note that you'll need to plug your computer into an Ethernet connection for Internet access to complete this step.  Leave the terminal open because you'll need it again in a little bit.

Then, follow the instructions in the README_STA file included in the zip file you downloaded.  It's a little complicated so let us know if you have trouble.

#-o If you make it through all that, there appears one more thing you have to do to get it working.  In your terminal window, run this command:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Then add the following lines to end of that file:
```
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib
```

Save and reboot and you should be good.  Once again, let us know if something goes awry.

---

### Post by chenry on 2010-12-29
Okay so I have downloaded the .tgz file.  I extracted it and so I have the extracted folder and the actual .tgz on my desktop.  I copy and pasted the first terminal command you gave me, except it said  "[sudo] password for *name*:".  I couldn't enter my password though. What do I do from here? Do I need to disable my password?
Thanks for all the help so far.

---

### Post by PatchesTheCaveman on 2010-12-29
No, you should just be able to enter your password at that screen and press Enter.  It won't show any stars or dots when you type it, just type it in and press Enter.

---

### Post by chenry on 2010-12-29
Okay so I'm on step 3 of the README_STA instructions. I don't understand what I am supposed to do for this step though.  The step is:
```
3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d
```How do I define the GCC and LD of the target machine? Also, when it says modify to meet your need I want to make sure no further modifications need to be made.
Thanks again for the help!

---

### Post by PatchesTheCaveman on 2010-12-29
Okay, so I double-checked with other people's experiences with this card and Ubuntu and you'll need to deviate a little from the README for it to work properly.  So bear with me...

First of all, I hope you changed absolutely nothing in the Makefile in step 2 because the defaults were correct.  If you did, delete the folder and re-extract it so you have the originial.

Then, in the os/linux/config.mk, change the HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT flags to *y* like so:
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

You shouldn't have to touch anything else in config.mk.  The GCC and LD are fine as is.

After that, go to Applications > Accessories > Terminal and run the following commands, which assume you have the extracted driver folder as originally named on your desktop:
```
cd ~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
make
```

Apparently you might get an error that says this:
```
too few arguments to function ¡¥iwe_stream_add_event"
```

If you do, run these commands:
```
patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c
make clean
make
```

After that, or if you don't get that error, run this command:
```
make install
```.

At this point, you'll want to edit the blacklist.conf file like I mentioned previously.  Just to keep things simple, I'll repeat those instructions.  Run:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Then add the following lines to the end of that file:
```
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib
```

Finally, just one more step to override the broken default Ubuntu drivers and make the one you just put together work.  Run the following commands:
```
sudo su
echo rt3562sta >> /etc/modules
exit
```

Reboot.  With any luck, your wireless card should work properly.

---

### Post by chenry on 2010-12-29
I did all of this and now I no longer have the option to connect to hidden wireless network.  I am not sure what went wrong? The only thing I can think of is that it said Error 2 when I ran the command```
cd ~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/ make
```I then ran the code:
```
patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c make clean make
```
Again I have no idea what went wrong here, except it now only says Wired Network and VPN connections when I click on the Wifi bars.

---

### Post by PatchesTheCaveman on 2010-12-29
Did you hit Enter between each command listed on the two you included?  You showed them all one one line, when you should have hit Enter between them.

If that's the case, your wireless options disappeared because you removed the faulty driver but did not install the working one.

Try just these steps again (I added one to remove any broken stuff from earlier):
```
cd ~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
make clean
make
```

Again, make sure you hit ENTER after each line.

Once again, you could get this error:
```
too few arguments to function ¡¥iwe_stream_add_event"
```

If you do, run these commands, again pressing ENTER after each line:
```
patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c
make clean
make
```

After that, or if you don't get that error, run these commands, once again pressing Enter after the first:
```
make install
modprobe rt3562sta
```

That should be enough to get your network icon to show wireless again, hopefully showing your wireless router along with it.  You don't need to repeat the rest of the steps.

If not, give it another reboot.  If you see any other error than the one I mentioned above, let me know.

---

### Post by chenry on 2010-12-29
It still is the exact same.  The first thing I noticed is that when I copied ```
cd ~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
```into terminal, it did something weird where it showed up twice (see attached screenshot)
Secondly, when I entered the command "make" (in the first set of codes), this was the last thing that popped up:```
cp: cannot create regular file `/tftpboot': Permission denied
make: *** [LINUX] Error 1
```Next, when I ran "make install", this is what showed up:```
connor@connor-Dell-DE051:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ make install
make -C /home/connor/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': Permission denied
make[1]: Entering directory `/home/connor/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
mkdir: cannot create directory `/etc/Wireless/RT2860STA': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/connor/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
make: *** [install] Error 2
connor@connor-Dell-DE051:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ ^C
connor@connor-Dell-DE051:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ 

```Lastly, when I ran 
modprobe rt3562sta, this showed up: ```
FATAL: Module rt3562sta not found.
connor@connor-Dell-DE051:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$
```.
Thanks for the help!

---

### Post by PatchesTheCaveman on 2010-12-29
> it did something weird where it showed up twice

That's fine.  If you notice, the Linux command line shows your username, the name of your computer, and the present folder your in before the dollar sign ($).  Before it just showed ~ as your current folder, because that's an abbreviation of your home folder (so ~ = /home/connor).  When you changed to the gigantic folder name that the driver is installed that, it shows it on each line.  If you maximize your terminal window so it fills the whole screen, it should give you a little more real estate.

I tried everything on my computer to see what was going on.  I now have a useless wireless driver, but I figured out your problem!  :?  For some reason, the "make" command is requiring administrator authority.  In ten years of messing with Linux, I've never seen the make command need that.  I guess an old dog sometimes can learn new tricks...

From a fresh terminal, run these commands.  Remember to hit Enter after each one:
```
cd ~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
make clean
sudo make
sudo make install
modprobe rt3562sta
```

Note that after you run the *sudo make* command and press Enter, you will need to enter your password and press Enter.  It remembers your password for about 5 minutes so you won't need to enter it for the second sudo command.

---

### Post by chenry on 2010-12-30
Thanks for all the time you are putting into this.  My problem now is that when I copied the last command, this showed up:```
FATAL: Error inserting rt3562sta (/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt3562sta.ko): Operation not permitted

```
Other than that there weren't any issues with the other commands.  Thanks again for the help!

---

### Post by PatchesTheCaveman on 2010-12-30
I'm sorry, I forgot to put sudo in front of it.
```
sudo modprobe rt3562sta
```

Rebooting would have had the same effect though so if you did that it might have started working.

---

### Post by chenry on 2010-12-30
yep I rebooted it and got it working.  Thank you so much for all of the help! There is no way I would have been able to figure this out by myself!

---

### Post by chenry on 2010-12-31
Would you mind helping me out with another issue?
It's on this thread: [http://ubuntuforums.org/showthread.php?p=10299445#post10299445](http://ubuntuforums.org/showthread.php?p=10299445#post10299445)

---

### Post by ariffe on 2011-01-11
i bought edimax wireless ieee802.11b/g/n 32bit pci adapter soys it is ok for linux try to install but i am a novice please can someone help me thankyou

---

### Post by PatchesTheCaveman on 2011-01-11
Plug it in.  It might Just Work.

If not, follow the instructions in this post to provide us with diagnostic information so we can help you:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by UrBob on 2011-03-06
Thanks for the instructions.
I have a PCI card with an RT3060F chip which was totally ignored by Ubuntu 10.10 until I followed the instructions. One additional problem has to be dealt with though.
During starting the PC I got an error, confirmed with dmesg, that rt2860sta was already loaded.
Executing
:~$ sudo rmmod rt2860sta
:~$ sudo modprobe rt3562sta
successfully loaded the correct support.
Trouble is, I have to do this every time I start. I guess I have to blacklist something, just not sure what. I would guess it's something like blacklist rt2xxx, but don't know how to find out what rt2xxx should be exactly.
PS I seem to always have had to use sudo with make in Ubuntu (although I only started using Ubuntu with the 8 series).

---

### Post by UrBob on 2011-03-07
OK, I was getting the problem I mentioned where I had to run rmmod and  modprobe every time I started Ubuntu, but after a few more shutdowns the  problem seems to have gone away. I think I restarted the PC at least  four times without making any other changes to configuration before the  problem solved itself.

---

