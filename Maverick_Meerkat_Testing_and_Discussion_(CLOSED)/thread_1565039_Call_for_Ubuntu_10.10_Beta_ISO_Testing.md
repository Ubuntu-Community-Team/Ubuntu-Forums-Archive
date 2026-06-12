---
title: "Call for Ubuntu 10.10 Beta ISO Testing"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-08-31
With beta freeze in effect in preparation for the beta release, which is to be out this Thursday, ISO testing is now underway.

*Note that not all images are available at this moment; check back in a few hours if the ones you'd like to test are missing.*

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the RC), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. During this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for Ubuntu 10.10 Beta are starting to appear on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs. 

We now have [upgrade cases]("http://iso.qa.ubuntu.com/qatracker/build/upgrade/all") to be tested, as well as [some new features]("http://ubuntutesting.wordpress.com/2010/08/03/alpha-3-iso-tracker-new-features/") in the tracker.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you're doing testing for the first time, please read the above, and remember that posting issues here is not enough; you should report your test results in the testing tracker.

If you need immediate help with testing, the best place to go is the #ubuntu-testing [IRC channel]("https://help.ubuntu.com/community/InternetRelayChat") on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by kansasnoob on 2010-08-31
Just preparing to do an i386 upgrade test and I was surprised to see this:

> Procedure

   1. Run **[COLOR="Red"]update-manager -d -c[/COLOR]** from a terminal 

[http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade](http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade)

I had always used just update-manager -d :confused:

No biggy, just glad I read :)

---

### Post by cariboo on 2010-08-31
The -c is for check if a new distribution release is available

---

### Post by kansasnoob on 2010-08-31
My upgrade testing went off without a hitch :)

I'm very impressed with the improvements Colin Watson has made to grub 2. I deliberately "fooled" my existing grub 2 into installing to an "improper" device before starting the upgrade and the upgrade process triggered a very understandable dialog along with the proper options, etc.

I love it :D

And, of course, I completed the required post-upgrade tests:

> Post-upgrade tests

   1.

      Desktop effects
          * If you had compiz running, test if it is still running after the upgrade
          * If compiz was not running, try to enable it via System/Preferences/Apperance, then go to Desktop Effects and set it to "Normal effects"
          * Verify that it works by pressing SUPER(windows key)+e
          * Verify that the workspace layout and the keybindings are preserved
          * Open the Example Documents and play the "Experience ubuntu.ogg" and see if that playing works
          * Press ALT+F2 and type "glxgears" and see if it works
          * Watch out for screen artifacts
          *

            Please report any problems you observe and include some details of the problem and the files "~/.xsession-errors" and the output of "lspci -n" 

Kudos to the QA team for writing such great and easily understandable instructions. We need more of our documentation written so well :)

I hope to get this horrible home remodel done soon (I'd anticipated this being done 2 or 3 months ago) and then I'll sign up for Desktop testing.

---

### Post by Nullack on 2010-08-31
No way is the beta ready based on my testing. I've reported the kernel panic I'm getting on the install test case I did. Also, when I apply the work around cludge for the kernel panic, there is various other problems such as sound not working (again) and bugs not resolved for many cycles such as the gnome event low complaining about not accessing btmp logs.

---

### Post by kansasnoob on 2010-08-31
> **Nullack said:**
> No way is the beta ready based on my testing. I've reported the kernel panic I'm getting on the install test case I did. Also, when I apply the work around cludge for the kernel panic, there is various other problems such as sound not working (again) and bugs not resolved for many cycles such as the gnome event low complaining about not accessing btmp logs.

Could you please link to the bug reports?

Without more info this amounts to nothing but a "rant" :)

I've tested Maverick on two sets of hardware and it seems to be great other than a few corner issues that are already being worked on.

---

### Post by Nullack on 2010-08-31
Its already linked to in the QA tracker test cases as per the process. Hardly a rant to report bugs and say its not ready.

On the off chance you a kernel developer with the skills to fix the kernel panic, here it is if you cant find it:

[http://iso.qa.ubuntu.com/qatracker/test/4447](http://iso.qa.ubuntu.com/qatracker/test/4447)

and

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627495)

