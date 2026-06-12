---
title: "Call for iso testing"
date: 2010-11-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-11-29
I got this email this morning:

> Hi everyone!

Natty Alpha 1 is due this week and candidate images will start appearing
hopefully on Tuesday.

As usual we'll be asking everyone on the QA team to participate in the
image testing to ensure we have good test coverage.

The procedures for testing ISO images and reporting results are
explained on [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

Test results will be tracked on [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

You may have accounts on the tracker from last time. Please register if
you are new to this.

Please let us know if you have any questions.

We will coordinate testing in #ubuntu-testing on freenode. Please, go
there often to see what others are testing or what needs to be tested.

Thank you very much for your help and happy testing!

-- Jean-Baptiste irc: jibel 

---

### Post by kevpan815 on 2010-11-29
Sorry Guys, but with my 5 GB Download Limit, I will have 2 wait 4 Alpha 1 Gold Master, Just Fyi.

---

### Post by kansasnoob on 2010-11-29
I knew it was coming :D

I'm sweating ubiquity/casper bugs:

[http://ubuntuforums.org/showthread.php?t=1629809](http://ubuntuforums.org/showthread.php?t=1629809)

Upon more testing a new one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

I've yet to devise a time efficient manner of iso-testing the new ubiquity, it's so darn buggy I need five days of iso-testing ;)

Seriously, I spent the past three days on those bugs. I performed 32 test installs trying different scenarios!

I did two today with the Natty Live Daily and about the only change I see is the return of the "import manager". like that's more important than wiping out partitions that you wanted to keep :oops:

The new ubiquity was IMHO the worst regression since Gutsy.

---

### Post by cariboo on 2010-11-29
I did a test install the other day, and used the install beside option. it worked perfectly on a system with a 40Gb hard try, it split the drive into two 20Gb partitions, and used the swap partition form the first install. I was quite happy with the results.

---

### Post by ratcheer on 2010-11-30
I cannot get anywhere with the ISO QA Tracker. I go to the linked page and log in. It says they are only doing Alpha testing at the moment and to click for details. When I click it, it takes me right back where I started. Around and around in circles.

I will be testing the alternate ISO, momentarily, but I cannot figure out how to get in to report my results.

Tim

---

### Post by cariboo on 2010-11-30
Are you logged in? IF you are you should see a page that looks like the screen shot.

---

### Post by ratcheer on 2010-11-30
Yes, I was logged in. I never could get to a test case page like that one. Just a page that said no testing is currently in progress. I'll try again.

Tim

---

### Post by ratcheer on 2010-11-30
Weird. When I go to the [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures), I am logged in. Then, when I go to the ISO Testing link on that page, I am not logged in and it will not accept my QA Tracker password. WTH?

Tim

---

### Post by cariboo on 2010-11-30
It's a separate login for the iso testing page. I just login, close the page, then reopen it

---

### Post by wilee-nilee on 2010-11-30
It was not until about 2 days ago that I could get the daily to load and install to virtual box.

Viva the testing, it is kinda fun if you have a method to do so without anything but the tested release breaking.

Also did a full install today to a SDHC card no menu dropdown hmmm, and looks to be unity.

---

### Post by kansasnoob on 2010-11-30
Hmmm, I'd tried the 11/29 daily and the Live Desktop worked fine with an few minor tweaks, the testing iso simply gives me an unusable desktop :(

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683356](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683356)

I see the bad bugs are stacking up:

[ATTACH]177027[/ATTACH]

This is why I respect the devs so much. Changing to unity is no small task, yet they'll get it done :D

I actually love these new challenges, of course I don't have to fix things, but even the learning curve as a user is a bit of a challenge.

I'd bet we'll see a rebuild.

---

### Post by kansasnoob on 2010-11-30
> **cariboo907 said:**
> I did a test install the other day, and used the install beside option. it worked perfectly on a system with a 40Gb hard try, it split the drive into two 20Gb partitions, and used the swap partition form the first install. I was quite happy with the results.

Yes, I don't like the presence of the "use entire partition/disc" options after selecting "alongside", but taking things a bit further I've been trying to figure out why people end up losing data/OS's.

I think I'm getting it narrowed down, ATM it looks like if no extended partition is present it might munch the largest primary. I'd hoped to test this more today but Unity basically shut me down.

---

### Post by cariboo on 2010-11-30
I just did a successful install of today's daily live in vbox, of course unity wouldn't run, but the classic desktop did. 

Now that it worked successfully, I have a hard drive with lots of unpartitioned space, so I'll give that a try.

---

### Post by kansasnoob on 2010-11-30
The upgrade test is up now but I'm really bummed out seeing that the bug I signed onto is triaged.

Basically that eliminates anyone from testing if they have a 2D GPU - not good.

---

### Post by cariboo on 2010-11-30
Triaged, means that the bug is on someone's radar, it doesn't ,eam nothing will be done about it.

From [The Launchpad Blog]("http://blog.launchpad.net/general/of-bugs-and-statuses")

> Triaged (Keep This Bug On The Radar)
This is an intermediate status that can be used to distinguish community-confirmed bugs from bugs that the official QA team has acknowledged and plans on working on. Many projects don&#8217;t need a separate stepping stone and developers can pick bugs directly from Confirmed into In Progress. At this point, we are sure that a) the bug has been reproduced and established b) developers have acknowledged.



---

### Post by kansasnoob on 2010-11-30
> **cariboo907 said:**
> Triaged, means that the bug is on someone's radar, it doesn't ,eam nothing will be done about it.

From [The Launchpad Blog]("http://blog.launchpad.net/general/of-bugs-and-statuses")

Regardless of the official definition I've generally found "triaged" to mean "no time soon". Of course I could be wrong but we have about 48 hours until release.

I love Ubuntu but I know some people like to "flame-out" like what happened with the supposed default wallpaper for Maverick. I'm generally patient regarding the problems I encounter myself.

Just updated my testing maverick so now it's time to run the upgrade test.

---

### Post by ranch hand on 2010-12-01
Good luck all.  I hope it works great.  Can't do it this time.

New job and I have to feed in the morning and there isn't even a phone there yet, let alone an internet connection.

I get to visit my box about once a week.  Kind of bummed about the ISO testing but really pumped about a Ranch manager/hand job for an absenty owner.  Pretty nice house and pretty good equipment.  Start up outfit so things are a little rough but the cows look pretty good and the breeding program is good.

---

### Post by cariboo on 2010-12-01
Good luck in your new job, ranch hand.

---

### Post by kansasnoob on 2010-12-01
> **ranch hand said:**
> Good luck all.  I hope it works great.  Can't do it this time.

New job and I have to feed in the morning and there isn't even a phone there yet, let alone an internet connection.

I get to visit my box about once a week.  Kind of bummed about the ISO testing but really pumped about a Ranch manager/hand job for an absenty owner.  Pretty nice house and pretty good equipment.  Start up outfit so things are a little rough but the cows look pretty good and the breeding program is good.

Good to hear from you.

---

### Post by kansasnoob on 2010-12-01
The upgrade went off without a hitch.

---

### Post by inportb on 2010-12-01
> **kevpan815 said:**
> Sorry Guys, but with my 5 GB Download Limit, I will have 2 wait 4 Alpha 1 Gold Master, Just Fyi.

Look, I know you're trying to stay within your networking limit, but can't you spare a few bytes?

---

### Post by lonniehenry on 2010-12-01
Ranch Hand,
Good luck in your new job.  Will miss your take on the testing and your suggestions to the people with problems, especially with grub problems. You have helped many in the past.  Drop in when you can.

---

### Post by kansasnoob on 2010-12-01
The new build is worse! I just get a compiz crash report but I'm not sure I was able to send it.

Oh, mail message popped up! It did file:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/683840](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/683840)

---

### Post by kansasnoob on 2010-12-02
The third round of testing went pretty well, and I managed to reproduce a few old Maverick bugs and add to the bug reports.

Sometimes trying to figure out how to reliably reproduce bugs can be a real bear, especially when the bug requires completing one or more actual installs.

---

### Post by kahping on 2010-12-03
Unsticky since Alpha 1's out?

---

### Post by jerrylamos on 2010-12-04
> **kahping said:**
> Unsticky since Alpha 1's out?

Nope, not really out, still to fat to fit on a CD.  I tried DVD/RW on Ubuntu a while ago but gave up because Ubuntu couldn't erase the DVD/RW disk and I don't want to buy a new DVD every time CD daily/build comes out.
CD/RW usually work on Ubuntu.

No clue why Ubuntu can't ditch enough code to fit on the CD.  Example I use Open Office Write all the time, but wouldn't have a problem with a .iso without it since Synaptic can fix that.

Three of my four test pc's won't boot from USB.

Jerry

---

### Post by teh603 on 2010-12-05
So if its out, why isn't there a sticky of the release announcement?

---

