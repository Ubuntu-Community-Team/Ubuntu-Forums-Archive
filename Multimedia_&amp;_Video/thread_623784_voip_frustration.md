---
title: "voip frustration"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by chromedome on 2007-11-26
I've recently become engaged to a woman in California; I'm in Atlantic Canada.  We both spend a fair amount of time working on our respective computers, and would like to find a mutually-functional voip client for reasons too obvious to require comment.  I'm running Edgy: she has Red Hat and Unix partitions on her box but spends most of her time in XP, because that's where she does her freelance work.

Context: I am an experienced user (go back to DOS 2.X), but a Linux n00b.  She has lots of *nix experience (hell, she wrote a flavour of UNIX for a corporate client, once), but has spent more time on UNIX than Linux, and has not had much time on Debian-based distros.  So in short, while you'll have to break things down for me a little bit, I can follow instructions accurately, and if you need system information that I can't find, she can probably give me "navigational assistance."

We've tried a handful of different voip clients, and nothing has quite worked...although the reasons seem to vary.  Yahoo Messenger for Unix demands an outdated library.  Skype keeps erroring out, looking for a library which is, in fact, installed and up to date.  Ekiga appears to install correctly and have no router issues, but can't connect...not even to their echo number.  Jabbin keeps telling me that it can't get a response from the Jabber server (tells my fiancee the same, on her XP box, so that's not a configuration thing).  Gizmo seems to come closest...calls ring through from either end (oh...we're only looking for PC-PC, not PC-phone) but do not connect properly.  I can hear her, but she can't hear me.

My computer is on a wireless network behind a Linksys router.  I've set up port forwarding as required, but to no avail.  

My preference, I think, would be to sort out what's going on with Ekiga.  If that's up and running properly I'd have the option of adding a cam as a (relatively) straightforward upgrade, later on.  Barring that, because Gizmo is the closest to working, that's probably the other one to pursue.  Just for the record, I have plugged dutifully through many, many pages of forum posts, but have not yet found anything that proved transferrable to my own situation.  

All help gratefully accepted...

Thanks,

'Dome

---

### Post by human-ness on 2007-11-26
Have you got the latest version of Skype?  I have two partitions, one running XP and the other Ubuntu Gutsy.  Skype should work without a hitch.

Also, have you considered updating to Gutsy or even Feisty?  They seem to have fixed many of my past lib problems.

Another way you could go, is hardware VOIP.  Some VOIP companies, offer free calls, between two people as members of the same company.  Like Engin.  I was with them for a few years and my mates and I could talk for hours, absolutely free, because they were members as well.  Until Engin got a bit dodgy.

As for the reason why these apps are not working for you, I have no idea sorry.  I've had no trouble with any of them to be honest.  And Skype I have to say has been the most trouble free in the latest releases such as Feisty and Gutsy.

---

### Post by chromedome on 2007-11-26
The version of Skype I tried was current as of last week, so I think that's pretty recent.  :)

I've been procrastinating about upgrades, because I had grief with wireless in the past.  Edgy recognized my new card OOTB, but Feisty didn't.  I haven't downloaded Gutsy yet, because I've learned the hard way about being an early adopter.  I like to wait for bug fixes.  Having said that, it's probably tweaked enough now for me to take a look at.

---

### Post by chromedome on 2007-11-27
<bump>

I've downloaded Gutsy.  I'm going to try to free up time this evening for the install, but first I'm going to run the Live CD and see if it recognizes all my stuff.  How else will I know how much time I need to allocate, right?

I'll post again after I'm upgraded, and have had a chance to see how everything reacts with the new version.

---

### Post by YannickDefais on 2007-11-29
Hi,

Good you decided to upgrade, as Gutsy has Ekiga 2.0.11 and Edgy 2.0.3. 
8 bug fix releases.

After what you said, I suspect a problem with your router.

Try Ekiga on gutsy, see if it works out of the box, and try the echo test sip:500@ekiga.net (you need to get an account on [http://ekiga.net](http://ekiga.net) to get it work, wait for the confirmation mail).

Tell me what the druid said at the NAT test (step 5), for you and for your friend.

As you guys seems to like computers, If we find a way to get it work, we may try to install the SVN version which will gives you the H.264 video codec @ 640*480 resolution (that means a really good video ;)

Regards,
Yannick

---

