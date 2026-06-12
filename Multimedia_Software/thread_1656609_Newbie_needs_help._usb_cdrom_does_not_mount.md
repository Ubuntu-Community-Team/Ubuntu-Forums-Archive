---
title: "Newbie needs help. usb cdrom does not mount"
date: 2010-12-31
forum: Multimedia Software
---

### Post by xr4ti on 2010-12-31
My cdrom is not mounting on ubuntu 8.04.  I find this message in syslog:

<code>


Dec 30 16:13:26 ubuntusap kernel: [  351.765683] usb-storage: device scan complete
Dec 30 16:13:26 ubuntusap kernel: [  351.766423] scsi 5:0:0:0: CD-ROM            Memorex  DVD+-RAM 530L v1 5M64 PQ: 0 ANSI: 0
Dec 30 16:13:26 ubuntusap kernel: [  351.766785] scsi 5:0:0:0: Attached scsi generic sg1 type 5
Dec 30 16:13:26 ubuntusap kernel: [  351.856208] Driver 'sr' needs updating - please use bus_type methods
Dec 30 16:13:26 ubuntusap kernel: [  351.861991] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 30 16:13:26 ubuntusap kernel: [  351.861994] Uniform CD-ROM driver Revision: 3.20
Dec 30 16:13:26 ubuntusap kernel: [  351.862029] sr 5:0:0:0: Attached scsi CD-ROM sr0

</code>

---

### Post by xr4ti on 2010-12-31
Surely someone has seen this issue???
 
> **xr4ti said:**
> My cdrom is not mounting on ubuntu 8.04. I find this message in syslog:
 
<code>
 
 
Dec 30 16:13:26 ubuntusap kernel: [ 351.765683] usb-storage: device scan complete
Dec 30 16:13:26 ubuntusap kernel: [ 351.766423] scsi 5:0:0:0: CD-ROM Memorex DVD+-RAM 530L v1 5M64 PQ: 0 ANSI: 0
Dec 30 16:13:26 ubuntusap kernel: [ 351.766785] scsi 5:0:0:0: Attached scsi generic sg1 type 5
Dec 30 16:13:26 ubuntusap kernel: [ 351.856208] Driver 'sr' needs updating - please use bus_type methods
Dec 30 16:13:26 ubuntusap kernel: [ 351.861991] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 30 16:13:26 ubuntusap kernel: [ 351.861994] Uniform CD-ROM driver Revision: 3.20
Dec 30 16:13:26 ubuntusap kernel: [ 351.862029] sr 5:0:0:0: Attached scsi CD-ROM sr0
 
</code>

---

### Post by xr4ti on 2011-01-04
> **xr4ti said:**
> Surely someone has seen this issue???
 
 
Another attempt to resurrect my thread.  Any helpers out there?

---

### Post by nomko on 2011-01-04
Do this:
 
-open a terminal
- type in: **lsusb**
- place the output here
- type in: **sudo blkid**
- place the output here

---

### Post by thefrenchdog1@hotmail.com on 2011-01-04
I don't know how much help this will be but had a asus mother board from 2003 and had this problem with ubuntu installs until the 9's.  It was so regular I just did it out of course when messing with  that MB.  

I installed the partition manager then ubuntu used to install and and then is deleted after install is done.  I would download that when done installing and up would pop usb and external HD's when I plugged them in and of course the optic drives.

---

### Post by xr4ti on 2011-01-04
> **nomko said:**
> Do this:
 
-open a terminal
- type in: **lsusb**
- place the output here
- type in: **sudo blkid**
- place the output here
 
lsusb:
 
<code>
BUS 006 Device 001: ID 0000:0000
BUS 005 Device 013: ID 4855:6288
BUS 005 Device 001: ID 0000:0000
BUS 004 Device 001: ID 0000:0000
BUS 003 Device 001: ID 0000:0000
BUS 002 Device 001: ID 0000:0000
BUS 001 Device 001: ID 0000:0000
</code>
 
blkid:
 
<code>
/dev/sda1: UUID='9defc1b5-9f90-450e-90aa-af2cfe55e554" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="d71f1c1a-96d2-490e-a426-bbc33101cc73"
</code>

---

### Post by matt_symes on 2011-01-04
Hi

A slightly unrelated question. Is there any reason you are using 8.04?

Kind regards

---

### Post by xr4ti on 2011-01-04
> **matt_symes said:**
> Hi
 
A slightly unrelated question. Is there any reason you are using 8.04?
 
Kind regards
 
 
Yes.

---

### Post by nomko on 2011-01-04
> **xr4ti said:**
> lsusb:
 
<code>
BUS 006 Device 001: ID 0000:0000
BUS 005 Device 013: ID 4855:6288
BUS 005 Device 001: ID 0000:0000
BUS 004 Device 001: ID 0000:0000
BUS 003 Device 001: ID 0000:0000
BUS 002 Device 001: ID 0000:0000
BUS 001 Device 001: ID 0000:0000
</code>
 
blkid:
 
<code>
/dev/sda1: UUID='9defc1b5-9f90-450e-90aa-af2cfe55e554" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="d71f1c1a-96d2-490e-a426-bbc33101cc73"
</code>
 
It looks like something is very wrong. 6 usb bus devices with nothing connected??? And i device connected and that's a device of Memorex???
Or is there more info after the listing you put here?
 
 
Don't you have any usb devices connected??
 
And when you gave the command blkid, was the usb cd-rom connected??

---

### Post by xr4ti on 2011-01-04
> **nomko said:**
> It looks like something is very wrong. 6 usb bus devices with nothing connected??? And i device connected and that's a device of Memorex???
Or is there more info after the listing you put here?
 
 
Don't you have any usb devices connected??
 
And when you gave the command blkid, was the usb cd-rom connected??
 
The USB cd rom is connected.  Yes it was connected.
 
No, I pasted all output.

---

### Post by xr4ti on 2011-01-04
> **xr4ti said:**
> My cdrom is not mounting on ubuntu 8.04. I find this message in syslog:
 
<code>
 
 
Dec 30 16:13:26 ubuntusap kernel: [ 351.765683] usb-storage: device scan complete
Dec 30 16:13:26 ubuntusap kernel: [ 351.766423] scsi 5:0:0:0: CD-ROM Memorex DVD+-RAM 530L v1 5M64 PQ: 0 ANSI: 0
Dec 30 16:13:26 ubuntusap kernel: [ 351.766785] scsi 5:0:0:0: Attached scsi generic sg1 type 5
Dec 30 16:13:26 ubuntusap kernel: [ 351.856208] Driver 'sr' needs updating - please use bus_type methods
Dec 30 16:13:26 ubuntusap kernel: [ 351.861991] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 30 16:13:26 ubuntusap kernel: [ 351.861994] Uniform CD-ROM driver Revision: 3.20
Dec 30 16:13:26 ubuntusap kernel: [ 351.862029] sr 5:0:0:0: Attached scsi CD-ROM sr0
 
</code>
 .

---

