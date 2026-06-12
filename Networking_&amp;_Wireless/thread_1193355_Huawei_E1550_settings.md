---
title: "Huawei E1550 settings"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by farbird on 2009-06-21
[i] Problem solved, see page 2 for expert users,
for newbies, I will come out with a complete guide by today[/i]
searched entire web for a solution to run this usb 3g dongle

only thread which gave some answers was this

[http://translate.google.com.sg/translate?hl=en&sl=sv&u=http://ubuntu-se.org/phpBB3/viewtopic.php%3Ff%3D103%26p%3D323210&ei=m08-SsaBJZOVkAXEz5i_Dg&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3De1550%2B1446%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3D0CP](http://translate.google.com.sg/translate?hl=en&sl=sv&u=http://ubuntu-se.org/phpBB3/viewtopic.php%3Ff%3D103%26p%3D323210&ei=m08-SsaBJZOVkAXEz5i_Dg&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3De1550%2B1446%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3D0CP)

however, i only get ttyusb0 and ttyusb1

and after which, it didnt work as per shown in the above link..


i am in singapore and the telco is starhub.

wvdial fails with msg "modem not responding"
edited wvdial.conf and changed modem to /dev/ttyUSB0 and USB1 , no avail.

below is a snippet from my dmesg
[ 4135.320428] usb 1-3: configuration #1 chosen from 1 choice
[ 4135.349111] usbserial_generic 1-3:1.0: generic converter detected
[ 4135.349354] usb 1-3: generic converter now attached to ttyUSB0
[ 4135.349779] usbserial_generic 1-3:1.1: generic converter detected
[ 4135.349985] usb 1-3: generic converter now attached to ttyUSB1

---

### Post by farbird on 2009-06-21
throw me a bone anyone?

---

### Post by GeorgeVita on 2009-06-22
Hi **farbird**,
please do some basic tests and supply more info:

Boot without the modem, wait for the system to load, open a terminal window and try:```
ls /dev/ttyU*
```
attach the modem, wait 15 seconds, try:```
lsusb
```
and then again:```
ls /dev/ttyU*
```
The purpose of above is to check VendorID : ProdictID (from lsusb) and see which ports existed or created (ls /dev/ttyU*). If there are no /dev/ttyUSBx ports try:
```
sudo modprobe usbserial vendor=0x12d1 product=0x1446
```
Note: **product=0x1446 must be the same as in lsusb command**
Above command will try to create the serial communication ports.
Try again:```
ls /dev/ttyU*
```
Post here all output (copy & paste is better than typing). Be careful with the lower UPPER case of letters: **ttyUSB0** is not the same to **ttyusb0** (best is to show the full path: /dev/ttyUSB0)ttyUSB0

**Which Ubuntu version are you using?**

Regards,
George

---

### Post by farbird on 2009-06-22
using 9.04 with updated kernel .13 or 15 [ not the kernel that came which is .11 ]

.13/15 came with the usbserial module which was not possible to modprobe on the .11.

i did the modprobe usbserial with the vendor=0x12d1 product=0x1446.
but usb-storage/usb_storage must be rmmod 1st.

after which, my /dev/ appeared only 2 new tty which is
ttyUSB0 and ttyUSB1 respectively.

by right it should have ttyUSB2 appearring but it didnt.

wvdialconf resulted in "modem not found"
I manually edit wvconf.dial and inserted modem = /dev/ttyUSB0 and tried /dev/ttyUSB1 without any luck too.

btw lsusb showed the modem is present 12d1:1446

read much of the guides here.. and elsewhere.
e220 methods cannot be applied for this modem... [maybe ]

there was once i got it working [ ttyUSB0,1,2 appeared].
but that was mere luck when i booted same laptop with osx and rebooted into jaunty without removing the dongle..

modprobe usbserial vendor=*** product=*** wasnt necessary then..
didnt even had to do any modprobe...

rebooted into jaunty and the light on the dongle stayed on..

didnt manage to recreate the scenerio again...sadly.

now, i tried blacklisting usb-storage and usb_storage.
blacklisted option.

but usb_storage will autoload again everytime i unplug the e1550 dongle and plug in again.

also added in a rule 
 /usr/share/hal/fdi/preprobe/20thirdparty/10-huawei-e1550.fdi
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="usb.vendor_id" int="0x12d1">
      <match key="usb.product_id" int="0x1446">
        <merge key="info.ignore" type="bool">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

which cannot autorun.... ie everytime i reboot, i need to manually modprobe the usbserial with the vendor and product code to get the ttyusb0 and ttyusb1 in the /dev list.

but so far, no ttyusb2 except for the special scenario which appeared only 1x which made it work in jaunty...

---

### Post by farbird on 2009-06-22
last but not least..
without the usb dongle [e1550] plugged in, there are no instances of ttyUSB* in /dev

---

### Post by GeorgeVita on 2009-06-22
Hi again,
... more reading results to more tries but not always a good result! I am not sure I can help you instaed of giving ideas.

Most times a usb-storage needs to be ejected to turn the device to the modem state. This also can be done with appropriate setting and use of usb-modeswitch. In both ways the output of lsusb changes! At your link (your 1st post) they do not declare this so:
a. it is working as 12d1:1446 (with their kernel),
b. they used the usb-modeswitch but not make it clear (at their posts), or
c. the modem responds to something else (you can check it) and the usbserial must have other parameters!

To check the **lsusb** behaviour: try some **lsusb** after ejecting the drive.

First you have to make it connect and then make it automatic!

For your case, after seen the /dev/ttyUSB0,1 running **wvdialconf** the result was "modem not found"?
Did it tried the /dev/ttyUSB0 port?
Also as 9.04 does not have wvdial (and assosiated programs) did you added manually?

Regards,
George

**[COLOR="Blue"]EDIT: take a look at [http://www.santinoli.com/open/e1692-howto.html](http://www.santinoli.com/open/e1692-howto.html) for a similar modem[/COLOR]**

---

### Post by farbird on 2009-06-22
installed wvdial via synaptics.
i tried unmounting the drive, via gnome, but without doing a "sudo rmmod usb_storage", the /dev/ttyUSB01 and /dev/ttyUSB00, will not appear.

when it does appear [ ttyUSB01 and ttyUSB00 ], i tried to use either name in the wvdial.conf and still it shows the same , modem not found.

wvdialconf will search for the modem at both ttyUSB00 and ttyUSB01 but it will report modem not found.

can u elaborate usb_modeswitch?

i dun see it in synaptics..

read somewhere before about it, it will need to be built from tar.gz?

the process was lengthy if i can remember... 
why 9.04 didnt make it simpler?

---

### Post by GeorgeVita on 2009-06-22
Hi, I never used usb-modeswitch! With my ZTE MF636 I was lucky as it changed to modem state with an AT command. I do not know the equivalent for Huawei.

Following your post, drives to [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) where is stated that > ...a Debian (Xandros/Ubuntu) package should be available soon at the Debian Repository...
When? I do not know. Till then we must search for a simpler method (like AT commands) or ... follow the "build" info.

If you will try the "build" way and find problems I could try it in parallel with you and find the way...

Keep in mind not to mess up various kernels and 'file trimming'! You can always check basic thinks running a LiveCD.

An idea for a test is: Boot without the modem, after full system load attach it and from terminal: **dmesg**

Look at the lines regarding 'usb-storage' to find the name, something like '**sd 6:0:0:0: [[COLOR="Red"]sdb[/COLOR]] Attached SCSI removable disk**'. Then from terminal **eject [COLOR="Red"]sdb[/COLOR]** (place your name). Finally check if **lsusb** gives you new numbers.

Good luck!
George

---

### Post by farbird on 2009-06-22
[http://www.santinoli.com/open/e1692-howto.html](http://www.santinoli.com/open/e1692-howto.html)

modinfo option

doesnt list my usb modem as selected.

ie 12D1:1441

sigh..
module option support up to only 143*

---

### Post by GeorgeVita on 2009-06-22
After usb_modeswitch the modem is 0x12d1 : 0x140c

> Eventually, I got it working on a Ubuntu system running a **2.6.28.5** kernel, but the instructions that follows are general enough to fit many different setups. 

You can check yours with: **uname -a**

For Ubuntu 9.04 the standard is 2.6.28-13-generic #44

Of course we are not sure if after all these will work, as he uses E1692 and not E1550!

---

### Post by farbird on 2009-06-22
i managed to recreate the scenerio..

i have to boot to osx... eject the drive while in osx and reboot to ubuntu..

the lsusb changed it to 12d1:1001

from there i am able to get ttyusb00,01,02,03,04.

while in jaunty, i tried replugging the e1550 and after that ejecting it via the gnome gui..

lsusb doesnt change.... still stuck 12d1:1446.

i guess i will have to wait for next kernel implementation..

they shd automate it in the next release... 9.10 perhaps?

---

### Post by GeorgeVita on 2009-06-22
Did you tried and cannot eject it from terminal?

> An idea for a test is: Boot without the modem, after full system load attach it and from terminal: dmesg

Look at the lines regarding 'usb-storage' to find the name, something like 'sd 6:0:0:0: [sdb] Attached SCSI removable disk'. Then from terminal eject sdb (place your name). Finally check if lsusb gives you new numbers.

---

### Post by farbird on 2009-06-22
havent tried at terminal yet.

will be reinstalling 9.04 with ext4.. previously on 8.10 upgraded to 9.04 with ext3.

---

### Post by gabrielqs on 2009-06-23
Hello Farbird.

I have just bought one Huawei E1550 modem and I'm having the same issue as you are.

This modem is being sold by danish TDC operator, and I'm also not able to get the /dev/ttyUSB2 to show up.

Will be trying here, pls let me know if you find anything out.

Regards,
Gabriel

---

### Post by farbird on 2009-06-23
will be considering doing the usbmodeswitch thingy later.

post my results soon.

---

### Post by gabrielqs on 2009-06-23
I have tried that also, no luck. Couldn't find the right message to send to the modem anywhere, and no usbsniffer available here... The product id never got changed with usb_modeswitch.

---

### Post by farbird on 2009-06-23
gab, which guide did u use for the usbmodeswitch?

care to share the url?

---

### Post by gabrielqs on 2009-06-23
Hi,

I've used [this one]("http://www.santinoli.com/open/e1692-howto.html"), it was listed here earlier in this post. I've had installed usb_modeswitch before, compiling it from source.

Cheers,
Gabriel

---

### Post by farbird on 2009-06-24
used the guide.... i think it cannot handle..

---

### Post by farbird on 2009-06-25
managed to get it working..
via the example case in [draisberghof.de modeswitch]("http://www.draisberghof.de/usb_modeswitch/") page.


and the [example here]("http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html").

u need to use a windows tool and run inside xp. sniffusb

follow his guide wisely..
u need to input the messageEndpoint and messagecontent in your /etc/usb_modeswitch.conf

here is mine, not sure if its the same as yours

```

#content of /etc/usb_modeswitch.conf
DefaultVendor = 0x12d1
DefaultProduct = 0x1446
MessageEndPoint = "0x01"
MessageContent = "55534243000000000000000000000011060000000000000000000000000000"

```

once you'd gotten the above settings via the log file of usbsnoop [ make sure u check the box for non-present hardware and install the filter for 12d1:1446 ], boot to linux, save your version of the /etc/usb_modeswitch.conf and run
"sudo usb_modeswitch"

it shd allow the switch to be done..
"lsusb" and u have your 12d1:1446 gone and replaced by 12d1:1001 [for my case ]


enjoy..

thanks to ubuntu forum and every site and everyone whom are listed in this thread

---

### Post by farbird on 2009-06-25
btw, this is posted in ubuntu using my e1550..

rebooting again to test if it works later.

---

### Post by farbird on 2009-06-25
cool... it works after reboot and I do not have to blacklist usb-storage and I do not have to modprobe usbserial at all.

all that is needed now is
sudo usb_modeswitch

i feel proud of myself!

---

### Post by farbird on 2009-06-27
use this thread to ask me questions if u need help with the e1550 or usb_modeswitch.

I will try to come out with a step by step guide by today..

---

### Post by farbird on 2009-06-29
how to install huawei e1550 in ubuntu jaunty 9.04..

Downloaded the [modeswitch]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.2.tar.bz2") file into your desktop

run "terminal"
"cd ~/Desktop"
"sudo mv usb_modeswitch-1.0.2.tar.bz2 /usr/src"
"cd /usr/src"
"sudo tar -xvf usb_modeswitch-1.0.2.tar.bz2"
"cd usb_modeswitch-1.0.2.tar.bz2"
"sudo make clean"
"sudo make install"

that will get usbmodeswitch installed.

next boot into windows
download the [sniffusb exe]("http://www.pcausa.com/Utilities/UsbSnoop/SniffUSB-x86-2.0.0006.zip")

install in xp.
run the sniffusb.
plug in your 12d1:1446 stick

now in the sniffusb screen, click on the "list device not present"
you shd see 3-4 devices with the id 12d1:1446

select them all and click on "install" under "filter control" on rightside.

u shd see in the main top window that the 3-4 devices with 12d1:1446 have the "filter installed" beside their id.

now, unplug the huawei usb and plug it back in after 5seconds.
if u do that, u shd see the log file size increased.

now view the log and save the logfile into a thumbdrive.

now we restart XP and boot into ubuntu. remove the stick before ubuntu starts booting.

once ubuntu starts. plug in the thumb drive, copy the log file into your desktop.

then run terminal

"cd ~/Desktop"
"sudo gedit snifflog.log"   or whatever filename u saved before

once gedit opens up on the gnome desktop, look for this by Control-F
"TransferBufferMDL"

there should be about 8 instances of it within the log file.
the one critical is the one that appears 4 rows after the line
```
PipeHandle           = 88bced1c [**endpoint 0x00000005**]
  TransferFlags        = 00000000 (USBD_TRANSFER_DIRECTION_**OUT**, ~USBD_SHORT_TRANSFER_OK)"
```

important here is the "out".
And there must be 2 long row of numbers below the transfermdl line which looks like this
```

   00000000: 55 53 42 43 90 4e d6 8a 24 00 00 00 80 00 08 ff
   00000010: 02 44 45 56 43 48 47 00 00 00 00 00 00 00 00

```
ignore the numbers before the colon and delete the spaces between the hex numbers. Join the 2 lines up so that it shows
```
55534243904ed68a24000000800008ff024445564348470000000000000000
``` 

* take note, this is just an example*

you will also need the "pipehandle" output which will show the endpoint hex, in this example, its **endpoint 0x00000005**.

now with these details, you can then create a usbmodeswitch config file

open another terminal
"sudo gedit /etc/usb_modeswitch.conf"
clear away all the contents of this file. 
put in these lines instead
```

DefaultVendor = 0x12d1
DefaultProduct = 0x1446

MessageEndpoint = 0x05
MessageContent = "55534243904ed68a24000000800008ff024445564348470000000000000000"

```

*make sure you use your own endpoint and messengecontent here n not directly clone the example above.*

now save the file in gedit.

next plug in the huawei usb stick, run terminal

"sudo usb_modeswitch"

u shd then be able to connect after u configure the network settings of your isp [ ie 3g access point name etc ]

there is also a way to automate it.

run terminal again
"sudo gedit /etc/udev/rules.d/45-huawei1660.rules"

gedit shd open an empty file
paste this code into it
```

SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"
```

since your vendor and product id is sames mine, u can clone the code above directly.
However, if u are following this guide to get your own huawei device, not 12d1:1446, working, u shd input the original vendor,product id [ ie the one shown in lsusb before switching]

enjoy

This works for me in Singapore using Starhub.

---

### Post by Macchi on 2009-07-15
I have a simpler workaround for the Huawei E1550 in three steps, using software from standard repositories and the network manager.

This uses udev-extras and modem-modeswitch (that is similar but NOT the same as usb-modeswitch!) 

Check here: [http://ubuntuforums.org/showpost.php?p=7622263&postcount=3](http://ubuntuforums.org/showpost.php?p=7622263&postcount=3)

---

### Post by iksu on 2009-08-08
Huawei E1550 mobile broadband modem on 3 (three) network in the UK works using this method (for the sake of googlers!)

Within seconds of running usb_modeswitch as described by farbird, Ubuntu brought up the mobile broadband wizard automatically and all i had to do was to choose the service provider. Thanks a lot guys for making this work.

Note, some of the posts mentioned adding target vendor and product ids to the usb_modeswitch.conf file. This is not mandatory and at least in my case made usb_modeswitch think that the switching had failed (although it had been successful).

---

### Post by bobby_d on 2009-08-10
Even with Macchi's method, I had some problems with finding the correct serial port to use with wvdial - the procedure that worked for me is listed here:

Bug 591047 - Huawei E1550 3G USB modem (HSDPA USB Stick) cannot connect (NetworkManager)
[http://bugzilla.gnome.org/show_bug.cgi?id=591047](http://bugzilla.gnome.org/show_bug.cgi?id=591047)

---

### Post by seuzo on 2009-09-07
> **Macchi said:**
> I have a simpler workaround for the Huawei E1550 in three steps, using software from standard repositories and the network manager.

This uses udev-extras and modem-modeswitch (that is similar but NOT the same as usb-modeswitch!) 

Check here: [http://ubuntuforums.org/showpost.php?p=7622263&postcount=3](http://ubuntuforums.org/showpost.php?p=7622263&postcount=3)

Hi,

wow nice i just type two command and it works! thanx.

---

### Post by jacobdongon on 2009-09-22
Honestly, i am not as tech savvy as the other people here, but I noticed when I reinstalled Ubuntu in my computer out of desperation I found out that Ubuntu recognized my modem (Huawei e1550) provided by sun cellular here in the Philippines. I hate windows and my computer crashes a lot so I always have a back up and I use Ubuntu ever since then. I just noticed when Ubuntu starts to go online it pops a window called "Update Manager", the first batch was of updates was ok it didn't affect the modem whatsoever even after rebooting it several times, then after 5 hours, a new update came in and I downloaded it, right after rebooting the modem stopped working. Thought it was over but if you try to check the grub loader, everytime the system gets updated the older version stays at the bottom of the list, tried loading that and my modem still works. 

If you want to try and reformat your computer and plug the modem while the system is installing, Ubuntu will automatically recognizes it. It worked for me with no problems though I'm not sure if it works with the downloaded version. 

My Ubuntu was mailed to me by Linux and the version is:

Kernel Linux 2.6.28-11-generic it upgraded to -15 that didn't work.

---

### Post by chkhurum on 2009-09-23
> **Macchi said:**
> I have a simpler workaround for the Huawei E1550 in three steps, using software from standard repositories and the network manager.

This uses udev-extras and modem-modeswitch (that is similar but NOT the same as usb-modeswitch!) 

Check here: [http://ubuntuforums.org/showpost.php?p=7622263&postcount=3](http://ubuntuforums.org/showpost.php?p=7622263&postcount=3)


Note: This method does not work on Ubuntu 8.0.4

---

### Post by joehill on 2009-09-29
Thanks Farbird, I tried following those steps and strange things happen (none of them what I want).

After sniffing for the message using a Windows machine, I inserted the Huawei an ran usb_modeswitch, and it says it successfully found the driver (usb-storage) and is communicating with the device. But it never shows up as a network device. The strange thing is that if I put the *wrong* info in the message area of the .conf file (change one of the 0s to 1 or something) it appears to work, setting up my broadband connection, asking me who my provider is, etc., but then if I click on the connection it looks like it's searching for a split-second then stops. So I'm not sure what to do now.

Does anyone have any suggestions? Thanks!

Joe

---

### Post by savinda on 2009-10-04
> **iksu said:**
> Huawei E1550 mobile broadband modem on 3 (three) network in the UK works using this method (for the sake of googlers!)

Within seconds of running usb_modeswitch as described by farbird, Ubuntu brought up the mobile broadband wizard automatically and all i had to do was to choose the service provider. Thanks a lot guys for making this work.

Note, some of the posts mentioned adding target vendor and product ids to the usb_modeswitch.conf file. This is not mandatory and at least in my case made usb_modeswitch think that the switching had failed (although it had been successful).

it works for me i follow the same procedure and i could  make it work for E1550 mobile broadband. Thanks a lot guys for making this work.(it works for sri lanka)

---

### Post by ibaihaqi on 2009-10-04
> **savinda said:**
> it works for me i follow the same procedure and i could  make it work for E1550 mobile broadband. Thanks a lot guys for making this work.(it works for sri lanka)

thank you also for the help, but after I "sudo usb_modeswitch", the terminal shows it's okay to read the device, but then it show error something like "cannot find driver", Im sorry I cannot remember the exact message, I use my office comp right now, my Ubuntu is in my home.

FYI, I use Ubuntu Hardy Heron, the modem is exactly the same (12d1:1446)

Please help me, Im new in Ubuntu, I was try to update to Interpid and then Jaunty but my internet connection (in office is too slow for download the update). Am I need to exchange my modem to the store? the store said give me two days for exchange the modem.

regards,
Imam Baihaqi

---

### Post by farbird on 2009-10-05
thanks for trying my method and congrats on your successful tries.

u might wanna check out another thread which provides a much simpler way

see  macchi post here

[http://ubuntuforums.org/showpost.php?p=7622263&postcount=3](http://ubuntuforums.org/showpost.php?p=7622263&postcount=3)

---

### Post by joehill on 2009-10-06
Ok I got mine working now. Thanks for the advice everyone. It's working now. It looks like at first the company had simply taken a really long time to activate my account. In any case, I still have to use a random, non-sniffed message in the usb-modeswitch.conf file because the one I got through usb sniffing always makes the device not show up. So I just change some numbers and it works. I can't really explain it but at least it's working now.

---

### Post by 2912pwil on 2009-11-14
Really really weird....

Had gotten the E1550 working - out-of-the-box- in Windoze,,, just plugged it in & off I went.. Couldn't get her going in 9.04... hmmmnnnn...

Went re-reading everything, found this thread (thanks all..) was just re-booting to Ubuntu, up comes 9.04 & she works straight off!!! No, I've no idea why either, I'm d***ed sure I changed nothing but... 

Couple of notes (for anyone else looking...) I use the "3" network in UK.  One difference I did notice (but hadn't yet changed) was that the "number" was set as *99# in ubuntu & *99***1# in Windoze... dunno if that is significant...

Cheers!

2912pwil

---

### Post by olalaaa on 2009-11-17
> **ibaihaqi said:**
> thank you also for the help, but after I "sudo usb_modeswitch", the terminal shows it's okay to read the device, but then it show error something like "cannot find driver", Im sorry I cannot remember the exact message, I use my office comp right now, my Ubuntu is in my home.

FYI, I use Ubuntu Hardy Heron, the modem is exactly the same (12d1:1446)

Please help me, Im new in Ubuntu, I was try to update to Interpid and then Jaunty but my internet connection (in office is too slow for download the update). Am I need to exchange my modem to the store? the store said give me two days for exchange the modem.

regards,
Imam Baihaqi
For Hardy Heron, you could use the steps shown in the link from my signature. Of course, you need to replace my device ID with your own ID ( 12d1:1446 ) . I have another modem than yours.

Please note : there are only the steps NOT the commands that you need ( because each modem has own strings to be used - you can see them if you use usb_modeswitch in the .conf file for your own modem!! )

---

### Post by dcameron on 2009-11-24
The udev-extras package is not available in 8.10 so I have to use the usb_modeswitch method. The latest version (1.0.5) has the settings for the e1550 already in the conf file so you don't have to do any sniffing, just uncomment the settings there. However this modem is not included in the list for fully automatic use, so run make install rather than make integrated_install. After putting into the network manager the settings my provider (Zain Ghana) gave me, plugging the modem in and running usb_modeswitch, it all worked perfectly!

---

### Post by m3asmi on 2009-12-20
[SIZE=4]Hi..
I have a modem huawai E1550 but I can not connect with him
He launched this as a normal usb![/SIZE]

[SIZE=4]**$>*lsusb***[/SIZE]
     ```

Bus 001 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 163f:1611  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```[SIZE=4]and I added to* /etc/usb_modeswitch.conf*[/SIZE]
      ```

# Huawei E1550
#
# Contributor: Anders Blomdell, Ahmed Soliman

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1446

;TargetVendor=   0x12d1
;TargetProduct=  0x1001

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="55534243123456780000000000000011060000000000000000000000000000" 
```[SIZE=4]
but it's not work Oncore !!...[/SIZE] :sad:

---

### Post by fred nemo on 2009-12-20
This is how I made my Huawei E1550 dongle work for 3 UK (three.co.uk) on Ubuntu 8.04.1 (Hardy Heron) on a Asus EeePC 901..

I put together info collected [here]("http://blogger.ziesemer.com/2008/10/alltel-um175al-usb-evdo-ubuntu.html"), [here]("https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/424050") and [here]("http://www.draisberghof.de/usb_modeswitch/").

Here is my distilled summary:


**1**. Install **usb_modeswitch** if not installed: 
**sudo apt-get install usb-modeswitch**


**2**. Backup your **/etc/usb_modeswitch.conf** file and replace it with the one below:
 
------------------ start of /etc/usb_modeswitch.conf  -------------------------
   DefaultVendor= 0x12d1
DefaultProduct= 0x1446

TargetVendor = 0x12d1
TargetProduct= 0x1001

MessageContent="55534243000000000000000000000011060000000000000000000000000000"
MessageEndpoint=0x01
CheckSuccess=5
  ------------------ end of /etc/usb_modeswitch.conf  --------------------------


**3**. Install **wvdial** (if not already installed).


**4.** Backup your** /etc/wvdial.conf** file and replace it with the one below:

------------------ start of /etc/wvdial.conf  -------------------------
   [Dialer Defaults]
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 Modem Type = USB Modem
 Baud = 460800
 New PPPD = yes
 Modem = /dev/ttyUSB0
 ISDN = 0
 Phone = *99#
 Password = three
 Username = three
 stupid mode = 1
   ------------------ end of /etc/wvdial.conf   -------------------------


**5.** You may want to change the **Phone** number and **Password/Username** fields above in case you are using other operators in other countries; this works for 3 in the UK.
You may also want to change the **Modem** device (mine appears on /dev/tty/USB0), but try this first.


**6.** Insert your Huawei USB dongle and wait until you see it in the list shown by the **lsusb** command in a terminal (or, alternatively, just wait for a few seconds).


**7.** From a terminal execute:
     **sudo usb_modeswitch**
 

**8.** Wait for a few seconds, then execute:
**    sudo wvdial **


**9.** Wait a few seconds to get connected and then... start surfing the net  :)


**10.** To disconnect just do **Ctrl-C** in the terminal where you started wvdial.


More recent versions of Ubuntu should recognize this dongle automatically (not sure, though) and tools like kppp should make the whole setup more user friendly, but I've found that the "brutal" approach above works for me, so I didn't investigate any further.

You may want to integrate /etc/usb_modeswitch.conf and /etc/vdial.conf with the data above instead of replacing the files: I didn't try, so that is up to you.

You can use **dmesg** to see what's going on behind the scenes in case of problems.

---

### Post by 2912pwil on 2009-12-22
Thanks Fred Nemo...

Your advice worked for me with 9.10 on a Dell 1525... also UK, also "3" network (PAYG if that matters).  Much obliged....

However (albeit it worked ..) after your Step 7 above,.. I got...
> phillip@phillip-laptop:~$ sudo usb_modeswitch

[sudo] password for phillip: 



 * usb_modeswitch: tool for controlling "flip flop" mode USB devices

 * Version 1.0.2 (C) Josua Dietze 2009

 * Works with libusb 0.1.12 and probably other versions



Error: MessageContent hex string has uneven length. Aborting.



phillip@phillip-laptop:~$
(Just documenting it for anyone else...)

Cheers!


2912pwil

---

### Post by pdc on 2009-12-22
not sure if the version number alone could be the issue, 

but usb_modeswitch is now at 1.0.6 and the latest versions seem to offer a more automated installation and run

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by olalaaa on 2009-12-23
> **m3asmi said:**
> [SIZE=4]Hi..
I have a modem huawai E1550 but I can not connect with him
He launched this as a normal usb![/SIZE]

[SIZE=4]**$>*lsusb***[/SIZE]
     ```

Bus 001 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 163f:1611  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```[SIZE=4]and I added to* /etc/usb_modeswitch.conf*[/SIZE]
      ```

# Huawei E1550
#
# Contributor: Anders Blomdell, Ahmed Soliman

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1446

;TargetVendor=   0x12d1
;TargetProduct=  0x1001

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="55534243123456780000000000000011060000000000000000000000000000" 
```[SIZE=4]
but it's not work Oncore !!...[/SIZE] :sad:
it's not OK what you did.

You must remove the sign ; before the lines of text above. If a string has before it a # or a ; then it is seen as "comment", not as a line of source code.

Therefore, you must use the code below instead.

```


# Huawei E1550
#
# Contributor: Anders Blomdell, Ahmed Soliman

DefaultVendor=  0x12d1
DefaultProduct= 0x1446

TargetVendor=   0x12d1
TargetProduct=  0x1001

# only for reference and 0.x versions
  MessageEndpoint=0x01

MessageContent="55534243123456780000000000000011060000000000000000000000000000" 


```I hope that it works now for you.

Success !

---

### Post by linuxonbute on 2010-05-15
I followed the OP's instructions but it didn't work for me.
I ran the Windows software which is on the device and monitored
/var/log/messages.
I added the last line as shown here :

DefaultVendor = 0x12d1
;DefaultProduct = 0x101
DefaultProduct = 0x1446
MessageEndpoint = 0x01
MessageContent = "55534243000000000000000000000011060000000000000000000000000000"
HuaweiMode=1


and now it works.

---

### Post by seuzo on 2010-05-22
This setting is for 10.4 LTS? before upgrade to 10.4 LTS. My Moblie boardband stick is working fine for 9.4 and 9.10.

During 9.4 i do some changes to enable the stick to work but i can't remember what i did areadly.

Does it link to something wrong with my setting since is 10.4 LTS?

i understand the network manager applet 0.8 is quite power.i use it to get the setting for moblie boardband. and no connection still.. 

i using starhub from singapore.
not sure what to do next.
i found this thread from the search. thank you.


> **linuxonbute said:**
> I followed the OP's instructions but it didn't work for me.
I ran the Windows software which is on the device and monitored
/var/log/messages.
I added the last line as shown here :

DefaultVendor = 0x12d1
;DefaultProduct = 0x101
DefaultProduct = 0x1446
MessageEndpoint = 0x01
MessageContent = "55534243000000000000000000000011060000000000000000000000000000"
HuaweiMode=1


and now it works.

---

### Post by desmondfoo on 2010-06-06
Hi Seuzo, 

i managed to get my huawei E1550 to work by using [Macchi]("http://ubuntuforums.org/member.php?u=70700")'s method (just step 2 and 3).  I am running ubuntu 10.04. 

Only plug in the stick after you had finished step 2 and 3.  

Cheers. 

> **seuzo said:**
> This setting is for 10.4 LTS? before upgrade to 10.4 LTS. My Moblie boardband stick is working fine for 9.4 and 9.10.

During 9.4 i do some changes to enable the stick to work but i can't remember what i did areadly.

Does it link to something wrong with my setting since is 10.4 LTS?

i understand the network manager applet 0.8 is quite power.i use it to get the setting for moblie boardband. and no connection still.. 

i using starhub from singapore.
not sure what to do next.
i found this thread from the search. thank you.

---

### Post by kyke on 2010-10-01
In 10.04.1 LTS I only had to install usb-modeswitch package (version 1.1.0-2), plug it and it worked just fine with Network-Manager. Cheers.

---

### Post by Computerfrek on 2011-03-14
Hi, i am also in Singapore using my new Starhub Mobile Broadband Modem(FYI, i am also using the Huawei E1550 modem). But i encountered some problems when following your steps, please advise.

Problem 1, i got and error message after trying to "make install" at the first part:
This is the error message:

gcc -o usb_modeswitch usb_modeswitch.c -Wall -l usb 
usb_modeswitch.c:57: fatal error: usb.h: No such file or directory
compilation terminated.
make: *** [usb_modeswitch] Error 1

and also i suppose u have a type over at the beginning where you said to cd into the tar file? You meant to cd to the extracted dir? (Correct me if i am wrong) I am quite new into linux esp the hardware part. 

Problem 2, i do not have WinXP in my system :P i wipe my whole hdd and left with ubuntu 10.10 and its swap only :P 

Thinking of using VM but on a second thought, if i using VM i would require the host machine to be able to recognise the USB modem in the first place. Can i try using another PC with XP/7 installed? What you are guiding us to do is to collect information for the modem using WinXP right?

Please advise!!! 

> **farbird said:**
> how to install huawei e1550 in ubuntu jaunty 9.04..

Downloaded the [modeswitch]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.2.tar.bz2") file into your desktop

run "terminal"
"cd ~/Desktop"
"sudo mv usb_modeswitch-1.0.2.tar.bz2 /usr/src"
"cd /usr/src"
"sudo tar -xvf usb_modeswitch-1.0.2.tar.bz2"
"cd usb_modeswitch-1.0.2.tar.bz2"
"sudo make clean"
"sudo make install"

that will get usbmodeswitch installed.

next boot into windows
download the [sniffusb exe]("http://www.pcausa.com/Utilities/UsbSnoop/SniffUSB-x86-2.0.0006.zip")

install in xp.
run the sniffusb.
plug in your 12d1:1446 stick

now in the sniffusb screen, click on the "list device not present"
you shd see 3-4 devices with the id 12d1:1446

select them all and click on "install" under "filter control" on rightside.

u shd see in the main top window that the 3-4 devices with 12d1:1446 have the "filter installed" beside their id.

now, unplug the huawei usb and plug it back in after 5seconds.
if u do that, u shd see the log file size increased.

now view the log and save the logfile into a thumbdrive.

now we restart XP and boot into ubuntu. remove the stick before ubuntu starts booting.

once ubuntu starts. plug in the thumb drive, copy the log file into your desktop.

then run terminal

"cd ~/Desktop"
"sudo gedit snifflog.log"   or whatever filename u saved before

once gedit opens up on the gnome desktop, look for this by Control-F
"TransferBufferMDL"

there should be about 8 instances of it within the log file.
the one critical is the one that appears 4 rows after the line
```
PipeHandle           = 88bced1c [**endpoint 0x00000005**]
  TransferFlags        = 00000000 (USBD_TRANSFER_DIRECTION_**OUT**, ~USBD_SHORT_TRANSFER_OK)"
```important here is the "out".
And there must be 2 long row of numbers below the transfermdl line which looks like this
```

   00000000: 55 53 42 43 90 4e d6 8a 24 00 00 00 80 00 08 ff
   00000010: 02 44 45 56 43 48 47 00 00 00 00 00 00 00 00

```ignore the numbers before the colon and delete the spaces between the hex numbers. Join the 2 lines up so that it shows
```
55534243904ed68a24000000800008ff024445564348470000000000000000
```* take note, this is just an example*

you will also need the "pipehandle" output which will show the endpoint hex, in this example, its **endpoint 0x00000005**.

now with these details, you can then create a usbmodeswitch config file

open another terminal
"sudo gedit /etc/usb_modeswitch.conf"
clear away all the contents of this file. 
put in these lines instead
```

DefaultVendor = 0x12d1
DefaultProduct = 0x1446

MessageEndpoint = 0x05
MessageContent = "55534243904ed68a24000000800008ff024445564348470000000000000000"

```*make sure you use your own endpoint and messengecontent here n not directly clone the example above.*

now save the file in gedit.

next plug in the huawei usb stick, run terminal

"sudo usb_modeswitch"

u shd then be able to connect after u configure the network settings of your isp [ ie 3g access point name etc ]

there is also a way to automate it.

run terminal again
"sudo gedit /etc/udev/rules.d/45-huawei1660.rules"

gedit shd open an empty file
paste this code into it
```

SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"
```since your vendor and product id is sames mine, u can clone the code above directly.
However, if u are following this guide to get your own huawei device, not 12d1:1446, working, u shd input the original vendor,product id [ ie the one shown in lsusb before switching]

enjoy

This works for me in Singapore using Starhub.

---

### Post by Lylex11 on 2011-05-31
I seem to have a similar problem. Following fresh install of 11.04 I had the Huawei modem working fine for me using QB carrier in Cambodia. I changed to Mobitel and now the modem will not connect. It seems stuck perpetually searching for a signal. I know there is a signal because I can connect using my mobile phone using usb connection.

The modem has two led colours: green for 2g and blue for 3g. Using the Mobitel sim card I only get a flashing green light. QB gets a blue light but no longer connects.

I changed /etc/usb_modeswitch.conf as per instructions and no change in behaviour.

Macchi's "3 step" approach also did not change the situation (udev-extras not found)

Am using 11.04

Unrelated, after the carrier switch I can no longer connect to internet with mobile phone via bluetooth. My wife's computer Asus EeePC 10.04 connects via bluetooth mobile phone fine.

---

