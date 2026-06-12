---
title: "Anybody getting Netflix in HD? (Using Pipelight, Netflix-Desktop app)"
date: 2015-05-12
forum: Multimedia Software
---

### Post by The Bright Side on 2015-05-12
Hey folks,

I've been having a bit of a troubled history with the netflix-desktop app. I used it in 14.04 and got HD with no problems. Then, I tried it in 14.10 and got no more HD. In addition, every couple days, some Wine thing popped up out of nowhere and installed always the same things over and over, so I just deleted the app along with Pipelight and continued watching Netflix in SD on Chrome.

Now that 15.04 is here, I gave it another shot. It installed fine (though I don't know yet if the automatic re-installation thing will keep happening), but I still don't get that HD button.

I just tried Netflix in Firefox in Windows 7 at my office, and the same shows I tried at home this morning do have an HD button here (The Fall, Archer).

Is anybody else getting Netflix in HD in Ubuntu? If not through the netflix-desktop app and Pipelight, then how?

---

### Post by efflandt on 2015-05-12
Google Chrome (right from Google) can do Netflix in Ubuntu without having to add any other packages. For that you might need to set preferences in your profile on Netflix website to "Prefer HTML5" (which still refuses default Linux Firefox). Using Chrome in 14.04 appeared to be better resolution than when I was using netflix-desktop package in 12.04 (maybe graphics is more direct with Chrome than going through wine?). Although, my desktop is WiFi connected to 5.1 Mbps DSL gateway, so that may not always be optimum for HD video.

I have also used Chromecast (a $35 device that plugs into HDMI and USB power) which seems to have excellent resolution (for Netflix, Hulu, YouTube), at least when I use Android phone apps to control it. The Chromecast device streams the video directly from WiFi (works best with included HDMI extender) and the phone just acts as a remote control. To use Chromecast from Linux (or Windows) Chrome, you add "Chromecast Extension" to Chrome.

If you install Chrome in Windows, just be careful that you are where you think you are (on google.com) and not somewhere else. When I tried to get Chrome for Win7 on my laptop I ended up on a bogus website that installed a Binkiland browser (even though filename contained "chrome") which also installed adware/malware. Installing Malwarebytes at that point would not get rid of it. I had to anti-virus and malware scan the drive from another computer to remove the bad files, then boot Windows to safe mode back in the laptop, uninstall/reinstall Malwarebytes, which could then finally remove remaining garbage from registry. Just one reason that I mostly run Linux at home (on mSATA SSD on that laptop).

---

### Post by The Bright Side on 2015-05-12
Thanks so much, efflandt! Yeah, I've been using Chrome on Ubuntu for Netflix for most of the time and the quality, while equalling DVD resolution "only", is actually pretty nice. It's just weird that for a while, I did manage to get HD using the "netflix-desktop" app and Pipelight, while I do understand it's basically a modified Firefox installation running a Wine-powered Silverlight.

The Chromecast is something I looked into for a while. It might be interesting, especially because it might also enable me to watch with 5.1 Surround. That said, I think I'll wait for Windows 10, at which point I will be able to install the Windows Netflix app, which then provides me HD and 5.1 sound. I won't mind so much booting into Windows for that, even though - of course - I would prefer having these options in Ubuntu.

I have Chrome (the browser) on both Ubuntu and Windows 7 at home and will give it another look in Windows when I get home tonight.

Thanks again!

---

