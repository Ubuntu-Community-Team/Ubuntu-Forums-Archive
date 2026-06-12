---
title: "Mythbuntu PC needs rebooting every day"
date: 2011-10-18
forum: Mythbuntu
---

### Post by icmdwilliams on 2011-10-18
Sorry if this has been covered before but I couldn't see it.

Every day when I come in from work I check my mythtv, and the channels are screwed up as in some (a lot) are missing and the ones that are there do not lock. I reboot the PC running mythbuntu and everything comes back.

I am using a PEAK221544AGPK dual tuner card running the latest the lastest download of Mythbuntu, I have patched it but not upgraded to ubuntu 11.10

Has anyone else experienced anything similar and if so how did they solve it.

Thanks in advance

Dave.

---

### Post by ian dobson on 2011-10-19
Hi,

Maybe provide some log files (dmesg, /var/log/syslog, and /var/log/mythtv/mythbackend.log)

Sound alot like a tuner problem, if your seeing i2c errors in your syslog then maybe try booting with the irqpoll kernel option.

Regards
Ian Dobson

---

### Post by icmdwilliams on 2011-10-19
> **ian dobson said:**
> Hi,

Maybe provide some log files (dmesg, /var/log/syslog, and /var/log/mythtv/mythbackend.log)

Sound alot like a tuner problem, if your seeing i2c errors in your syslog then maybe try booting with the irqpoll kernel option.

Regards
Ian Dobson

OK will have a look, but yes I do agree it does feel like a tuner issue. My problem is I'm very new to mythbuntu and  not very experienced with ubuntu.

Many thanks

Dave.

---

### Post by icmdwilliams on 2011-10-19
Yes I am seeing  these, not a lot but some, I think they coincide with the times I try and watch the TV.


Oct 19 13:13:59 MEDIA-SERVER kernel: [72689.384073] af9013: I2C write failed reg:ae00 len:1

and

Oct 19 08:57:03 MEDIA-SERVER kernel: [57273.614871] tda18271_read_regs: [6-00c0|M] ERROR: i2c_transfer returned: -1

You mention trying  irqpoll kernel option, I will have a look and see if I can spot where this is located.

Again many thanks

Dave.

---

### Post by ian dobson on 2011-10-20
Hi,

The irqpoll option needs to be added to the kernel command line, so you need to add it to grub. I don't have access to a linux box so I can't provide you with exact instructions.

Have a look here: [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Regards
Ian Dobson

---

