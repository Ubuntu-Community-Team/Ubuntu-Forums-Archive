---
title: "OLD 3com driver help"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by devildoc5 on 2010-03-30
ok so I guess I am either too young or too new to ubuntu or a combination of both of the above....

I have a 3com etherlink3 3c509b-c isa combo ethernet card I am trying to get to work for a file server I am trying to setup (reclaimed parts are cheaper...specifically FREE, my favorite!)  I have managed to locate the "driver" on the 3com website here: [http://www.3com.com/swd/jsp/user/result.jsp?selected=5&sort=effdt&sku=3C509B-COMBO&order=desc](http://www.3com.com/swd/jsp/user/result.jsp?selected=5&sort=effdt&sku=3C509B-COMBO&order=desc)

Problem is that I am unsure as to what driver to download.  It states at the bottom that there is an "unsupported unixware driver"  I would assume that this would be a good driver to dl, however it is and .exe file...  Seems kinda bass-ackwards to me...  anyone have any advice or directions to point me in?  Which one would work best with ndiswrapper?

Thanks for all the help.

---

### Post by chili555 on 2010-03-30
I notice the driver you linked is dated 1995. Let's just say I am quite skeptical. I also notice that it is an ISA card. My skepticism is raised!

However, there is a driver called 3c509 and here is a snip from:```
modinfo 3c509
```> filename:       /lib/modules/2.6.31-20-generic/kernel/drivers/net/3c509.ko
license:        GPL
description:    3Com Etherlink III (3c509, 3c509B, 3c529, 3c579) ethernet driver
srcversion:     ED5E3052DFDB2E5D2DB8867
alias:          e[COLOR="Red"]isa[/COLOR]:sTCM5098*
alias:          eisa:sTCM5095*
alias:          eisa:sTCM5094*
alias:          eisa:sTCM5093*
alias:          eisa:sTCM5092*
alias:          eisa:sTCM5091*
alias:          eisa:sTCM5090*Do you actually supopose it supports ISA cards? If you plug the card in, or hammer it or super-glue it, however ISA cards work and then do:```
sudo modprobe 3c509
```Is an interface created? Check with:```
ifconfig
```You might also do:```
sudo tail -n25 /var/log/syslog
```See if the kernel recognizes it and has any complaints, warnings, errors, etc.

Just when I thought I'd heard it all...

---

### Post by devildoc5 on 2010-03-30
I am trying to create new problems everyday...lmao

The problems is I am unable to get anything recognized so it may be a compatibility issue with the kernel but I am unsure of anyway to actually test this out...is there something like an lsisa or something like that I can try?

---

### Post by Iowan on 2010-03-30
I have some of those cards... I'm trying to remember if I got them working... most of the computers that used them have been retired (most of the replacements I buy have onboard NIC's).

Now that I think about it, that may have been on the '486 router/firewall (FREESCO) I used until I upgraded to DSL.

---

### Post by new_tolinux on 2010-03-30
Until somewhere in the Pentium 1 (maybe even P2) series there often was still 1 ISA slot.

About the 3c509
It can conflict with your current hardware. At best you download the DOS configuration utility, get yourself a DOS bootable floppy and then run that configuration utility. Don't run any driver, just boot and run the configuration-utility.

If the card works and you installed the hardware correct it will give you the opportunity to review and edit IRQ and some other stuff like cable/network type.
If the card is not working anymore, or the hardware is not properly installed it will produce a not-found error.

If you finished editing those settings, you may also want to run the diagnostic tests. Don't run them "forever". If it ran about 10 times without producing any error you're almost 100% sure that the card works. If it produces an error during those 10 passes..... better skip any plan you had with it.

---

### Post by Iowan on 2010-03-31
I'd forgotten that (on FREESCO, at least) the 3c509 acted like a PCI card and could be configured as such. I found [this]("http://support.3com.com/infodeli/tools/nic/3c509b/docs/obs/ch4.htm") configuration page. There's also this [3-com]("http://support.3com.com/infodeli/tools/nic/3c509b.htm") page. Hopefully, the configuration utility is listed there, somewhere...

---