---

### Post by ranch hand on 2010-08-31
I am not sure what the point of raid is, doesn't seem to fit in with the way I use my drives, but it something that needs fixed as many do use it.

My new install just worked very nicely.

---

### Post by Nullack on 2010-08-31
mate raid can provide mirroring, striping, parity, jbod just a bunch of disks spanned together and other raid levels. So basically it provides users with varying amounts of storage fault tolerance in limited circumstances and/or performance gains over one disk depending on the raid level used. Its not a backup solution though.

---

### Post by VastOne on 2010-09-01
> **ranch hand said:**
> I am not sure what the point of raid is, doesn't seem to fit in with the way I use my drives, but it something that needs fixed as many do use it.

My new install just worked very nicely.

Did you you use today's daily Alternate as your source?  That appears to be my only source.

And since this is my first time iso testing (having signed up already), is this the source to use or do I wait until Thursday for the actual beta?

---

### Post by ranch hand on 2010-09-01
I just downloaded the desktop and burned it.  Will be testing it directly.

I did the Alt earlier when it was the only one available.

If you check now the desktop, both 32 and 64 are there.

---

### Post by VastOne on 2010-09-01
> **ranch hand said:**
> I just downloaded the desktop and burned it.  Will be testing it directly.

I did the Alt earlier when it was the only one available.

If you check now the desktop, both 32 and 64 are there.

Hmmmm...

I am still only seeing the Alt as a selection but will look further.  Was it the daily today that you dloaded?

And thanks Ranch Hand

Edit - I found it in the LiveCd 20100901 section, I was looking at the Current Daily.

Thanks

---

### Post by Slug71 on 2010-09-01
Is BTRFS / bootable with grub2 now?

---

### Post by kansasnoob on 2010-09-01
> **Nullack said:**
> Its already linked to in the QA tracker test cases as per the process. Hardly a rant to report bugs and say its not ready.

On the off chance you a kernel developer with the skills to fix the kernel panic, here it is if you cant find it:

[http://iso.qa.ubuntu.com/qatracker/test/4447](http://iso.qa.ubuntu.com/qatracker/test/4447)

and

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627495)

OK, let's break this down:

> Its already linked to in the QA tracker test cases

So, it's up to me to search?

> Hardly a rant to report bugs and say its not ready.


But this is the wrong place to report bugs. Some ranting is expected, I've done my fair share :)

> On the off chance you a kernel developer

Nope! Just an idiot end user that loves Ubuntu :)

I didn't mean to sound harsh but you said, "No way is the beta ready based on my testing. I've reported the kernel panic I'm getting on the install test case I did. Also, when I apply the work around cludge for the kernel panic, there is various other problems such as sound not working (again) and bugs not resolved for many cycles such as the gnome event low complaining about not accessing btmp logs."

