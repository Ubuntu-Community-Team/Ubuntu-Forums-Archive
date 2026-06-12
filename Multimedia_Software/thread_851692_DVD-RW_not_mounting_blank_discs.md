---
title: "DVD-RW not mounting blank discs"
date: 2008-07-06
forum: Multimedia Software
---

### Post by ian-johnson on 2008-07-06
I've read most of the posts on similar issues with this problem to no avail.  I cannot get my machine to mount a blank DVD in order to burn a movie.  This all happened after upgrading to Hardy.  Does anyone know why this is happening?  My drive is definitely a DVD-RW drive and I seem to have all the codecs installed that everyone recommends.  Can we please get some help with this issue.  It seems I am not alone.  I have used Ubuntu as my primary OS since it was first made available.
Please help.

---

### Post by scragar on 2008-07-06
You can't mount blank discs, but I know what you mean, I had a similar problem once(which intrestingly enough was solved by restarting with a blank disk in the drive btw). I'm sure dmesg will have something to say about the drive, it had a lot to say when I had my problem:
```
dmesg | tail -n 20
```
paste output back please.

---

### Post by ian-johnson on 2008-07-07
Thanks scragar for the response.  The following is the output I receive from your command:
[   90.210749]  domain 0: span 03
[   90.210752]   groups: 02 01
[   90.210757]   domain 1: span 03
[   90.210760]    groups: 03
[   90.210764]    domain 2: span 03
[   90.210768]     groups: 03
[  101.599834] NET: Registered protocol family 17
[  103.651390] wlan0: Initial auth_alg=0
[  103.651398] wlan0: authenticate with AP 00:1b:2f:df:e0:98
[  103.652756] wlan0: RX authentication from 00:1b:2f:df:e0:98 (alg=0 transaction=2 status=0)
[  103.652761] wlan0: authenticated
[  103.652765] wlan0: associate with AP 00:1b:2f:df:e0:98
[  103.654420] wlan0: RX AssocResp from 00:1b:2f:df:e0:98 (capab=0x411 status=0 aid=3)
[  103.654426] wlan0: associated
[  103.654506] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  103.654512] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  103.654516] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  103.654521] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  103.657328] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  120.489086] wlan0: no IPv6 routers present

It doesn't look like this will be helpful...

I appreciate your help and would love any other advise.

Thanks,

Ian.

I just tried dmesg by itself and got a lot of system info including the following that I cut out.  Perhaps this is helpful.

Again, thanks.

[   44.537817]  sda1 sda2 sda3 sda4
[   44.559227] sd 0:0:0:0: [sda] Attached SCSI disk
[   44.563943] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.563963] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   44.566687] usb 1-2: USB disconnect, address 2
[   46.747919] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   46.747924] Uniform CD-ROM driver Revision: 3.20
[   46.747973] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   44.799563] usb 1-2: new full speed USB device using uhci_hcd and address

---

### Post by scragar on 2008-07-08
I used to get lot's of messages regarding the cd rom not being ready and asking me to check the drive,

I'm lost as to a solution, there's nothing showing the problem there.:(

---

### Post by lisati on 2008-07-08
Sometimes the brand can be problematical. There are some I've been able to use with Nero & other Windows software, but not with my stand-alone DVD recorder or with some Linux software.

---

