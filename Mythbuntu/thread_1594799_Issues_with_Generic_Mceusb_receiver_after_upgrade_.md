---
title: "Issues with Generic Mceusb receiver after upgrade to 10.10"
date: 2010-10-12
forum: Mythbuntu
---

### Post by Neon Dusk on 2010-10-12
I've upgraded a 10.04 system to 10.10 and seem to have problems with my generic mceusb receiver (the receiver works fine in 10.04)

```

 dmesg | grep lirc
[   17.618734] lirc_dev: IR Remote Control driver registered, major 249
[   17.630203] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0

```

```

 dmesg | grep mceusb
[   17.630203] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   17.630222] mceusb 2-9:1.0: Registered Formosa21 SnowflakeEmulation on usb2:2
[   17.630241] usbcore: registered new interface driver mceusb

```

```

cat /proc/bus/input/devices
...
I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (147a:e017)"
P: Phys=usb-0000:00:04.0-9/input0
S: Sysfs=/devices/virtual/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=100003
B: KEY=fff 0 108fc326 217604100000000 0 118000 418000100001 9e968000000000 10000000

```

The device seems to be recognised and /dev/lirc0 is created but irw does not respond to any buttons
```

cat /etc/lirc/hardware.conf
REMOTE="Windows Media Center Transceivers/Remotes (all)"
TRANSMITTER="None"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

Connecting a genuine Microsoft receiver to the machine using the same config works fine.

Does anyone have any ideas?

---

### Post by My Name on 2010-10-13
I'm having the same problem with a Hauppauge dvb usb stick. I need to use devinput at event4 but i'm getting absolutely no response using irw. just can't work it out...

---

### Post by nocares on 2010-10-15
I'm having the same problem with both Pinnacle and Dell usbmce lirc devices.  Every release of Ubuntu seems to break lirc differently :(

Anyone know if the pvr150 blaster will work with the zilog driver in Maverick?

---

### Post by uniden9 on 2010-10-17
New with Maverick is the lirc kernel module are now merged into the kernel. If you upgraded, then you have the older lirc source modules loaded as well.  With the two modules loaded at the same time, neither work.  I have tried to use the kernel module myself and threw in the white towel.  Ubuntu seems to treat the remote as a keyboard device, and it incomplete.  Most keys work, but are either out of place or incomplete.  Then if you configure inputlirc or just lirc, the remote repeats key press because its receiving them from several sources.
To see the two modules run:
#sudo lsmod |grep mseusb
#sudo lsmod |grep ir
You will see lirc_mseusb and mseusb loaded.  They are trying to accomplish the same thing.

Options.
1. Blacklist/Remove the old lirc dkms built modules and use the kernel built in modules.
   A1. To remove. #sudo apt-get remove lirc-modules-source
   A2. To blacklist.  Edit /etc/modprobe.d/blacklist.conf , create it if it doesn't exist.
       Add> 
       blacklist lirc_mseusb
       to the file and save it.
       Update initrmafs,  #sudo update-initramfs -u -k all
       reboot
   B. Now with just the kernel source modules present. 
      1. Install input-utils package
         #sudo apt-get install input-utils
      2. Find your remote input event# and make note
         #lsinput
      3. Reconfigure lirc.  
         #dpkg-reconfigure lirc 
         On the remote select "Linux input layer (/dev/input/eventX)
         Then select the /dev/input/event that matches your remote.
      4. run irw
         #irw
      5. You should see you remote button press show up, and you are done. 
         Note that the remote has a different lirc profile and remote key names are different, but the kernel source drivers are more universal.
      
2. Blacklist the kernel source drivers and use the old dkms built drivers.
   -Well you already have lirc-sources-modules install and probably had this working on 10.04 or older version of ubuntu.
   A. Edit /etc/modprobe.d/blacklist.conf , create it if it doesn't exist.
      Add> 
      blacklist mceusb
      line to the file and save it.
   B. Update initrmafs,  #sudo update-initramfs -u -k all
   C. reboot
   D. Reconfigure lirc if its not already working.
      #sudo dpkg-reconfigure lirc
      On the Remote, Select "Windows Media Center Transceiver/Remote (All)
   E. Thats it. 
   This is the method I chose after wrestling with button repeats on option 1.  I use XBMC and could not figure out how to disable Ubuntu treating the remote as a keyboard device.
   
Also for others having issues with lirc and Maverick but using a different remote than the microsoft media center type, something similar approach will more than likely be needed as well.

---

### Post by nocares on 2010-10-17
Thanks Uniden9 - option 2 worked like a charm for me

---

### Post by Neon Dusk on 2010-10-17
@uniden9

I didn't have the old lirc modules installed but I installed lirc-sources-modules and followed your instructions to use the old modules. 

Everything seems to work now, thanks.

---

### Post by Kheops_74 on 2010-10-18
I have a PVR150 and i'm sure i have the same kind of problem as you. lirc didn't work since the update to 10.10. I was using the lirc_zilog module. Is anybody knows what i must do to make lirc_zilog work again.

Thanks

---

### Post by Kheops_74 on 2010-10-21
Ok i solve my problem ([http://ubuntuforums.org/showthread.php?t=1598968](http://ubuntuforums.org/showthread.php?t=1598968)). Thanks

---

### Post by Kipee on 2010-10-23
Thanks, option 2 worked perfectly for me.

---

### Post by psykodan on 2010-10-23
Option 2 worked for me as well, though I had to make further tweaks, because of some reason XBMC started before lirc:

1) Installed "GNOME Infrared Remote Control Properties" to set-up my dodgy Formosa eHome Device

2) Modified /etc/rc.local by adding the lines:
*    sleep 5*
*    service lirc restart*

3) Setup XBMC to delay 10 secs befor starting. (bash -c "sleep 10;xbmc")

...and now all's well again, and the missus isn't shouting at me because the remote isn't working :P

---

### Post by mael on 2010-10-27
uniden9, you're the man! option2 is perfect! thank you!
i cannot understand why ubuntu is "ditching" lirc for such a poor implementation

---

### Post by Spr0k3t on 2010-10-27
Option2 worked perfectly here.  Thanks!

---

### Post by mrand on 2010-10-28
> **mael said:**
> uniden9, you're the man! option2 is perfect! thank you!
i cannot understand why ubuntu is "ditching" lirc for such a poor implementationThis isn't a Ubuntu thing...  the standard Linux kernel is gaining more ability to handle remote controls.  I'm very surprised it has taken this long.  In todays world of plug-and-play, users should not be required to know that they need to install something called lirc in order for their remote to work.  Oh, and not only that, but they have to configure lirc.  And probably key mappings.

Please note that I'm not arguing that the transition isn't causing problems, simply that it is overdue.

[INDENT]Marc[/INDENT]

---

### Post by rhpot1991 on 2010-10-28
> **uniden9 said:**
> New with Maverick is the lirc kernel module are now merged into the kernel. If you upgraded, then you have the older lirc source modules loaded as well.  With the two modules loaded at the same time, neither work.  I have tried to use the kernel module myself and threw in the white towel.  Ubuntu seems to treat the remote as a keyboard device, and it incomplete.  Most keys work, but are either out of place or incomplete.  Then if you configure inputlirc or just lirc, the remote repeats key press because its receiving them from several sources.
To see the two modules run:
#sudo lsmod |grep mseusb
#sudo lsmod |grep ir
You will see lirc_mseusb and mseusb loaded.  They are trying to accomplish the same thing.

Options.
1. Blacklist/Remove the old lirc dkms built modules and use the kernel built in modules.
   A1. To remove. #sudo apt-get remove lirc-modules-source
   A2. To blacklist.  Edit /etc/modprobe.d/blacklist.conf , create it if it doesn't exist.
       Add> 
       blacklist lirc_mseusb
       to the file and save it.
       Update initrmafs,  #sudo update-initramfs -u -k all
       reboot
   B. Now with just the kernel source modules present. 
      1. Install input-utils package
         #sudo apt-get install input-utils
      2. Find your remote input event# and make note
         #lsinput
      3. Reconfigure lirc.  
         #dpkg-reconfigure lirc 
         On the remote select "Linux input layer (/dev/input/eventX)
         Then select the /dev/input/event that matches your remote.
      4. run irw
         #irw
      5. You should see you remote button press show up, and you are done. 
         Note that the remote has a different lirc profile and remote key names are different, but the kernel source drivers are more universal.
      
2. Blacklist the kernel source drivers and use the old dkms built drivers.
   -Well you already have lirc-sources-modules install and probably had this working on 10.04 or older version of ubuntu.
   A. Edit /etc/modprobe.d/blacklist.conf , create it if it doesn't exist.
      Add> 
      blacklist mceusb
      line to the file and save it.
   B. Update initrmafs,  #sudo update-initramfs -u -k all
   C. reboot
   D. Reconfigure lirc if its not already working.
      #sudo dpkg-reconfigure lirc
      On the Remote, Select "Windows Media Center Transceiver/Remote (All)
   E. Thats it. 
   This is the method I chose after wrestling with button repeats on option 1.  I use XBMC and could not figure out how to disable Ubuntu treating the remote as a keyboard device.
   
Also for others having issues with lirc and Maverick but using a different remote than the microsoft media center type, something similar approach will more than likely be needed as well.

I'm not really sure how correct this information is, all you really need to do is: sudo apt-get remove lirc-modules-source

There really isn't any reason to have that installed in the first place.

See: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512)

---

### Post by Neon Dusk on 2010-10-28
> **rhpot1991 said:**
> I'm not really sure how correct this information is, all you really need to do is: sudo apt-get remove lirc-modules-source

There really isn't any reason to have that installed in the first place.

See: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512)

Please see the original post. The generic Mceusb receiver doesn't work using the new kernel source modules (even with lirc-modules-source removed) but works fine with the old lirc modules.

---

### Post by cliffordsnow on 2010-10-29
I have a mceusb remote/receiver that almost works with option 1.  Option 2 doesn't work at all.  The remote has a built in mouse if that makes any difference.  

With option 1 using irw i see the following

000000008001009b 00 KEY_MAIL devinput
000000008001009b 00 KEY_MAIL_UP devinput

I see this on every key press.  There is a KEY_something and a KEY_something_UP.  Both have the exact same key code.  

I tried modifying my lircrc with the key code without the UP suffix but that did not work.  

Any suggestions?

---

### Post by rhpot1991 on 2010-10-29
> **cliffordsnow said:**
> I have a mceusb remote/receiver that almost works with option 1.  Option 2 doesn't work at all.  The remote has a built in mouse if that makes any difference.  

With option 1 using irw i see the following

000000008001009b 00 KEY_MAIL devinput
000000008001009b 00 KEY_MAIL_UP devinput

I see this on every key press.  There is a KEY_something and a KEY_something_UP.  Both have the exact same key code.  

I tried modifying my lircrc with the key code without the UP suffix but that did not work.  

Any suggestions?

Check your /etc/lirc/hardware.conf

Make sure you don't have a --r or --release for the lircd args.

---

### Post by cliffordsnow on 2010-10-30
Thanks removing the -r option solved the UP problem.  Now there is only one key code per press.  I had added that option for hulu.  For now, it is more important just to get the remote working.  Hulu is a much lower priority.

However, in mythtv, pressing key down jumps the menu two places.

---

### Post by cliffordsnow on 2010-10-30
Fixed the double by changing proto options in /etc/init.d/lirc - changed rc5 to rc5-sz.

---

### Post by flakpyro on 2010-11-18
Having the same problem, was using option 2 but it suddenly stopped working this week when blacklisting the kernel mceusb stopped working, no matter what i do the module loads. 

 i have determined my remote is on /dev/input/event4 thanks is 'lsinput'  and evtest /dev/input/event4 shows all the buttons, i have ran sudo dpkg-reconfigure lirc and pointed it at event4 but when i run irw i still get nothing, im at a total loss here, any ideas?

/var/log/daemon.log shows:

Nov 18 18:09:30 ubuntu-media lircd-0.8.7-pre3[840]: accepted new client on /var/run/lirc/lircd
Nov 18 18:09:30 ubuntu-media lircd-0.8.7-pre3[840]: initializing '/dev/input/event4'
Nov 18 18:09:36 ubuntu-media lircd-0.8.7-pre3[840]: removed client
Nov 18 18:09:36 ubuntu-media lircd-0.8.7-pre3[840]: closing '/dev/input/event4'
Nov 18 18:25:19 ubuntu-media lircd-0.8.7-pre3[840]: caught signal
Nov 18 18:25:19 ubuntu-media lircd-0.8.7-pre3[2895]: lircd(devinput) ready, using /var/run/lirc/lircd

---

### Post by RichardK3 on 2010-12-09
> **Kipee said:**
> Thanks, option 2 worked perfectly for me.

This fixed the problem for me also!  But before it would work, I did need to install "lirc-modules-source" using Synaptic Package Manager.  

Doing the steps in Option 2 without installing this package didn't help at all.  The remote still missed key presses.

Thanks to everyone for posting the solution!

Hope this also helps someone out there with the same problem.

---

### Post by lazysalamander on 2010-12-16
I used option 2 and installed lirc-modules-source. 

Thanks so much for this fix! I was going crazy. XBMC works perfectly now. :popcorn:

---

### Post by mhouck on 2011-03-08
Option 2 isn't working for me...

I blacklisted the mceusb driver, installed the lirc source modules... followed all the steps exactly.  once I reboot, I have lirc_mceusb loaded.  dmesg says it found the ir receiver and is using the lirc_mceusb driver.  No errors anywhere, everything should be working.

Except it isn't.  irw doesn't receive any commands at all.

---

### Post by mhouck on 2011-03-08
Fixed the issue.  I also had to blacklist ir_core.

---

### Post by Another Monkey on 2011-03-14
I blacklisted "lirc_mceusb" and XBMC now seems to be working.  "irw" gives the correct output as well, but does seem to duplicate them.  Not sure if that is normal or not.

Not quite sure where "lirc_mceusb", maybe when I followed some documentation that turned out to be old?

---

### Post by winewood on 2011-03-15
Option #2 This worked for me!!  I have been without a remote for almost a month now.

I was hoping someone who knew what they were doing could fix the official myth remote guide (installing lirc), this is good stuff.  Thanks for the posts.

---

### Post by SpiffBB on 2011-04-04
Im on MythBuntu 10.10 and the MS MCE remote worked out of the box. However after some configuration it suddenly stoped working. Reinstall didnt help. Solution 2 in post 4 worked! 
Many thanks!

---

### Post by darumo on 2011-04-16
Solution 2 in post 4 worked.

Ubuntu 10.10 + kernel 2.6.38 (I feel the system works better and more agile) but you have to install "modules lirc deb sources" of "Ubuntu Natty 11.04" (the "lirc modules source" of "Ubuntu 10.10 " does not work with the new kernel)

---

### Post by psypher on 2011-04-17
Neither option 1 or option 2 works in a fresh install of natty. I have logged a bug about this:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/763412](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/763412)

---

### Post by illumilore on 2011-11-08
After doing option 2 from uniden9's instructions, irw is recognizing the keys, but xbmc is still not working. Any ideas?

---

### Post by emgee11 on 2011-11-10
> **illumilore said:**
> After doing option 2 from uniden9's instructions, irw is recognizing the keys, but xbmc is still not working. Any ideas?
 
I'm in the same boat too. IRW is responding and showing the proper responses, but XBMC is not responding at all.
 
I have posted on the XBMC forums as well, but no feedback there yet. I realize this is an Ubuntu forum but hope those who are running XBMC as well might be able to provide some assistance.
 
Thanks!

---

### Post by illumilore on 2011-11-19
> **emgee11 said:**
> I'm in the same boat too. IRW is responding and showing the proper responses, but XBMC is not responding at all.
 
I have posted on the XBMC forums as well, but no feedback there yet. I realize this is an Ubuntu forum but hope those who are running XBMC as well might be able to provide some assistance.
 
Thanks!

If you just upgraded to oneiric, then the keys lirc sends to xbmc has changed, so you need to modify the lirckeymap to match the changed keys.
[http://forum.xbmc.org/showthread.php?p=931482](http://forum.xbmc.org/showthread.php?p=931482)

Make sure lirc itself is still operating with irw first though.

---

### Post by emgee11 on 2011-11-21
Hi illumilore,

Thanks for replying!
 
I had lirc running OK and irw was showing button presses, but no matter what I did XBMC wouldn't repsond. I figured I probably followed a posting or wiki post on how to get a remote working with XBMC and it was out-of-date with respect to what I was setting up and I ended up buggering something up.
 
I reinstalled XBMC Live and did just the stuff to setup up the remote, tested with irw and all is good! I assume something with XBMC got messed up with my first round of tinkering.

---

### Post by Superdude_123 on 2011-12-29
Guys, on 11.10 I get the same problem. The solution is as follows:

Try this:

sudo sed -i '$i echo lirc > /sys/class/rc/rc0/protocols' /etc/rc.local

Read [http://ubuntuforums.org/showthread.php?p=11525835](http://ubuntuforums.org/showthread.php?p=11525835) (bottom)

---

