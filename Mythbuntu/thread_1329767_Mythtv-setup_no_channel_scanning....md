---
title: "Mythtv-setup no channel scanning..."
date: 2009-11-17
forum: Mythbuntu
---

### Post by beerse on 2009-11-17
As in 2 other threads, I have problems setting up analog channels. ([http://ubuntuforums.org/showthread.php?t=1325556](http://ubuntuforums.org/showthread.php?t=1325556) and [http://ubuntuforums.org/showthread.php?t=1315329](http://ubuntuforums.org/showthread.php?t=1315329)).

While running mythtv-setup, scanning for the channels, in the mythtv-setup-terminal I see the next line roughly at the moment I press the scan button:
========
 DTVParamHelper::toString() index out of bounds
========
There are 2 differences to previous installations:
- the current is 64 bits, previous ones have been 32 bits
- the current uses native (dutch) interface, previous was (default) english.

Is this a bug, a feature or something to get around in some other way?

I donnot expect this to be due to 64 bits installattion, I have the idea this is due to the localizing to dutch, however I donnot have a clue how.

As this is during setup, a workaround is acceptable for me, if someone has something, please report.

btw: unfortunately I did not expect this and liked a fresh install hence did no bother to take a backup...

For what its worth, the card is a haupauge 500 (the dual tuner one)

---

### Post by SiHa on 2009-11-18
You're scanning for analogue channels?
You have a Hauppauge Nova-T 500?

That's your problem, the Nova-T is a DVB-T card, and needs to be stup as a 'DVB MPEG Capture card V3.x' in the backend setup.

---

### Post by beerse on 2009-11-18
No,sorry, not the dvbt card, I have the pvr500, effectively 2 times pvr150 on one card. Works nice if I get it going... Anyhow, it is an analog card which needs some channel information.

btw: I just found a matching bug report at [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/452779](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/452779)

---

### Post by bcambre on 2009-11-19
Have had exactly the same issue with my pvr-500. Progress bar would stay at 0% when scanning channels.

Installed an older 8 something version (which i then upgraded to 9.04), this went perfect for scanning the channels and setting it up.  Very reluctant to upgrade to 9.10 though.

Only way to force scanning channels with 9.10 is to run a manual full scan in the background using ivtv-tune

---

### Post by thusgaard on 2009-11-19
This is a very annoying bug. And I'm considering a downgrade and then an update. If I can get 8.04 working I might just stay with it since its a LTS

J;-)

PS I know I'll be "killed" for saying so. But my friend has the same hardware setup as me and it works with windows 7. The machine originaly came with XP Home.

---

### Post by thusgaard on 2009-11-19
If just done manual tuning of the channels. Works very well. Thanks for the links.

---

### Post by Jim_Rogers on 2009-11-19
I don't know if this is of any help, but I was having the same problem and I have a pvr-500. I'd go to the scan page and try to scan and nothing would happen.

However, if I hit the "fetch channels" button next to it, it gives you no indication it's doing anything (other than holding up the computer for a few seconds), but after that all the channels are there.

If you go to the scan channels page, it still shows nothing, but all the channels are there and it works.

---

### Post by thusgaard on 2009-11-20
Fetch channels dosn't work in Denmark

---

### Post by outleradam on 2009-11-22
I've got the same issue.  I have a HVR-1600 card.

---

### Post by outleradam on 2009-11-24
I've got the same issue.  It's really annoying.  I wish there was some resoloution.  I switched to Ubuntu just for Mythtv.

---

### Post by outleradam on 2009-11-24
There was no mythtv.org ticket.  I opened one.

[http://svn.mythtv.org/trac/ticket/7658](http://svn.mythtv.org/trac/ticket/7658)

---

### Post by dvanbrunt on 2009-11-28
> **bcambre said:**
> 
Only way to force scanning channels with 9.10 is to run a manual full scan in the background using ivtv-tune

How exactly does this work? I am installing the ivtv-utils package now to make this possible... not sure what to do next or how this will affect what gets into the Mythtv datbase...

I had a working system 3 days ago, backed up all my movies and figured I could re-record all my shows eventually... but now, no tuners! 

REALLY took a hit on the WAF... ("why don't we just go buy a TIVO... this doesn't even work")... ouch.

Scanning in the backend-setup just hangs at 5%... 

So with the "manual scan in the background"... does doing "ivtv-tune" on the command line once just solve the problem? Or is there more?

---

### Post by mmoe8800 on 2010-01-30
save this to a file and run it with perl ./tvscan.pl

#tvscan.pl
foreach $channel (0..1000) {
system('ivtv-tune -d /dev/video1 -f ' . $channel);
}

change the video1 for 0 when scanning for the first device on hauphauge pvr 500 and others like it.

/Mike

---

