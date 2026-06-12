---
title: "Huawei E160 with Lucid - still not working permanently"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by night-wing on 2010-05-05
Hi.

The problem, I described here

[http://ubuntuforums.org/showthread.php?t=1448896&highlight=E160](http://ubuntuforums.org/showthread.php?t=1448896&highlight=E160)

is still active. The final brought no solution...

---

### Post by alexfish on 2010-05-05
Hi

from a fresh boot with the dongle out can you try this

connect the dongle then  open up the Disk Utility

wait until the device settles . if a device appears on the the desk top just leave it there for now

from the disk utility you may see something like the screen shot below

I have highlighted the CD mass storage device

first click on the    	 	 	 	 	 Unmount Volume Button from the bottom menu

then wait a few moments until the device settles

then click on the Safely Remove Button in the top menu

then try the connection

if the device does note show up on the desk top, still continue with the above



could you post the results of this command from two separate terminals

first terminal : do this after the modem is connected

Code:

dmesg | grep -e "modem" -e "tty"

  	 	 	 	 	[COLOR=#000000][FONT=Courier New, Courier, mono]****[/FONT][/COLOR]   	 	 	 	 	 	   
 second terminal use the same command but after the operations above


also I need to ask a question ; do you have  usb modeswitch installed

thanks in advance

alexfish

---

### Post by night-wing on 2010-05-05
Hi.

Yes, usb_modeswitch ist installed - but also without it I have no difference.
The modem is shown in lsusb every time - also, when I can't use it. dmesg shows the same info when modem is usable or when it is not.
Don't have any clue. In Jaunty or Intrepid it works perfectly.

---

### Post by pdc on 2010-05-05
> The modem is shown in lsusb every time 

what does lsusb say?

> dmesg shows the same info when modem is usable or when it is not.

what does 

> dmesg | grep tty give you?

If you copy and paste this command and copy and paste back the result

I have found 10.04 fine with 3565-Z, E220 and MF636

---

### Post by alexfish on 2010-05-05
> **night-wing said:**
> Hi.

Yes, usb_modeswitch ist installed - but also without it I have no difference.
The modem is shown in lsusb every time - also, when I can't use it. dmesg shows the same info when modem is usable or when it is not.
Don't have any clue. In Jaunty or Intrepid it works perfectly.

Hi

the lsub is not the information I require

the information I have requested (but not posted ) is in my first post , with exemption of the usb mode switch , I do know that if the mode switch is not installed then doing the procedure above may replicate what the the mode switch does / as represented by the screenshot ' 

what I am trying to confirm is how many ports are registering on your system , if the the mode switch is installed please carry out what has been mention , IE check what is shown in the DiskUtility

from this I may be able to find a solution

Please Post the Information Requested

Added since we know the modeswitch is installed / need more info /

1.When you have a connection :from the network manager   . Connection information can post the detail of the  Interface  it may look like {GSM (ttyUSB2) } or other port identifier after the tty

after this I will ask you to look in a system file to look for some particular lines , This will apply when you do not have a connection

Regards 

alexfish

---

### Post by night-wing on 2010-05-07
Hello.

Sorry for the delay. I've had to install lucid on my second thinkpad to be able to try all these steps (because on my primary I restored my intrepid image to be able to work...).

First, I tried lsusb, which gives me the same output, when the modem is online or not (also when it's not recognized by network-manager):

Bus 006 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

Then I tried dmesg | grep tty (when it is not recognized):
dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.266054] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.373774] tty tty3: hash matches

In the drive manager I have 
device /dev/sdb0
firmware 2.31
the other output is nearly the same as shown in your screenshot (see my attachment)

dmesg | grep -e "modem" -e tty
[    0.000000] console [tty0] enabled
[    0.266054] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.373774] tty tty3: hash matches

when I try to sure remove the drive via the tool, I got an error:

Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.1/0000:07:00.2/usb6/6-2)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

sure removal via desktop works without problem.
So I again made the dmes command, which shows exactly the same as on the output above!

When I remove the stick and plug it in again, after 1 minute or so, it is available in the network-manager. Then I did the dmesg command again:

dmesg | grep -e "modem" -e tty
[    0.000000] console [tty0] enabled
[    0.266054] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.373774] tty tty3: hash matches
[ 2572.219319] USB Serial support registered for GSM modem (1-port)
[ 2572.222200] option 6-2:1.0: GSM modem (1-port) converter detected
[ 2572.222766] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 2572.222808] option 6-2:1.1: GSM modem (1-port) converter detected
[ 2572.229542] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 2572.229668] option: v0.7.2:USB Driver for GSM modems

Hope, these informations helps?!

Regards
nightwing

---

### Post by alexfish on 2010-05-07
hi

the last message

[ 2572.219319] USB Serial support registered for GSM modem (1-port)
[  2572.222200] option 6-2:1.0: GSM modem (1-port) converter detected
[  2572.222766] usb 6-2: GSM modem (1-port) converter now attached to [COLOR=Blue] ttyUSB0[/COLOR]
[ 2572.222808] option 6-2:1.1: GSM modem (1-port) converter  detected
[ 2572.229542] usb 6-2: GSM modem (1-port) converter now  attached to[COLOR=Blue] ttyUSB1[/COLOR]
[ 2572.229668] [COLOR=Blue]option: v0.7.2:USB Driver for GSM  modems[/COLOR]


now indicates the modem has configured and the drivers are ready I have highlighted the important bits in blue .

so you should be able to configure the device in the Network Manager

so try to make the connection / click on the applet to make a new connection

open up the terminal and enter this code

