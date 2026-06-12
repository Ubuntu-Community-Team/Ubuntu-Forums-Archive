---
title: "ASUS USB-N13 fails to communicate"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by ibates on 2010-12-05
Chili555 where are you?

I am running Ubuntu Release 10.04 (lucid), Kernel Linux 2.6.32-26-generic-pae, GNOME 2.30.2.

I have installed the ASUS USB-N13 according to your advice in previous posts, specifically, in your advice to 828688 Ben.

The dongle seems to be operating as it should.  The LED does its flashing at what appears to be the correct time.  Wicd also looks correct.  Networks are found with good signals shown.  Everything looks correct.  But when I attempt to connect, "validating authentication" runs for quite some time, and eventually results in a dialogue window stating the communication failed.  The required WEP password is entered in the RT2870STA.dat file, and again in the wicd window.

I have entered as much detail in the RT2870STA.dat file as I dare, and believe it to be correct.

ndiswrapper is not installed.  Network Manager is uninstalled.  Only wicd remains.

Any thoughts, or queries which might allow you to diagnose this predicament?

---

### Post by chili555 on 2010-12-05
Remind me, or better yet, link me to the method you used, please.> Chili555 where are you?Feel free to send a private message if you feel that I can help and I don't catch the thread right away.

---

### Post by ibates on 2010-12-05
[http://ubuntuforums.org/showthread.php?t=1444746&highlight=ASUS+USB-N13](http://ubuntuforums.org/showthread.php?t=1444746&highlight=ASUS+USB-N13)

That is the thread I referred to.  It all went exactly as per the results of terminal inputs (modified a bit for my own particular case, but none the less, the same outputs) until we got to about post #40.  The user you were responding to then had problems with validating authentification.

And that is where I am up to.

Everything looks good.  Wicd seems to be working OK.  I am running two WLANs and wicd recognises both, but I can not vallidate authentification with either although I am entereing the correct WEP Hex password, which I have also entered in the RT2807STA.dat file.

I am at a bit of a loss.  Out of ideas in fact.  So hopefully you can dig me out of the hole.

I would really appreciate your help.

---

### Post by chili555 on 2010-12-05
Please remove, if you have them, /etc/udev/rules.d/network_drivers.rules and /etc/modprobe.d/network_drivers.conf. Reboot. Is your device available when you click the Wicd icon? If so, try to connect a couple of times and then do:```
sudo cat /var/log/wicd/wicd.log > ibates.txt
sudo cat /etc/Wireless/RT2870STA/RT2870STA.dat >> ibates.txt
zip ibates.zip ibates.txt
```Attach the ibates.zip file you will find in your home directory to your reply.

---

### Post by ibates on 2010-12-05
Please remind me how to remove those two files.  Memory moment!

---

### Post by chili555 on 2010-12-05
No worries. Please do:```
sudo rm <some_file>
```You can copy and paste from the forum page to the terminal.

---

### Post by ibates on 2010-12-05
OK.  That's done, 

First question - no.  The device is not available in wicd following removal of the two files.  Also no LED activation on the dongle.

And here is the .zip file

[http://ubuntuforums.org/attachment.php?attachmentid=177552&stc=1&d=1291604730](http://ubuntuforums.org/attachment.php?attachmentid=177552&stc=1&d=1291604730)

Let's know if you didn't get it.  I was feeling in the dark a bit how to do it.

---

### Post by chili555 on 2010-12-06
The method in the link you provided took two different approaches; one didn't work (see post #4) and the next one did (see post #16 and following). Did you do the download and compile? Let's see:```
sudo modprobe rt3070sta
iwconfig
modinfo rt3070sta | grep -i version
dmesg | grep -i rt3
```Some of these commands may produce an error or no output; each result is significant and we need to know what it is. Also, I notice that, in your Wicd log, you successfully connect with wired ethernet. I doubt you will also get a simultaneous wireless connection. After we sort out the driver, our tests must be with the ethernet detached.

Your requested file came through just fine.

---

### Post by ibates on 2010-12-06
Since my last post, in an attempt to sort out what the heck, I had reinstalled the two files you asked me to remove.  Do you want me to remove them again before continuing?

---

### Post by chili555 on 2010-12-06
No. Please proceed.

---

### Post by ibates on 2010-12-06
I have not removed those two files.  And here are the results of your requests in your last post:

hedy@hedy-laptop:~$ sudo modprobe rt3070sta
hedy@hedy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"beerwah"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:60:64:3F:5B:DC   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-35 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

hedy@hedy-laptop:~$ modinfo rt3070sta | grep -i version
version:        2.1.2.0
srcversion:     490C020EB5EF0484E8F2833
vermagic:       2.6.32-26-generic SMP mod_unload modversions 586 
hedy@hedy-laptop:~$ dmesg | grep -i rt3
hedy@hedy-laptop:~$ 

I was online via eth0 with the ASUS dongle inserted and LED on steady when I ran these commands.  (What are the emoticons in the text all about?)

As for compiling, etc: Using the file 2009_1110_RT2030_Linux_STA_v2.1.2.0 which was included in the archived file on the ASUS CD, I ran the commands sudo make -> make install and then created the network_drivers. rules file and network_drivers.conf.

Other than the fact that I did the whole business again at a later time because for some reason it looked to me like things hadn't installed properly, I can't recall fiddling with anything else.

Pity about the 15 hours time difference between where you are and where I am.  It makes continuity a bit difficult, eh?

---

### Post by chili555 on 2010-12-06
> ra0 RT2870 Wireless [COLOR="Red"]ESSID:"beerwah"[/COLOR] Nickname:"RT2870STA"
Mode:Managed Frequency=2.462 GHz Access Point: 00:60:64:3F:5BC
[COLOR="Red"]Bit Rate=54 Mb/s[/COLOR]
RTS thrff Fragment thrff
[COLOR="Red"]Link Quality=100/100[/COLOR] Signal level:-35 dBm Noise level:-63 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0This looks suspiciously like you are....*connected!!* Would you please detach the ethernet cable and try Firefox?

You can disable the smileys below when you reply, as I have done.> Pity about the 15 hours time difference between where you are and where I am. Where would that be?

---

### Post by ibates on 2010-12-06
I disconnected the ethernet cable - removed it completely from the machine in fact.  Wicd scanned for a connection and found the router and network (as it has been doing).  Attempting to connect resulted in a lot of "connecting" and finally the message

ERROR  Connection Failed: Bad password

And this has been the problem all along.  I have entered the WEP hex Key in Wicd and also the RT2870STA.dat, but still no joy.

As I mentioned earlier, the USB-N13 flashes away and is probably connected, but for the password (whatever that means).  Wicd certainly recognises the router to which the USB-N13 is trying to connect so that implies that the wireless connection has, as you suggested, succeeded, but not the "login".

Maybe we have just moved out of the Ubuntu arena into the router arena?

(For my location, please check you Yahoo mail.  Please let me know if you haven't received my messages).

---

### Post by ibates on 2010-12-06
Just a bit more info on all of this.

I have just shut down the laptop, and started it up again with the ASUS USB-N13 plugged in.

At first wicd found the "beerwah" network and attempted to connect.  The usual failure occurred.

Now, when I again attempt to connect, the "beerwah" option is greyed out, and I can do nothing.  But wicd is attempting to connect every minute or so.

(I am using another machine to communicate at present).

Interestingly, when I double click on the wicd icon, I am presented with the Wicd Network Manager screen which gives me the option of either of the two wireless networks I currently run.  The second network is the one I am using for this machine.  It has a different network name.

Because I have "Automatically connect to this network" ticked for "beerwah", wicd attempted to connect, again.  No go.  The same error message.

---

### Post by ibates on 2010-12-06
One more piece of information which tends to bring the whole business back into the Ubuntu arena.

I have just attempted to log on to the other wireless network, and I get exactly the same error message.

Two entirely independent WLANs in two different locations, and the same error message.

What can this mean ????

---

### Post by chili555 on 2010-12-06
> For my location, please check you Yahoo mail. Please let me know if you haven't received my messagesI have not.

Is the behavior the same with the password blank in RT2870STA.dat? You will probably have to rmmod and modprobe rt3070sta.

---

### Post by ibates on 2010-12-06
I have removed the password from the .dat files, rebooted the machine, but no change.

For what it is worth, each wireless network has a different SSID.  But despite changing the SSID in the .dat file, there is no apparent change to what is presented in the wicd menu.

Selecting Properties->information from the Wicd Network Manager shows all the correct information for the AP/Router being accessed.  Which confirms that the wireless device is actually communicating with the relevant AP/Router.

But still the "bad password" error message.

I am not aware of any other password.  The Encryption Key has been removed from the .dat file and has been correctly entered into the Properties page of the WICD Network Manager.

I am simply unaware of any other authentication required.

(There certainly is none entered in the wireless setup for another computer used on these AP/Routers.  There is also a MacBook Pro accessing one of the routers with no hassles and no "bad passwords".  So it is unlikely that it is a router requesting some kind of a password.

I do not understand "rmmod and modprobe rt3070sta".  Perhaps you could straighten me out on that.

---

### Post by chili555 on 2010-12-06
> I do not understand "rmmod and modprobe rt3070sta". Perhaps you could straighten me out on that.In order to get the driver to reload and re-read the .dat file, you probably need to do:```
sudo rmmod -f rt3070sta 
sudo modprobe rt3070sta
```

---

### Post by ibates on 2010-12-06
I ran both those commands.  I then rebooted the machine.

No change. Same error message.

---

### Post by ibates on 2010-12-06
Could it possibly be that we are barking up completely the wrong tree?  Could it be that the "password" or failure to "validate authentication" is something completely separate from the wirelesss connection?

Is it possible that somewhere, in the setting up of Ubuntu in the first place, a "general" requirement for authentication has been setup, but for which there is no option when attempting to connect the Wireless dongle?

This is really clutching at straws, but I am totally confused at why the dongle recognises the AP/Routers, but that, despite that recognition, cannot actually connect because it is unable to validate authentication?

Could it be that some part of the software for the dongle might have been set up using root and that is locking the thing out at normal user level.  I can't imagine how that could be, but with my limited knowledge of what I am doing, I must consider that anything is possible.

Mysteriouser and mysteriouser!

---

### Post by ibates on 2010-12-07
One last bit for today.

I have removed the SSID, set the AuthMode=OPEN, EncrypType=wep, kEYXsTR= , and nothing seems to change, including the usual Error messgae about Bad Password.

I will be back on the air again at 201012072200 UTC (1700 SC time).  More then.

---

### Post by chili555 on 2010-12-07
> (1700 SC time). More then.I'll see you then.

I wonder if the problem is here, in the README:> 3> In os/linux/config.mk 
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
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -dDid you make the changes to allow Network Manager to control the interface? Well, you aren't using it; you are using Wicd. Did you make the change to recognize wpa_supplicant? Well, you aren't using it, you are using WEP. I wonder if there might be a difference if you recompiled *without* those changes. If you do so, your carefully written RT2870STA.dat file will be overwritten. Move yours to a backup location for now.```
sudo cp /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat.bak
```Now make the changes to change the switches from HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y to =n and HAS_WPA_SUPPLICANT=y to =n. Next, recompile:```
cd download/directory/2010_whatever
sudo su
make clean
make
make install
rmmod -f rt3070sta
modprobe rt3070sta
iwconfig
```Do you have an interface? Can Wicd connect?

I wouldn't replace the .dat file just yet, see what Wicd says and note any errors. You can always copy the backup back to active at any time:```
sudo cp /etc/Wireless/RT2870STA/RT2870STA.dat.bak /etc/Wireless/RT2870STA/RT2870STA.dat
```

---

### Post by ibates on 2010-12-08
Before I do any of the above commands, I have just a few minutes ago received an email from ASUSTek Support advising that anew driver is available.  They seem to know about these problems and have updated the drivers.

The link is:

[http://support.asus.com/download/download.aspx?model=USB-N13&f_name=Linux_2302.zip&f_type=19&os=5](http://support.asus.com/download/download.aspx?model=USB-N13&f_name=Linux_2302.zip&f_type=19&os=5)

The attached comments are interesting.  I will leave it to you to translate:

[I]Then please short the distance and connect to your wireless network again for a try.  Please make sure the passwork is right and other wireless clients can connect your wireless network
[/I]
I have downloaded the file but am reluctant to do anything with it until I know a bit more of what I am doing.

Should I remove/purge the previous driver?

If so, please let me have the codes for the various steps as I am now well out of my depth.

If not, should I just install the new driver over the top of the old?

Being a .tar.gz file, what is the code for installing the driver?

---

### Post by ibates on 2010-12-08
There is perhaps another little point which I note you mention.

*Did you make the changes to allow Network Manager to control the interface? Well, you aren't using it; you are using Wicd.*

That may not actually be the case.  As I recall, when I first installed this driver, I think I was using NetworkManager.  Subsequently uninstalled it in favour of the more informative Wicd.

Bit by bit it comes out - like pulling teeth, eh?

---

### Post by chili555 on 2010-12-08
I am very glad there is a newer rt3070sta driver. This will help the searchers, too. Searchers should read my note at the end of this post before proceeding.

This will over-write the previous driver automagically if the Makefile is properly written; they usually are. You can check the version you have installed now with:```
modinfo rt3070sta | grep -i version
```When we are all done, the version should escalate to 2.3.02. 

Download the file, if you haven't already. Based on your version of Ubuntu, I'm assuming it was downloaded to your desktop. Substitute Downloads or whatever other location you downloaded the file to as we go along. Right-click the file and select 'Extract Here.' A folder will be created named Linux. Open it and see the .tgz file within. Right-click the file and select 'Extract Here.' A folder will be created named DPO_RT3070_LinuxSTA_V2.3.0.2_20100422. 

Open it and navigate to the folder os/linux and find the file config.mk. For now, I suggest that we *do* make the changes mentioned in the README; we can undo them and re-make the driver later if needed. Open config.mk with the text editor and change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread, save and close the text editor.

For now, we will make no changes to RT2870STA.dat. After the driver builds, we will decide if we need to copy over the backup you are holding.

Open a terminal and do:```
cd Desktop/Linux/DPO
```Press 'Tab' and the rest will fill in.```
make
sudo make install
```In order to get the newer version to load, remove the device and do:```
sudo rmmod -f rt3070sta
```Plug the device back in and give me your report.

*******************************************************************
NOTE TO SEARCHERS

ibates kernel version is older. If you are running a newer 2.6.35  kernel version:```
uname -r
```You may have an error:> error: implicit declaration of function ‘usb_buffer_alloc’If so, please make the change here:> Edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. DO NOT replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.Then run:```
make clean
make
sudo make install
```If you experience more errors, not warnings, stop and post a thread.
********************************************************************

---

### Post by ibates on 2010-12-08
I have followed the instruction exactly, down to and including sudo make install.

The following errors have been reported.  I have gone no further.

This was done with the device NOT inserted, and the ethernet connection offline.

hedy@hedy-laptop:~$ cd /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
hedy@hedy-laptop:~/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ make
make -C tools
make[1]: Entering directory `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h
cp -f os/linux/Makefile.6 /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile
make -C /lib/modules/2.6.32-26-generic/build SUBDIRS=/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-26-generic'
  CC [M]  /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt3070sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt3070sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-26-generic'
cp -f /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt3070sta.ko /tftpboot
cp: cannot remove `/tftpboot': Permission denied
make: *** [LINUX] Error 1
hedy@hedy-laptop:~/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ sudo make install
make -C /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: cannot stat `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
make: *** [install] Error 2
hedy@hedy-laptop:~/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ cd /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
hedy@hedy-laptop:~/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ 

I will await your advice before continuing.

(This is the read out from the second attempt at "make" and "sudo make install".  There were a lot of files created on the first attempt which do not appear in this attempt.  But there were no errors reported with any of them.

Sorry about the long directory path.  It's the only way I can find things.

---

### Post by chili555 on 2010-12-08
Please amend your commands to:```
sudo su
make clean
make
make install
exit
```Post back; I'm hoping we will crack the nut before supper.

---

### Post by ibates on 2010-12-09
Dinner may have to wait !!!!  This is getting to be a tough nut to crack.

No errors for the "clean" or "make" commands.  Here is the result from the "make install"

root@hedy-laptop:/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422# make install
make -C /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: cannot stat `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
make: *** [install] Error 2
root@hedy-laptop:/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422# 

And the error message is quite correct.  There is no RT3070sta.dat in the directory "/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/".  Or in the directory "/etc/Wireless/RT3070STA"

I'll await further.

Thanks for your extreme patience and persistence.

---

### Post by chili555 on 2010-12-09
> cp: cannot stat `/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat': No such file or directoryWithout seeing the Makefile, I can't be certain, but I believe it wants to move RT3070STA.dat to the appropriate directory. However, what you have in the folder next to the Makefile is probably RT*2870*STA.dat. A slight but easily fixable error on the part of the developer. In the same directory as the Makefile, do:```
cp RT2870STA.dat RT3070STA.dat
sudo make install
```Post back any errors or problems.

---

### Post by ibates on 2010-12-09
Great stuff - why didn't I think of that ???.  

Done.  No errors.

I assume I now continue where I left off above which is

sudo rmmod -f rt3070sta

Over ....

---

### Post by chili555 on 2010-12-09
> I assume I now continue where I left off above which is

sudo rmmod -f rt3070sta
Correct. Your humble servant anxiously awaits...

---

### Post by ibates on 2010-12-09
From which directory should I run that command.

I tried from the directory it was in

/home/hedy/Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/

but get the dreaded

ERROR: Removing 'rt3070sta': No such file or directory

Should I be doing this in the /etc/Wireless directory?

---

### Post by chili555 on 2010-12-09
From any directory. The command *rmmod* figures that all out for you. That was a precautionary command to unload the old module and reload the shiny newly compiled one. The response merely means that no such module was loaded. Please proceed.

---

### Post by ibates on 2010-12-09
What can I say?  Pure genius!

Yes; the thing is finally taking to the router.

But I now think I must do a bit of work on the 
/etc/sysconfig/network-scripts/ifcfg-ra0 file.

The error message I received from Wicd was that the device failed to obtain an IP address.  I believe I should add the line

BOOTPROTO='dhcp'

to that file.

No other modification has been made to the new .dat file but it seems unnecessary as apart from obtaining that IP address, everything appeared to be doing what it should.

I think most, if not all, of the configuration can be done from the Wicd menus.

What do you think?

---

### Post by chili555 on 2010-12-09
> But I now think I must do a bit of work on the
/etc/sysconfig/network-scripts/ifcfg-ra0 file.That's a Fedora file. It's nearest equivalent in Ubuntu is /etc/network/interfaces, which is the manual way to do things. Wicd and Network manager are the automatic way. One should use one or the other; not both.

First, I'd look at the various settings in Wicd and be sure evrything is as it should be. Then after trying and failing to get an IP address, I'd look in:```
sudo less /var/log/wicd/wicd.log
```Use the arrow keys to scroll up and down till you see the relevant entries. See if you can see where and why it fails to lift off. I'll be glad to help if you can post the suspicious lines.

---

### Post by ibates on 2010-12-09
OK.  I will do that.

I got the idea for this from page 8 of the "README_STA_usb" file.

All of the files and additions listed in that files have been saved from previous attempts and are probably still influencing the system - I think.

But I will do the log print out and see what come of it.

---

### Post by chili555 on 2010-12-09
Tell me a bit more; the wireless device sees the router and tries to connect but doesn't get an IP address? I assume there is no complaint about a bad password.

---

### Post by ibates on 2010-12-09
Wigh the device unplugged, and the ethernet connection also diabled, the following results from sudo less /var/log/wicd/wicd.log

2010/12/10 09:03:04 :: 
2010/12/10 09:03:04 :: using dhcpcd or another supported client may work better
There is already a pid file /var/run/dhclient.pid with pid 3881
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:c0:9f:1b:dc:99
Sending on   LPF/eth0/00:c0:9f:1b:dc:99
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
2010/12/10 09:03:07 :: Connecting to wireless network beerwah
2010/12/10 09:03:07 :: attempting to set hostname with dhclient
2010/12/10 09:03:07 :: using dhcpcd or another supported client may work better
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/ra0/e0:cb:4e:bd:bf:6d
Sending on   LPF/ra0/e0:cb:4e:bd:bf:6d
/var/log/wicd/wicd.log 

and the log sits blinking waiting for something else to happen.

The only error message is that it fails to obtain an IP address.

If I select "dhcp host name" in Wicd, then I get a Bad Password error message.  But deselecting it, reverts to the IP address error.

And for what it is worth, adding that line to the "sysconfig" file and rebooting has no effect one way or another as you predicted.

---

### Post by chili555 on 2010-12-09
> And for what it is worth, adding that line to the "sysconfig" file and rebooting has no effect one way or another as you predicted. It's not a recognized file in Ubuntu. It is not sought or used in any way.

I suggest you look at:```
dmesg | grep -i rt3
```Is there any issue with the driver or with RT3070STA.dat? I'd also look at:```
sudo cat /var/log/syslog | grep -i wicd
```So far, we haven't seen any issues that prevent an IP address; however, there obviously is one.

---

### Post by ibates on 2010-12-09
Here is the output.  It doesn't mean a lot to me, but there could be something there.

hedy@hedy-laptop:~$ dmesg | grep -i rt3
hedy@hedy-laptop:~$ sudo cat /var/log/syslog |grep -i wicd
[sudo] password for hedy: 
Dec 10 08:34:16 hedy-laptop kernel: [ 3225.823109] type=1503 audit(1291934056.613:16):  operation="open" pid=3728 parent=3702 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 10 08:35:42 hedy-laptop kernel: [ 3311.879441] type=1503 audit(1291934142.669:17):  operation="open" pid=3860 parent=3842 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 10 09:13:06 hedy-laptop kernel: [  447.789676] type=1503 audit(1291936386.598:16):  operation="open" pid=1555 parent=1525 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 10 09:17:26 hedy-laptop kernel: [  707.720362] type=1503 audit(1291936646.530:17):  operation="open" pid=1878 parent=1863 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 10 09:40:21 hedy-laptop kernel: [ 2082.763832] type=1503 audit(1291938021.570:18):  operation="open" pid=2772 parent=2743 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 10 09:55:23 hedy-laptop kernel: [  135.748988] type=1503 audit(1291938923.852:16):  operation="open" pid=1588 parent=1560 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 10 10:09:09 hedy-laptop kernel: [  259.894216] type=1503 audit(1291939749.674:16):  operation="open" pid=1618 parent=1588 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 10 11:30:41 hedy-laptop kernel: [ 5151.391740] type=1503 audit(1291944641.170:17):  operation="open" pid=5995 parent=5979 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
hedy@hedy-laptop:~$

---

### Post by chili555 on 2010-12-09
> 2010/12/10 09:03:07 :: Connecting to wireless network beerwah
2010/12/10 09:03:07 :: attempting to set hostname with dhclient
2010/12/10 09:03:07 :: using dhcpcd or another supported client may work betterI am still struggling a bit to find anything apparent to fix!

Is your Wicd preference set to dhclient or automatic? See attached. Is the behavior improved if you set it to automagic?

---

### Post by ibates on 2010-12-10
Wicd is set to automatic.

For some reason, I am now getting the "Bad Password" error message again.

I had a look at the so-called "new" README_STA_usb file.  Unlike the 2.1.1.0 version which refers to "Model name:  RT3070 Wireless Lan Linux Driver", the new 2.3.2.0 version refers to "Model name:  RT2870 Wireless Lan Linux Driver".

I simply do not understand what is going on.  And I am having my doubts about ASUSTek also.

Any suggestions as to where we should go now?  Clean the whole box and dice off and start again from scratch.

And what are your thoughts on the /etc/udev/rules.d/network_drivers.rules and /etc/modprobe.d/network_drivers.config files?

Are they necessary with this procedure?

---

### Post by ibates on 2010-12-10
OK.  There seems to be something fundamentally incorrect with the ASUSTek drivers.  The failures are no longer logical.

As a result of this thought, I went to the Ralink web site.  They are the mnanufacturers of the USB wireless dongle marketed by ASUS.

[http://www.ralinktech.com](http://www.ralinktech.com)

I note that the Ralink Support site shows the latest software (v2.4.0.1) for this device at

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Although there are two software suites, the most likely updated drivers is for RT2870.

[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D)

Interestingly, the release notes for this version place emphasis on the inability to log on to a router under certain password/security circumstances.

I will attempt to clean and reinstall this latest version and post the results on this site.

---

### Post by ibates on 2010-12-10
Of course, what I failed to mention in the last post is that I need assistance in how to actually install this new driver software on account of the downloaded file not having quite the same structure as the previous version 2.3.0.1.

Chili555 - Want to have a go?

---

### Post by chili555 on 2010-12-10
> **ibates said:**
> Of course, what I failed to mention in the last post is that I need assistance in how to actually install this new driver software on account of the downloaded file not having quite the same structure as the previous version 2.3.0.1.

Chili555 - Want to have a go?I'm in! There are devices that advertise themselves as RT2870 devices but really work with the RT3070 driver. The latest in-kernel driver rt2870sta is an attempt to merge them:> $ modinfo /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
[COLOR="Red"]description:    RT2870/RT3070 Wireless Lan Linux Driver[/COLOR]
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
Which version is actually correct depends on the usb.id. I'm embarrassed that I've never asked for it so we can try to determine the correct driver. Please post:```
lsusb
```> And what are your thoughts on the /etc/udev/rules.d/network_drivers.rules and /etc/modprobe.d/network_drivers.config files?That is used to force the in-kernel driver to recognize a usb.id and therefor get the in-kernel driver to drive the device. It is useful when a new device is introduced that is, under the skin, actually the same as a previous device, but has a different identifier because an OEM chipset is being packaged by a different manufacturer.

In contrast, the way to force a compiled tar.gz driver to recognize a usb.id is to amend a .c file in the package before you make and make install. Here is an example. The D-link 125 line was added after the fact by me. The two procedures are for different purposes and, as far as I know, should not be mixed.

You know your usb.id is recognized, the driver grabs the card and sees networks and will connect, at least to unencrypted networks.

Of course, at the end of the day, the correct driver is the one that works. 

Let's look at your usb.id before we decide how to proceed.

---

### Post by ibates on 2010-12-10
OK; here is the lsusb result:

hedy@hedy-laptop:~$ lsusb
Bus 004 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
hedy@hedy-laptop:~$

---

### Post by chili555 on 2010-12-10
RT3070STA is correct for your device, as per the rtusb_dev.id.c file. So, are you ready to download the later driver and proceed as outlined in post #25? If you get an error, post it here; I'm waiting.

---

### Post by ibates on 2010-12-10
Ah ....  That's the one I currently have installed.

hedy@hedy-laptop:~$ modinfo rt3070sta | grep -i version
version:        2.3.0.2
srcversion:     27760B9B04537BF01DDF9E0
vermagic:       2.6.32-26-generic SMP mod_unload modversions 586 
hedy@hedy-laptop:~$

---

### Post by chili555 on 2010-12-10
I believe 2.**4**.0.1 is the latest available at Ralink.> Ah .... That's the one I currently have installed.

hedy@hedy-laptop:~$ modinfo rt3070sta | grep -i version
version: 2.**3**.0.2
srcversion: 27760B9B04537BF01DDF9E0
vermagic: 2.6.32-26-generic SMP mod_unload modversions 586 

---

### Post by chili555 on 2010-12-10
I notice the module it builds is called rt3370sta.

---

### Post by ibates on 2010-12-10
All installed as per amended procedure in post #25.

But here is an interesting thing, done after the install:

hedy@hedy-laptop:~$ sudo rmmod -f rt3070sta
hedy@hedy-laptop:~$ modinfo rt3070sta | grep -i version
version:        2.3.0.2
srcversion:     27760B9B04537BF01DDF9E0
vermagic:       2.6.32-26-generic SMP mod_unload modversions 586 
hedy@hedy-laptop:~$ 

What do you make of that.  Whatever happened to the ver 2.4.0.1?

---

### Post by ibates on 2010-12-10
And that was definitely after using the downloaded v 2.4.0.1 package from Ralinktech.com

I have just checked what I did, and that is confirmed.

---

### Post by chili555 on 2010-12-10
> What do you make of that. Whatever happened to the ver 2.4.0.1?Please see post #50. It is called rt3370sta. I hope they don't both load! We can fix that with a blacklist.

Please remove and insert the device. Run:```
lsmod | grep rt3
```Did they both load or just rt3370sta? If both, do:```
sudo rmmod -f rt3070sta
```Now, how is the wireless? We can take steps to permanently remove rt3070sta, if it is loading.

---

### Post by ibates on 2010-12-10
No; just one shows:

$ lsmod | gre[ rt3
rt3070sta          573063   1
$

I had previously run sudo rmmod -f rt3070sta before my last post.

In the meantime, I have rebooted, unplugged the Ethernet cable, and attempted to connect with the USB dongle.

This is the first time I have seen lights flashing on both the dongle and the router while the thing was attempting to validate authentication.

But it did no real good.  We are back at the "Bad Password" error message.

---

### Post by ibates on 2010-12-10
Just a bit more info.  Going to /etc/Wireless/RT3070STA/RT3070STA.dat
reveals that that file is the old, unchanged, .dat file.

But going to /etc/Wireless/RT2870STA/RT2870STA.dat, the .dat file is apparently new.  There is no data in it that I had previously inserted.

---

### Post by chili555 on 2010-12-10
> But it did no real good. We are back at the "Bad Password" error message.After the reboot, is rt3070sta loaded?```
lsmod | grep rt3
```If so, remove it:```
sudo rmmod -f rt3070sta
```And load the new module:```
sudo modprobe rt3370sta
```How is it operating now?

We will still have some work to do to get it to work permanently.

---

### Post by ibates on 2010-12-10
It must be very frustrating doing this remotely.  It is a shame you can't just peek into what is going on and do it your way directly.

I am currently posting via a different computer so that there is nothing which could interfere with what is going on on the Laptop.

After the reboot, with the dongle removed, it indicates that rt3070sta is not loading

With the dongle inserted, it shows that it is loading.  (see post above.  It is the exact same response).

Attempting the sudo rmmod -f rt3070sta with the dongle inserted, says ERROR; and then something about it can't do it because the resource is temporarily unavailable.

I have not run this command with the dongle removed.  Should I?  Reboot first?

---

### Post by chili555 on 2010-12-10
Let's do it the right way. Remove the device and do:```
cd Downloads/ComputerRelated/ASUS/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
sudo su
make uninstall
echo "blacklist rt3070sta" >> /etc/modprobe.d/blacklist.conf
echo rt3370sta >> /etc/modules
exit
```Reinsert the device and do:```
sudo modprobe rt3370sta
iwconfig
```Any activity from Wicd?

---

### Post by ibates on 2010-12-10
Ok; now let me just confirm.  You want me to remove the earlier installation altogether.  That is the v 2.3.0.1 which came from the ASUSTek site?  Not the version 2.4.0.1 which came from the Ralink site?

I am sure that is what you really want me to do by virtue of the complete directory you have printed.

I will await you reply before continuing.

---

### Post by chili555 on 2010-12-10
> Ok; now let me just confirm. You want me to remove the earlier installation altogether. That is the v 2.3.0.1 which came from the ASUSTek site? Not the version 2.4.0.1 which came from the Ralink site?Yes, sir. Please proceed.

---

### Post by ibates on 2010-12-10
No errors from the "make uninstall"

Both "echo" commands were accepted.

"sudo modprobe rt3070sta" reveals:

FATAL: Module rt3070sta not found

"iwconfig" reveals:

lo       no wireless extensions

etho     no wireless extensions

There is nothing from Wicd.  Blank.

---

### Post by chili555 on 2010-12-10
> Reinsert the device and do:
Code:

sudo modprobe rt***3370***sta
iwconfig

Please try again.

---

### Post by ibates on 2010-12-10
FATAL: Module rt3370sta not found

---

### Post by ibates on 2010-12-10
And for what it is worth, when the same command is run for rt2870sta, there is no message.  It just goes to the next cmd prompt.

---

### Post by chili555 on 2010-12-10
> **ibates said:**
> FATAL: Module rt3370sta not foundPlease go back to the file you downloaded and try again:```
cd wherever/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO
sudo su
make clean
make
make install
modprobe rt3370sta
exit
```At the end of the 'make install' step, you ought to see something like:> # make install
make -C /home/chili/ibates/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/chili/ibates/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/chili/ibates/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-23-generic/kernel/drivers/net/wireless/
[COLOR="Red"]install -m 644 -c rt3370sta.ko /lib/modules/2.6.35-23-generic/kernel/drivers/net/wireless/[/COLOR]
/sbin/depmod -a 2.6.35-23-generic
make[1]: Leaving directory `/home/chili/ibates/2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO/os/linux'


---

### Post by ibates on 2010-12-10
Sorry for the delay; the same output from iwconfig also.

No wireless extensions.

---

### Post by chili555 on 2010-12-10
No errors in the compile process? Warnings are OK, not errors.

---

### Post by ibates on 2010-12-10
OK; down to the end of the "make install" procedure, no errors, a few warnings, and some funny comments, but no errors.

The line you were asking about reads

"install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-26-generic/kernel/drivers/net/wireless"

"Modeprobe rt3370rta" FATAL: Module rt3370sta not found.

---

### Post by chili555 on 2010-12-10
> "install -m 644 -c [COLOR="Red"]rt2870sta.ko[/COLOR] /lib/modules/2.6.32-26-generic/kernel/drivers/net/wireless"
What the heck?? I thought we said that RT3070STA was correct for your device. What did you download and compile? 2010_0831_RT[COLOR="Red"]3070[/COLOR]_Linux_STA_v2.4.0.1_DPO? Yes? Hopefully? Maybe?

Time for me to put it in the hangar. I'll be back later.

---

### Post by ibates on 2010-12-10
Go to

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

The package I downloaded was the eight down from the top.  And yes; it is for an RT2870.

Now I am embarrassed.  Which one should I have downloaded?

---

### Post by chili555 on 2010-12-11
> Which one should I have downloaded?2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO; it's the third one down called RT8070/RT3070/RT3370 USB.

It is tricky to open. In a terminal, please do:```
cd Downloads/wherever
tar jxvf 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO.bz2
cd 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO
```Now is the time to make the changes in config.mk as discussed previously. For now, I'd leave the RT2870STA.dat file alone; we can copy over your fine-tuned version by command line later if Wicd doesn't do the heavy lifting for us. Then proceed in the usual way:```
sudo su
make
make install
modprobe rt3370sta
iwconfig
exit
```See you at 1700.

---

### Post by ibates on 2010-12-11
OK;  all done.

hedy@hedy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"beerwah"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:60:64:3F:5B:DC   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-31 dBm  Noise level:-31 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

hedy@hedy-laptop:~$

Everything installed OK.  I did not change the HAS_WPA_SUPPLICANT='n' or HAS_NATIVE_SUPPLICANT='n' parameters at build as that is what they were and the README file indicates that it is only for "Build being controlled by NetworkManager" which it is not.

I note that the only .dat file created is RT2870STA.dat, not RT3070STA.dat as I had expected.

The files described under B), and C), on page 8 of README file have been created, included the step described in "NOTE:"

In /etc/Wireless/RT2870STA.dat the following changes have been made:

CountryRegion=0
CountryCode=AU
SSID=xxxxxxx
WirelessMode=9
AuthMode=OPEN
EncrypType=WEP
Key1Str=xxxxxxxxxx

Wicd configured correctly.

As can be seen from the iwconfig readout above, it would appear that the wireless device is connected.

Result after reboot with dongle inserted and correctly operating router:

ERROR: Connection Failed: Bad Password

I simply do not understand what authentication it is looking for.

---

### Post by chili555 on 2010-12-11
As before, I'd look at:```
dmesg | grep -i rt2
sudo cat /var/log/wicd/wicd.log
```See if there are any clues as to why it doesn't connect.

I'd also look at:> Key1Type=0Is that what you have in the .dat file? If not, remove the device, amend the .dat and do:```
sudo rmmod -f rt3370sta
```Reinsert the device and see if things improve.

Does it scan?```
sudo iwlist ra0 scan
```Please obscure any personally identifiable data.

---

### Post by chili555 on 2010-12-11
When I read this:> > [COLOR="Red"]Key1=value[/COLOR]
    Key2=value
    Key3=value
    Key4=value
	value
		10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
		0   hexadecimal type
		1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
		10 or 26 characters (key type=0)
		5 or 13 characters  (key type=1)
    (usage : reading profile only)	

@> WPAPSK=value              	
	value
		8~63 ASCII  		or 
		64 HEX charactersIt appears to me that perhaps the values in Key1=<your_WEP_key> might have to be filled in, also.

---

### Post by ibates on 2010-12-12
"dmesg | grep -i rt2"


hedy@hedy-laptop:~$ dmesg | grep -i rt2
[   26.581674] usbcore: registered new interface driver rt2870
[   29.330592] ===>rt2870_probe()!
[   29.376891] <===rt2870_probe()!
[   33.148075] <==== rt28xx_init, Status=0
[   39.356845] rt28xx_get_wireless_stats --->
[   39.356851] <--- rt28xx_get_wireless_stats
[   39.643275] ===> rt28xx_close
[   39.643281] RT28xxUsbMlmeRadioOFF()
[   40.080512] <=== rt28xx_close
[   40.928157] <==== rt28xx_init, Status=0
hedy@hedy-laptop:~$ 

"sudo cat /var/log/wicd/wicd.log"  Last attempt at connection.

2010/12/12 17:33:41 :: attempting to set hostname with dhclient
2010/12/12 17:33:41 :: using dhcpcd or another supported client may work better
2010/12/12 17:33:44 :: Connecting to wireless network <my network name>
2010/12/12 17:33:44 :: attempting to set hostname with dhclient
2010/12/12 17:33:44 :: using dhcpcd or another supported client may work better
2010/12/12 17:33:45 :: attempting to set hostname with dhclient
2010/12/12 17:33:45 :: using dhcpcd or another supported client may work better
2010/12/12 17:33:45 :: Putting interface down
2010/12/12 17:33:45 :: Sending connection attempt result Failed
2010/12/12 17:33:46 :: Releasing DHCP leases...
2010/12/12 17:33:46 :: attempting to set hostname with dhclient
2010/12/12 17:33:46 :: using dhcpcd or another supported client may work better
2010/12/12 17:33:46 :: Setting false IP...
2010/12/12 17:33:47 :: Stopping wpa_supplicant
2010/12/12 17:33:47 :: Flushing the routing table...
2010/12/12 17:33:47 :: Putting interface up...
2010/12/12 17:33:49 :: Attempting to authenticate...
2010/12/12 17:34:25 :: wpa_supplicant authentication may have failed.
2010/12/12 17:34:25 :: connect result is 
2010/12/12 17:34:25 :: exiting connection thread
2010/12/12 17:34:25 :: Sending connection attempt result bad_pass
2010/12/12 17:34:25 :: attempting to set hostname with dhclient
2010/12/12 17:34:25 :: using dhcpcd or another supported client may work better
2010/12/12 17:34:26 :: attempting to set hostname with dhclient
2010/12/12 17:34:26 :: using dhcpcd or another supported client may work better
2010/12/12 17:34:35 :: Autoconnecting...
2010/12/12 17:34:35 :: attempting to set hostname with dhclient
2010/12/12 17:34:35 :: using dhcpcd or another supported client may work better
2010/12/12 17:34:37 :: attempting to set hostname with dhclient
2010/12/12 17:34:37 :: using dhcpcd or another supported client may work better
2010/12/12 17:34:37 :: Attempting to autoconnect with wired interface...
2010/12/12 17:34:37 :: Putting interface down
2010/12/12 17:34:37 :: Releasing DHCP leases...
2010/12/12 17:34:37 :: attempting to set hostname with dhclient
2010/12/12 17:34:37 :: using dhcpcd or another supported client may work better
2010/12/12 17:34:37 :: Setting false IP...
2010/12/12 17:34:37 :: Flushing the routing table...
2010/12/12 17:34:37 :: Putting interface up...
2010/12/12 17:34:39 :: Running DHCP with hostname hedy-laptop
2010/12/12 17:34:39 :: attempting to set hostname with dhclient
2010/12/12 17:34:39 :: using dhcpcd or another supported client may work better
2010/12/12 17:34:39 :: Internet Systems Consortium DHCP Client V3.1.3
2010/12/12 17:34:39 :: Copyright 2004-2009 Internet Systems Consortium.
2010/12/12 17:34:39 :: All rights reserved.
2010/12/12 17:34:39 :: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
2010/12/12 17:34:39 :: 
2010/12/12 17:34:39 :: Listening on LPF/eth0/00:c0:9f:1b:dc:99
2010/12/12 17:34:39 :: Sending on   LPF/eth0/00:c0:9f:1b:dc:99
2010/12/12 17:34:39 :: Sending on   Socket/fallback
2010/12/12 17:34:41 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
2010/12/12 17:34:41 :: DHCPOFFER of 118.208.27.170 from 192.168.0.1
2010/12/12 17:34:41 :: DHCPREQUEST of 118.208.27.170 on eth0 to 255.255.255.255 port 67
2010/12/12 17:34:41 :: DHCPACK of 118.208.27.170 from 192.168.0.1
2010/12/12 17:34:41 :: bound to 118.208.27.170 -- renewal in 120 seconds.
2010/12/12 17:34:41 :: DHCP connection successful
2010/12/12 17:34:41 :: Connecting thread exiting.
2010/12/12 17:34:41 :: Sending connection attempt result Success
hedy@hedy-laptop:~$ 

I have "Key1Type=0" alreqdy in the .dat file.  My WEP key, which I have double checked as correct.

The only .dat file I can find is the one in /etc/Wireless which I believe to be the only applicable .dat file.  Is this correct?

In case it is likely to be relevant, and I can't see why it would be, I have also setup the router with restricted MAC access.  (WEP by itself is probably not as secure as it should be).  Do you think it would be worth while disabling that restriction to see what happens?  I have of course entered the MAC address of the dongle into the router "allowed" list.  But I cannot see where the MAC address is actually passed to the router.

But in any case, I have removed the dongle, run "sudo rmmod -f rt3370sta", reinstered the device, and then run "sudo iwlist ra0 scan":

hedy@hedy-laptop:~$ sudo rmmod -f rt3370sta
hedy@hedy-laptop:~$ sudo iwlist ra0 scan
ra0       Interface doesn't support scanning.

hedy@hedy-laptop:~$

Haven't seen that one before.  But whatever it says, Wicd did in fact scan and identified the device correctly, but the same old error.

Perhaps I should disable the restricted MAC list and see what happens.

---

### Post by ibates on 2010-12-12
This README file is associated with the downloaded Ralink drivers:

http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV4THpFeEwyUnZkMjVzYjJGa05UY3dNekE1TXpFd09DNTBlSFE5UFQxU1pXRmtUV1U9Qw%3D%3D

It has some very interesting points in it with respect to sending MAC address to an AP, and authentification in general.

As mentioned in my earlier post, that is one area where I believe it is possible that we may be being locked out of the router.  I cannot see where the MAC address of the device is being sent to the router.

Perhaps this gives some sort of a clue.

What do you think.

---

### Post by chili555 on 2010-12-12
> 2010/12/12 17:34:41 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
2010/12/12 17:34:41 :: DHCPOFFER of 118.208.27.170 from 192.168.0.1
2010/12/12 17:34:41 :: DHCPREQUEST of 118.208.27.170 on [COLOR="Red"]eth0 [/COLOR]to 255.255.255.255 port 67
2010/12/12 17:34:41 :: DHCPACK of 118.208.27.170 from 192.168.0.1
2010/12/12 17:34:41 :: bound to 118.208.27.170 -- renewal in 120 seconds.
2010/12/12 17:34:41 :: DHCP connection successfulWicd did, as it's supposed to do, favor the wired ethernet. Once it had a connection, it proceeded no further. In these tests, please be sure the ethernet is disconnected.> Do you think it would be worth while disabling that restriction to see what happens?Yes, sir. Please do.

---

### Post by ibates on 2010-12-12
I have disconnected the ethernet cable completely and run the tests over.  Essentially the results are identical minus the reference to eth0.  Do you need me to send these rather long logs again?

I have not done anything about disabling the MAC filter on the router, because upon consideration, it is unlikely that that would cause a validation of authentication error.

But I am concerned about the following line in the wicd.log, and have a gut feeling that this may be the root cause of all these problems.

2010/12/13 07:35:35 :: Stopping wpa_supplicant 
2010/12/13 07:35:35 :: Flushing the routing table... 
2010/12/13 07:35:35 :: Putting interface up... 
2010/12/13 07:35:37 :: Attempting to authenticate... 
2010/12/13 07:36:13 :: wpa_supplicant authentication may have failed. 

(You will note that the same lines appear in the earlier log extract also).

In the config.mk file in the "Linux" directory for the installed drivers the following exists, despite my not having attempted to edit that file before or since installation of this latest driver.

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

But in this matter, the "Build Instructions" referred to in the README file states

"**Build for being controlled by NetworkManager or wpa supplicant functions .... "

And neither apply in this situation.  Network Manager does not exist on the machine (well at least it doesn't appear anywhere visible), and in the config.mk file, wpa supplicant is disabled; or so it would appear.  So neither should have any effect on this whole thing - should it?

I have one remaining thought after all of this.  I do not want to have to do it, because of the number of other devices which currently use this network, but it could be worth changing the WEP encryption to WPA encryption to see what happens then. But I do not particularly want to go down that track unless I really have to.

---

### Post by ibates on 2010-12-12
Just to see what would happen, I have re-configured one of my wireless networks to WPAPSK encryption, edited the README file, and configured wicd accordingly.

Result:  "Bad Password" ERROR.

What must be remembered is that at build time, the relevant config.mk file showed "HAS_WPA_SUPPLICANT='n', and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT='n'.  (I don't know why because I did not edit the file prior to "make").

I am now just about out of ideas.

Is there a more Linux-friendly USB wireless device?  This ASUS USB-N13 certainly is NOT!

---

### Post by chili555 on 2010-12-12
> 2010/12/13 07:36:13 :: wpa_supplicant authentication may have failed. I was not aware that wpa_supplicant was called in a WEP network. As I have indicated to you, I learn every day! Let's try to fix the driver. Please remove the device. Make the change you've referred to:> # Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]Then rebuild the driver module:```
cd 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO
sudo su
rmmod rt3070sta
make clean
make
cp /etc/Wireless/RT2870STA/RT2870STA.dat RT2870STA.dat
make install
```Now re-insert the device. Are these messages gone or repeated?

---

### Post by chili555 on 2010-12-12
> edited the README file,I hope you actually edited os/linux/config.mk.

---

### Post by ibates on 2010-12-12
Before I go on.  I have edited the "config.mk" file, and run "susdo su" followed by "rmmod rt3070sta" as you describe, but I get the rather unexpected result of:

ERROR: Module rt3070sta does not exist in /proc/modules

How could that be?

And is there anything I should do about that before continuing?

---

### Post by chili555 on 2010-12-12
[http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)

There are two types of WEP; open and shared key:> In Open System authentication, the WLAN client need not provide its credentials to the Access Point during authentication. Thus, any client, regardless of its WEP keys, can authenticate itself with the Access Point and then attempt to associate.> In Shared Key authentication, the WEP key is used for authentication. A four-way challenge-response handshake is used:Please be certain whether your router is set to Open or Shared. Make sure your RT2870STA.dat file is written correctly. If you change it, unload and reload the module:```
sudo rmmod -f rt3070sta
sudo modprobe rt3070sta
```Then check the logs for encouraging messages.

---

### Post by chili555 on 2010-12-12
> ERROR: Module rt3070sta does not exist in /proc/modules
It just means that when you removed the device, the module rt3070sta unloaded all by itself with no human intervention. It therefor no longer appears in the list of loaded modules.

You should ignore the message and continue.

---

### Post by ibates on 2010-12-12
All instructions from post #80 have been executed.

I have not changed the MAC filters in the Routers.  I have changed both routers to SHARED with WEP encryption.

Guess what?  ERROR; Connection Failed.  Bad Password.

I went to edit the /etc/Wireless/RT2870STA/RT2870STA.dat only to find that, after "make clean", "make", and "Make install" exactly the same .dat file as was there previously was still the one there.  (Does that make sense?)

It appears that nothing changed.

During the "make install" there was a message that it was unable to create the /etc/Wireless directory as it already existed.  Perhaps I should have deleted it completely before starting.

But what; this whole saga has gone on too long now.  You have done your best, and I think you have really covered every possible base.  But we are just not getting anywhere.

I had a read one of my very early posts, and what is happening now is precisely what was happening then.

I am now of the opinion that whatever the reason, this USB device does not work with Ubuntu Linux, at least with my equipment (an HP Laptop).

What I would like to do now is purge the system of everything and anything that would even give a clue that we have been down this road.  Is that possible?

Then I will install the driver which ASUSTek support told me to install, which will then allow me to get heavy with their support people.

Of course, that will probably do no good because they will then say it is the routers I am using.  The router manufacturers technical support people will then tell me, no; it is the drivers that are at fault.

Of course.  There is one remaining unexplored possibility, and that is the the device itself is a lemon!

Do you have any advice on how to purge the system of the existing driver and associated files?

---

### Post by chili555 on 2010-12-13
> I went to edit the /etc/Wireless/RT2870STA/RT2870STA.dat only to find that, after "make clean", "make", and "Make install" exactly the same .dat file as was there previously was still the one there. (Does that make sense?)It makes perfect sense in view of my suggested step:> cp /etc/Wireless/RT2870STA/RT2870STA.dat RT2870STA.datThat was intended to copy your existing, fine-tuned .dat file to the build folder so you didn't have to amend a basically default file once again. When you went to the file and saw that all your settings were present already, I hoped you would think; not, something's amiss here, but, gosh that Chili is clever!> During the "make install" there was a message that it was unable to create the /etc/Wireless directory as it already existed. Perhaps I should have deleted it completely before starting.Nope. That just means we need a dat file in a specific location. Let's create the folder; oops, it already exists; OK, we'll put our dat in the existing folder. In my opinion, it's an example of too much information that essentially worries the less experienced users. It's perfectly harmless.> What I would like to do now is purge the system of everything and anything that would even give a clue that we have been down this road. Is that possible?Certainly. In a terminal, cd to the directories of each of the files you downloaded. Do:```
sudo su
make uninstall
exit
```Then I'd delete the folders, such as 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO as well as the tar.gz files.

Next, look in /etc/modules and remove any rt28xx or rt33xx or similar entries we may have added.

Make sure these files have been deleted: /etc/udev/rules.d/network_drivers.rules and /etc/modprobe.d/network_drivers.conf.

Finally, check /etc/modprobe.d/blacklist.conf and remove any rt28xx or rt33xx or similar entries we may have added.

You are more patient than me; I would have put this device under the back wheel of my old truck long about post #25 or 30.

---

### Post by micako on 2010-12-21
Any one can help me please. I have got this error when trying to install the driver :



cii@cii-pc:~/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ sudo make
make -C tools
make[1]: Entering directory `/home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
/home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h
cp -f os/linux/Makefile.6 /home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile
make -C /lib/modules/2.6.35-23-generic-pae/build SUBDIRS=/home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make[2]: *** No rule to make target `/home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/.c', needed by `/home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/.o'.  Stop.
make[1]: *** [_module_/home/cimi/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make: *** [LINUX] Error 2

thanks

---

### Post by chili555 on 2010-12-21
First of all, I'd suggest the later version, 2.4.0.1 here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)> RT8070/RT3070/RT3370 USBSecond, please start a new thread; this one's a bit cluttered. Did the built-in RT2870sta not work for you? Tell us more. Please send me the link to your thread by private message if I don't catch it right away.

---

