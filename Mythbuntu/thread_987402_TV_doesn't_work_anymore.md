---
title: "TV doesn't work anymore"
date: 2008-11-19
forum: Mythbuntu
---

### Post by nexusgx on 2008-11-19
I just installed Mythbuntu 8.10 two nights ago, and when I booted it up for the first time, the TV option worked.  I was able to flip through the channels and watch tv.

Now, suddenly, as I was trying to watch TV on it today, it doesn't work.  It goes to black and the kicks me back to the main menu.

I have tried manually recording through the command line using the cat command, but that returns a whole mess of symbols that doesn't stop until I manually stop the script, not to mention nothing is recorded.

I have a pvr-250 (ivtv).  If I need to give any more information, please let me know.

---

### Post by issih on 2008-11-19
Make sure that the server side of things is up and running. try running the following in a terminal:

```
sudo /etc/init.d/mythtv-backend restart
```

and enter your password when prompted.

That ought to restart the server. Try running the front end again once you have done that.

Hope that helps

---

### Post by nexusgx on 2008-11-19
> **issih said:**
> Make sure that the server side of things is up and running. try running the following in a terminal:

```
sudo /etc/init.d/mythtv-backend restart
```

and enter your password when prompted.

That ought to restart the server. Try running the front end again once you have done that.

Hope that helps

Didn't work.  Restarted just fine, but still won't play any tv channels

---

### Post by rnelson0 on 2008-11-19
I'm having the exact same problem. This problem just started this morning. I was able to watch Live TV fine earlier. I can watch what has already been recorded.

Here is some more info:

- When I do a channel scan, it finds the channels and signal strength is good.

-When I go to 'Upcoming Recordings', all of my recordings are listed, but they are all highlighted red with the note 'Channel Record -- Recorder Off-Line"

-MythWeb shows NO upcoming recordings when it should list upwards of 10.

-When I try to edit an upcoming recording, it tells me that it will not be recorded because the backend recorder is off line.

Any help? Anybody seen this before?

---

### Post by dmfrey on 2008-11-19
i am not sure if this will help at all or not, but I have read that with multiple capture cards in, the order of the cards attached to /dev/video0 and /dev/video1 may switch.  I have two cards, a 150 and pcHDTV-5500.  I found a post that tells you to set an option that always ties the card to a specific input.  This was specific to the pcHDTV card, but may still apply to your problem as well.

See the issues section here: [http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500](http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500)

and adapt if it applies to your cards as well.

---

### Post by nexusgx on 2008-12-02
> **dmfrey said:**
> i am not sure if this will help at all or not, but I have read that with multiple capture cards in, the order of the cards attached to /dev/video0 and /dev/video1 may switch.  I have two cards, a 150 and pcHDTV-5500.  I found a post that tells you to set an option that always ties the card to a specific input.  This was specific to the pcHDTV card, but may still apply to your problem as well.

See the issues section here: [http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500](http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500)

and adapt if it applies to your cards as well.

That didn't seem to help any.  Thanks for trying, though.

---

### Post by hardyn on 2008-12-14
**solved** major brain cramp

> **nexusgx said:**
> I just installed Mythbuntu 8.10 two nights ago, and when I booted it up for the first time, the TV option worked.  I was able to flip through the channels and watch tv.

Now, suddenly, as I was trying to watch TV on it today, it doesn't work.  It goes to black and the kicks me back to the main menu.

I have tried manually recording through the command line using the cat command, but that returns a whole mess of symbols that doesn't stop until I manually stop the script, not to mention nothing is recorded.

I have a pvr-250 (ivtv).  If I need to give any more information, please let me know.

exactly the same issue, although i never had it running.

i can open /dev/video0 in mplayer, so the capture card works.  I have had mythtv working by adding mythtv to linux mint.

I have read threads about permissions and having directories for liveTV and recording... everything should be right.

I was thinking about trying a reinstall and see if that helps, although i somehow dont think it will.

anybody have any other ideas?  i am only running one pvr-150

---

### Post by joho500 on 2009-01-18
Hi Hardyn,

Did you find a solution for your problem? I've encountered the same problem after updating to 8.10 yesterday.

Cheers,
Joost

[edit] It seems that ivtv is broken in 8.10. I found a solution in this post: [http://www.uluga.ubuntuforums.org/showpost.php?p=6096932&postcount=6]("http://www.uluga.ubuntuforums.org/showpost.php?p=6096932&postcount=6") [/edit]

---