Code:

tail -f /var/log/syslog

click on the network manager to make the new connection

see what happens and post the outputs of the terminal

thanks in advance

alexfish

---

### Post by night-wing on 2010-05-07
Hi.

Sorry, I fear, you misunderstood me.
The last message, which - as you said - indicates the modem is ready -
is only shown, when I remove the stick and re-plugin it. Then it is
ready to go (after 1 minute or so).
But I want to use it without needing to do this.
In jaunty and intrepid this was possible - since karmic not...

Sometimes the stick works after booting without having to do this - most times I have to remove/replug or reboot.

---

### Post by alexfish on 2010-05-07
hi

the only thing I can think of is this 

try disconnecting the connection in NM before powering down

Also some devices need time to settle , Ubuntu 10.04 boots very fast , so may be when its going through the probing of devices then the actual device has not reached its stable state

can you try this and see If it has any effect

Add a delay  in the  /etc/modprobe.conf: 

 
Code:

sudo gedit /etc/modprobe.conf

options usb-storage delay_use=1 (or  10, or other) 5 is a good bench mark To start

Save and exit

regards

alexfish
[SIZE=2]
[/SIZE]

---

### Post by night-wing on 2010-05-08
Hi.

Thanks. I tried this (also with 10 as parameter). Did not work... :-(

---

### Post by night-wing on 2010-05-08
Hurrah. I made it!

I had to edit the file /lib/udev/rules.d/61-option-modem-modeswitch.rules
and added the line

ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

After a reboot, the Huawei E160 worked perfectly!!!

Thanks for your help. Think, you brought me to the right direction ):P

Regards
nightwing

---

### Post by pdc on 2010-05-08
so how did you get there? It seems a leap in the dark from prior moves;

as I understand it, the udev rule just means the computer does it each time it boots up;

interesting the E160 needs that; ironically, it worked perfectly well on older distros: eg ubuntu 8.04 etc

(oh, and you may wish to edit the thread to say SOLVED ..............

---

### Post by alexfish on 2010-05-08
> **night-wing said:**
> Hurrah. I made it!

I had to edit the file /lib/udev/rules.d/61-option-modem-modeswitch.rules
and added the line

ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

After a reboot, the Huawei E160 worked perfectly!!!

Thanks for your help. Think, you brought me to the right direction ):P

Regards
nightwing

Hi

which version of usb_modeswitch are you using

or have you recently updated your system

thanks in advance

alexfish

---

### Post by night-wing on 2010-05-08
Marked as solved now :-)

usb_modeswitch: It's the most recent one from lucid (don't ask me what version).

How did I get there?
Ok. I thought, when the usb_delay did not make any difference, maybe one of the configuration files from the old releases (where the e160 worked - like in intrepid) is possibly different from the one in lucid. 
Because the usb_modeswitch.conf is not, it must be an udev rule.
In intrepid (which is installed on my primary notebook), I saw, that the e160 has an entry
in the /lib/udev/rules.d/61-option-modem-modeswitch.rules

In lucid not...
So I tried (trial and error of course) to put this line in the file in lucid too.
Rebooted...
and was happy :-D

---

### Post by alexfish on 2010-05-08
hi

just for a bit of clarity

from synaptic can you do a search "modeswitch"

this will indicate the version and if the modeswitch-data is installed

see below ,although , as you can see from my screen shot I don't have modeswitch installed'

there may be an easier way than writing rules ; have a read here

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by night-wing on 2010-05-08
That's right of course.
But I'm a little bit the "never touch a running system" - type ;)
So as long as it runs now, I would not make any new configuration.

Thanks anyway.

Regards
nightwing

---

### Post by alexfish on 2010-05-08
> **night-wing said:**
> that's right of course.
But i'm a little bit the "never touch a running system" - type ;)
so as long as it runs now, i would not make any new configuration.

Thanks anyway.

Regards
nightwing

mmm!

---

### Post by jmuzz on 2010-05-09
Thanks for the solution, seems to be working for me now too.

To summarize what I did.
I first (before thread solved) tried enabling the proposed updates and applied them all in case there was a fix in there, didnt fix it. I dont know if that had any effect on the final positive outcome? (try the edit first).

edit file /lib/udev/rules.d/61-option-modem-modeswitch.rules

add
```

ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"
```

To the last line before the comments at the bottom. Save.

Reboot. Works now.
Or at least seems to, it would work on the rare occasion previously, it has successfully detected for 3 reboots and a couple of unplugs while logged in.

---

### Post by 2badgersblue on 2010-06-05
I had to join up just to say thanks for the fix here.

I have a Huawei E160E which worked fine all the time I used Ubuntu 9. After doing a fresh install to 10 with all the updates etc it wouldn't even detect as modem.

I added the line as previously instructed in this thread, rebooted and it works a treat again.

Wonder why that line was taken out of the config file? It's not like it's old tech that hardly anyone uses.

Cheers very much once again.

---

### Post by alexfish on 2010-06-05
Delving around in the back end of the system is not for the novice or a new comer to Linux
the only way forward is for things to work without having to add rules  via the terminal, hence the **updated usb modeswitch**  should work without having  to do any thing to the system.So it pays to keep the modeswitch up to date , also new devices are added , as and when details are found

What is really strange is I have a E160 and works without any rules been added  or usb modeswitch been installed , and this will take some beating ,it will even start up on boot , did not ask to .

---

### Post by rsw1965 on 2010-06-06
This solution also worked for my Huawei e169 - although I took a slightly different path to the rule.

