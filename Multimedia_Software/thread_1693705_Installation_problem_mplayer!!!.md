---
title: "Installation problem mplayer!!!"
date: 2011-02-23
forum: Multimedia Software
---

### Post by insecure hyena on 2011-02-23
Hi everyone I write this post to ask some help installing mplayer on Ubuntu Lucid Lynx 10.04.
I added some ppa's and some other repo to my list and precisely here there are my additions:

[[img]http://s2.postimage.org/bbu07pf6t/Screenshot_Software_Sources.png[/img]](http://www.postimage.org/)

The result is that now I can't install mplayer cause it seems that it has some unsatisfied dependencies.
If I try to install the specified libraries I get that two of them are already installed and the other two requires the uninstallation of a lot of package in particular related to the vlc mediaplayer.
Here there are the two libraries that requires the uninstall of packages already installed on my system.

[[img]http://s2.postimage.org/p1rajzhg/Screenshot_user_user_laptop_1.jpg[/img]](http://postimage.org/image/p1rajzhg/)

[[img]http://s2.postimage.org/p1sy3bz8/Screenshot_user_user_laptop_2.jpg[/img]](http://postimage.org/image/p1sy3bz8/)

What should I do?
I added the overmentioned repos and ppas to have some backports of cutting edge and updated software like vlc or rhytmbox on Lucid and now it seems that they are the cause of the impossibility to install new software like mplayer on my machine.

P.S: I should say sorry for my bad English and at the same time if something I've exposed is not clear please ask. I'll try to give additional information or better explanation. Thanks to all.

---

### Post by SeijiSensei on 2011-02-23
One of the best third-party repositories for mplayer I know of is [https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa).  While you're there, install his smplayer app as well.  You'll be happy you did.

You'll need to remove any existing mplayer files first.  A "sudo apt-get purge mplayer mplayer-*" should be all you'll need.

If you're really adventurous, you can [build mplayer from source]("http://ubuntuforums.org/showthread.php?t=1542240").

---

### Post by insecure hyena on 2011-02-23
Thank you very much for your intervention :)!
I tried to add the ppa you suggest me but the situation didn't change at all...I get the same result...same unsatisfied dependencies... :(
However let me say thank you again for your advice :D!

---

### Post by mc4man on 2011-02-23
this is the best mplayer ppa atm, updates to current a couple of times a week
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)
The mplayer build there uses an internal ffmpeg so no conflicts with what you have

If still getting error then it's not because of installing mplayer - don't have time r. now to check your enabled ppa's, you should take a look and see if any have replaced the lucid ffmpeg shared libs with ones backported from maverick.
One needs to be careful when using multiple ppa's

( you can remove the gstreamer ffmpeg plugin's dependency on shared ffmpeg libs by using this ppa, will provide superior gstreamer packages
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)


You may want to disable some of your current ppa's, at least ck. and see what they are providing - synaptic > Origins tab

---

### Post by insecure hyena on 2011-02-23
Oh thank you I've done as you suggest me, I've added the two repos and now I've installed mplayer.
However I don't get it where resided the problem.
I'll try to further investigate which of the repos and ppas I've added created the problem.
However I said again thank you.
If that's not a problem I'll leave this thread open just to investigate the nature of the problem.

---

### Post by joseph tucker on 2011-02-23
how do i install audio and vidio codecs in ubuntu 10.10

---

### Post by gordintoronto on 2011-02-23
> **joseph tucker said:**
> how do i install audio and vidio codecs in ubuntu 10.10

Start Administration/Synaptic Package Manager. Enable the medibuntu repository. Install "ubuntu-restricted" applications.

---

### Post by tommcd on 2011-02-23
> **insecure hyena said:**
> 
However I don't get it where resided the problem.

The problem here is you are using PPA repos, which are totally unsupported by Ubuntu. If you stick with the MPlayer that is already in the Ubuntu repositories you will be fine.
As soon as I saw your thread I knew it was a problem with those all too often problematic PPAs even before I read it.

---

### Post by beew on 2011-02-24
> **tommcd said:**
> The problem here is you are using PPA repos, which are totally unsupported by Ubuntu. If you stick with the MPlayer that is already in the Ubuntu repositories you will be fine.
As soon as I saw your thread I knew it was a problem with those all too often problematic PPAs even before I read it.

The problem is mplayer in Ubuntu's repo is outdated and crippled so who cares if it is "supported"?

To OP,

Use a ppa by all means.

I use this one [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/~ripps818/+archive/coreavc")

I don't use coreavc but this is a very good version of mplayer, it is multithreded and updated frequently.If you don't use coreavc then don't install dishowserver.

---

### Post by beew on 2011-02-24
> **SeijiSensei said:**
> One of the best third-party repositories for mplayer I know of is [https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa).  While you're there, install his smplayer app as well.  You'll be happy you did.

You'll need to remove any existing mplayer files first.  A "sudo apt-get purge mplayer mplayer-*" should be all you'll need.

If you're really adventurous, you can [build mplayer from source]("http://ubuntuforums.org/showthread.php?t=1542240").

I read about rvm quite a bit but it seems that it hasn't been updated for quite a while and also it doesn't work for Maverick.

---

### Post by tommcd on 2011-02-24
> **beew said:**
> The problem is mplayer in Ubuntu's repo is outdated and crippled so who cares if it is "supported"?

I have found that the MPlayer in Ubuntu's repos works fine for my needs.
The problem with those PPA repos is plainly evident here. People commonly run into all kinds of package dependency and or package corruption problems that they have no idea how to solve.
It seems there is quite a bit of disagreement here about which is the "best" (i.e., least problematic) PPA for MPlayer.

---

### Post by beew on 2011-02-25
> **tommcd said:**
> I have found that the MPlayer in Ubuntu's repos works fine for my needs.
The problem with those PPA repos is plainly evident here. People commonly run into all kinds of package dependency and or package corruption problems that they have no idea how to solve.
It seems there is quite a bit of disagreement here about which is the "best" (i.e., least problematic) PPA for MPlayer.


For your needs maybe. But I find it inadequate in playing high resolution content and it is buggy (among other things it uses only a single core in my dual core machines) I uses a lot of ppas with no problem. In fact I install most of my applications (ie non system software) with ppas. Open source software usually has very frequent release cycle, Ubuntu's repo just cannot keep up with  the new features and bug fixes and in 6 months you will be terribly out of date, this is especially true with multimedia software. Moreover, I don't want to upgrade my whole OS every 6 months,  my plan is to keep a release for about a year, so I am keeping Maverick til about November and will skip Natty altogether. Two points : 1) If I don't use ppas I would be even more outdated. 2) Using ppas would have a lot less stability problems,--if any,--than upgrading the whole OS.

Think about that, it is unreal to expect people who use LTR to stick to 2 -3  year old software just because it is officially supported. I would rather use up to date tools with a bit of risk (minimal in my experience and I am quite new at this) than museum pieces which are "stable". With commercial software it may be reasonable but open source projects typically evolve a lot more quickly.

---

### Post by insecure hyena on 2011-02-25
I totally agree with beew. That's also my exactly point of view! :D

---

### Post by SeijiSensei on 2011-02-25
> **beew said:**
> Open source software usually has very frequent release cycle, Ubuntu's repo just cannot keep up with  the new features and bug fixes and in 6 months you will be terribly out of date, this is especially true with multimedia software.

That's why I build mplayer from source two or three times a year.  I don't do that for any other mainstream software in the Ubuntu repos, but mplayer just moves too fast for the Ubuntu packagers to keep up.

---

### Post by tommcd on 2011-02-25
> **beew said:**
> 
Think about that, it is unreal to expect people who use LTR to stick to 2 -3  year old software just because it is officially supported. I would rather use up to date tools with a bit of risk (minimal in my experience and I am quite new at this) than museum pieces which are "stable". 
The whole point of using a LTS release is that it focuses on *stability*, rather than having the newest of everything. People who want the newest software should just use the newest versions of Ubuntu when they are released. Not only are the apps newer, but all the libs, the kernel, gcc, and everything else will be newer. Therefore it will easier to use the newest software which often depends on the newest libraries. Trying to use a lot of unsupported PPAs, which are all to often of dubious quality, as opposed to just upgrading to the newest version of Ubuntu, is hardly a recipe for stability.
Also, the newest version of any software is not necessarily the best. Sometimes newer software introduces bugs that were not present in that older museum piece of software.

The problems caused by PPAs are all over this these forums. Furthermore, it is my belief that most of the problems that people have when doing a dist-upgrade to a newer version of Ubuntu are caused by using many unsupported repos. This is why 3rd party repos are disabled by default when doing a dist-upgrade.

I am not saying that nobody should ever use a 3rd party repo. The problem is that people all to often get themselves into trouble with those PPAs that they are unable to fix. Also, because the PPAs are hosted on LaunchPad, it seems that a lot people think the PPAs are supported by Ubuntu when they are not. Anyone, regardless of their skill or lack therof, can upload software to a PPA.

---

### Post by beew on 2011-02-25
> **tommcd said:**
> The whole point of using a LTS release is that it focuses on *stability*, rather than having the newest of everything. People who want the newest software should just use the newest versions of Ubuntu when they are released. Not only are the apps newer, but all the libs, the kernel, gcc, and everything else will be newer. Therefore it will easier to use the newest software which often depends on the newest libraries. Trying to use a lot of unsupported PPAs, which are all to often of dubious quality, as opposed to just upgrading to the newest version of Ubuntu, is hardly a recipe for stability.


The problems caused by PPAs are all over this these forums. Furthermore, it is my belief that most of the problems that people have when doing a dist-upgrade to a newer version of Ubuntu are caused by using many unsupported repos. This is why 3rd party repos are disabled by default when doing a dist-upgrade.

I am not saying that nobody should ever use a 3rd party repo. The problem is that people all to often get themselves into trouble with those PPAs that they are unable to fix. Also, because the PPAs are hosted on LaunchPad, it seems that a lot people think the PPAs are supported by Ubuntu when they are not. Anyone, regardless of their skill or lack therof, can upload software to a PPA.


Sorry, I am really having a problem with this attitude.  You keep saying "stability" as if  this is the be all and end all, what about performance? 

You sound like someone who would shiver in  fear at home all day because it would be risky to go out.. you may get run over by a car, or get mugged etc. Now if someone does get run over, you would show up in the hospital to lecture him/her  "I told you so, if you have stayed home you wouldn't  have gotten into the traffic accident that landed you in hospital" (This is exactly what you do with OP here, there is no constructive suggestion, only that you shouldn't have ventured out of the official repo,--home)

"Stability" in Ubuntu talk doesn't mean more reliable performance, it just means not changing, therefore predictable. So something which fails or breaks predictably would be more "stable" than something that just might work in this technical sense (like mplayer in the official repo) It is not necessarily desirable  in spite of the sound of it.

I use A LOT of ppas and never had I got into a problem that I could not get myself out of, sometimes with a little help from the forums. So your diatribes against PPA are just pure fear mongering. Linux is about customization and if you want to customize your machine in the way you want, you are going to run a little risk, whether you install from ppas or compile from source (also not officially supported)

 So what is the problem that people show up in the forums asking for  help because of ppas? The forums are also full of people with problems  upgrading  distros (not because of ppas) or updating kernel. So maybe we should also turn off the update manager once we get things in working order (or not quite, but just predictable enough so it is "stable") You are inexperienced but eager to tinker and learn, you mess up and come to ask for help. You learn how to fix your  problems so next time when someone new come along with similar  problems you can help them out. This is what the forums are for! You never learn unless you have tried to fix  some problems. 

I really cannot see how upgrading the whole OS every 6 months, with the risk of incompatible drivers and new bugs (at the system level) is a better way to keep software fresh. Moreover, Ubuntu's repo freezes before the actual release, so even with a distro upgrade you may still be stuck with outdated software, only less outdated and some will be aging rather rapidly within the 6 months before the next release. So you are asking we should go through the hassel of distro upgrade every 6 months while always putting up with diminished performance, that doesn't make a lot of sense.

> Also, the newest version of any software is not necessarily the best.  Sometimes newer software introduces bugs that were not present in that  older museum piece of software.Then by your logic why update anything at all? New Ubuntu has bugs that are not in old version. Some people get busted because of a kernel update, etc etc. 

By the way old museum pieces  often have bugs that are fixed in the new version. With ppas you always have choice, you can use another ppa if one version is bad,  or lock your version, or downgrade your versio by purging the ppa. What is wrong with choice?

---

### Post by tommcd on 2011-02-26
> **beew said:**
> Sorry, I am really having a problem with this attitude.  You keep saying "stability" as if  this is the be all and end all, what about performance? 
First off, where exactly is the *attitude*??? Perhaps you should read your last post again. 
> **beew said:**
> 
You sound like someone who would shiver in  fear at home all day because it would be risky to go out.. you may get run over by a car, or get mugged etc. Now if someone does get run over, you would show up in the hospital to lecture him/her  "I told you so, if you have stayed home you wouldn't  have gotten into the traffic accident that landed you in hospital"
Now *that*!!! is an attitude!!!  
You are making this personal. I was only talking about software. 

I never said there is anything wrong with choice or using PPAs. You really need to read my last post again. You know, the part where I said:
> I am not saying that nobody should ever use a 3rd party repo. ...

---

