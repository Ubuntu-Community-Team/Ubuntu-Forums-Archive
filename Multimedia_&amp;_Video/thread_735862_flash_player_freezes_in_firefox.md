---
title: "flash player freezes in firefox"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by lemonlaw95 on 2008-03-26
i've had this problem in other distros too.  in firefox, with a flash video or game playing (eg youtube), every 5 or so seconds the video freezes.  then i have to drag the bar forward to get it to keep going.  then it freezes again.  any idea what's happening?

any help is GREATLY (since this problem is so darn annoying!) appreciated.

oh, and did i mention that it doesn't do this with flash ads?

---

### Post by Dojan5 on 2008-03-27
Amusing, everything you want to see is freezing but the ads are displaying properly.
I would un-install the flash package and try to reinstall it. Maybe try another package.
If that dont work, im clueless.
Good luck

---

### Post by CIZZO20 on 2008-03-27
I have the same problem i just installed Hardy Heron yesterday and right away i am having problems with flash.

My flash vids start and play for a few seconds before it just stops. It has no sound or anything but it always plays for about 3 to 4 seconds before just stopping in its place. I click play but nothing happens but if i skip the video up a little using the slider it will play again for 3 to 4 seconds then stop again.

I have tried letting firefox install the flash plug-in (which is that nonfree one i think) and i have tried swfdec and had no luck . I have uninstalled and reinstalled everything that has to do with flash many times over again and tried everything i can think of. I have tried installing firefox 2 and it does the same thing.

I never had these problems in 7.10 . In 7.10 everything worked without any problems. Never even had sound issues with flash which i seen that was a issue with many other people in 7.10 .

---

### Post by Bubba64 on 2008-03-27
Here is a thread which lists a lot of stuff that helps flash and other stuff work.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by CIZZO20 on 2008-03-27
Ok well i don't know if this has something to do with the flash problem or not but i have also noticed mplayer has been playing all my videos very very slow. also has no sound and i have to mess with it to get it to play in the first place. 
Like i said in my post above when i try to watch a flash video i also have no sound but one thing i didn't say anything about is how the video is very slow for the 5 seconds it does play.

so I'm thinking some how mplayer has something to do with this problem because its pretty much doing the same thing as my flash is. Very weird to me tho because I'm not trying to watch flash things on my mplayer. The videos im trying to watch are avi. kaffeine is playing these avi vids fine. a reinstall of mplayer did not help at all.

o ya i also tried a few things from that how-to.  they didnt fix it :(

---

### Post by Prefix100 on 2008-03-27
i had this issue because of 64bit firefox.

Install the 32bit firefox, theres some really good setup file somewhere....

---

### Post by CIZZO20 on 2008-03-27
i have 32 bit pc

---

### Post by Prefix100 on 2008-03-27
which flash player are you using?

The open source or the macromedia one?

---

### Post by CIZZO20 on 2008-03-27
I went through all of them that i seen in the synaptic package manager. The non free one was the only one that worked even a little in firefox.

---

### Post by Prefix100 on 2008-03-28
only have one of them installed at one time, and try the nonfree one again

---

### Post by ubuntu-freak on 2008-03-28
> **Bubba64 said:**
> Here is a thread which lists a lot of stuff that helps flash and other stuff work.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

 
The thread mentioned above is mine. I made some changes today, so have another look at part 1, the "Adobe Flash Installation" section. Try purging flashplugin-nonfree and install it with the alternative methods (both 32/64-Bit architectures are covered). If you still have issues, install alsa-oss and take a look at no.7 in the troubleshooting section concerning Firefox's configuration file. 

Hope that helps.
 
Nathan

---

### Post by scott petersen on 2008-04-11
Hi 
I've had the same problem,I'm not sure how,but my wireless card seemed to be conflicting with
adobe flash player as soon as the player caught up to the cache ,the network stopped responding
 well here is the weird part,on the same system i changed operating systems,suse 10.3,ubuntu,xp pro,with iexplorer6 and mandriva all had the same problem,the wireless card was a belkin dwl-650.flash player was ver 9 I switched to an usb linksys wireless adapter,now all is fine,I don't know what the problem is,but changing the wireless card fixed it there seemed to be no other problems with the system

---

### Post by Anxiety35 on 2008-04-30
I was having this same problem of no sound and the video freezing after a couple seconds. I had tried what was posted on that linked thread above with no luck. The trick that fixed it for me was what Prefix100 said. Only have one installed at a time. I guess I had tried so much that too much was installed.

I went into the package manager and uninstalled "flashplugin-nonfree" and "libflashsupport"

Now it works like a charm!

---

### Post by oooh on 2008-05-01
This helped me out:

[http://ubuntuforums.org/showthread.php?t=598034&highlight=FLASH+PLAYER+SECONDS](http://ubuntuforums.org/showthread.php?t=598034&highlight=FLASH+PLAYER+SECONDS)

---