I created a file called "temp-e169-modem.rules" in the /etc/udev/rules.d directory. I used the same settingsline as in the post above - except that I changed the product ID to 1001. 

ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

Nothing else in the file.

Rebooted and now the e169 has been picked up each time, unplugged and reconnected etc - all seems to work now.

The README in the /etc/udev/rules.d directory explained that rules written there would be persistent (while those in /lib/udev/ would be overwritten with any update. It also noted that simply using any text based name for the file was sufficient for it to be executed after all other rules.

Excellent outcome - Lucid was not happy with the e169 before this.

rsw1965

Thanks for the solution

---

### Post by 2badgersblue on 2010-06-07
So, we're probably better off creating our own file in the /etc/udevrules.d directory or we may find the modem stops working after some future update.

Thanks for the heads up!

---

### Post by RonCam on 2010-06-29
> **rsw1965 said:**
> This solution also worked for my Huawei e169 - ... Excellent outcome - Lucid was not happy with the e169 before this.
Your assistance will be appreciated to learn why I wasn't able to reproduce your success, also with Lucid / 10.04.  From other posts, I suspect that in some cases, there may be a kernel problem, as well.

Could you please give the following command at your Command Prompt and, if you don't see the same kernel version, please paste what you see in a reply?

```
~$ cat /proc/version
Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010
```

This is quite a mystery as to why some, such as yourself, have success in getting the E169 going, and others, with apparently the same Ubuntu version, have no luck.  Something must be different ... I'll be curious to learn whether or not we have the same kernel version.  

While we're comparing notes, would you please also give this command and see if your modem gives the identical read-out?

```

~$ lsusb
Bus 003 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
```

When this modem installed 'without a hitch' on Jaunty, I recall a box popping up identifying it as a model E620.  I now see that this came from its firmware.  

The model number printed on the modem and its box is E169.  I am wondering if the difference in results may (also) be due to a difference in firmware on various E169's?  Is this model number I'm seeing just a typo, or could some E169's actually have incorrect firmware?  Since your modem works so well, does the above line from yours read exactly the same, as mine?

---

### Post by rsw1965 on 2010-07-02
cat/proc

Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010


lsusb
Bus 007 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

The kernel was updated in the last day or so and the modem has continued to work without any further changes required.

I had no problems at all out of the box on Ubuntu 9.04 with the e169 - but have only got it to work by creating the rules file above in Ubuntu 10.04.

rsw1965

---

### Post by rsw1965 on 2010-07-02
This is the tail end of dmesg that I get after connecting and watching the e169 modem startup.

[   48.292039] usb 7-1: new full speed USB device using uhci_hcd and address 2
[   48.458185] usb 7-1: configuration #1 chosen from 1 choice
[   50.496069] usb 7-1: USB disconnect, address 2
[   50.739205] Initializing USB Mass Storage driver...
[   50.739260] usbcore: registered new interface driver usb-storage
[   50.739990] USB Mass Storage support registered.
[   51.232038] usb 7-1: new full speed USB device using uhci_hcd and address 3
[   51.399180] usb 7-1: configuration #1 chosen from 1 choice
[   51.411085] scsi8 : SCSI emulation for USB Mass Storage devices
[   51.414818] usb-storage: device found at 3
[   51.414821] usb-storage: waiting for device to settle before scanning
[   51.453349] usbcore: registered new interface driver usbserial
[   51.454092] USB Serial support registered for generic
[   51.454881] usbcore: registered new interface driver usbserial_generic
[   51.454884] usbserial: USB Serial Driver core
[   51.464572] USB Serial support registered for GSM modem (1-port)
[   51.465431] option 7-1:1.0: GSM modem (1-port) converter detected
[   51.465635] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB0
[   51.465650] option 7-1:1.1: GSM modem (1-port) converter detected
[   51.465775] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB1
[   51.465790] option 7-1:1.2: GSM modem (1-port) converter detected
[   51.465906] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB2
[   51.465930] usbcore: registered new interface driver option
[   51.465932] option: v0.7.2:USB Driver for GSM modems
[   56.413112] usb-storage: device scan complete
[   56.418109] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   56.421100] scsi 8:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[   56.443080] sr1: scsi-1 drive
[   56.443224] sr 8:0:0:0: Attached scsi CD-ROM sr1
[   56.443310] sr 8:0:0:0: Attached scsi generic sg2 type 5
[   56.443453] sd 8:0:0:1: Attached scsi generic sg3 type 0
[   56.475102] sd 8:0:0:1: [sdb] Attached SCSI removable disk
[   61.098844] PPP BSD Compression module registered
[   61.111114] PPP Deflate Compression module registered
[   77.800424] ISO 9660 Extensions: Microsoft Joliet Level 3
[   77.943347] ISOFS: changing to secondary root


Hope that might help you.

rsw1965

---

### Post by rsw1965 on 2010-07-02
Have now been able to access a Windows machine to examine the diagnostics on the device.

This shows

IMEI: (not disclosing publicly)
IMSI: (not disclosing publicly)
FIRMWARE: 11.314.17.00.00
HARDWARE: CD57TCPU
MODEL: E169
SERIAL: (not disclosing publicy)

So that might also help identify why your modem is or is not responding.

---

### Post by RonCam on 2010-07-02
Thanks, rsw1965, for all the details. :)

I think we've ruled out a kernel problem and both E169's appear identical.  I'm going to completely uninstall USB-ModeSwitch, reinstall, and start over.  But, before I do, two questions:

:?: Where did you get your USB-ModeSwitch package, the one that gives good results with the E169?  

