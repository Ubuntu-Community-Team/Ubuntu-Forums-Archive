---
title: "vobcopy errors"
date: 2010-08-18
forum: Multimedia Software
---

### Post by wurlyfan on 2010-08-18
Hello all, please help a noob!

Has anyone successfully used vobcopy to merge .vob files that are  already on the hard disk? ? I am running 10.04 LTS with vobcopy 1.1.0 to  merge multiple .vob files into one .vob file in preparation for ffmeg conversion to avi..

When I start vobcopy I get the error "Could not find the provided path"  however I try to specify it. The terminal output follows ...

graham@graham-desktop:~$ pwd
/home/graham
graham@graham-desktop:~$ ls V*
Videos:

VIDEO_TS:
VIDEO_TS.BUP  VTS_01_0.BUP  VTS_01_1.VOB  VTS_02_0.VOB  VTS_02_3.VOB
VIDEO_TS.IFO  VTS_01_0.IFO  VTS_02_0.BUP  VTS_02_1.VOB  VTS_02_4.VOB
VIDEO_TS.VOB  VTS_01_0.VOB  VTS_02_0.IFO  VTS_02_2.VOB

graham@graham-desktop:~$ vobcopy -i /home/graham/VIDEO_TS -v -n1 -l -o /home/graham
[Hint] You use -i. Normally this is not necessary, vobcopy finds the input dir by itself. This option is only there if vobcopy makes trouble.
[Hint] If vobcopy makes trouble, please mail me so that I can fix this (robos@muon.de). Thanks
Vobcopy 1.1.0 - GPL Copyright (c) 2001 - 2007 [EMAIL="robos@muon.de"]robos@muon.de[/EMAIL]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library
[Error] Could not find the provided path (/home/graham), typo?
[Error] Could not get the device which belongs to the given path!

Can anyone suggest an alternative solution for vob merging?

My thanks to anyone who can help ;)

---

### Post by musicisbest on 2010-08-18
You can convert the vob files to avi and then merge the avi files with mencoder providing your avi files are encoded the same:

mencoder -oac copy -ovc copy file_1.avi file_2.avi file_3.avi -o final.avi

I'm no expert but that has worked for me.

---

