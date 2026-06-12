---
title: "DVD codec and region change"
date: 2009-02-05
forum: Multimedia Software
---

### Post by BradleyAtkins on 2009-02-05
Hi Folks

I could do with some help getting a laptop to play DVD's. 2 Problems I think: -

1) Loaded a DVD and launched MoviePlayer. It informed me I needed a new codec to play the DVD and offered me a choice of either of two free ones or to purchase one. I selected to install the first free one in the list and proceeded to install it. Now when I try to play a DVD it tries then pops up a dialogue box informing me there was an error (no details). I cannot get back to the form that offered to let me search for a codec to purchase. 
2) I think the DVD drive was previously set to region 1 format when it was a windows machine so I don't know if there is a problem with the codec or just the region settings.

Can anyone tell me how to reset the region to region 2 and how to manually install a propriatry codec if I need one?

Thanks

Brad

---

### Post by wolfen69 on 2009-02-05
here is the free one.
```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```then
```
sudo apt-get install libdvdcss2
```

---

### Post by SuperSonic4 on 2009-02-05
If that doesn't work use regionset

```
sudo apt-get regionset
```

```
sudo regionset
```

---

### Post by binbash on 2009-02-05
sudo apt-get install libdvdcss2 should work

---

### Post by BradleyAtkins on 2009-02-06
Hi Thanks that got the DVD player working but as I feared only for region 1. Nice to see progress though! I see the other posts below which I will reply to as well, trying the region set command: -

brad@TX5N:~$ sudo apt-get regionset
E: Invalid operation regionset

I thought that command was to go get the regionset application so am puzzled to see it report an invalid operation on the E: drive. Trying the region set command on its own: -

brad@TX5N:~$ sudo regionset
sudo: regionset: command not found

Any ideas?

---

### Post by BradleyAtkins on 2009-02-06
Hi thanks,

Didn't work unfortunately, see my reply to Wolfen.

Do you think maybe I need a driver from Sony or something? This is a Vaio VGN-TX5XN

Thanks for the feedback

Brad

---

### Post by gandaran on 2009-02-06
> **BradleyAtkins said:**
> Hi Thanks that got the DVD player working but as I feared only for region 1. Nice to see progress though! I see the other posts below which I will reply to as well, trying the region set command: -

brad@TX5N:~$ sudo apt-get regionset
E: Invalid operation regionset

I thought that command was to go get the regionset application so am puzzled to see it report an invalid operation on the E: drive. Trying the region set command on its own: -

brad@TX5N:~$ sudo regionset
sudo: regionset: command not found

Any ideas?
it's **sudo apt-get install regionset**
you can only change the regionset 3 or 5 times the it locks up

---

### Post by mc4man on 2009-02-06
If you have a Matshita laptop dvd drive then it will only allow playback when there is a region match. (no work around
So your forced to pick a region where the bulk of your titles are from and forget about the others.
You're only allowed 4 changes after the initial setting before the drive locks permanently, so if this is the case choose the region carefully.

To ck. what drive you have run 
```
sudo lshw -C disk
```

---

### Post by BradleyAtkins on 2009-02-06
Brilliant, thanks very much that did the trick ok.

As you guys are so sharp I'll push my luck and ask you if you can help me with something else.

When I load a DVD a dialogue box opens asking me what application I want to use to play it. This box has an eject button on it that works ok and ejects the CD fine.

However Movie player has the Eject option on the Movie menu greyed out so I cannot eject easily, ( I have to poke a little button on the DVD tray with a pen tip to get it to open. The laptop has dedicated buttons at the base  of the screen to use DVD's, (stop / play / eject etc ) but these do not work.

Any ideas on how I can get these working ok?

Using the post about how to discover your drive details from mc4man I got this: -

brad@TX5N:~$ sudo lshw -C disk
[sudo] password for brad: 
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK1011GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: BK00
       serial: 17QGS24FS
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=c0be833d
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-852S
       vendor: MATSHITA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.30
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by BradleyAtkins on 2009-02-06
Thanks that's very helpful

---

### Post by BradleyAtkins on 2009-02-06
PS Great wallpapers thanks!!

---