The version from the Ubuntu repository (including its configuration file) is a few months old, and the one from the Debian repository is only a couple of weeks old.  A version number would be helpful, if not too much trouble.  

:?: Is *ModemManager* installed on your system?  

On my system, Synaptic shows it's *not* installed, and a search for its files confirms this.  NetworkManager *is* installed, of course.  

There are differing opinions on this, one post saying the E169 started to work after a missing M-M was installed, and another, saying it shouldn't make any difference.  

At this point all the differences between your success and my continuing problems will be resolved, so I'll make a fresh start and see what happens.

---

### Post by rsw1965 on 2010-07-04
I am using the usb-modeswitch below - I am pretty sure from the Ubuntu repo. 

* usb-modeswitch: handle USB devices with multiple modes
 * Version 1.1.0 (C) Josua Dietze 2010
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !


As for the Modemmanager - synaptic shows it as installed - 0.3-0Ubuntu2 version.

I have had other GSM modem devices connected to the laptop such as a Nokia 6220c classic phone and a ZTE F156 phone - both of which can operate and were recognised as GSM modems prior to finally getting the e169 to work. In fact I was relying on the Nokia 6220c while I tried to get the e169 back into operation after upgrading from Ubuntu 9.04. Perhaps modem manager was installed as part of the that recognition process?

Hope this helps.

rsw1965

---

### Post by RonCam on 2010-07-12
> **rsw1965 said:**
> As for the Modemmanager - synaptic shows it as installed - 0.3-0Ubuntu2 version.This is likely the difference between your success and my failure, though through the info received on USB-ModeSwitch forum, they are saying it should make no difference.  But, in my distro the box is clear, vs. dark green, for properly-installed packages.  

But, apparently it *does *make a difference in some cases.  I will go back, install both programs, and see what happens.  We will do this, ModemManager first, then ModeSwitch on top of that.  

Someone else on the Leeenux forum made passing reference to ModemManager helping for the E169, but then dropped the thread when more details were requested.  So thanks so much.  

Thanks for the interest and your reply - was in the hospital for 8 days right after I posted the message.  Will get back to the "important things in life" (i.e., having my wireless connection set-up right :rolleyes:) ASAP.

[edit]
Yes, you are correct. They are telling me on the ModeSwitch forum that having the latest version of their utility is NOT necessary for the E169.
[/edit]

---

### Post by dougfractal on 2010-07-16
Thanks guys. I'm working now too. E169g

After following to many different guides, I ended up here.

I did reinstall usb-modeswitch and modemmanager

```
lsusb | grep -e "modem" 

Bus 003 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

cat /proc/version
Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010

```
```

sudo apt-get install usb-modeswitch-data usb-modeswitch

sudo nano /lib/udev/rules.d/61-option-modem-modeswitch.rules
```
insert this line.
> ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"


Rebooted and working.

---

### Post by afhx on 2010-08-24
Would this work with the E1750 from t-mobile in the same directory?

---

### Post by RonCam on 2010-08-24
> **dougfractal said:**
> Thanks guys. I'm working now too ... [with the] E169g.

After following to many different guides, I ended up here.
I did reinstall usb-modeswitch and modemmanager.
Rebooted and working.Thanks, dougfractal, for showing the way and making me think it was worthwhile to get started (once again) on the modem.  It's now working as well in Lucid as it was in Jaunty.  

Knowing I could drop back to your steps, I tried even more simplification, without the Command line:

Open Synaptic Package Manager, and check both *usb-modeswitch* and *modemmanager*.  The modeswitch data file will be selected automatically.  Click apply.

These are the packages from the current repository, and not the latest versions, but it seems these are all that's needed if the goal is just to get this particular modem working.

Then, plug in the modem.  Nothing 'pops up' automatically.  You have to left-click on the 'antenna icon' to see that something new has appeared.  

Go through the setup wizard.  Accepting the defaults is fine (this is for the Portuguese TMN 'banda larga' service, already on the wizard's menu).  Make the connection available to 'all users' and put in the PIN, to avoid unnecessary prompts during subsequent modem reinsertions.  

This part is a bit tricky if you're testing the setup where you also have an active Wi-Fi wireless connection available:  the NetworkManager applet keeps trying to 'lock in' on the wireless, in preference to the 3G connection, making you think something's gone wrong.  So, turn your wireless adapter off.  

You can't test by switching back-and-forth between the wireless and 3G.  You have to pull the modem out, and reinsert, to initiate another 3G connection.  You don't have to 'eject' or 'disable' as for other USB devices.  At least, I saw no benefit or difference.  

I was ready to edit '61-option-modem-modeswitch.rules' as dougfractal said, but at this time, the line he gave is now in the data file, just as it comes from the repository.  So, I just backed out of the edit without saving.  

This is with Leeenux v4.01 Extended on a ASUS 701-4G.  In Synaptic on v4.01, the check-boxes for both *usb-modeswitch* and *modemmanager* were empty. This would explain the difficulty in getting this specific modem to work "out of the box".  

If your distro/fork has these packages installed (the check-boxes will then be solid green), I doubt you'd have to reinstall, but to be sure, just update to the current version in the repository.  If both packages are there, and updated, you probably won't be reading this, because you had no problem, in the first place ... :biggrin:

[FONT="System"][SIZE="1"][COLOR="Blue"]P.S.: The subject line has been changed to the correct model, E169.  There's apparently a typo in this modem's firmware that makes it come up as an E620, creating confusion.  E169 is printed on the modem as well as its package.[/COLOR][/SIZE][/FONT]

---

### Post by skkeeper on 2010-09-07
Hi there,
I'm running Ubuntu 10.10 beta 1 amd64(but I've been having this problem since 10.04) and I can't seen to make my HUAWEI E160 to work. Before 10.04, everything just worked out of the box, but since 10.04 the dongle shows up in the network manager but just fails to connect (enter infinite loop trying to connect sometimes).

