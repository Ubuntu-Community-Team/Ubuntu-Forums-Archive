---
title: "ATI TV Wonder Pro Help"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by Explodicle on 2006-06-17
Hi! I'm running Kubuntu 6.06, and I can't seem to get my ATI TV Wonder Pro to work. I've searched the forum, and the best I could find was a Breezy thread that shifted focus to the All-In-Wonder for some reason. I've installed TVtime, but [this is all I'm getting for a display]("http://img160.imageshack.us/img160/6843/tvtimeoutput033243pm7ai.png"), with no sound. I'm living in the Eastern United States, and just installed Kubuntu and TVtime.

Does anyone have any ideas as to what I should try?

---

### Post by Explodicle on 2006-06-18
So, I take it no one else has any leads?

---

### Post by kraz on 2006-06-18
I tried installing the drivers for an ati 128 rage today, with no luck. Gave up and went back to using my pinnacle USB2 TV tuner instead.

---

### Post by kringle on 2006-07-02
[QUOTE=Explodicle]Hi! I'm running Kubuntu 6.06, and I can't seem to get my ATI TV Wonder Pro to work. I've searched the forum, and the best I could find was a Breezy thread that shifted focus to the All-In-Wonder for some reason. I've installed TVtime, but [this is all I'm getting for a display]("http://img160.imageshack.us/img160/6843/tvtimeoutput033243pm7ai.png"), with no sound. I'm living in the Eastern United States, and just installed Kubuntu and TVtime.

Does anyone have any ideas as to what I should try?[/QUOTE]

I just bought an installed an ATI TV Wonder Pro today after having given up trying to use my Hauppauge WinTV 150 with TVTime, or XawTv, or Zapping TV, or any TV application I could find.  I tried to set up MythTV, but as I'm a complete Linux n00b, I gave up after my second attempt(with a clean install of Dapper) with messed up connections to my MySQL server.  Needless to say, I was about to call it quit with getting Linux to run TV and was ready to settle on watching it on my Windows XP partition.

However, when I installed my Wonder Pro and downloaded TVTime, through the add/remove package list, I saw the same screen you showed.  This gave me hope. I *dmesg*ed and saw that my card and my tuner was not recognized.  It told me to use the *insmod option*, but I have no idea how to do that.  After various searches on my friend Google, I finally came across this: 

> -open terminal, use "sudo -s" to get a root shell
```
cd /etc/modprobe.d
echo "options cx88xx card=4" > cx88xx
modprobe -r cx8800
modprobe cx8800

```
-"dmesg" to check if it worked
from [http://www.linuxquestions.org/questions/showthread.php?t=344884](http://www.linuxquestions.org/questions/showthread.php?t=344884)

Viola, I loaded up TVTime and it worked.  Now, I'm running a Tivo into my TV card, so I only really know that channel 3 works; however, I turned up my line-in volume in my volume control panel, and I now have a functioning TV on my Dapper install-yea!  I still have some duplicate entries in my dmesg, but I just ran dmesg -c to clear the old messages.  Now, I'm going to reboot to see if the duplicates are still there.  I will let you know the results.  Sorry for being so verbose, but this is my first entry and I wanted to share what I learned.

I

---

### Post by crazedgremlin on 2006-12-21
[here]("http://www.animewine.com/index.php?entry=entry060720-151531")
works fine for me now
there's a section in there that tells you how to fix the tv card (ubuntu recognizes it wrong or something)

---

### Post by Explodicle on 2007-01-01
That did it! Thanks!

---

