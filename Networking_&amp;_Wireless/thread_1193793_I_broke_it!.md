---
title: "I broke it!"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by carterw65 on 2009-06-21
Well I have went and done it this time. I had a PX-500 card working just fine. Then I needed to get my Linksys WPC54GS Ver 2 card working (ndiswrapper) and it took me a full day to do that. Now I plug the PX-500 card in and it isn't even recognized. I was able to click on the little wireless strength symbol and it would be there to select and connect it. Not any longer. Nothing shows up. It is still in the network devices though. I am not the best trouble shooter and I really don't know where to begin. I could use wvdial, except for one small problem, no internet access where I am so I can't get it from the repository. Please help me so I don't have to use Windoze any longer than necessary!

---

### Post by GeorgeVita on 2009-06-22
Hi **carterw65**,
to restore **wvdial** on 9.04:
[http://ubuntuforums.org/showpost.php?p=7465501&postcount=3](http://ubuntuforums.org/showpost.php?p=7465501&postcount=3)
Regards,
George

---

### Post by carterw65 on 2009-06-22
The WVDIAL work around worked just fine, however, when I went to configure wvdial it could not find the PX-500. I ran "sudo wvdialconf" and it said "no modem found". So now I am really stumped. Any thoughts?

Thanks,

Bill

---

### Post by carterw65 on 2009-06-22
I ran these two commands and here is the output:

carterw65@carterw65-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 006 Device 002: ID 106c:3702 Curitel Communications, Inc. Pantech PX-500[/COLOR]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB

carterw65@carterw65-laptop:~$ ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory

---

### Post by GeorgeVita on 2009-06-23
Hi **carterw65**,
some modems are using /dev/ttyACM0 so check all with:```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
```

If you do not have any port you will try to create them with **usbserial** driver. With 9.04 this is difficult as in the standard kernel it is encapsulated (you cannot run 'sudo modprobe usbserial ...').

Check your kernel version:```
uname -a
```

Do you have the option of ethernet or wifi internet?
If YES: do a full update to get kernel **2.6.28-13-generic**
Otherwise you must try to fix connection with the initial 9.04 kernel, connect and do the update, fix again the connection with the 'standard' modprobe way.

Both **usbserial** fixes (encapsulated/external) are shown to [http://ubuntuforums.org/showthread.php?t=1193682](http://ubuntuforums.org/showthread.php?t=1193682)
(You have to use your modem's IDs 106c:3702).

Regards,
George

---

### Post by carterw65 on 2009-06-23
I don't have an alternate internet source where I am. It's this or nothing. I installed the Linksys card for my home wireless DSL, but I am only home every couple of weeks. I am mostly gone.

Anyway, here is the following from the commands you gave me:

carterw65@carterw65-laptop:~$ ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
ls: cannot access /dev/ttyU*: No such file or directory
ls: cannot access /dev/ttyA*: No such file or directory
ls: cannot access /dev/ttyH*: No such file or directory

carterw65@carterw65-laptop:~$ uname -a
Linux carterw65-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 
i686 GNU/Linux

Thanks for your help,

Clueless Bill :)

---

### Post by carterw65 on 2009-06-23
George,

I did the USBserial fix using 0x106c and 0x3702. I rebooted and still get the same status on all the commands. It didn't seem to make any difference at all.

Thanks!

---

### Post by carterw65 on 2009-06-23
I also tried sudo modprobe usbserial vendor=0x106c product=0x3702. It gave me a bunch of warnings then failed. I attached a modified version of the fix I used to get the Linksys card working. I did try many things prior to this, but this got it working. If if doesn't display properly please let me know and I will fix it.

Thanks!

---

### Post by GeorgeVita on 2009-06-26
Hi again,
looking into HAL info file I realize that Pantech PX500 (106c : 3702) is included. I think it should work directly with the Network Manager 0.7 as it is reported as EVDO card and not as 3G modem (file: /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi).
You can check booting without the card and inserting it later. From terminal use **dmesg** to see at the last lines all system activity about the card recognition and any port created.

It is reported as EVDO card and not as 3G modem.

As possibly something is missing ... for your kernel **2.6.28-11-generic** the way must be (according to my link above):
```
sudo gedit /boot/grub/menu.lst
```
find the long line ```
kernel      /boot/vmlinuz-2.6.28-11-generic root=UUID=43c8028b-a7d0-453a-bea0-ee259aaa246f ro quiet splash
```
add to the end the usbserial data to become:```
kernel      /boot/vmlinuz-2.6.28-11-generic root=UUID=43c8028b-a7d0-453a-bea0-ee259aaa246f ro quiet splash usbserial.vendor=0x106c usbserial.product=0x3702
```
Note: add the 'usbserial' parameters at the end. Do not copy paste all above as I do not know the meaning of other Hex parameters at the kernel line!

Save and Exit gedit. After reboot check if any port created with:```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
```

The alternative is firstly update to the recent kernel (You need an internet connection!) and then run from terminal:
```
sudo modprobe usbserial vendor=0x106c product=0x3702
```

I used various names to 'ls /dev/tty...' command because sometimes a different driver creates other port like /dev/ttyACM0 or /dev/ttyHS0.

Finally, full data for PX-500 installation found at [http://www.sprint.com/assets/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux.pdf](http://www.sprint.com/assets/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux.pdf)
This can be used only for reference as it is for previous versions.

Regards,
George

---