My ISP is Optimus Kanguru in Portugal if that is relevant.

I've compiled usb_modeswitch manually and changed the rules of udev like its described in this topic nothing worked. I even tried to run the sakis3g script, but no luck.

I've been wondering about google and I'll dump here some information I hope its usefull to solve this problem.

lsusb | grep Huawei
Bus 002 Device 011: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

dmesg | grep HUAWEI
[   59.057641] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   59.060908] scsi 11:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2405.406416] scsi 16:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2405.410738] scsi 15:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2637.465544] scsi 20:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2637.468978] scsi 21:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2666.163494] scsi 25:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2666.165624] scsi 26:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2

cat /var/log/usb_modeswitch_2-1\:1.0
USB_ModeSwitch log from Tue Sep 07 14:52:28 WEST 2010

Using global config file: /etc/usb_modeswitch.conf
raw args from udev: /2-1:1.0
Bus ID for device not given by udev.
 Trying to determine it from kernel name (2-1:1.0) ...
Top sysfs directory not found (/sys/bus/usb/devices/2-1)! Exiting

This is really getting anoying, since I have to come back to Windows everytime I'm out of reach of a wifi spot. Please help if you can.

Thanks & namaste

---

### Post by romankarlfranz on 2011-07-28
Hi everyone!  I have the HUAWEI E 160 and Ubuntu 11.04  The modem is working right now but all the time it disconnects automatically and also disappears in the network manager. Then my Mobile Broadband provider is not available for selection. Then I click Enable/Disable Mobile Broadband like crazy and restart like crazy and eventually it will work again.  Any ideas what's the problem could be?  By the way I had the same problem in Ubuntu 10.10. I think it was working fine in Ubuntu Hardy something. 8 something. can't remember.