Several problems, no links, no way for someone to know if they can help or not :(

---

### Post by kansasnoob on 2010-09-01
> **Slug71 said:**
> Is BTRFS / bootable with grub2 now?

AFAIK using btrfs still requires a separate ext4 /boot. Maverick will still have ext4 as a default fs.

---

### Post by kansasnoob on 2010-09-01
I was unable to login to my qa account using Firefox 3.6.9.

I wonder what's up with that?

Too tired ATM to think straight, but I installed Seamonkey and got logged in fine :(

---

### Post by VastOne on 2010-09-01
> **kansasnoob said:**
> I was unable to login to my qa account using Firefox 3.6.9.

I wonder what's up with that?

Too tired ATM to think straight, but I installed Seamonkey and got logged in fine :(

I am logged in now with 3.6.10...

---

### Post by dext on 2010-09-01
> **Slug71 said:**
> Is BTRFS / bootable with grub2 now?

i dont think they have settled the license issue between **Grub2** and **btrfs** yet. going by what i have read on the Grub mailing list

Grub2 uses GPLv3 an btrfs uses GPLv2, so untill they sort that out i dont think btrfs will be used as default in any Distro that uses Grub2 as default

[http://lists.gnu.org/archive/html/grub-devel/2010-08/msg00073.html](http://lists.gnu.org/archive/html/grub-devel/2010-08/msg00073.html)

though the only way you could use it as default i think an thats to Use it in Grub-Legacy

---

### Post by VastOne on 2010-09-01
> **dext said:**
> i dont think they have settled the license issue between **Grub2** and **btrfs** yet. going by what i have read on the Grub mailing list

Grub2 uses GPLv3 an btrfs uses GPLv2, so untill they sort that out i dont think btrfs will be used as default in any Distro that uses Grub2 as default

[http://lists.gnu.org/archive/html/grub-devel/2010-08/msg00073.html](http://lists.gnu.org/archive/html/grub-devel/2010-08/msg00073.html)

though the only way you could use it as default i think an thats to Use it in Grub-Legacy

Man you look eerily familiar, like a distant relative. :confused:

I wish this would settle...I am wanting to test and run btrfs.  I know that I can now but I had issues with it in a separate boot partition and came away very frustrated.

---

### Post by ranch hand on 2010-09-01
> **VastOne said:**
> Hmmmm...

I am still only seeing the Alt as a selection but will look further.  Was it the daily today that you dloaded?

And thanks Ranch Hand

Edit - I found it in the LiveCd 20100901 section, I was looking at the Current Daily.

Thanks
If you just go to;
[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)
Click on the basic ISO you want.  The page that comes up has the list of test subjects (Live Session, Idiot Install, OEM install, etc).  Also at the top of that page is a link to download the testing version of the ISO.

In this case it was the one you used but that is the link to use.  If there are a lot of redos of the testing that is the only link yo can really trust to be the right version.  Happened with A3.  Could with this one.

---

### Post by VastOne on 2010-09-01
> **ranch hand said:**
> If you just go to;
[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)
Click on the basic ISO you want.  The page that comes up has the list of test subjects (Live Session, Idiot Install, OEM install, etc).  Also at the top of that page is a link to download the testing version of the ISO.

In this case it was the one you used but that is the link to use.  If there are a lot of redos of the testing that is the only link yo can really trust to be the right version.  Happened with A3.  Could with this one.

Aye sir, if you look closely you will see me already completed an install.

Appreciate your help~

---

### Post by ranch hand on 2010-09-01
I really did not need to look that closely.  You got downloaded and tested before I got back to do my install and nightly switch back to the land of stable OS'.

Glad to see yours went as rough as mine did.  This is one time that boring is a real good thing.  That whole test was.

Hope the devs ore happy with it so we do not have to do it again.

Looks like we will with the alt-install.

---

### Post by VastOne on 2010-09-01
> **ranch hand said:**
> I really did not need to look that closely.  You got downloaded and tested before I got back to do my install and nightly switch back to the land of stable OS'.

Glad to see yours went as rough as mine did.  This is one time that boring is a real good thing.  That whole test was.

Hope the devs ore happy with it so we do not have to do it again.

Looks like we will with the alt-install.

Aye again... My old eyes are getting worse and my patience even more so.. 

I remember reading long ago about how fast a web page must load in order to keep a user at that page and it was a pretty low number.  Now, with so many tabs open at once, it is even exponentially lower..

Point being in look at that page I now see that there are two links side by side, once for the iso and one for the test page...

Too old, maybe, but testing edge daily releases and promoting a solid package, is never dull, and always a good days work...

---

### Post by inportb on 2010-09-01
Okay, I cheated by installing the Aug/31 daily build netbook edition off a microSD card, but -- it didn't let me set my hostname during the installation process. Is this a problem for anyone else?

---

### Post by VastOne on 2010-09-01
> **inportb said:**
> Okay, I cheated by installing the Aug/31 daily build netbook edition off a microSD card, but -- it didn't let me set my hostname during the installation process. Is this a problem for anyone else?

Yes.  I knew there was something different (other than the obvious changes) but didn't catch it.  No host naming option for me either.

---

### Post by Wobblybob on 2010-09-01
Yes what happened to being able to name my host system? and for that matter what happened to all the ubuntu desktop amd 64 results on the iso tracker, they have all gone missing? I've added a few this am and now everyone's have gone...

---

### Post by ranch hand on 2010-09-01
> **Wobblybob said:**
> Yes what happened to being able to name my host system? and for that matter what happened to all the ubuntu desktop amd 64 results on the iso tracker, they have all gone missing? I've added a few this am and now everyone's have gone...
I would say we are in for a rebuild.  Oh goody, a third install for me.

---

### Post by ranch hand on 2010-09-01
Yup, got the email notice and everything, got the ISO on its way right now.

---

### Post by VastOne on 2010-09-01
> **ranch hand said:**
> Yup, got the email notice and everything, got the ISO on its way right now.

Aye and burning as we speak..

Edit - Completed with still no option for host name selection..

Gonna check on a bug status and if none set one.

---

### Post by Wobblybob on 2010-09-01
> **ranch hand said:**
> I would say we are in for a rebuild.  Oh goody, a third install for me.

ok I'm new to this testing lark, I've zsync'd my amd64 iso again and it has not found any changes so does that mean the errors I found earlier today and reported [now wiped from the iso tracker] will still occur so there's no point in doing the tests again?

---

### Post by zenarcher on 2010-09-01
I downloaded and installed the 64 bit Alt. Install disk for Kubuntu 10.10 Beta and it installed perfectly for me. Not a hitch at all.  Did my usual full hard drive encryption (except small boot partition, of course) and all went well.

Cheers,
zenarcher

---

### Post by ranch hand on 2010-09-01
> **Wobblybob said:**
> ok I'm new to this testing lark, I've zsync'd my amd64 iso again and it has not found any changes so does that mean the errors I found earlier today and reported [now wiped from the iso tracker] will still occur so there's no point in doing the tests again?
Maybe you need to check that link in the Testing teams pages.  If there were no changes they wouldn't be doing this again.

---

### Post by kansasnoob on 2010-09-01
RE: the host name issue I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

---

### Post by VastOne on 2010-09-01
> **kansasnoob said:**
> RE: the host name issue I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

Thanks..

I saw this there:

> Colin Watson - I believe this was intentionally removed as part of the installer redesign, but design work may be open to re-evaluation in light of user feedback, so this bug might as well remain open ...

And I find this interesting if it is true in removing this option due to the amount of pride and ownership/branding in naming ones own computer.

Granted it is easy to change but there is bound to be more issues with new users in changing after the fact than during the install, IMHO.

---

### Post by Tracy177 on 2010-09-01
it took me 3 months to make ubuntu lucid work.

now it work almost perfect and im not installing anything any version of ubuntu for the next 3 years no way !!!!


:)

---

### Post by arpanaut on 2010-09-01
> **Tracy177 said:**
> it took me 3 months to make ubuntu lucid work.

now it work almost perfect and im not installing anything any version of ubuntu for the next 3 years no way !!!!


:)

More power to ya!
Some of us just don't have our heads screwed on right...

):P

---

### Post by cariboo on 2010-09-01
+1 for not having our heads screwed on right.

@kansasnoob, I added my affects me too.

---

### Post by kansasnoob on 2010-09-01
> **VastOne said:**
> Thanks..

I saw this there:



And I find this interesting if it is true in removing this option due to the amount of pride and ownership/branding in naming ones own computer.

Granted it is easy to change but there is bound to be more issues with new users in changing after the fact than during the install, IMHO.

What happens with that will depend greatly on the amount of constructive feedback there at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

I've fought a few battles there, just always remember to be polite and explain your POV in detail.

Also be sure to choose "this effects me too" and be absolutely sure to SUBSCRIBE! Once you're subscribed you'll get every new message to your mailbox so you'll be able to stay abreast of things.

If it's a design decision you may have to jump through some hoops and join into some other team or discussion group. This happened with me more than once.

If you really care you'll jump through the hoops and based on my own experience you'll be pleased with the results more often than not.

---

### Post by ktp on 2010-09-01
> **arpanaut said:**
> More power to ya!
Some of us just don't have our heads screwed on right...

):P

nicely put it!!!

---

### Post by ktp on 2010-09-01
> **kansasnoob said:**
> RE: the host name issue I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

I hope there is some way to set host name at install time.  It's not the end of the world if it's not there, but it sure would be nice to set it as part of the install and not worry about it.

---

### Post by bcbc on 2010-09-01
> **Wobblybob said:**
> Yes what happened to being able to name my host system? and for that matter what happened to all the ubuntu desktop amd 64 results on the iso tracker, they have all gone missing? I've added a few this am and now everyone's have gone...

I experienced the same thing. I think you have to subscribe to the testcase first or else your reports just vanish into the ether. So far, after subscribing, my bug report still seems to be there.

---

### Post by ranch hand on 2010-09-01
The QA tag does have some weight to it.

---

### Post by kansasnoob on 2010-09-01
> **bcbc said:**
> I experienced the same thing. I think you have to subscribe to the testcase first or else your reports just vanish into the ether. So far, after subscribing, my bug report still seems to be there.

IMHO that's quite true.

If I just report a bug it may be ignored indefinitely!

However if I properly report a bug while performing any type of official qa testing, once it get's the qa tag, you do get a response! It may not always be the response you'd like but if it's a true "bug" you will get some response.

IMHO Ara Pulido has done an exemplary job with QA. I must also credit Henrik because he drew me in.

I'm thinking we need a Henrik style recruitment effort again for iso and upgrade testing. And they've now added desktop testing!

The QA team has done a really good job of writing test case instructions.

---

### Post by bcbc on 2010-09-01
> **kansasnoob said:**
> IMHO that's quite true.

If I just report a bug it may be ignored indefinitely!

However if I properly report a bug while performing any type of official qa testing, once it get's the qa tag, you do get a response! It may not always be the response you'd like but if it's a true "bug" you will get some response.

IMHO Ara Pulido has done an exemplary job with QA. I must also credit Henrik because he drew me in.

I'm thinking we need a Henrik style recruitment effort again for iso and upgrade testing. And they've now added desktop testing!

The QA team has done a really good job of writing test case instructions.
I was referring to the qa test tracker - but I agree with you as well regarding bugs being noticed. :)

