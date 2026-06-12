---
title: "Dvico DVB-T Duo Tuning problems"
date: 2011-12-08
forum: Mythbuntu
---

### Post by image_editor on 2011-12-08
I have recently updated from  Mythbuntu Ver 10.1 to 11 and my Dvico DVB-T Duo card has some Tuning problems.
When i add the card only one tuner shows (dev 0). This tuner shows up and can be connected to the Australian freeview DVBt source however when a scan is completed to pick up the freeview channels the signal is almost non existant. No channels are picked up at all. This is despite the fact i can watch tv on my lcd screen through the lcd tv tuner without any reception issues.
I never had this problem with Version 10 and I really wanted version 11 to work. Can anyone help me? Please be gentle as Im a newbie!!:confused:

Just had a look at dmesg and heres what it showed.

[   16.066791] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   16.066796] cx88/2: registering cx8802 driver, type: dvb access: shared
[   16.066801] cx88[0]/2: subsystem: 18ac:db50, board: DViCO FusionHDTV DVB-T Dual Digital [card=44]
[   16.066804] cx88[0]/2: cx2388x based DVB/ATSC card
[   16.066807] cx8802_alloc_frontends() allocating 1 frontend(s)
[   16.100637] DVB: registering new adapter (cx88[0])
[   16.100645] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   16.176048] usb 1-2: new high speed USB device number 8 using ehci_hcd
[   16.289371] init: plymouth-upstart-bridge main process (538) killed by TERM signal
[   16.308845] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in cold state, will try to load a firmware
[   16.311149] dvb-usb: did not find the firmware file. (dvb-usb-bluebird-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   16.311165] dvb_usb_cxusb: probe of 1-2:1.0 failed with error -22
[   16.720687] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   16.739500] NFSD: starting 90-second grace period
[   19.834167] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   20.096870] init: plymouth-stop pre-start process (1702) terminated with status 1
[   43.853855] r8169 0000:01:00.0: eth0: link up
[   43.854062] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   54.296032] eth0: no IPv6 routers present

Hope someone can help. :)

---

### Post by nickrout on 2011-12-10
It's pretty obvious that the firmware file dvb-usb-bluebird-01.fw is missing.

If you go to packages.ubuntu.com and search for the package that contains that file you will find that you need to install the package linux-firmware-nonfree

so ```
sudo apt-get install linux-firmware-nonfree
``` should fix it.

---