my dmesg
```
[    0.610590] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.610602] pci 0000:00:1c.1: setting latency timer to 64
[    0.610618] pci 0000:00:1e.0: setting latency timer to 64
[    0.610628] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.610636] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.610644] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.610652] pci_bus 0000:00: resource 7 [mem 0x7f700000-0xffffffff]
[    0.610661] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.610668] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.610677] pci_bus 0000:01: resource 2 [mem 0x7f700000-0x7f8fffff 64bit pref]
[    0.610685] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.610693] pci_bus 0000:02: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.610702] pci_bus 0000:02: resource 2 [mem 0x7f900000-0x7fafffff 64bit pref]
[    0.610710] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.610718] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.610726] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.610734] pci_bus 0000:03: resource 7 [mem 0x7f700000-0xffffffff]
[    0.610838] NET: Registered protocol family 2
[    0.611036] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.611794] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.612837] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.613306] TCP: Hash tables configured (established 131072 bind 65536)
[    0.613316] TCP reno registered
[    0.613330] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.613351] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.613631] NET: Registered protocol family 1
[    0.613674] pci 0000:00:02.0: Boot video device
[    0.640142] PCI: CLS 64 bytes, default 64
[    0.640774] cpufreq-nforce2: No nForce2 chipset.
[    0.641213] audit: initializing netlink socket (disabled)
[    0.641238] type=2000 audit(1311879412.636:1): initialized
[    0.662936] highmem bounce pool size: 64 pages
[    0.662951] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.669189] VFS: Disk quotas dquot_6.5.2
[    0.669384] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.671776] fuse init (API version 7.16)
[    0.672145] msgmni has been set to 1668
[    0.672917] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.673039] io scheduler noop registered
[    0.673046] io scheduler deadline registered
[    0.673116] io scheduler cfq registered (default)
[    0.673666] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.673755] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.673966] intel_idle: MWAIT substates: 0x20220
[    0.673983] intel_idle: v0.4 model 0x1C
[    0.673988] intel_idle: lapic_timer_reliable_states 0x2
[    0.674008] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.674951] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.675972] ACPI: AC Adapter [ADP1] (on-line)
[    0.676236] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.676251] ACPI: Power Button [PWRB]
[    0.676422] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.676989] ACPI: Lid Switch [LID0]
[    0.677149] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.677161] ACPI: Power Button [PWRF]
[    0.677541] ACPI: acpi_idle yielding to intel_idle
[    0.689682] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.689836] ERST: Table is not found!
[    0.690053] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.690680] isapnp: Scanning for PnP cards...
[    0.725739] ACPI: Battery Slot [BAT0] (battery present)
[    1.010175] Freeing initrd memory: 17760k freed
[    1.044824] isapnp: No Plug & Play device found
[    1.056171] Linux agpgart interface v0.103
[    1.056346] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.056536] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.056785] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.057017] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.059925] brd: module loaded
[    1.061369] loop: module loaded
[    1.061595] i2c-core: driver [adp5520] using legacy suspend method
[    1.061600] i2c-core: driver [adp5520] using legacy resume method
[    1.061811] ata_piix 0000:00:1f.2: version 2.13
[    1.061857] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.061867] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.216046] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.216754] scsi0 : ata_piix
[    1.216980] scsi1 : ata_piix
[    1.219372] ata1: SATA max UDMA/133 cmd 0xf0e0 ctl 0xf0d0 bmdma 0xf0a0 irq 19
[    1.219379] ata2: SATA max UDMA/133 cmd 0xf0c0 ctl 0xf0b0 bmdma 0xf0a8 irq 19
[    1.220482] Fixed MDIO Bus: probed
[    1.220596] PPP generic driver version 2.4.2
[    1.220725] tun: Universal TUN/TAP device driver, 1.6
[    1.220730] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.220940] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.221001] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.221032] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.221040] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.221129] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.221232] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.221249] ehci_hcd 0000:00:1d.7: debug port 1
[    1.225135] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.225166] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeb05000
[    1.240027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.240298] hub 1-0:1.0: USB hub found
[    1.240309] hub 1-0:1.0: 8 ports detected
[    1.240476] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.240512] uhci_hcd: USB Universal Host Controller Interface driver
[    1.240582] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.240596] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.240603] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.240697] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.240783] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000f080
[    1.241086] hub 2-0:1.0: USB hub found
[    1.241097] hub 2-0:1.0: 2 ports detected
[    1.241228] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.241241] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.241247] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.241352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.241432] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f060
[    1.241720] hub 3-0:1.0: USB hub found
[    1.241730] hub 3-0:1.0: 2 ports detected
[    1.241879] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.241892] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.241899] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.241991] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.244098] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f040
[    1.244392] hub 4-0:1.0: USB hub found
[    1.244402] hub 4-0:1.0: 2 ports detected
[    1.244535] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.244552] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.244558] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.244653] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.244749] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000f020
[    1.245046] hub 5-0:1.0: USB hub found
[    1.245056] hub 5-0:1.0: 2 ports detected
[    1.245342] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.251394] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.251409] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.251709] mousedev: PS/2 mouse device common for all mice
[    1.252099] rtc_cmos 00:04: RTC can wake from S4
[    1.252238] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.252275] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.252493] device-mapper: uevent: version 1.0.3
[    1.252696] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.252859] device-mapper: multipath: version 1.2.0 loaded
[    1.252867] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.253066] EISA: Probing bus 0 at eisa.0
[    1.253072] EISA: Cannot allocate resource for mainboard
[    1.253078] Cannot allocate resource for EISA slot 1
[    1.253083] Cannot allocate resource for EISA slot 2
[    1.253088] Cannot allocate resource for EISA slot 3
[    1.253093] Cannot allocate resource for EISA slot 4
[    1.253099] Cannot allocate resource for EISA slot 5
[    1.253105] Cannot allocate resource for EISA slot 6
[    1.253112] Cannot allocate resource for EISA slot 7
[    1.253120] Cannot allocate resource for EISA slot 8
[    1.253125] EISA: Detected 0 cards.
[    1.253427] cpuidle: using governor ladder
[    1.253670] cpuidle: using governor menu
[    1.254241] TCP cubic registered
[    1.254555] NET: Registered protocol family 10
[    1.255684] NET: Registered protocol family 17
[    1.255726] Registering the dns_resolver key type
[    1.256621] Using IPI No-Shortcut mode
[    1.256894] PM: Hibernation image not present or could not be loaded.
[    1.256917] registered taskstats version 1
[    1.257384]   Magic number: 3:910:949
[    1.257437] tty tty6: hash matches
[    1.257523] rtc_cmos 00:04: setting system clock to 2011-07-28 18:56:54 UTC (1311879414)
[    1.257531] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.257534] EDD information not available.
[    1.273996] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.388545] ata1.00: ATA-8: WDC WD2500BEVT-22A23T0, 01.01A01, max UDMA/133
[    1.388553] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.404542] ata1.00: configured for UDMA/133
[    1.404795] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.405132] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.405230] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.405360] sd 0:0:0:0: [sda] Write Protect is off
[    1.405370] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.405473] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.464765]  sda: sda1 sda2 < sda5 > sda3
[    1.465626] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.465707] Freeing unused kernel memory: 700k freed
[    1.466117] Write protecting the kernel text: 5192k
[    1.466198] Write protecting the kernel read-only data: 2148k
[    1.522571] <30>udev[69]: starting version 167
[    1.664128] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.710421] sdhci: Secure Digital Host Controller Interface driver
[    1.710430] sdhci: Copyright(c) Pierre Ossman
[    1.760348] jme: JMicron JMC2XX ethernet driver version 1.0.7
[    1.760423] jme 0000:02:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.760447] jme 0000:02:00.5: setting latency timer to 64
[    1.762511] jme 0000:02:00.5: eth0: JMC260 Fast Ethernet ver:22 rev:2 macaddr:54:42:49:77:ed:c8
[    1.798247] hub 1-3:1.0: USB hub found
[    1.798632] hub 1-3:1.0: 4 ports detected
[    1.803139] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.803220] sdhci-pci 0000:02:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.804574] sdhci-pci 0000:02:00.0: setting latency timer to 64
[    1.804600] mmc0: no vmmc regulator found
[    1.804700] Registered led device: mmc0::
[    1.816178] mmc0: SDHCI controller on PCI [0000:02:00.0] using ADMA
[    1.816226] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.816257] sdhci-pci 0000:02:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.816276] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[    1.816293] sdhci-pci 0000:02:00.2: PCI INT B disabled
[    1.946621] [drm] Initialized drm 1.1.0 20060810
[    1.979946] mmc0: new SD card at address d555
[    2.024067] usb 1-7: new high speed USB device using ehci_hcd and address 5
[    2.054197] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.054210] i915 0000:00:02.0: setting latency timer to 64
[    2.061325] mmcblk0: mmc0:d555 SU01G 968 MiB 
[    2.063285]  mmcblk0: p1
[    2.106588] i915 0000:00:02.0: irq 40 for MSI/MSI-X
[    2.106600] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.106604] [drm] Driver supports precise vblank timestamp query.
[    2.187694] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.188105] [drm] initialized overlay support
[    2.524473] Console: switching to colour frame buffer device 128x37
[    2.524541] fb0: inteldrmfb frame buffer device
[    2.524547] drm: registered panic notifier
[    2.526874] acpi device:20: registered as cooling_device2
[    2.528129] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.528452] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.529513] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.732097] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.852137] usb 2-2: device descriptor read/64, error -71
[    3.076084] usb 2-2: device descriptor read/64, error -71
[    3.148169] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.148178] EXT4-fs (sda1): write access will be enabled during recovery
[    3.292506] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    3.412060] usb 2-2: device descriptor read/64, error -71
[    3.485328] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.485350] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1447765
[    3.485403] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1447764
[    3.485423] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1447763
[    3.485441] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1447762
[    3.485458] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1447761
[    3.485473] EXT4-fs (sda1): 5 orphan inodes deleted
[    3.485477] EXT4-fs (sda1): recovery complete
[    3.636073] usb 2-2: device descriptor read/64, error -71
[    3.852046] usb 2-2: new full speed USB device using uhci_hcd and address 4
[    3.903775] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.260066] usb 2-2: device not accepting address 4, error -71
[    4.372079] usb 2-2: new full speed USB device using uhci_hcd and address 5
[    4.780072] usb 2-2: device not accepting address 5, error -71
[    4.780100] hub 2-0:1.0: unable to enumerate USB device on port 2
[    5.020072] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    5.268419] usb 1-3.2: new high speed USB device using ehci_hcd and address 6
[    5.436405] usb 1-3.3: new high speed USB device using ehci_hcd and address 7
[    5.600409] usb 1-3.4: new low speed USB device using ehci_hcd and address 8
[   11.841677] <30>udev[305]: starting version 167
[   11.899923] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.951803] lp: driver loaded but no devices found
[   12.274198] type=1400 audit(1311879425.513:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=435 comm="apparmor_parser"
[   12.277860] type=1400 audit(1311879425.517:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=435 comm="apparmor_parser"
[   12.278541] type=1400 audit(1311879425.517:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=435 comm="apparmor_parser"
[   12.579567] jmb38x_ms 0000:02:00.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   12.579584] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[   12.917794] jme 0000:02:00.5: irq 41 for MSI/MSI-X
[   12.918175] jme 0000:02:00.5: eth0: Link is down
[   12.919808] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.326358] usbcore: registered new interface driver uas
[   13.547581] Linux video capture interface: v2.00
[   13.636293] sony-laptop: Sony Notebook Control Driver v0.6.
[   13.640543] Initializing USB Mass Storage driver...
[   13.647389] scsi2 : usb-storage 1-3.2:1.0
[   13.660092] scsi3 : usb-storage 1-3.3:1.0
[   13.683835] usbcore: registered new interface driver usb-storage
[   13.683845] USB Mass Storage support registered.
[   13.891152] uvcvideo: Found UVC 1.00 device USB2.0 Webcam (0bda:5801)
[   13.935523] input: USB2.0 Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/input/input5
[   13.953115] usbcore: registered new interface driver uvcvideo
[   13.953124] USB Video Class driver (v1.0.0)
[   14.011152] type=1400 audit(1311879427.249:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=725 comm="apparmor_parser"
[   14.027219] type=1400 audit(1311879427.265:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=724 comm="apparmor_parser"
[   14.037021] type=1400 audit(1311879427.277:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=725 comm="apparmor_parser"
[   14.037719] type=1400 audit(1311879427.277:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=725 comm="apparmor_parser"
[   14.060486] type=1400 audit(1311879427.301:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=732 comm="apparmor_parser"
[   14.092600] type=1400 audit(1311879427.333:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=732 comm="apparmor_parser"
[   14.112334] type=1400 audit(1311879427.353:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=736 comm="apparmor_parser"
[   14.658837] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GP08NU6B  1.00 PQ: 0 ANSI: 0
[   14.665302] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   14.665314] cdrom: Uniform CD-ROM driver Revision: 3.20
[   14.666022] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   14.666611] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   14.716270] scsi 3:0:0:0: Direct-Access     Samsung  G2 Portable           PQ: 0 ANSI: 2 CCS
[   14.728907] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   14.732919] sd 3:0:0:0: [sdb] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[   14.733925] sd 3:0:0:0: [sdb] Write Protect is off
[   14.733938] sd 3:0:0:0: [sdb] Mode Sense: 3c 00 00 00
[   14.743553] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   14.749063] cfg80211: Calling CRDA to update world regulatory domain
[   14.753767]  sdb: sdb1
[   14.759186] sd 3:0:0:0: [sdb] Attached SCSI disk
[   14.897459] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0xa0400
[   14.945810] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   15.024242] Bluetooth: Core ver 2.15
[   15.024604] NET: Registered protocol family 31
[   15.024612] Bluetooth: HCI device and connection manager initialized
[   15.024620] Bluetooth: HCI socket layer initialized
[   15.154189] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.168076] usbcore: registered new interface driver btusb
[   15.519415] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/SNY5001:00/input/input7
[   15.534096] input: Sony Vaio Jogdial as /devices/virtual/input/input8
[   15.534431] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   15.584217] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0/input/input9
[   15.585570] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.7-3.4/input0
[   15.595316] usbcore: registered new interface driver usbhid
[   15.595325] usbhid: USB HID core driver
[   15.666709] cfg80211: World regulatory domain updated:
[   15.666719] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.666729] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.666738] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.666747] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.666757] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.666766] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.806065] Bluetooth: L2CAP ver 2.15
[   15.806074] Bluetooth: L2CAP socket layer initialized
[   15.945042] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.945050] Bluetooth: BNEP filters: protocol multicast
[   16.212805] Bluetooth: SCO (Voice Link) ver 0.6
[   16.212815] Bluetooth: SCO socket layer initialized
[   16.282398] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.282420] rt2800pci 0000:01:00.0: setting latency timer to 64
[   16.292167] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.292180] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292188] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   16.292196] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292204] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   16.292213] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292221] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   16.292230] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292238] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   16.292248] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292256] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   16.292265] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292273] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   16.292281] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292289] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   16.292298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292306] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   16.292315] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292323] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   16.292333] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292341] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   16.292350] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292358] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   16.292367] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292375] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   16.292384] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.292393] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   16.292402] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   16.425205] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.429447] Registered led device: rt2800pci-phy0::radio
[   16.429693] Registered led device: rt2800pci-phy0::assoc
[   16.429936] Registered led device: rt2800pci-phy0::quality
[   16.433617] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.509455] Bluetooth: RFCOMM TTY layer initialized
[   16.509471] Bluetooth: RFCOMM socket layer initialized
[   16.509478] Bluetooth: RFCOMM ver 1.11
[   16.815742] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.815872] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   16.815928] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.962050] hda_codec: ALC269VB: BIOS auto-probing.
[   16.997726] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.998532] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.047525] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.654382] ppdev: user-space parallel port driver
[   17.783367] audit_printk_skb: 15 callbacks suppressed
[   17.783377] type=1400 audit(1311879431.021:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1119 comm="apparmor_parser"
[   17.792556] type=1400 audit(1311879431.033:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1119 comm="apparmor_parser"
[   18.130557] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   18.267086] Intel AES-NI instructions are not detected.
[   18.291412] padlock_aes: VIA PadLock not detected.
[   18.474148] padlock_sha: VIA PadLock Hash Engine not detected.
[   19.318568] Adding 7811068k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:7811068k 
[   20.966352] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   83.461965] jme 0000:02:00.5: irq 41 for MSI/MSI-X
[   83.462319] jme 0000:02:00.5: eth0: Link is down
[   83.462794] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   84.103144] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.208118] usb 4-2: USB disconnect, address 2
[   86.208182] btusb_bulk_complete: hci0 urb f0867c00 failed to resubmit (19)
[   86.209190] btusb_intr_complete: hci0 urb f0867100 failed to resubmit (19)
[   86.209228] btusb_bulk_complete: hci0 urb f0867600 failed to resubmit (19)
[   86.209424] btusb_send_frame: hci0 urb efa40e80 submission failed
[  107.560152] usb 1-2: new high speed USB device using ehci_hcd and address 9
[  107.694634] hub 1-2:1.0: USB hub found
[  107.695040] hub 1-2:1.0: 4 ports detected
[  107.968438] usb 1-2.3: new full speed USB device using ehci_hcd and address 10
[  108.093424] cdc_acm 1-2.3:1.0: ttyACM0: USB ACM device
[  108.095622] usbcore: registered new interface driver cdc_acm
[  108.095632] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[  111.256573] usb 1-2.4: new high speed USB device using ehci_hcd and address 11
[  111.363627] scsi4 : usb-storage 1-2.4:1.0
[  111.366307] usb 1-2.4: USB disconnect, address 11
[  116.888575] usb 1-2.4: new high speed USB device using ehci_hcd and address 12
[  116.997962] scsi7 : usb-storage 1-2.4:1.2
[  117.001357] scsi8 : usb-storage 1-2.4:1.3
[  117.081630] usbcore: registered new interface driver usbserial
[  117.081707] USB Serial support registered for generic
[  117.084589] usbcore: registered new interface driver usbserial_generic
[  117.084599] usbserial: USB Serial Driver core
[  117.104363] USB Serial support registered for GSM modem (1-port)
[  117.106860] option 1-2.4:1.0: GSM modem (1-port) converter detected
[  117.107466] usb 1-2.4: GSM modem (1-port) converter now attached to ttyUSB0
[  117.107512] option 1-2.4:1.1: GSM modem (1-port) converter detected
[  117.108399] usb 1-2.4: GSM modem (1-port) converter now attached to ttyUSB1
[  117.110692] usbcore: registered new interface driver option
[  117.110701] option: v0.7.2:USB Driver for GSM modems
[  118.000762] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  118.005582] scsi 8:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  118.012603] sr1: scsi-1 drive
[  118.013252] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  118.013741] sr 7:0:0:0: Attached scsi generic sg3 type 5
[  118.017223] sd 8:0:0:0: Attached scsi generic sg4 type 0
[  118.025380] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[  149.588204] PPP BSD Compression module registered
[  149.610232] PPP Deflate Compression module registered

```my lusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 010: ID 1546:01a5 U-Blox AG 
Bus 001 Device 009: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 008: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 001 Device 007: ID 04e8:6034 Samsung Electronics Co., Ltd 
Bus 001 Device 006: ID 152e:2571 LG (HLDS) 
Bus 001 Device 005: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by romankarlfranz on 2011-08-04
I can not find the file 61-option-modem-modeswitch.rules in Ubuntu 11.04

---

### Post by romankarlfranz on 2011-08-04
just figured that the modem works also without modeswitch installed. maybe it will work now without disconnecting all the time?

---

