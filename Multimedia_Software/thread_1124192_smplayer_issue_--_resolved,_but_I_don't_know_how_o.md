---
title: "smplayer issue -- resolved, but I don't know how or why"
date: 2009-04-13
forum: Multimedia Software
---

### Post by Citizen Bleys on 2009-04-13
I discovered tonight that when smplayer was launched with an argument -- either by using the command-line or double-clicking a video -- it would launch with a black screen, but the sound would be working fine.  Any other video player on my system...mplayer, totem, vlc, and gxine were the ones I tested--would play the same videos as normally.  If I opened smplayer from the Applications menu and used the open dialog box from that instance of smplayer, it would play the same videos normally.

How I fixed it:  I uninstalled and reinstalled ALL of my codecs.  No joy.  The old uninstall/reinstall trick doesn't seem to work to well in Linux, since reinstalled applications always seem to remember any settings I'd changed since install time, but it was worth a try.  I installed ffmpeg via aptitude since the .deb file I had in my "medibuntu crap" directory didn't work.  What's the difference between aptitude and apt-get anyways?  I just use aptitude whenever apt-get doesn't work for me.  Finally, I downloaded a .deb from BerliOS directly since the latest version of smplayer isn't included in Ubuntu's repositories.  After upgrading to 0.6.7, everything worked fine.

How I *think* I might have broken it:  I spent quite a bit of time trying to install fuppes last night.  I was running Hardy x64 and failing pretty bad.  I installed a lot of crap trying to do that, and none of it worked.  I finally solved that issue by updating to Intrepid.  I'm pretty sure I didn't watch any videos inbetween my failed attempt to install fuppes and when I discovered smplayer wasn't working anymore, but not 100%.  I did do an awful lot of frigging around.  I know it's not Intrepid itself since I was already running Intrepid (albeit the 32-bit version) on my laptop and it plays everything just fine.

Has anybody had any similar experiences and can suggest what happened?  I'm afraid I'm not happy with "oh well, it works now" because if I don't know why the problem occured and why what I tried worked then I'm still SOL the next time a similar problem crops up.

Sorry for the infodump up there, but I don't know what 1% of what I just said is actually relevant.

---

