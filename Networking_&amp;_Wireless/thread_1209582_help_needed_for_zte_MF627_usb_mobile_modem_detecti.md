---
title: "help needed for zte MF627 usb mobile modem detection an operation"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by sxcmandan on 2009-07-10
I have an acer aspire one netbook. I have a zte MF627 usb modem. My operating system is Ubuntu Netbook Remix. I need to connect to the 3 mobile network when out and about. When i insert the usb modem nothing happens. I am aware of many threads on how to install 'usb_modeswitch'. My problem is that nothing happens when i plug the modem in...
PLEASE HELP ME with a simple, non explanation bullet pointed list on what to do!

---

### Post by GeorgeVita on 2009-07-12
Hi **sxcmandan**,
at first you must do a full update of your system (you must have an internet connection other than mobile broadband). Then you can follow instructions of the 1st post of:
[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

If you have no other internet connection on your Ubuntu running PC, try the following:

- Boot with the modem attached
- Wait up to 1 minute for the 'connection wizard' to start, if not try a manual setup: System > Preferences > Network Connections > Mobile Broadband > Add > select country and your provider
- Try to connect (from Network Manager icon)
- If cannot connect (or cannot do something above) open a terminal window
- Try the following commands (copy or type them exactly):
```
lsusb
``````
ls /dev/ttyU*
``````
dmesg | grep usb
``````
uname -a
```
- Post here the responds to follow up

Regards,
George

---

### Post by sxcmandan on 2009-07-12
Thank you very much! Its now working fine. Followed instructions on the link and aok.
Now i dont have to revert back to windows xp which was rather laggy on my netbook. :)

---

### Post by utonto on 2009-08-25
hi i need help
i do not want to come back and install windows on my netbook because of this stupid internet modem by zte

i have an aspire one 110 with linux4one distro which is based on ubuntu. i have tried my zte mf627 on a windows xp pc and works fine.
instead on my linux4one netbook it does not work.

i think it is because of a pin number required.
in fact when i use the mf627 on windows xp it lights up with a red light. after that the software made for windows xp asks me for the pin number of my simcard. only after i provide it with my sim pin number the light of my mf627 becomes green.

when i have tried to use it on linux the first time, right after i put my mf627 in a usb port, used to appear a the page with the autorun files for windows such as autorun.exe. 
then i tried the things suggested in this [guide]("http://ubuntuforums.org/showthread.php?t=1017630") and now when i insert the mf627 the page with the autorun.exe doesn't show up anymore.
instead the red light on the usb stick goes away and then comes back but it is always red.
i think that the problem is that in this way there is no way to insert the pin number and so the light does not turn green.
thanks for anybody's help and excuse me for my poor english.

p.s. i have done the things suggested above by georgevita and the results are shown here:
> larry@larry-laptop:~$ 1susb
bash: 1susb: command not found
larry@larry-laptop:~$ ls /dev/ttyU*
ls: impossibile accedere a /dev/ttyU*: Nessun file o directory
larry@larry-laptop:~$ dmesg | grep usb
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
usb usb1: configuration #1 chosen from 1 choice
usb usb2: configuration #1 chosen from 1 choice
usb usb3: configuration #1 chosen from 1 choice
usb usb4: configuration #1 chosen from 1 choice
usb usb5: configuration #1 chosen from 1 choice
usb 5-2: new high speed USB device using ehci_hcd and address 3
usb 5-2: configuration #1 chosen from 1 choice
usbcore: registered new interface driver usb-storage
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usb 5-5: new high speed USB device using ehci_hcd and address 4
usb 5-5: configuration #1 chosen from 1 choice
usb 1-1: new low speed USB device using uhci_hcd and address 2
usb 1-1: configuration #1 chosen from 1 choice
usbcore: registered new interface driver hiddev
input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input6
generic-usb 0003:0461:4D17.0001: input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
usbcore: registered new interface driver usbhid
usbhid: v2.6:USB HID core driver
input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/input/input7
usbcore: registered new interface driver uvcvideo
usb-storage: device scan complete
larry@larry-laptop:~$ uname -a
Linux larry-laptop 2.6.29.1v1aspireeepc #1 SMP PREEMPT Thu Apr 16 00:04:30 CEST 2009 i686 GNU/Linux
larry@larry-laptop:~$ 


