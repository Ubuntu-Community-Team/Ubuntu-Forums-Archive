---
title: "Can't Play DVD's"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by ayapejian on 2008-02-10
Hey Everyone, 
   Having a problem playing DVDs ... If I insert a DVD into the tray totem pops up and gives an error about unable to read the disc.  Below is the dmesg output, I've tried various DVD's, this is the first time I've tried to play a dvd in ubuntu, any help would be appreciated.

```

$uname -a
Linux Pheonix 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

```

```

[48865.454958] UDF-fs: Partition marked readonly; forcing readonly mount
[48865.491825] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Pans_Labyrinth_D1', timestamp 2007/03/14 17:10 (1ed4)
[48866.513521] end_request: I/O error, dev sr0, sector 294980
[48866.513526] Buffer I/O error on device sr0, logical block 73745
[48866.513531] Buffer I/O error on device sr0, logical block 73746
[48866.513533] Buffer I/O error on device sr0, logical block 73747
[48866.513535] Buffer I/O error on device sr0, logical block 73748
[48866.513537] Buffer I/O error on device sr0, logical block 73749
[48866.513539] Buffer I/O error on device sr0, logical block 73750
[48866.513541] Buffer I/O error on device sr0, logical block 73751
[48866.513543] Buffer I/O error on device sr0, logical block 73752
[48866.513545] Buffer I/O error on device sr0, logical block 73753
[48866.513547] Buffer I/O error on device sr0, logical block 73754
[48866.669671] end_request: I/O error, dev sr0, sector 295712
[48866.839344] end_request: I/O error, dev sr0, sector 295712
[48866.993472] end_request: I/O error, dev sr0, sector 295712
[48867.240300] end_request: I/O error, dev sr0, sector 295720
[48867.394547] end_request: I/O error, dev sr0, sector 295720
[48867.548779] end_request: I/O error, dev sr0, sector 295720
[48867.795598] end_request: I/O error, dev sr0, sector 295724
[48868.042239] end_request: I/O error, dev sr0, sector 295728
[48868.196511] end_request: I/O error, dev sr0, sector 295732
[48868.451843] end_request: I/O error, dev sr0, sector 295760
[48868.698734] end_request: I/O error, dev sr0, sector 295764
[48868.852951] end_request: I/O error, dev sr0, sector 295760

```

---

### Post by jan quark on 2008-02-10
perhaps the dvd is encrypted?

I had to do the following to be able to watch dvds on ubuntu
run this in terminal

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

and then that also in terminal

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

then start the application gxine from  applications > sound and video

---

