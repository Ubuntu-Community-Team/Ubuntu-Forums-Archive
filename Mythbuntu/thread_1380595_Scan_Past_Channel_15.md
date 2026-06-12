---
title: "Scan Past Channel 15"
date: 2010-01-13
forum: Mythbuntu
---

### Post by NertSkull on 2010-01-13
So I have the Happauge HVR-1600 and have it set up to receive analog cable signal, but I can't get it to scan past channel 15.  Any ideas?  Details below.

-Mythbuntu 9.10 - fresh install as of two days ago.
-v4l-dvb drivers installed exactly according the MythTV wiki page for that card
-Hauppauge HVR-1600, just a week old (replaced an ancient Hauppauge that won't work with the new myth 0.22)
-If I boot into windows XP and use WinTV 7 I get ALL the channels
-When I scan for channels in mythtv-setup it will scan to channel 14 and then hang up on 15.  It will just sit on channel 15 for forever (i've let it sit up to 30 minutes) and just say "No Lock" and never move past 15.
-If I scan for channels, let it hang, click on back, scan for channels again it will ad 16, then i hit back and then scan again and it will ad 17.  I can keep doing this and it will eventually add all those channels.  BUT all those channels come in with no signal if I do that.  Just white noise
-Digital ATSC antenna seems to work fine and I get that just fine.
-My cable is analog cheap cable (I think that makes it NTSC, but not 100% positive).

Let me know if there is anything else I can provide to be helpful.

---

### Post by OffAxis on 2010-01-14
There are related bug reports here:

[http://svn.mythtv.org/trac/ticket/6530](http://svn.mythtv.org/trac/ticket/6530)

and here:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/452779](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/452779)

---

