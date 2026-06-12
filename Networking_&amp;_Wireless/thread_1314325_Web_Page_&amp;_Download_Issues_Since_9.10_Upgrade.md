---
title: "Web Page &amp; Download Issues Since 9.10 Upgrade"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by tacantara on 2009-11-04
I upgraded to 9.10 a couple of days ago, after several attempts to get a working version of the upgrade.  I would consider the upgrade successful, except for some internet issues:

1.  Spontaneous re-direct:  When I click on a bookmark, I don't always get the page I expect.  For instance, this morning, I clicked the bookmark I set up for this forum, and was redirected to the Skype home page.  Immediately after that, I clicked the bookmark I set up for my Yahoo mail account, and it took me right to the page.

2.  Web pages not available:  Again, this is an intermittent problem.  If I try to go from my Facebook home page to one of the various games I play in FB, I sometimes get a notice that the URL was not available or incorrect, with a Port 80 error.  On subsequent tries, I eventually get to where I was going.

3.  Can't download add-ons from Mozilla and themes from GNOME.org:  I try every day, yet this problem remains consistent.  I'd love to download the few add-ons that I had on my Firefox browser, but the download manager refuses to provide.  This is true of the download manager in Tools, and if I attempt to download from the Mozilla website.  I get the same problem when I go to GNOME.org to download icon and window border themes.  The page eventually times out.

I suspect that the problem goes back to networking issues, but I can't put my finger on the actual problem.  I've tried removing network manager and replacing it with Wicd, but that made more problems for me.  I've posted on this issue before (not in this much detail), and have yet to get any help.  At this point, I can't even download the ISO so I can attempt a clean installation, because the FF download manager is so borked that it doesn't give me the entire ISO (it got to about 30% and considered itself done).

Please help me

---

### Post by tacantara on 2009-11-04
I've checked to make sure I could ping by url and site name, and I've even opened up a bunch of ports on the firewall.  Nothing yet.  Surely, someone out there must know what is causing my variety of internet issues.

Update 1:  To rule out the possibility of a flawed upgrade, I downloaded the ISO and did a reboot using the Live CD.  Once again, internet works, but certain things are still unreachable.  This must be a 9.10 bug.

---

### Post by axlecrusher on 2009-11-04
I am having the exact same problem. It spans across browsers (Firefox and Chrome). I have tried changing DNS servers on my router with no effect. 

I do not believe it is a network problem because it did not exist before the upgrade, and other computers on the network do not have a problem.

BTW: I'm using the 64bit build.

---

### Post by axlecrusher on 2009-11-04
I'm trying what is suggested here, [http://ubuntuforums.org/showpost.php?p=8132991&postcount=35](http://ubuntuforums.org/showpost.php?p=8132991&postcount=35)

I'll post my results tomorrow.

---

### Post by tacantara on 2009-11-04
So this may confirm my gut feeling on this.  I thought that it may be yet another 9.10 bug.  I reinstalled 9.04 on a separate partition, and downloaded the updates necessary to have it running smoothly, then started my web browsing.  No "unexpected surprises" when I clicked on bookmarked pages, etc.  I was even able to download items from the GNOME.org website to get icon themes and window dressing.


@axlecrusher:  I followed the suggestions in the link you provided, and it worked when I attempted to download an add-on from Mozilla for FF.  I think I can consider this one solved.  Thank you for redirecting me to that link.

---

### Post by axlecrusher on 2009-11-06
I have not any issues since applying that "fix". I guess it looks like there is something wrong with Ubuntu's DNS handling.

---