I think some credit should go to you for pushing upgrade cases. Definitely wasn't done enough for 10.04, hopefully 10.10 will be smoother as a result of that.

---

### Post by TDK800 on 2010-09-02
Running alpha-2 atm, when should the beta version related updates be expected to appear in the update-manager?

---

### Post by 23meg on 2010-09-02
> **TDK800 said:**
> Running alpha-2 atm, when should the beta version related updates be expected to appear in the update-manager?

If you've installed all updates, you're not running Alpha 2; you're running beta, regardless of what milestone you've started with. There's no such thing as beta-related updates; like all other milestones, the beta is a snapshot of certain subsets of the package archive on a predetermined date which sees a bit of extra (ISO) testing against showstoppers.

---

### Post by kansasnoob on 2010-09-02
I see ubiquity is up to version 2.3.15, I wonder if we'll have a third round of testing?

I feel bad about having to "fail" the "entire disc" and "side by side" tests, but I'd feel even worse if I saw dozens of Windows users complaining about installer confusion resulting in their Win getting munched :shock:

---

### Post by ranch hand on 2010-09-02
> **kansasnoob said:**
> I see ubiquity is up to version 2.3.15, I wonder if we'll have a third round of testing?

I feel bad about having to "fail" the "entire disc" and "side by side" tests, but I'd feel even worse if I saw dozens of Windows users complaining about installer confusion resulting in their Win getting munched :shock:
I have to admit that this would be a bad thing.  It would also give me a very good feelling.  I have been "munched" one too many  times by MS to not enjoy the very thought of just screwing entire systems (so far the Dreaded Mother in Laws MS install is intact but boy is it tempting).

---

### Post by Nullack on 2010-09-02
> **kansasnoob said:**
> 
So, it's up to me to search?


Mate the process is that bug reports are linked to in the QA tracker for ISO testing.

If you want to help with coding fixes for bugs with ISO testing, the best place to do so is looking at the QA tracker.

Not all bugs being reported will end up here in the forum, if any at all.

cheers

---

### Post by 23meg on 2010-09-02
Closing this, as the beta has been released. Thanks to everyone who participated.

---

