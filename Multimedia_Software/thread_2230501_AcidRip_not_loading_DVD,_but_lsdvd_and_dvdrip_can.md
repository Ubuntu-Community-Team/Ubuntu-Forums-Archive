---
title: "AcidRip not loading DVD, but lsdvd and dvd::rip can"
date: 2014-06-19
forum: Multimedia Software
---

### Post by superian on 2014-06-19
I know I used to use AcidRip with 13.10, but since upgrading to 14.04, it can't load the DVD properly.

If I set the Path to /dev/sr0 (SATA-connected DVD drive) the log file says:

```
AcidRip message - dvd_device has been set to /dev/sr0
AcidRip message - Reading DVD / file(s)... please wait
AcidRip message - DVD read ok
```

.. but no 'tracks' appear to select from.

The default reader is lsdvd, and it can get the streams:

```
$ lsdvd /dev/sr0
Disc Title: SOME_DVD
Title: 01, Length: 01:10:10.680 Chapters: 12, Cells: 12, Audio streams: 01, Subpictures: 01

Title: 02, Length: 00:02:16.000 Chapters: 12, Cells: 12, Audio streams: 01, Subpictures: 00

Title: 03, Length: 00:00:01.480 Chapters: 01, Cells: 01, Audio streams: 00, Subpictures: 00

Longest track: 01
```

.. and dvd::rip can too.

So why not AcidRip?

---

### Post by Yellow Pasque on 2014-06-19
I wonder if it's: [https://bugs.launchpad.net/ubuntu/+source/acidrip/+bug/1310049](https://bugs.launchpad.net/ubuntu/+source/acidrip/+bug/1310049)

---

### Post by superian on 2014-06-19
Ah, that looks very plausible, thanks for confirming it probably isn't 'just me' :)

Given there's a patch, I wonder what's the delay is in fixing this...

---

### Post by Yellow Pasque on 2014-06-19
I really doubt they're going to backport it to main Trusty repo. The patch may not have the intended effect either: [https://bugs.launchpad.net/ubuntu/+source/lsdvd/+bug/1330415](https://bugs.launchpad.net/ubuntu/+source/lsdvd/+bug/1330415)

---

### Post by superian on 2014-06-20
A quick look shows that later Debian packages don't depend on anything dramatic, and so install fine.

Installing  lsdvd 0.16-5 (compared to Ubuntu's 0.16-4) doesn't work with the Ubuntu  acidrip, and the 0.14-0.3 acidrip still has the same issue.

Hmm. If dvdrip weren't good enough, and my Perl was good enough, I'd be doing diffs with older versions to see what happened.

---

### Post by superian on 2014-06-20
"lsdvd 0.16-5 (compared to Ubuntu's 0.16-4) doesn't work with the Ubuntu  acidrip" - as in 'doesn't make it work'.

---

### Post by alanbowden on 2014-08-31
You can make it work by installing the old version of lsdvd from 13.10. The only problem with this fix is that you need to do it each time you update your system.
Download lsdvd_0.16-3ubuntu1_amd64.deb from:
[http://pkgs.org/ubuntu-13.10/ubuntu-universe-amd64/lsdvd_0.16-3ubuntu1_amd64.deb.html](http://pkgs.org/ubuntu-13.10/ubuntu-universe-amd64/lsdvd_0.16-3ubuntu1_amd64.deb.html)
Then install it as follows
sudo apt-get remove lsdvd  (This will remove acidrip too)
sudo apt-get install acidrip

Note that dvdrip also depends on lsdvd so if you use that too, it also needs to be reinstalled each time.

---

### Post by Yellow Pasque on 2014-08-31
You can put the packages on hold so they don't get updated. [https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages](https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages)

---

### Post by digitography on 2015-03-06
I am not sure if this is the correct way to fix it, but here is what I did

[http://digitography.co.uk/digitographyblog/?p=590](http://digitography.co.uk/digitographyblog/?p=590)

---

