---
title: "newbie help please - half keys on haup pvr150 remote not working"
date: 2007-12-06
forum: Mythbuntu
---

### Post by arjay1 on 2007-12-06
I have a Hauppauge pvr150 card with the newer Hauppauge grey (silver) remote with the 4 coloured buttons along the bottom.

The remote works fine for numbers,forward and back keys and the mute button - but nothing from pretty well any of the others: the guide, video, or pictures keys or the coloured keys.  However, using IRW correctly identifies ALL the keys.

I have tried replacing the provided lirc file with the one provided by Jarrod Wilson on the mythdora site - but no difference.  EDIT: Found out why.  As well as the lirc file you need a "jumppoints.sql" file which is no longer available from the author's HOWTO guide.

I am a bit confused because after the install I had THREE lirc files - one in /home/richard/.mythtv (main user) one in /home/mythtv and one in /home/mythtv.mythtv.. If I am logged in as richard, presumably it is using the lirc file in /home/richard/.mythtv?  EDIT:  OK found the answer in another post on this site.  Two lircs are redundant.Anyway - I copied the Wilson version over all the above lircs (having backed them up first <g>).

BTW - I also don't understand how I log in as mythtv.  I have tried, but since I was never asked to create the mythtv user or the password I have no idea what the password is!  I have tried the classic mythtv for name and password but no go.

Can anyone help with how to get these keys working?

EDIT; UPDATE - Removed the wilson version of lirc and re-ran the latest version of mythbuntu-lircrc-generator to get the latest lirc file.  Now a few more keys work, including the up/down channel - but nothing on tv, videos, pictures, music, or the four along the bottom.

Many thanks

Richard

---

### Post by armware on 2007-12-09
just wanted to say thanks for keeping this post updated. you're beyond me at this point, but i hope to catch up and help out on this.

---

### Post by arjay1 on 2007-12-09
> **armware said:**
> just wanted to say thanks for keeping this post updated. you're beyond me at this point, but i hope to catch up and help out on this.

OK - I found out a couple more things about the keys.  Apparenbtly, in Mythbuntu, none of the keys other that the pvr ones work - i.e. tv, pictures, video or the ones along the bottom.  See this thread - post 26 on page three:


[http://ubuntuforums.org/showthread.php?t=621771&goto=newpost]("http://ubuntuforums.org/showthread.php?t=621771&goto=newpost")

---

