---
title: "Ubuntu 12.04: No mp3 in Clementine"
date: 2012-07-17
forum: Multimedia Software
---

### Post by amalgamas on 2012-07-17
I have tried everything I could find on the net and in the forums: installed and reinstalled the "restricted extras", fluendo, you name it.  I have removed, purged, then reinstalled.  But no way I can get Rhythmbox or Clementine to play mp3-files.  I hear a short sound, then it stops.

flac-files and some other formats play normally in both players.

mp3 files play normally in mplayer.

I need help!

---

### Post by BicyclerBoy on 2012-07-17
Clementine uses gstreamer backend (I think)..

Check you have gstreamer plugins good, bad & ugly..the fluendo plugins are a likely a better quality decoder, but mp3 is often over compressed & low sample rate to begin with..

---

### Post by amalgamas on 2012-07-19
Thanks for the reply.  I already  had that in place, and redid the procedure.  Still no mp3 in Clementine.

Should I buy the Fluendo thing?  What are the benefits, and will it make Clementine/Rhythmbox play mp3's?

---

### Post by shantiq on 2012-07-19
in your synaptic    do you have all these installed?   if not install them.   all of them are free.    2 images shown below


[ATTACH]221487[/ATTACH]
[ATTACH]221486[/ATTACH]

---

### Post by BicyclerBoy on 2012-07-19
I don't think a mp3 decoder is worth the money..
I have no problem playing mp3 in Clementine (just checked with 12.04 & latest Clementine daily build)
Was harder to find one to play..

Install:
ubuntu-restricted-extras

Then reload/refresh synaptic/apt-get etc & then this should bring in libavcodec-extra-53 etc..

Check you have (free):
gstreamer0.10-fluendo-plugins-mp3-partner 
(this is same as "shantiq" screenshot)

---

### Post by amalgamas on 2012-07-19
thank you for your help, but...

Once again I have done all reinstalling/apt-get/synaptic I ca think of. Strange things are happening: if I try to remove gstreamer-related libraries in Synaptic, it crashes (eg. phonon-backend-gstreamer and others).  I have tried to remedy it by:[INDENT]sudo apt-get update
sudo apt-get dist-upgrade -f
sudo apt-get clean
[/INDENT]So I use apt-get, but trying to remove ubuntu-restricted-extras (for a clean reinstall) automatically installs kubuntu-restricted-extras.  I have even seen xubuntu-restricted-extras during my trials.  Seems I cannot get rid of the files for clean reinstall

These are the files I think are relevant (from synaptic):

[ATTACH]221512[/ATTACH]

[ATTACH]221513[/ATTACH]

[ATTACH]221514[/ATTACH]

I am about to give up, luckily most of my music collection is .flac-files

---

### Post by shantiq on 2012-07-19
amalgamas


you have not installed the one that matters   on your second picture it is   **[unticked]("http://ubuntuforums.org/attachment.php?attachmentid=221514&d=1342727428")**

we both advised you to install it


please try that and see:KS

---

### Post by amalgamas on 2012-07-19
The Fluendo plugins: I have tried both. they are mutually exclusive, I install one then the other one is automatically removed.  I googled it and the partner thing seems to be the preferred one in ubuntu 12.04 amd64

---

### Post by shantiq on 2012-07-20
ok well:KS puzzling puzzling....



how about a total cleanse and reinstall



```
sudo apt-get remove --purge clementine
```    and then reinstall

---

