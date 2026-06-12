---
title: "Error reading copied VOB files from disk with Totem"
date: 2011-03-12
forum: Multimedia Software
---

### Post by kenotoole on 2011-03-12
Trying to copy videos from DVD to disk for backup using Ubuntu 10.10. These are home movies so I'm not dealing with any copy protection issues. The movies were transferred from VHS to DVD using a SONY DVD burner.

After successfully copying files from DVD to disk, 2 of the 3 files return the following error from Totem " An Error Occured Could not determine type of stream". 
I am able to succesfully play the third file.

here's some details.
Totem Movie Player 2.32.0
Movie Player using GStreamer 0.10.30

Here are the files after copying
kenotoole@kenotoole-ME052:~/Videos/bball$ ls -lh
total 2.5G
-rwxr-xr-x 1 root root  12K 2011-03-12 13:18 VIDEO_TS.BUP
-rwxr-xr-x 1 root root  12K 2011-03-12 13:18 VIDEO_TS.IFO
-rwxr-xr-x 1 root root  96K 2011-03-12 13:18 VIDEO_TS.VOB
-rwxr-xr-x 1 root root  62K 2011-03-12 13:18 VTS_01_0.BUP
-rwxr-xr-x 1 root root  62K 2011-03-12 13:18 VTS_01_0.IFO
-rwxr-xr-x 1 root root 1.0G 2011-03-12 13:19 VTS_01_1.VOB
-rwxr-xr-x 1 root root 1.0G 2011-03-12 13:20 VTS_01_2.VOB
-rwxr-xr-x 1 root root 487M 2011-03-12 13:29 VTS_01_3.VOB
kenotoole@kenotoole-ME052:~/Videos/bball$ file *
VIDEO_TS.BUP: Video manager, v11
VIDEO_TS.IFO: Video manager, v11
VIDEO_TS.VOB: MPEG sequence, v2, program multiplex
VTS_01_0.BUP: Video title set, v11
VTS_01_0.IFO: Video title set, v11
VTS_01_1.VOB: data
VTS_01_2.VOB: data
VTS_01_3.VOB: MPEG sequence, v2, program multiplex

I can view VTS_01_3.VOB without a problem but recieve the error message with the other two VTS_01_1.VOB and VTS_01_2.VOB. Not 
sure why the problem files are type "data".

Similar results with VLC 1.1.4 media player.

Any ideas?

Thanks for any help you can provide.

Ken

---

