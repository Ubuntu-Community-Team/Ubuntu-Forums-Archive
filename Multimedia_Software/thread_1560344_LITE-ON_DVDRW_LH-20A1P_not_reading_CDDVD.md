---
title: "LITE-ON DVDRW LH-20A1P not reading CD/DVD"
date: 2010-08-24
forum: Multimedia Software
---

### Post by Automat2 on 2010-08-24
For over a week and a half, more or less, this DVD drive does not read any CD or DVD that I put on the tray.

When I insert the disk, the light on the drive might be on, and then flashing for a while, but neither the selection screen, the icon on the Desktop nor the name of the disk on "Places" show the disk at all.

I changed the IDE cable, I swapped the places of my two drives but nothing.

Can anybody help?

---

### Post by tommcd on 2010-08-24
First, run ```
dmesg | tail
``` just to see what the last output was. Then insert a data CD or DVD or a music CD or something. Then run **dmesg | tail** again. The dmesg output should show references to sr0 (the optical drive) after inserting a CD or DVD into the drive.

If dmesg shows nothing after inserting a disc into the cdrom drive. It is possible that the drive is dead.
Did the cdrom drive used to work in Ubuntu? But now it does not?
Perhaps try testing the cdrom drive in a different computer just to verify that it works ok.

---

### Post by Automat2 on 2010-08-25
> **tommcd said:**
> First, run ```
dmesg | tail
``` just to see what the last output was. Then insert a data CD or DVD or a music CD or something. Then run **dmesg | tail** again. The dmesg output should show references to sr0 (the optical drive) after inserting a CD or DVD into the drive.

If dmesg shows nothing after inserting a disc into the cdrom drive. It is possible that the drive is dead.
Did the cdrom drive used to work in Ubuntu? But now it does not?
Perhaps try testing the cdrom drive in a different computer just to verify that it works ok.
I did what you suggested and this is the output
with the try empty:
> [   13.810942]  domain 0: span 0-3 level MC
[   13.810944]   groups: 2 3 0 1
[   13.810947] CPU3 attaching sched-domain:
[   13.810948]  domain 0: span 0-3 level MC
[   13.810949]   groups: 3 0 1 2
[   21.020015] eth0: no IPv6 routers present
[   74.061944] input: Logitech MX5000 Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.2/1-2.2.1/1-2.2.1:1.0/bluetooth/hci0/hci0:11/input6
[   74.062122] generic-bluetooth 0005:046D:B305.0002: input,hidraw1: BLUETOOTH HID v45.01 Keyboard [Logitech MX5000 Keyboard] on 00:07:61:45:5E:11
[   90.566756] input: Logitech MX1000 mouse as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.2/1-2.2.1/1-2.2.1:1.0/bluetooth/hci0/hci0:12/input7
[   90.566980] generic-bluetooth 0005:046D:B003.0003: input,hidraw2: BLUETOOTH HID v43.10 Mouse [Logitech MX1000 mouse] on 00:07:61:45:5E:11

And with a data CD on the drive:
> [   13.810942]  domain 0: span 0-3 level MC
[   13.810944]   groups: 2 3 0 1
[   13.810947] CPU3 attaching sched-domain:
[   13.810948]  domain 0: span 0-3 level MC
[   13.810949]   groups: 3 0 1 2
[   21.020015] eth0: no IPv6 routers present
[   74.061944] input: Logitech MX5000 Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.2/1-2.2.1/1-2.2.1:1.0/bluetooth/hci0/hci0:11/input6
[   74.062122] generic-bluetooth 0005:046D:B305.0002: input,hidraw1: BLUETOOTH HID v45.01 Keyboard [Logitech MX5000 Keyboard] on 00:07:61:45:5E:11
[   90.566756] input: Logitech MX1000 mouse as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.2/1-2.2.1/1-2.2.1:1.0/bluetooth/hci0/hci0:12/input7
[   90.566980] generic-bluetooth 0005:046D:B003.0003: input,hidraw2: BLUETOOTH HID v43.10 Mouse [Logitech MX1000 mouse] on 00:07:61:45:5E:11


I can't see any references to sr0. I used to have this unit as main drive until about 10 days ago.

---

### Post by tommcd on 2010-08-25
> **Automat2 said:**
> 
I can't see any references to sr0. I used to have this unit as main drive until about 10 days ago.
What do you mean there when you say "*I used to have this unit as main drive until about 10 days ago*"? 
Did you change the drive's position on the IDE cable or something? If you did, then did you change the jumper accordingly? Set the jumper to either master or slave according to it's position on the IDE cable. Don't rely on cable select.
Those 2 outputs from dmesg are identical. So Ubuntu did not see the drive when you put a CD in it. 
Is the cdrom drive listed in the computer's BIOS?

---

### Post by Automat2 on 2010-08-26
Yes, it was very strange. BIOS detected the drive. It was listed everywhere, but did not read anything at all.

Except from one occasion where it took about half an hour to mount a DVD. And another one where I had to hold the unit and keep a rather odd position for it to read discs.

What I meant by "it used to be my main drive..." is that it was the drive I used the most, and the master. It used to be a lot faster reading than the other one.

Well, I didn't change the jumper but I tried both drives on both ports of the IDE and my other drive read and mounted CD's and DVD's without any problems in both. It was only this drive that caused the problems.

Anyway, I tried the drive on an XP PC and gave the same problem, so I had to buy another drive.

Thanks for your help, tommcd

---

