---
title: "Problem in installing lucent modem on ubuntu 10.04"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by aliirani on 2011-01-14
Hello all!
I have a lucent modem!
I instal this modem with this help:
[http://www.spinics.net/lists/linmodem/msg11004.html](http://www.spinics.net/lists/linmodem/msg11004.html)
but my modem is not detect!
```

ali@ali-desktop:~$ sudo agrsm-test 

Found drivers for boot kernel 2.6.32-21-generic at:
/lib/modules/2.6.32-21-generic/updates/dkms/agrmodem.ko
/lib/modules/2.6.32-21-generic/updates/dkms/agrserial.ko



Loading drivers:
FATAL: Error inserting agrmodem (/lib/modules/2.6.32-21-generic/updates/dkms/agrmodem.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting agrserial (/lib/modules/2.6.32-21-generic/updates/dkms/agrserial.ko): No such device

Drivers loaded:

and symbolic link created:
lrwxrwxrwx 1 root root 12 2011-01-14 20:41 /dev/ttySAGR -> /dev/ttyAGS3

Checking for utility wvdialconf
Found /usr/bin/wvdialconf, preparing to run:
    wvdialconf /etc/wvdial.conf

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   SAGR 

A reboot may be necessary before modem detection through:
    sudo modprobe agrserial
Which will load agrmodem, agrserial and create the symbolic link needed for:
    sudo wvdialconf


The installation record has been written to ./agrsm-test.txt

```and wvidial:
```
ali@ali-desktop:~$ sudo modprobe agrserial
[sudo] password for ali: 
FATAL: Error inserting agrmodem (/lib/modules/2.6.32-21-generic/updates/dkms/agrmodem.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting agrserial (/lib/modules/2.6.32-21-generic/updates/dkms/agrserial.ko): No such device
ali@ali-desktop:~$ sudo wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   SAGR 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
ali@ali-desktop:~$ 


```Is there any idea?

---

### Post by powerz on 2011-02-14
[SIZE=4]hi, i m using ubuntu 10.04 lts and i m writing here first  time. i m facing some problem, i dont know where i should post it. any  one can help me plz.
i hv installed ubuntu with my xp. my laptop is toshiba  L500-s502. i  want to connect internet with my wimax 802.16e usb adapter. but i cant.  can anyone help me plz....
config of my modem.
1.US211 wimax 802.16e usb adapter
2.IEEE 802.16e-2005 complaint.
3. Support MIMO, MRC and IO beamforming radio technologies.[/SIZE]

---