---

### Post by GeorgeVita on 2009-08-25
Hi **utonto**,
prego (!) try one more time:

- boot without modem
- wait for the system to fully load
- attach modem
- wait 10 sec
- open a terminal window and try ```
lsusb
```
(below is lsusb and not 1susb you tried, first letter is small 'L')

Regards,
George

---

### Post by utonto on 2009-08-25
here is the result
> larry@larry-laptop:~$ lsusb
Bus 005 Device 008: ID 19d2:0064  
Bus 005 Device 004: ID 064e:d101 Suyin Corp. 
Bus 005 Device 001: ID 1d6b:0002  
Bus 004 Device 001: ID 1d6b:0001  
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0001  
Bus 001 Device 002: ID 0461:4d17 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0001  
larry@larry-laptop:~$ 


---

### Post by GeorgeVita on 2009-08-25
Ok, so your modem is identified as```
Bus 005 Device 008: ID 19d2:0064 
``` which is a little bit strange or new.

As the link you mentioned has a lot of solutions, show me which actions you followed.

If you want to change HAL info file (and nothing else) try the following:
```
gksudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```Search (CTRL-F) for **19d2**, go some lines below and change ```
<match key="@info.parent:usb.product_id" int="0x0002">
```**TO**```
<match key="@info.parent:usb.product_id" int="0x0064">
```SAVE, REBOOT and test.
If this did not work, try also changing nest line **FROM** ```
<match key="@info.parent:usb.interface.number" int="2">
```**TO**```
<match key="@info.parent:usb.interface.number" int="3">
```SAVE, REBOOT and test again.

Regards,
George

---

### Post by utonto on 2009-08-25
the suggenstions changed nothing

i attach here part of the file you suggested to edit since it could help you i think
> match key="@info.parent:usb.vendor_id" int="0x19d2">
        <!-- Qualcomm: Telstra/NextG CDMA , ZTE CDMA Tech -->
        <match key="@info.parent:usb.product_id" int_outof="0x0001;0xfffe">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
        <!-- ZTE MF626 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x2000">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
        <!-- ZTE MF628 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0015">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
        <!-- ONDA MF632 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0064">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
      </match>

      <!-- Bandrich C100 1/2 -->
      <match key="@info.parent:usb.vendor_id" int="0x1a8d">
        <match key="@info.parent:usb.product_id" int_outof="0x1002;0x1003">
          <match key="@info.parent:usb.in

---

### Post by GeorgeVita on 2009-08-25
I am not sure if your kernel will accept it, but try:
```
sudo modprobe usbserial vendor=0x19d2 product=0x0064
```and after some seconds```
dmesg | grep tty
```
Post here the output.

P.S. Sorry for the multiple tests but I do not have your h/w

---

### Post by utonto on 2009-08-25
larry@larry-laptop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0064
[sudo] password for larry: 
larry@larry-laptop:~$ dmesg | grep tty
console [tty0] enabled
larry@larry-laptop:~$

---

### Post by GeorgeVita on 2009-08-25
Lets take it from the start:

Boot without the modem, **wait** for the system to load, open a terminal window: ```
sudo modprobe usbserial vendor=0x19d2 product=0x0064
```Above command will try to make some serial communication ports for the USB device **19d2:0064**

Attach the modem, wait some seconds, check that system recognizes it: ```
lsusb
``` you must see 19d2:0064 within lsusb lines. Then check all system activity (last lines): ```
dmesg
```last lines will show system activity regarding the new 'usb-peripheral attached' and possibly any driver used. If some ports created they will listed also with: ```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
``` (I used the most common tty names for 3G modem)

If still nothing done ... we have stucked here.

I would try to check all above with a LiveCD running on another PC. In a different system behavior (created ports) we would have a progress to continue our efforts.

Regards,
George

(P.S. I can stay online for 15 minutes and then after 2 hours) 

**ls**)

---

### Post by utonto on 2009-08-25
here is the last lines
> usb-storage: device found at 7
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 5:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
sd 5:0:0:0: [sdb] Attached SCSI removable disk
sd 5:0:0:0: Attached scsi generic sg1 type 0
larry@larry-laptop:~$ ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
ls: impossibile accedere a /dev/ttyU*: Nessun file o directory
ls: impossibile accedere a /dev/ttyA*: Nessun file o directory
ls: impossibile accedere a /dev/ttyH*: Nessun file o directory
larry@larry-laptop:~$ 


