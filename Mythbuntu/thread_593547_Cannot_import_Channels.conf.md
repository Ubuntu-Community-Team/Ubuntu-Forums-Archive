---
title: "Cannot import Channels.conf"
date: 2007-10-27
forum: Mythbuntu
---

### Post by dark_ixion on 2007-10-27
I've successufully scanned all the satellite channels on my Hauppauge Nova-S Plus card and have a Channels.conf file.  When I give this to MythTV backend setup it doesn't complain, but then it gets stuck on 3% scanning for channels.

I can't work out what is wrong here.  I can see the channels if I type mplayer dvb://[channel name] but I can't get MythTV to pick them up.  I've even gone into the Watch TV section on the MythTV frontend to see if it's still stored them, but it's just a blank channel.

Can anyone help?  Is this a bug?

---

### Post by bawilson2 on 2008-03-04
Have you found any solution for this problem?  I'm getting the exact same thing!

---

### Post by bawilson2 on 2008-03-05
I finally figured this thing out.  It sounds like there is sometimes a problem with the 0.20 version and importing a channels.conf file.  What I did was add each frequency as a transport.  Then when I scanned for channels I told it to search existing transports.  After that everything worked just fine.

---

