---
title: "NPR (National Public Radio) and Ubuntu"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by drhiii on 2007-09-09
I know this has been slightly beat up, but I have not found a good solution without breaking something else.

Am looking how to tweak either Firefox, Konqueror, Opera, or whatever, to be able to listen to NPR off of their web site.  I can slurp down live feeds, but I am unable to go to their site and play their streams.  

Have tried the above three and get same results.  It won't play, but when I click to go to a Standalone Player, RealPlayer 10 pops up, and stalls.  

I went through a series of steps on a prior machine to enable multimedia and ended up downloading a ton of codes and applications, and things go goofy from there.  Right now, almost everything works on this fresh installation of Feisty and I want to stay this way, reasonably at least.  

Soooo, anyone have recommendations as to how to tweak up NPR and perhaps other multimedia types beyond the out of the box installation Feisty ones?  

tx

---

### Post by u-slayer on 2007-09-09
Download VLC

$sudo apt-get install vlc

Then launch the standalone player and save the .wax file to your desktop and open it with vlc

Vlc is great because, unlike totem, it doesn't need a bunch of "goofy codecs". It just works.

---

### Post by drhiii on 2007-09-09
Tx for this advice.  It makes sense and also in keeping with other stream casts I listen to where I pull them down.  This way at least I don't have to start down the install-everything road which ends up creaking more havoc than it solves....

regards and thank you for the very fast response...


> **u-slayer said:**
> Download VLC

$sudo apt-get install vlc

Then launch the standalone player and save the .wax file to your desktop and open it with vlc

Vlc is great because, unlike totem, it doesn't need a bunch of "goofy codecs". It just works.

---

### Post by the badger on 2007-09-26
hi there - i'm having the same issue with NPR and listening to older programs. I've tried saving the .wax file and opening with vlc, but it doesn't work. file open's and vlc quits after a few seconds. it seems like there isn't the right/complete info there.

i thought that maybe if i choose "open with..." and select something from the vlc file i could get it to work - however i don't know which file i am looking for in there (hello, i'm new).

any other suggestions?

---

### Post by adpatter on 2007-10-06
NPR seems to stream pretty well using the RealPlayer.



Using Ubuntu 7.04, and installing RealPlayer with the Synaptic Package Manager, NPR streams work.