---

### Post by GeorgeVita on 2009-08-25
sorry, only

```
lsusb
```

---

### Post by utonto on 2009-08-25
the outcome
> larry@larry-laptop:~$ sudo eject sdb
larry@larry-laptop:~$ lsusb
Bus 005 Device 007: ID 19d2:0064  
Bus 005 Device 003: ID 064e:d101 Suyin Corp. 
Bus 005 Device 001: ID 1d6b:0002  
Bus 004 Device 001: ID 1d6b:0001  
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0001  
Bus 001 Device 002: ID 0461:4d17 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0001  
larry@larry-laptop:~$ 


---

### Post by GeorgeVita on 2009-08-25
as I have to go offline for 2 hours, can you:

a. post here the actions you have done from [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630) to check

b. do you know how to remove all changes (.fdi file) and .rules and then try the tests as described at [http://ubuntuforums.org/showpost.php?p=7844440&postcount=11](http://ubuntuforums.org/showpost.php?p=7844440&postcount=11)

If the modem is 'as bought' lsusb shows: 19d2:2000
After ejecting the virtual CD-ROM that contains win-drivers it shows the 'real modem' as 19d2:0015 or 19d2:0031 or 19d2:0064 (?)

Regards,
George

---

### Post by GeorgeVita on 2009-08-25
Hi **utonto**
Just came back. I reviewed all our posts and thread [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630) 
This thread has a lot of ideas:
- udev extras
- usb_modeswitch
- auto run of usb_moodeswitch using .rules
- changes to .fdi (as the one tried together)
- and manual insertion of usbserial driver

Also it covers devices with various product id's 19d2:00**xx**

With our tests we did not managed to get at least the /dev/ttyUSBx ports which is the base line to continue with th 'dialing'.

Regards,
George

---

### Post by liamgh on 2009-08-25
Hi, I did a package for a friend who has a ZTE MF627 to get it working under Jaunty, details are at: [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way) see the update at the bottom of the post for how to install from my PPA. After installing the package and plugging the modem in allow a few seconds for the modem to be reconfigured.

---

### Post by GeorgeVita on 2009-08-26
Hi **liamgh**,
at first I would like to thank you for 'searching this forum and posting for help!'. Your professional looking blog must be 'searched' after ubuntuforums.org but surely before ... google!

**utonto** first try to return system to initial stage (removing .rules and .fdi changes), test **lsusb**,**dmesg** and then get [http://www.greenhughes.com/files/zte-mf627-switch_0.1_all.deb](http://www.greenhughes.com/files/zte-mf627-switch_0.1_all.deb)

Post here any question to follow up.

Regards,
George

---

### Post by liamgh on 2009-08-28
It's probably best to use the version in my PPA as there is also a package for usb-modeswitch in there too which is also needed.

On a side note - haven't tried this on Karmic (have copied the package, but I don't have a MF627 to test), so if anyone find it works (or otherwise) let me know!

---

### Post by onlymee on 2009-09-04
I spent a while using my ZTE MF627 modem with usb_modeswitch... It seemed clumsy and needs a lot of config to achieve a simple task.

I stumbled upon this post:
[http://www.matt-barrett.com/2008/11/telstra-pre-paid-wireless-broadband-ubuntu/comment-page-1/#comment-1918](http://www.matt-barrett.com/2008/11/telstra-pre-paid-wireless-broadband-ubuntu/comment-page-1/#comment-1918)

Which discusses some AT commands to switch of the ZeroCD behaviour of the modem so it appears immediately as a modem.  I used gtkterm and connected to /dev/ttyUSB3.  Of course you need to get passed ZeroCD manualy at least once to be able to do this.

I don't ever intend to use the modem in a Windows box, 

(I tried turning the ZeroCD setting on and of and could reverse the  behaviour - Googling AT+ZCDRUN and AT+ZOPRT diggs up a few other posts))

YMMV.

Antony

---

### Post by cataztrophe on 2009-11-13
wow,, nice info!
gotta go test it! :D

---

