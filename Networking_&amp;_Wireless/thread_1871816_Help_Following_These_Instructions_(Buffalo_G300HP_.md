---
title: "Help Following These Instructions (Buffalo G300HP Adapter)"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by mrgoodfox on 2011-10-29
I'm trying to follow the instructions [on this page]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596686") and am having problems with this lines:

> 
3) modify the common/rtusb_dev_id.c file to include the device id: {USB_DEVICE(0x0411,0x0148)}, /* Buffalo WLI-UC-G300HP*/

4) make, make install


So I use the following command:
```

gksudo gedit common/rtusb_dev_id.c

```

then copy paste the {USB_DEVICE(0x0411,0x0148)}, /* Buffalo WLI-UC-G300HP*/ line in that file and try to save but i get an error saying that 

```

Could not find the file /home/red/common/rtusb_dev_id.c.

```

---

### Post by b0b138 on 2011-10-29
Did you get the driver downloaded? Assuming you did, it will probably have to be unzipped or something and then you will have a folder with the drivers.

If you have that folder on you desktop for example, the command would be gksudo gedit /home/red/Desktop/driverfolder/common/rtusb_dev_id.c  or cd to that directory (cd /home/red/Desktop/driverfolder) then run the command the way you did before gksudo gedit common/rtusb_dev_id.c

---

### Post by mrgoodfox on 2011-10-30
Got it. Thanks

What does this line mean:
> 
make, make install


That's not a command. Does it imply something that I gotta do?

---

### Post by b0b138 on 2011-10-30
its two commands...

make

make install

These also get run inside the driver folder.

---

