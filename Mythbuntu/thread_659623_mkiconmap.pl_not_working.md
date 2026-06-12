---
title: "mkiconmap.pl not working"
date: 2008-01-05
forum: Mythbuntu
---

### Post by aaltieri on 2008-01-05
Greetings.

I'm having some trouble getting the mkiconmap script to work.  I am getting the following when I try to run it:


> $ perl mkiconmap.pl --grab --share=/tmp --out=iconmap.xml 
Calling tv_grab_na_icons...

Postal Code: 18702

Lineup?
0: 4DTV (USA)
1: AFN Satellite (USA)
2: Alaska
3: C-Band (USA)
4: Central
5: Comcast - Cable (Dunmore)
6: Comcast - Digital (Dunmore)
7: DIRECTV (USA)
8: DIRECTV Wilkes Barre (Wilkes Barre)
9: DISH Network (USA)
10: DISH Wilkes Barre (Wilkes Barre)
11: Eastern
12: Hawaii
13: Local Broadcast (Antenna)
14: Mountain
15: Pacific
16: Service Electric Company - Cable (Wilkes Barre)
17: Service Electric Company - Digital (Wilkes Barre)
18: Sky Angel (USA)
Select one: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18 (default=11)] 16
ERROR:No icons were found.  Please check 'na_icon_error.html'
Generating iconmap.xml...

I have tried the direction listed at:

[http://www.gossamer-threads.com/lists/mythtv/users/209254?nohighlight=1#209254]("http://www.gossamer-threads.com/lists/mythtv/users/209254?nohighlight=1#209254")

to see if it helped, and not dice.

I've tried running the script found in the contrib directory as well as the one listed in PLB's walk thought at:

[http://https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons]("http://https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons")

The odd thing is that when I open na_icon_error.html with my favorite browser, it is a copy of the zap2it page with all the icons there smiling at me in the guide.  iconmap.xml is empty.

Does any one have any idea what I might be missing here to make this work?  I can't find anyone else having this problem, so I figure I'm doing something stupid.  Or...not doing something...one or the other.

thanks!


Anthony

---

### Post by Anubis on 2008-01-10
[http://www.mythtvtalk.com/forum/viewtopic.php?t=7104](http://www.mythtvtalk.com/forum/viewtopic.php?t=7104)

---

### Post by aaltieri on 2008-01-10
heh...that was my post there too, actually.


Thanks though!  At least someone responded!

---

### Post by Anubis on 2008-01-11
> **aaltieri said:**
> heh...that was my post there too, actually.


Thanks though!  At least someone responded!


:lolflag:

---

### Post by Kawayanan on 2008-01-11
I have had the same problem as you.  I even [posted about it]("http://ubuntuforums.org/showthread.php?t=658654") too.  My post go no replies.  :(  I tried both methods I could find ([here]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons") and [here]("http://www.mythtv.org/wiki/index.php/Channel_icons")).  I finally just went to [this webpage]("http://www.lyngsat-logo.com/") and downloaded a couple of icons.  I can manually add them to each channel without  problem.  I just don't want to do that for 100 channels. :(

Maybe someone will eventually post some suggestions. :)

---

### Post by aaltieri on 2008-01-11
Kawayanan

Actually, the post referenced by Anubis, has the answer.  It links to a page that links to:

[http://www.mythtv.org/wiki/index.php/Channel_icons]("http://www.mythtv.org/wiki/index.php/Channel_icons")

Which I think is one of the pages you tried.  For me, it worked.  Now, I'm in North America.  I'm not sure that made a difference.  When I went through that process I noted three things:

1) I had to manually select about twenty of my icons, although it found suitable replacements auto-magically.

2) Since I didn't map my digital channels to the normal channel numbers yet, it didn't find any icons for those.  So I would recommend setting up your tuners and lineups COMPLETELY before running this.

3) the directory setup isn't exactly right.  You need to enter the literal path to where you want the icons saved, not the relational path.  So enter "/home/myuser/.mythtv" not "../.mythtv"  It will LOOK like it worked as it will create the directory and put all the icons there.  But when you look at the database, the icons are reported as being stored in "/../.mythtv"  Atleast mine were.

You may need to install subversion to get updated script.




EDIT -- Oh...and PAY ATTENTION TO THE BUG NOTICE!!! You will need to edit the script once you have it, but it's an easy edit to do. 

The Ubuntu guides do need to be updated to reflect the newer version of Mythtv.  If you run into any problems with this, let me know and I'll try to help as best as I can.

---

### Post by laga on 2008-01-12
There's a new and spiffy version of the channel icons script in trunk, maybe you can use that for 0.20.x as well. Don't break anything :) (Read: get a database backup at least).

---

### Post by lingenfr on 2008-01-17
Will this be integrated into mythbuntu at some point? I am hoping to maintain my backend as a pristine mythbuntu and don't really want to start adding a bunch of crap. Unfortunately, I didn't think to back up my channel icons before I rebuilt my machine. Rats.

---

### Post by Big_Rog on 2008-03-10
As mentoined in another post, the automatic retreival that's in 0.21 will be with the 8.04 release of mythbuntu.  until then...?

---

