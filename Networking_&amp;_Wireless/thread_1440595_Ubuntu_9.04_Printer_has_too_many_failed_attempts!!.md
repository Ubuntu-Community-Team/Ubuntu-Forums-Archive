---
title: "Ubuntu 9.04 Printer has too many failed attempts!!!"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by jaime256 on 2010-03-27
Why is it that the darn printer keeps breaking on this thing (Ubuntu) ??? It's either every damn update that keeps messing this up. One computer is bad enough, I can't imagine having to take care of even five with this thing always screwing something up. What the hell is going on??? Yeah I'm tired of this thing always messing up the printer. Please fix this thing, separate the browsers if you have to, do whatever it takes, but please STOP messing up the printers...and I don't even print that often.

Oh yeah, when you first start the OS up, the drive seems to go on for a while longer now. I only put the regular updates and don't tweak anything. Maybe it's time to try another distro.

---

### Post by jaime256 on 2010-03-27
I just rebooted the computer, twice and nothing, still get the same damn thing. So I went ahead and rebooted the nas where the printer is on...and still nothing. I was just trying to add the windows printer via samba and still...nothing...oh by the way, there is NO firewall on that menu!

Well, decided to wait it out and try again, it finally let me re-install the printer and apparently every time there is an update I have to keep deleting and re-installing the printer. For crying out loud, please stop doing that.

---

### Post by ajgreeny on 2010-03-27
You don't even say what printer you are talking about so there is not much that can be done to help at the moment.

There have been a few **cups** updates just recently in both 9.04 and 9.10, if I remember correctly, so it could simply be that which has caused the problem.  Give a bit more information on the problems, and what printer, and there may be some help available.

EDIT:
I posted before your second post arrived and didn't notice it's a network printer on a samba network, about which I know absolutely nothing.

There were some samba updates on 18 and then 24 March which may have had some effect on your system and network printer, I suppose, but can't help any further, I'm afraid.

---

### Post by jaime256 on 2010-03-28
Thank you for offering to help out. I had to vent earlier when I posted. I was just trying to print a single page and needed to run out to a store that was going to close, but no browser or screen shot would print. So far it's been happening quite a few times on many updates actually. And I noticed that you have to keep re-setting up the printers every time something changes. I'm not too worried about me, but I got a lady on Ubuntu and her printer is directly connected to the computer and when things like this keep changing, it's hard to fix them on the remote machine every time it gets broken. So it's not just networked printers and my printer (brother) has always worked well with Ubuntu. Hers is an HP, but had a different HP laser that just gave us hell, and these changes that keep messing stuff up with the printers sure don't help any. Don't get me wrong I love using the OS, but sometimes even this one can drive you nuts. And I don't mind updates, but they really need to test them way before they just push them out.

---

### Post by jaime256 on 2010-03-29
Well, I turned on the computer again today and tried printing something else I was just working on...I'm still getting the same error message. This is the first print I'm trying since turning the computer on this morning.

---

### Post by jimbop99 on 2010-03-29
Try assigning it a static IP address.

---

### Post by jaime256 on 2010-03-29
I have that already set up with a static IP. It's not the nas or where the printer is plugged into, it's Ubuntu. I just checked the printer and the shared printer is accessible. I can't get anything to print at the moment but thank you.

---

### Post by jaime256 on 2010-04-23
Does anyone have a clue as to why Ubuntu 9.04 still can't print from a pdf file? Yeah, I'm still having problems with this version and I even uninstalled Firefox and the Ephyfany browser. Just running Chrome and Opera. Chrome still won't print anything there, but I found out Opera does print, but I can't print a regular pdf file. I'm not sure that Chrome would have anything to do with this. Ah, the printing ghosts of Ubuntu...I should note that I'm still getting the same message as before.

I decided to uninstall Chrome and then shut the computer down and I turn it back on. I know you really don't need to turn it off, but I just wanted to see if anything would change. I tried printing the pdf file, I just download that and I still can't print it from the 9.04. 

However when I print the same pdf from 9.10 it asks me for the password. I also used the same old password I've been using and the pdf file printed. Here's the catch. I used the same password I used to use, but I changed the password yesterday and that still allowed me to print? I couldn't access the nas shares with the old password of course, but why can I still print with the old password??? Now this is getting interesting...this printing was on 9.10 just to clarify. And yes I'm aware a new version is coming again, but I got too much stuff on the old system and not enough room to move so I can try the new one.

---

### Post by jaime256 on 2010-04-23
I decided to play with this thing again. So I found out since all the changes that happened from the updates things kept changing. Here's the fix for anyone else having the same problems.

1. Don't follow the setup in the first picture. As you can see, when you try to verify it, it doesn't work. I got it working by taking out the :631 after the ip before but still kept having problems, so I just won't recommend this from my experience.

2. Follow what's on picture 2 and 3. I just did it, but now I can print the pdf file I was trying to print before. Not to mention anything else I'm sure. So far I've been having to do this more times than I would like, but I hope this will stick now. I hope it helps.

---

### Post by jaime256 on 2010-04-23
I spoke too soon. Apparently there IS a problem with Ubuntu 9.04. I left the computer for a while, came back, logged in and this is what I'm getting when I tried to test print these pdf files...I think reloading the printer will work for a bit, but what a pita! The only browser I have installed is Opera now, but no go printing anything else. So I have tried adding the printer both ways and I still get the same problem. I should also note that even after logging into my shares, I still get the same problem. Can't print anything.

---