### Post by BicyclerBoy on 2012-07-20
Some ideas here..
[http://forums.opensuse.org/english/get-technical-help-here/applications/457259-clementine-error-can-not-play-mp3-3.html](http://forums.opensuse.org/english/get-technical-help-here/applications/457259-clementine-error-can-not-play-mp3-3.html)

Could rename ~/.gstreamer-0.10/registry.x86_64.bin

or
renaming folder ~/.config/Clementine/

don't delete or you'll have to rebuild the database & download artwork..

---

### Post by amalgamas on 2012-07-21
(I thank you guys for your efforts, but I am afraid nothing helps.  I am about to give up and will have to use another player for mp3s.  To bad I really like that Clementine.)

EDIT!!!: While writing this (and the below message) I copied a mp3 from my NAS to my PC and tried to play the local mp3-file. ***It played!***  All my mp3's are located on a NAS which I use for all media.  HD videos and flac-files from this player play without problems.  mp3s played without problems in ubuntu 11.10.  

Which of course raises a new question: what happened to the mp3-transfer from that NAS in ubuntu 12.04?
************************************************************************************
Just to show you that I really have tried I leave the log of todays efforts in 

To day I did the following:

[LIST]
[*]removed all packages with :i386 in the name.  That made Clementine disappear (among other programs I use including Rhythmbox), additionally I purged it.
[*]then I removed every mp3-related package I could think of (then reinstalled the ones I needed).  See pictures of my packages:

[ATTACH]221573[/ATTACH]

[ATTACH]221574[/ATTACH]

[ATTACH]221575[/ATTACH]


(the packages shown are after reinstall of Clementine.  I have tried both fluendo-plugins)
[*]when Clementine was purged I installed a small command-line player called gst123
[*]even this did not help.  It played 1 sec, then stopped
[*]than I used strace to log the processes (truncated at 200 lines):
[ATTACH]221576[/ATTACH]
[ATTACH]221577[/ATTACH]
[/LIST]
..this is where I left off after being able to play a local mp3
******************************************************************************
Now I will go for a run in the sun.  Then I will reinstall lost programs and start pondering over what happened to mp3-transfer from my NAS.

One question remains:

[LIST=1]
[*]Is it impossible to remove the restricted extras?  If I remove the ubuntu r-e, kubuntu r-e are automatically installed and vice versa.
[/LIST]

Ok, guys, I regret having bothered you with the wrong problem.  But if anone culd suggest what happened to mp3's from my NAS, I would still be grateful

---

### Post by amalgamas on 2012-07-21
I have tested the issue  a little:

when I play the file from the NAS  in gtk123/clementine, the network goes haywire.  I get download speeds over 2MB/sec, normally I can't get over 1.2Mb/Sec.  The music plays for 1 sec, then silence.  The counter in the player continues normally and the network load stays over 2Mb/s.  

when I play the local file in gtk123/clementine it plays normally and I see nothing strange

I am going away for some time.  When I come back I will start a new thread: Rhythmbox/Clementine: no mp3 from NAS

---

### Post by oldos2er on 2012-07-21
Have you tried running Clementine from a terminal, load an mp3, and check the terminal output? Might be worth a try.

---

### Post by amalgamas on 2012-07-30
Back again

Yes I have tested the output in the terminal.  I see no differences:
[ATTACH]221976[/ATTACH]

NB: the "Invalid sample rate"-messages in Clementine refer to the local file that played normally.

I will now open a new thread

Edit:
It is definitely a network issue.  I use a hidden credentials file to log in to my NAS, but when I write username and password directly into fstab, the mp3's from my NAS play normally.  Remember: flac-files (the majority of my music) played correctly all the time.  And: nothing is changed in fstab and my cred-file since 11.04, when mp3's also played correctly.

---

### Post by amalgamas on 2012-07-31
I finally solved the problem.

I have set up my own fstab file a couple of years ago as well as I was able to.  But being a linux n00b I put in the parameters in a trial and error fashion.  Finally I was able to get a working fstab, which worked up to ubuntu ver. 11.10.  For some reason it doesn't under 12.04.

Removing the "directio" parameter from my fstab solved the problem and gave higher network throughput.  

As I regret having used precious time for the people that helped with the issue I will mark the issue as solved.

Btw: where is the fstab manual that also explains to us normals what all those shady parameters mean and do?

---

