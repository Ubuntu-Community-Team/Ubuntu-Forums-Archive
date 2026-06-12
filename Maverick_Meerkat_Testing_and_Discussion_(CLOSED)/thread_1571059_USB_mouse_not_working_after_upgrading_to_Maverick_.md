---
title: "USB mouse not working after upgrading to Maverick beta"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MandeaSaracu on 2010-09-09
Hi all,
I have recently upgraded to Maverick beta from Lucid. I thought to wait until the final version is out, but I gave in to the excellent reviews I read so far about this new version.
So, here is how things are for me. The upgrade was Ok, I rebooted and then surprise! I cannot click my mouse on anything. The icons do not even "light up" on hover.
I can move the cursor on the screen, though. I thought it might me just a known bug that will solve after a few updates. But here I am a week later and still no resolution. I searched this forum and Google but I did not find a similar problem. My system is on 32 bits.
I also installed the xubuntu-desktop package and on that DE everything works.
My mouse is an A4tech X-718BK, if it matters.
Now I am at work, but later in the evening I will be available to answer your questions, if any and try solutions.
So what happens on the ubuntu desktop that my mouse is not working?

---

### Post by VMC on 2010-09-09
What's the output of 'lsusb' ? Here's mine as example:

```
$ lsusb
Bus 002 Device 003: ID 04ca:0040 Lite-On Technology Corp. <--keyboard
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by MandeaSaracu on 2010-09-09
The command outputs as follows:
```
$ lsusb
Bus 005 Device 002: ID 09da:8090 A4 Tech Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0458:704c KYE Systems Corp. (Mouse Systems) Genius i-Look 1321
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by ranch hand on 2010-09-09
I can be of no help at all.

I ran a search on "Genius i-look 1321" and "Genius ilook 1321" in reference to ubuntu and got a lot of stuff on some webcam.

---

### Post by VMC on 2010-09-09
See if 'dmesg' reports anything of value:


```
$ dmesg|grep MOUSE
[    2.151802] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[    2.151870] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:02.0-1/input0
```

---

### Post by MandeaSaracu on 2010-09-09
It doesn't have any output. Just brings me back to $. Like this:
```
octi@octi-desktop:~$ dmesg|grep MOUSE
octi@octi-desktop:~$ 

```

---

### Post by VMC on 2010-09-09
It doesn't look as though it gets detected.

It should show up on several logs. Open up "/var/log/udev" and search for "mouse". There should be several postings.

---

### Post by jrd on 2010-09-09
When you first login run cat /var/log/messages and let's see if that will give any hints.

EDIT: Didn't see the above post before I posted.

---

### Post by RJ12 on 2010-09-09
I had this problem in Lucid. What made it work for me was doing the follow code in the terminal

```
sudo modprobe usbhid
```


This will load the USB Human Interface Device Modules (drivers) if they are not currently loaded.

For me it also did this with USB drives, to fix that try

```
sudo modprobe usb_storage
```

---

### Post by MandeaSaracu on 2010-09-10
> **VMC said:**
> It doesn't look as though it gets detected.

It should show up on several logs. Open up "/var/log/udev" and search for "mouse". There should be several postings.
Yes, there are postings in the udev file about the mouse. Like this:
```
DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input3/mouse0
DEVNAME=/dev/input/mouse0
DEVLINKS=/dev/char/13:32 /dev/input/by-id/usb-A4Tech_USB_Full_Speed-mouse /dev/input/by-path/pci-0000:00:1d.3-usb-0:2:1.0-mouse
KERNEL[1284091506.216416] add      /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input3/mouse0 (input)
ID_INPUT_MOUSE=1
ID_VENDOR=A4Tech
ID_VENDOR_ENC=A4Tech
ID_VENDOR_ID=09da
ID_MODEL=USB_Full_Speed
ID_MODEL_ENC=USB\x20Full\x20Speed
ID_MODEL_ID=8090
ID_REVISION=0606
ID_SERIAL=A4Tech_USB_Full_Speed
ID_TYPE=hid
ID_BUS=usb
ID_USB_INTERFACES=:030102:030101:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usbhid
ID_PATH=pci-0000:00:1d.3-usb-0:2:1.0
MAJOR=13
MINOR=67
DEVLINKS=/dev/char/13:67 /dev/input/by-id/usb-A4Tech_USB_Full_Speed-event-mouse /dev/input/by-path/pci-0000:00:1d.3-usb-0:2:1.0-event-mouse
```I will try the modprobe usbhid and to be honest I did not try to connect a USB memory, so I will also try that. I will write again after I try this. Perhaps I will be able to edit this post after. Thank you.

