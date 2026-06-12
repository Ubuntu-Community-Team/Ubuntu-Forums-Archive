---
title: "KnoppMyth -&gt; Mythbuntu - Remote Buttons Different"
date: 2009-05-17
forum: Mythbuntu
---

### Post by Ruler2112 on 2009-05-17
I installed KnoppMyth as a test to see if a DVR would be something my family would like.  This was several months ago and we love it.  However, I kept running into a few problems (mostly with videos not playing or locking up the UI when we try to play them), plus didn't like a few design decisions made by the KnoppMyth team, so decided to try Mythbuntu 9.04.  Overall, I'm VERY impressed!  The install/setup was easier than with KnoppMyth, plus my remote was picked up during install.  However, I'm having one problem that may actually force me to give up on Mythbuntu and search for a different MythTV distro. :(   I don't use MythTV to watch or record TV, but rather just play back AVIs, MPGs, FLVs, etc.  I store these on external USB hard drives.  I have my remote buttons set up like the following:  Directional Keypad: Up, Down, Left, Right Channel Up: mount /dev/sdb1 Channel Down: umount /dev/sdb1 Volume Up: mount /dev/sdc1 Volume Down: umount /dev/sdc1  This has worked great in the past; since the volume is controlled by the surround sound receiver and the channel never needs changing, they were unused buttons on my remote that I was able to use for something.  However, under Mythbuntu, the Channel Up and Channel Down buttons don't seem to be distinguishable from the standard Up and Down buttons.  When I go into the button setup and re-map something, they show up the same as the codes output by the directional keypad.  I tried copying the same lircrc config file from my old KnoppMyth install and it made no difference.  The lircd.conf file references the lircd.conf.packard_bell file, which has the CHUp and CHDown as separate scan codes from the Up and Down buttons on the directional keypad, so I'm not quite certain why they appear as the same key under Myth.  Any ideas as to how I can get these different keys separated and recognized as different keys so that they can do different things???

---

### Post by Ruler2112 on 2009-05-17
OK, it appears as though I cannot play ANYTHING under Mythbuntu... from AVI to FLV files, mplayer locks up and the UI just shows 'loading' until I log into a console and kill the mplayer processes.  Anybody seen this problem before???

---

### Post by Ruler2112 on 2009-05-17
And why are all the carriage returns stripped out of posts on here???  It makes everything run together instead of being in nice neat paragraphs.

---

### Post by uncle hammy on 2009-05-17
Honestly (and at the risk of being blasphemous in the Mythbuntu forum), MythTV is probably way overkill for what you are saying you're using it for.  If you're really only using it to play saved video files, I'd be taking a good hard look at Boxee.  The real power of MythTV comes from the PVR functionality, IMO.

Having said that, have you enabled the proprietary codecs?  Myth COntrol Center > Proprietary Codecs.  Just a thought.

For what it's worth.

---

### Post by Ruler2112 on 2009-05-20
I wasn't aware that I needed to enable the various codecs, but poking around in the Mythbuntu control center, found the boxes you're referring to.  However, I ran into another problem when trying to check them - I get errors telling me that it cannot download the package.  Of course not - this system is a DVR and not connected to the internet.  Great, so I go down in my basement and dig out a LONG ethernet cable to stretch across the floor so I could install these codecs, only to discover that the box doesn't have an ethernet card in it.  (Of course all the PCI slots are full.)  Is there any way of either pulling these off the install CD or downloading them to a flash drive and using that to install?  Also, might I suggest that enabling these codecs be added as a simple option/question to the install routine?  I don't see very many people not wanting to be as flexible as possible in the type of media they're able to play.    I looked at Boxee and it doesn't appear to be something that would work all that well for my application - too integrated with the social networking BS fad for my taste.  I am very open to using something other than myth to build the system though.  Basically, I want something that I can play as many types of media on as possible, be stable, relatively fast on an old celeron 1.3 ghtz, output to my TV using an ATI Rage card with TV-out, and be able to use my remote to control.  (The wireless keyboard I have is good for about 4' or so, plus is very awkward to use as a remote control. ;) )  I have the media organized in directories on external drives, so it only needs to be able to read the directory structure and allow me to pick what file I wish to play.  Like I said, I'm entirely open to using something other than myth to accomplish this; myth is just what I've heard the most about and what has the best reputation.

---

### Post by uncle hammy on 2009-05-20
A pretty basic assumption with MythTV (heck, even Linux) these days, is there is network / internet connectivity on the box.  I am not sure about installing them off the CD.

Also, I was thinking about your remote problem.  Have you looked at your ~/.mythtv/lircrc file to see how your buttons are mapped, and perhaps customize them to remove some of the overlaps?  You can then use the Edit Keys function in MythTV setup for further customization.

---