First add the repository that contains RealPlayer.  (Adapted from [http://www.debianadmin.com/install-opera-web-broweser-and-realplayer-10-in-ubuntu.html](http://www.debianadmin.com/install-opera-web-broweser-and-realplayer-10-in-ubuntu.html))
 
One way to do this is to open a terminal window and enter the command:

sudo gedit /etc/apt/sources.list

Add the following text to sources.list.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

Save and close sources.list.

Open the Synaptic Package Manager.

Search for realplay.

Install RealPlayer.

The Synaptic Package Manager puts the Firefox RealPlayer plugins in the proper place.  ([http://plugindoc.mozdev.org/linux.html#RealPlayer](http://plugindoc.mozdev.org/linux.html#RealPlayer))

Open Firefox.

Open [http://www.npr.org](http://www.npr.org)

Left click "24-hour Program Stream".

A window will open.

Left click "Set Player Preference".  (Try deleting cookies if there is no response.)

Choose RealPlayer.

---

### Post by JoseArmandoJeronymo on 2007-10-07
In case this helps, I listen to many NPR stations with Beep Media Player (it works even when Click & Clack identify themselves as NPR).

I installed BMP from Synaptic and created a folder called "webradios" which I populated with program launchers with "beep-media-player [http://.](http://.).. stream url ..." in the property>launcher>command field.

All I have to do is to click on the launcher and BMP loads the stream.

(BMP is excellent for MP3 and Ogg streams. For WMA I use gxine instead.)

---

### Post by drhiii on 2007-10-10
So I must ask, how do you create the [http://url](http://url) in a Launcher.  When I right click to Copy Link Location on say, NPR or the following which is Fresh Air, it returns something like the following:

javascript:launchPlayer('13','2', '10-Oct-2007', '&prgCode=FA&tableModifier=&v1st=169780B1665AA3A9', 'RM,WM');

Where, how to extract the URL from this?   Would be cool to learn as this plagues me every time I try to listen.  

By the way, I did slurp down Beep Media Player and I like this quite a bit more than other media players.   Is very simple and smooooth.  Tx for this pointer.  




> **JoseArmandoJeronymo said:**
> In case this helps, I listen to many NPR stations with Beep Media Player (it works even when Click & Clack identify themselves as NPR).

I installed BMP from Synaptic and created a folder called "webradios" which I populated with program launchers with "beep-media-player [http://.](http://.).. stream url ..." in the property>launcher>command field.

All I have to do is to click on the launcher and BMP loads the stream.

(BMP is excellent for MP3 and Ogg streams. For WMA I use gxine instead.)

---

### Post by JoseArmandoJeronymo on 2007-10-12
I think you are using their webpage javascript link to the tuner pop-up instead of the stream URL.

I think a step-by-step example may help. Let's say WNYC.

1. go to their webpage wnyc.org (right now they're on a fund raising drive, skip that for now)
2. at their homepage left side there is a list of streams. Pick an MP3 stream, let's say the FM one (which, as of this writing is straming Fresh AIr). RIGHT-click on it and copy the link location.
3. Open that link in another tab by pasting it on the address box.
4. In my Firefox it opens the MediaPlayer Connectivity plug-in, so if the below does not work for you please install MPC.
5. Ctrl+U to see the page source and, voilà, there you will find the URLs:

[playlist]
NumberOfEntries=3
File1=http://wnycfm.streamguys.com/
Title1=WNYC 93.9 FM
File2=http://wnycfm2.streamguys.com/
Title2=WNYC 93.9 FM
File3=http://wnycfm3.streamguys.com/
Title3=WNYC 93.9 FM
Version=2

6. Pick one and use it in your launcher as I earlier suggested.

Some streams are harder to find out than others but in general the trick is to see the page source of the (right!) page. On NPR's website I navigated until I reached a pop-up with Real and WM logos on it. I clicked on the latter, saw the source of the page that opened (right into the pop-up) and copied this URL to a launcher:

mms://a1671.l2063252432.c20632.g.lm.akamaistream.net/D/1671/20632/v0001/reflector:52432?v1st=EE8CA0BA5451DA43&mt=5

It worked fine.

I hope the above helps you and please let me know if it doesn't.

---

### Post by drhiii on 2007-10-12
Thank you for the response.  

The method for extracting the mp3 and ogg streams makes sense and I have been reasonably successful at that.

Am still wrapped around the axle however with NPR.  Just trying to listen to a Morning Edition replay, or anything else, is still not mastered.  I do get theat Real/WinMedia popup and I look at the source, but I do not see a 'call' for the .wm stream, like the mms: line.  The next thing I get is to either run an application or Save to Disk, and it is not always the same.  It either goes to a .wax file, or sometimes I can get as far as a .smil file.   Part of this is deleting cookies and trying to start over because things get 'selected' and then you can;t get to new popups or views that would provide the kind of link you describe for something like NPR.  It is a drag because for all the wonderful thing in Ubuntu, media play is a maze.

Thoughts....


> **JoseArmandoJeronymo said:**
> I think you are using their webpage javascript link to the tuner pop-up instead of the stream URL.

I think a step-by-step example may help. Let's say WNYC.

1. go to their webpage wnyc.org (right now they're on a fund raising drive, skip that for now)
2. at their homepage left side there is a list of streams. Pick an MP3 stream, let's say the FM one (which, as of this writing is straming Fresh AIr). RIGHT-click on it and copy the link location.
3. Open that link in another tab by pasting it on the address box.
4. In my Firefox it opens the MediaPlayer Connectivity plug-in, so if the below does not work for you please install MPC.
5. Ctrl+U to see the page source and, voilà, there you will find the URLs:

[playlist]
NumberOfEntries=3
File1=http://wnycfm.streamguys.com/
Title1=WNYC 93.9 FM
File2=http://wnycfm2.streamguys.com/
Title2=WNYC 93.9 FM
File3=http://wnycfm3.streamguys.com/
Title3=WNYC 93.9 FM
Version=2

6. Pick one and use it in your launcher as I earlier suggested.

Some streams are harder to find out than others but in general the trick is to see the page source of the (right!) page. On NPR's website I navigated until I reached a pop-up with Real and WM logos on it. I clicked on the latter, saw the source of the page that opened (right into the pop-up) and copied this URL to a launcher:

mms://a1671.l2063252432.c20632.g.lm.akamaistream.net/D/1671/20632/v0001/reflector:52432?v1st=EE8CA0BA5451DA43&mt=5

It worked fine.

I hope the above helps you and please let me know if it doesn't.

---

### Post by JoseArmandoJeronymo on 2007-10-12
> **drhiii said:**
> Thank you for the response.  

The method for extracting the mp3 and ogg streams makes sense and I have been reasonably successful at that.

Am still wrapped around the axle however with NPR.  Just trying to listen to a Morning Edition replay, or anything else, is still not mastered.  I do get theat Real/WinMedia popup and I look at the source, but I do not see a 'call' for the .wm stream, like the mms: line.  The next thing I get is to either run an application or Save to Disk, and it is not always the same.  It either goes to a .wax file, or sometimes I can get as far as a .smil file.   Part of this is deleting cookies and trying to start over because things get 'selected' and then you can;t get to new popups or views that would provide the kind of link you describe for something like NPR.  It is a drag because for all the wonderful thing in Ubuntu, media play is a maze.

Thoughts....

Actually I thing media play has improved a since  first tried Linux in 2003 (and could lsiten to no more than a midi file of Axel Foley's theme) and would be much simpler if the world suddenly converted all streams to Ogg and we did not have to bother with mp3 (which is ok though proprietary), real (which I think impossible) and wma anymore.

Now regarding your problem, I believe you saw the source of the pop-up page whereas it is the player page that has the URL. Do you have Media Player Connectivity installed? If you do, click on the WM Player logo. A black screen with a play icon at its center will appear. Ctrl+U will open a tab with that page's code. Look for the 'mms' resource locator (which is the one I posted earlier)

Hope this helps.

---