LE: Well, it doesn't work. I enter the sudo modprobe usbid command in the terminal and I cannot see any change, nor can I see a result, an output of the command, it just returns to the $ prompt.

---

### Post by VMC on 2010-09-10
Did you try plugging the mouse into another port ?

---

### Post by jrd on 2010-09-10
Since the mouse works with another DE I doubt (could be wrong though) it is udev or modules or anything like that since the other DE uses the same modules and also uses the same udev. I imagine it's an issue with Gnome itself ( a service is crashing etc...). I would try browsing through the messages log and see if anything is messing up or giving errors when you log in. 

It may not help but it wouldn't hurt to check anyway.

---

### Post by MandeaSaracu on 2010-09-10
> **VMC said:**
> Did you try plugging the mouse into another port ?
Of course, it was the second thing I did, after inspecting the mouse itself.
@jrd: Where on the disk is the log located? What's the path to it?

---

### Post by cariboo on 2010-09-10
All the logs are located in /var/log, you can also use System->Administration->Log File Viewer. Have you tried a different mouse?

---

### Post by MandeaSaracu on 2010-09-10
I found my old PS/2 mouse in a desk drawer. Plugged it in, no succes. Same problem.
I also noticed something odd.
I test the behaviour and every advice you give me on Xubuntu, wich runs fine. Then I log out from Xubuntu and choose Ubuntu Desktop Edition at the login screen, and test there, and it doesn't work. But when I log back into Xubuntu, the problem appears there as well.
And I also saw an error report at PC startup just before the Ubuntu loading screen, it said something about
Error Fatal: could not load /lib/modules/ kernel version /modules.dep 
and after a while, it continues to load and it works. Didn't see it before, because I usually don't sit next to the PC while it boots.
Could that have something to do with the problem I face?

---

### Post by cariboo on 2010-09-10
you can check if the error message is still there, by opening a terminal and typing:

```
cat /var/log/messages | grep error | less
```

It would be best to run this just after a reboot, as it will also print any other errors that have occurred since reboot.

---

### Post by amaster on 2010-09-13
I have similar problem. Suddenly the clisk doesn't works :S but the light up works correctly.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/630024](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/630024)

---

### Post by MandeaSaracu on 2010-09-13
Ok, I have some new info...
Yesterday I made a backup of my info from the hard drive and reinstalled Ubuntu Maverick, the daily build at that time. (11 or 12 sept 2010). I had the same problems even from the live session, before installing on the disk. Useless to mention that in the new installation it was the same. Then, I connected my PS/2 mouse I was talking about in an earlier post, and on another fresh installation, knock on wood, it works fine so far...
If it is a bug, why isn't it more widespread among the users, and why it seems to affect both USB and PS/2 systems?

---

### Post by KingsLee on 2010-10-01
I experienced the same problem...

Now I can only use RemoteDroid with my android phone to control the mouse pointer...

---

### Post by Yumi on 2010-10-01
Yesterday it hit me. Just the usual update, restart, and - USB mouse, pointer not moving. Dual install and it works in windows, no hardware problemmm. I changed no setting, no files, no preferences since.

Update: Played a bit around and unplugged the USB mouse from the rear port and into the front USB port. Working again! But not in the back.

Michael

---

### Post by swatkat1076 on 2010-10-01
> **Yumi said:**
> Yesterday it hit me. Just the usual update, restart, and - USB mouse, pointer not moving. Dual install and it works in windows, no hardware problemmm. I changed no setting, no files, no preferences since.

Update: Played a bit around and unplugged the USB mouse from the rear port and into the front USB port. Working again! But not in the back.

Michael

It happens to me too. Same config.

Dual boot and I have Alienware Keyboard and a Razer mouse. I installed Ubuntu Maverick RC and then did update using update manager after reboot as soon as the kernel loads, the mouse and keyboard are not detected [ It works fine on Windows ] Even moving the keyboard to different USB ports dont work.

Can anybody help please ?

Thanks

---

### Post by MandeaSaracu on 2010-10-10
Well, well, Maverick is out today and after downloading the CD imager, I tought to give it another try, with a fresh install. Everything worked smoothly, just before selecting the partions, and then the mouse died. And this is from the LIVE SESSION, without modifing anything, just left it do its job and installing... It only moved the arrow on the screen. No right click, no left click, nothing. I installed, and I am posting now from Linux Mint. The same mouse works flawlessly. I would post a bug, but I do not have the system installed anymore. All the hype with the perfect 10 distro etc, and for me, nothing... Such a shame...

---

