---
title: "FireFox 3 and Flash"
date: 2008-07-07
forum: Multimedia Software
---

### Post by BightningLug on 2008-07-07
I have an issue with displaying flash on Fx3 on Hardy. This was not an issue on Gutsy. Every flash is displayed as a gray box with a play symbol in the middle (see attached image). This happens on everything that is flash, but only some times does it not actually play/run the flash.

Once I click the play symbol, the flash video usually loads and plays, but if it's something interactive then it will not do anything and the frame the flash is in turns completely gray. There are also some instances where a video will load but refuses to play correctly, being choppy at first for a few seconds and then stopping all together.

I didn't have an issue like this before being forced to "upgrade" to Firefox 3 beta 5 when I upgraded Gutsy to Hardy. The issue persists even in the non-beta Fx3.

I tried using Firefox 2, but the issue is persistent there as well.

I imagine there is a package I have installed that is the source of the problem, but I'm not sure how to check that and fix the issue. I hope I have explained the problem well enough. Any help on this matter will be greatly appreciated.

---

### Post by gandaran on 2008-07-08
that's because you have 'swfdec' flash installed instead abode flash.
open up synaptic, look up swfdec, check-mark for complete removal, next find the flashplugin-nonfree package (adobe flash) mark for install and click the apply button.

---

### Post by BightningLug on 2008-07-08
Well, that was easy. Thanks, that fixed the problem. :)

---

### Post by BightningLug on 2008-07-08
Spoke too soon. Turns out that this does fix the problem with the big gray box with the play button inside, but now I have no sound and the videos only play for a few seconds and then stop.

---

### Post by gandaran on 2008-07-08
> **BightningLug said:**
> Spoke too soon. Turns out that this does fix the problem with the big gray box with the play button inside, but now I have no sound and the videos only play for a few seconds and then stop.

try adobe flash 10  before trying any other fix, remove the flash 9 (flashplugin-nonfree) and download flash 10 tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html).

---

### Post by BightningLug on 2008-07-08
After the sound stopped working and the videos only played for a couple seconds, I took a look at one of the tutorials posted in this forum: [Comprehensive Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=766683")
Come to find out, I should have looked at this first.

After following directions in parts 1 and 2 and rebooted the computer, all is well. I no longer have the annoying gray box, sound works and all the previous flash items that didn't work at all are all working now.

Thank you for your help.

---

### Post by BightningLug on 2008-07-08
> **gandaran said:**
> try adobe flash 10  before trying any other fix, remove the flash 9 (flashplugin-nonfree) and download flash 10 tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html).

I tried to install flash player 10 but it will not install on my 64bit system.

---

### Post by sirant on 2008-10-07
For what its worth......

I have been having this issue for a long time now. Been driving me nuts actually. I decided earlier today, for the first time in a year since 100% removing winblows from my system, if this flash issue wasn't resolved today, I would wipe ubuntu and go back to microsoft.

How rotten is that?

I was having the same issues as soo many others it seems. I tried EVERY fix I could read, and I couldnt even possibly begin to list them, to fix the nagging flash video problem in Firefox 3. It seemed to first start when I installed Americas Army to check it out. The videos still worked, but sometimes crashed. Then I installed Google Earth and bang, I got a white box where videos used to be. Not just youtube, but every flash site....

So I followed every forum post and walkthrough, all they did was turn my white blank box into a grey box with a play icon in the middle that did nothing. Arrrggggghh!!! of course it did not play.

In desperation I did this:

In synaptic I searched gnash and swfdec.

swfdec was installed, gnash was not. So I installed gnash too... No joy.

So I removed swfdec... Lo-and-behold, the box was white again, no Grey box with a circle and a triangle (typical play button)....

Went back to synaptic and uninstalled (complete removal for both) gnash....

Bam, flash videos are back and work great.....

I have heard rumors that Americas Army installs a flash player and perhaps Google Earth does too, which mess with Firefox. I have no idea.

All I do know is by fully removing gnash and swfdec I got my flash back, hours before resorting to going back to the dark side....

I hope this works for others, and if it does, please spread it around the net! I know there are too many ubuntu'ites out there suffering this same problem.

Hopefully the fix is this easy for everyone. (And hopefully they wont jump through hoops for 3 days like I did....

Maybe if I am feeling lucky I will install Google Earth again just to see if it mucks it up, but as for Americas Army, meh..... Urban Terror and so many other FPS are so much better. So wont bother testing that one.

Hope that helped some of you.

sirant

---

### Post by richiesan on 2008-10-15
I too was having problems getting sound with Flash videos in Firefox and tried almost all the ideas posted here without success. I was reduced to running Chromium every time I wanted to use Youtube.

I finally tried another suggestion I saw elsewhere which was to remove Adblock from Firefox, reinstall Flash then re-install Adblock. 

Result - Success!

If all else fails, give it a go.

---

### Post by Nexon on 2008-11-28
I also had problems with Firefox and Flash.

My complaint was not so much the sound, but the video.  Flash frames would have this continuous sideways jitter, where the whole frame would jump about a half inch to the right and back again.  The frame would twitch like that several times per second, making it very 'unpleasant'  to watch.

Uninstalling AdBlock Plus and re-installing it, looked like it solved the problem, but it came back.  What it turned out to be is an interaction between Flash, StumbleUpon, and TinyMenu, for certain customizations.

Watch out for the add-ons, they can cause probs.

---

### Post by rjbeeth on 2009-02-01
I too had the same problem. It occurred even before I had installed any plugins and without a doubt it is this sort of dumb thing that really hurts any effort to get "the masses" moving towards Linux/Ubuntu.

It has taken me months to find this particular solution (having tried others - there are lots and LOTS of people out there having problems with this)

I understand and appreciate Ubuntu's desires and efforts to stay 100% free and clean of anything that is completely free from any copyright issues but something like this needs to be fixed  and should have been found way before it became a major problem - I'm really stunned that removing swfdec fixed the problem (in other words it was the problem) but it did.

Thanks again for posting the fix - I too was inches away from canceling my move from Windows to Ubuntu. Now I'm on to (waiting?) for the next hurdle - but this one was big - there are way way WAY too many sites out there running flash to not have had a concerted effort to have this fixed earlier.

Thanks again to all those who helped me keep my sanity - AND Ubuntu as my main machine!:popcorn::D

---

### Post by khelben1979 on 2009-02-05
delete this post which I made here. (ooops.)

---

### Post by Barney Oatmeal on 2009-03-13
[SIZE="4"]I had nightmares with Flash, too, in Firefox3.
What I finally had to do was install it from a .tar file as per instructions in this post [/SIZE]http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+player

I think the flash player instructions were down the page a bit - and the troubleshooting guide really helped me alot!

Hope this helps,
                Barney Oatmeal

---

