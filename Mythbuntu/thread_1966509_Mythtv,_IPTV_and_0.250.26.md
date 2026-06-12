---
title: "Mythtv, IPTV and 0.25/0.26"
date: 2012-04-27
forum: Mythbuntu
---

### Post by larsbj on 2012-04-27
Hi

I have upgraded my mythbuntu 11.10 to 12.04. My original setup was 0.24 with IPTV configured, and update to 0.25. That didn't work out. So clever as I am, I google and find that there is a problem concerning IPTV, and there is none expactation to get it solved in 0.25, and a rewrite of the code has begun in 0.26. So just jumping into it and mark 0.26 as the one I want to use in the mythtv control panel. So here I am by now. I can see one livetv channel, the one I left last time i left mythtv. If changing channel the frontend chrashes and the next recorder in line is picked up. When all recorders has been used I get all recorders are busy, and nothing more happens, other than a littlg glimpse from the frontend. Any help to get along with this.

larsbj

---

### Post by ian dobson on 2012-04-29
Hi,

You know that 0.26 is a development branch and will be quite often broken. What's the actual problem you had with 0.25 and IPTV?

I've just upgraded to 0.25 and the IPTV changes (Channel change script no longer used) broke my system abit. As I miss used the IPTV tuner to grab video from VLC that grabs data from my Dreambox recorder.

I'm working on a script that sees when the next recording from the Dreambox is and sets up the Dreambox/VLC from outside MythTV. So that when MythTV starts the actual recording VLC is ready to supply the video.

Regards
Ian Dobson

---

### Post by vince2k on 2012-05-11
I have the same problem as larsbj, where switching channels of the IPTV seems broken. 

Have you found a solution?

---

### Post by ian dobson on 2012-05-11
Hi,

The problem is that the iptv recorder leaves the tuner open (and writes to the fs) after the recording is finished.

There are afew patches here ( [http://code.mythtv.org/trac/ticket/10493#](http://code.mythtv.org/trac/ticket/10493#) ) that seem to fix it. I've not tested them and the mythtv devs seem to ignore them.

Regards
Ian Dobson

---

### Post by vince2k on 2012-05-15
I've build a mythtv version from the patches you ian mentioned, and used a separate database (i.e., a 'fresh' setup). I was able to configure multiple IPTV cards, where in mythtv-setup you now can parse your playlist. 

I guess the new code reads you playlist upon setup and stores the 'tuner information' to the database, instead of downloading the playlist every time you start mythbackend.
The new tables iptv_channel in the database seem to confirm this. So I guess that you should run mythtv-setup again after upgrading to 0.25+fixes+rtp (which you have to build yourself), and do the proper channel setup.

---

### Post by ian dobson on 2012-07-08
Hi,

Looks as if the is a fix for this:- [https://github.com/MythTV/mythtv/commit/d83672529ac1d851d67ca0c06b0b11b64e141119](https://github.com/MythTV/mythtv/commit/d83672529ac1d851d67ca0c06b0b11b64e141119)

Does anyone know if this patch made it into the .25-fixes branch.

Regards
Ian Dobson

---

### Post by vince2k on 2012-08-20
I've just installed the latest mythtv version, which seems to include the above mentioned patch.  I can watch the first channel. However, I still cannot switch channels and it thus does not seems to fix all problems..

But it might be a configuration issue in my virtual machine..

---

### Post by ian dobson on 2012-08-24
Hi vince2k,

After finishing recording, does MythTV actually stop recording?

The IPTV recorder in 0.25 doesn't call the channel change script anymore, as the dev's say the the source should always be the same/one ip address : port combination per channel.

Regards
Ian Dobson

---

