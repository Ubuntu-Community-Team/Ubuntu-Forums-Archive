---
title: "Vodafone (Huawei K3520) mobile broadband dongle"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by tomliw on 2010-02-12
Hello people of the forum,
I'm new here. This is my first post. Something tells me my problem will be met with great sighs and shrugs of shoulders. I think you may have heard this problem just a few thousand times.....this is a few thousand and one i'm afraid......sorry.

couple of days ago i took the plunge and installed Ubuntu 9.10. I already run XP Pro. I have the system set for dual booting until i get to grips with Linux and have all that i use daily from software to hardware comprehesively installed and running. then i have this ideal romantic dream of dumping my microsoft heartache, and living a happy life with the new love in town (an OS that works!)

Vodafone (Huawei K3520) mobile broadband dongle. Yes i know its a touchy subject but i am going cross-eyed reading info on various forums from this one to the betavine forums and a detour through vodafone themselves.

I just can't find clear concise info on how to get this dongle up and running with Ubuntu. My laptop is Acer Aspire 5633 WLMi. I would really really appreciate your help on this subject i need to get online with this dongle and Ubuntu.....PLease Help.

Thank you.

---

### Post by alexfish on 2010-02-12
hi

you could try looking here

[http://ubuntuforums.org/showthread.php?t=1244135](http://ubuntuforums.org/showthread.php?t=1244135)

It relates to Ubuntu 9.04 , so you may get it working in 9.10 , you will need your own provider details

regards

alexfish

---

### Post by tomliw on 2010-02-12
hi,

thanks for replying. i read that post you gave link to and can't desipher it. i'm so new to Ubuntu.... want to make it work but feel i've hit a brick wall. i'm slightly dissappointed that i cannot get things moving. it seems to me that linux in general is purely for programmers and developers. every forum ive read there are instances of typing command line txt/code in order to make things work in ubuntu.
i am quite ready and willing to put in the effort to end up with a solid fast safe OS but i can't even get online with mobile broadband, can't play music because mp3's are not supported (due to legalities) it appears that i boot up ubuntu and there is my desktop.....and assuming all i want to do is look at the desktop then its absolutely fine.
i've been reading posts all over for hours over the last couple of days and am back to square one arrghh.
thanks anyway for being the one to reply first. however think i'll ditch linux and stick with crappy windows, at least i can get online and watch video and use itunes.

over and out

thank you

---

### Post by GeorgeVita on 2010-02-12
Hi **tomliw**, welcome to this forum!

I think that Huawei K3520 will work fine with an updated Ubuntu 9.10.
Initial kernel version (included into liveCD) had a bug that affects most 3g modems. The only problem is that you must install (from LiveCD) and then update using any other internet connection (wifi or ethernet).

Post any progress to follow up.

Regards,
George

---

### Post by coffeecat on 2010-02-12
My Vodafone Huawei K3565 works well with 9.10 so, hopefully, the K3520 will as well. But....

> **GeorgeVita said:**
> Initial kernel version (included into liveCD) had a bug that affects most 3g modems. The only problem is that you must install (from LiveCD) and then update using any other internet connection (wifi or ethernet).

Agreed. Install 9.10, then update it with a different internet connection. Then you should be OK. When I plugged my K3565 in to an updated 9.10, network manager detected it. I simply clicked on "Mobile Broadband", followed the simple wizard and was soon connected.

---

### Post by tomliw on 2010-02-13
thanks GeorgeVita and CoffeeCat, will give it a try. apologies for being on a downer in my message regarding this topic. i am not the type of person who wants others to do things for me because if something is worth doing then the fun is in deciphering it. however i will always hold my hands up and ask for help...its the only way to learn.
the version i downloaded was the wubi installer version if that makes any sense....so could i still do what you suggest from that version, or will i have to uninstall and the get a cd version?

thanks

---

### Post by tomliw on 2010-02-28
Hi all,
haven't been able to get my vodafone mobile broadband dongle working with ubuntu 9.10. haven't had chance to update 9.10 using alternative net connection so don't know whether advice from previous posts will work. getting real fed up now...........:(

also tried to use a download from betavine. for vmc connection. although apparently when downloaded it stated the version was for a jaunty 9.04.

tried it anyway and got the following dialogues.

after double clicking the tgz compressed file the archive manager said.

an error occurred while loading the archive.
command line output
tar: this does not look like a tar archive

tar: skipping to next header

tar: exiting with failure status due to previous errors

got some other erors saying wrong architecture i386


apart from this have had things going wrong in ubuntu such as 

going into system, admin, computer janitor,

error dialogue says 'essential package dash missing. there may be problems with apt sources.list or packages files may be missing.

im losing all faith in the claims that linux is the best thing since sliced bread....its clean, slick, fast, stable and it just works! well i disagree, it obviously doesn't.....i cannot seem to do anything...........even opening standard files it has errors or needs patch downloads etc............. im at the end of my tether

[-o<

---

### Post by coffeecat on 2010-02-28
> **tomliw said:**
> Hi all,
haven't been able to get my vodafone mobile broadband dongle working with ubuntu 9.10. haven't had chance to update 9.10 using alternative net connection so don't know whether advice from previous posts will work. getting real fed up now...........:(

You **have to have an updated 9.10 before the Vodafone dongle will work**! A previous poster has already explained why (bug in original kernel - fixed by updating). There is no point in your reproducing problems that are already known about. Do you not have a friend/relative/enemy that can let you plug your machine into their adsl router with an ethernet cable to do the update?

> **tomliw said:**
> also tried to use a download from betavine. for vmc connection. although apparently when downloaded it stated the version was for a jaunty 9.04.

tried it anyway and got the following dialogues.

after double clicking the tgz compressed file the archive manager said.

an error occurred while loading the archive.
command line output
tar: this does not look like a tar archive

tar: skipping to next header

tar: exiting with failure status due to previous errors

got some other erors saying wrong architecture i386

Several points:

You don't really need the Betavine package unless you want a few Vodafone bells and whistles. The Vodafone dongle works just fine with Network Manager **so long as you have updated the original default installation**.

I've just downloaded the Ubuntu.tgz package and unpacked it with the "tar xvfz Ubuntu.tgz" command recommended on the Betavine site. It unpacked without error for me, which suggests you have a corrupted download.

The i386 architecture message you got is about 32-bit/64-bit incompatibility. That being said, I can only find a 32-bit package on the Betavine site, and I'm sure this installed fine for me on my 64-bit Karmic system. 

> **tomliw said:**
> im losing all faith in the claims that linux is the best thing since sliced bread

You've already made yourself fed up by not following advice on this thread. If you fight the operating system, it will fight back. It's your choice. I say this kindly.

---

### Post by tomliw on 2010-02-28
agreed.
i will have to find someone whose router i can use to update 9.10
working away all week so will have to do it next weekend. i hope it all goes ok.
thanks

---

### Post by coffeecat on 2010-02-28
@tomliw, just to add:
 

 I've now checked the 64-bit Karmic laptop installation I set up with the Vodafone dongle and with the Betavine software. The Ubuntu.tgz tarball from Betavine includes three deb packages as follows:
 

 ozerocdoff_0.4-2_i386.deb
 usb-modeswitch_0.9.7_i386.deb
 vodafone-mobile-connect_2.20.01-1_all.deb
 

 Of the three, the 1.0.2 version of usb-modeswitch is available in the Ubuntu repositories, which is what I installed instead of the 0.9.7 package from Betavine. Which is probably why I avoided a 32-bit/64-bit conflict. Also – I can't be 100% sure of this – but I think there is a repo version of ozerocdoff, which is what I installed. Which left the vodafone-mobile-connect package which, being an “all” package, can be installed on 32 or 64-bit systems.
 

 Having said all that, I'm not impressed with the vodafone-mobile-connect app – I tend to simply use Network Manager (you can connect with either). The Betavine vodafone-mobile-connect GUI is not as comprehensive as (I hate to say this) the Windows app that comes with the device.
 

 Also – I had already activated the dongle in Windows.
 

 Anyway – good luck with this. And just to prove that the Vodafone PAYG dongle works with (an updated) Ubuntu Karmic connected via Network Manager, that is how I am posting now. :wink:

---

### Post by coffeecat on 2010-02-28
> **coffeecat said:**
> Also &#8211; I can't be 100% sure of this &#8211; but I think there is a repo version of ozerocdoff, which is what I installed.

I was wrong - and also now confused. I've checked in another 64-bit Karmic installation without the Betavine packages and ozerocdoff isn't showing up in Synaptic, which means I must have used a Betavine ozerocdoff package. Except that the ozerocdoff_0.4-2_i386.deb package gives me a "Wrong Architecture" error just like you - which is hardly surprising: i386 packages are compiled for 32-bit systems. But to have installed ozerocdoff in a 64-bit system, I must have found a 64-bit package. But I can't (at the moment) find a 64-bit package on the Betavine site. Which is mystifying.

If I find (or remember) anything pertinent I'll post back.

---

### Post by coffeecat on 2010-03-01
@tomliw, I don't know whether you're still following this thread, but I'm posting this for anyone else puzzled as to how to install the Betavine software on 64-bit Ubuntu. After a lot of googling (it wasn't easy to find), I rediscovered the page I must have found first time around.

First, I guess you were using [this Betavine page]("http://www.betavine.net/bvportal/resources/datacards/os/ubuntu"). Although it clearly states, "This package has been created for Ubuntu Hardy, Intrepid or Jaunty running on chip sets compatible with Intel 386 architecture" (386 = 32-bit), it nowhere (that I can find) gives links/instructions for 64-bit. Although I can understand Betavine's focus on netbooks, which are 32-bit, 64-bit installations are fairly standard now on newer laptops, and I find Betavine's neglect of 64-bit on their main pages nothing short of unprofessional. And it makes Ubuntu look bad when newcomers get the sort of problems you got - which is unfair because this is down to Betavine. Tch!

Anyway - rant over :wink: - the packages seem to work on Karmic, so don't worry about the "Hardy, Intrepid and Jaunty bit".

So - **Installing Betavine packages on 64-bit Ubuntu Karmic**.

Go to: [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

Scroll down to the "Debian, Ubuntu, etc" heading.

You need to download the following packages:

usb-modeswitch_0.9.7_amd64.deb
ozerocdoff_0.4-2_amd64.deb
vodafone-mobile-connect_2.20.01-1_all.deb

(Those were the latest versions at the time of this post. If there is a later numerical version when you download, choose that. Simply make sure you get the *amd64.deb versions for the first two, and *all.deb for the third. "amd64" is the generic marker for 64-bit - such packages will run on Intel 64-bit processors as well as AMD. *all.deb packages will install on 32 or 64-bit.)

Now, simply install them by double-clicking on them in that order. There is, in fact, a later version of usb-modeswitch in the Ubuntu repositories which you can install via Synaptic if you prefer. If you use the downloaded version, it will probably get updated anyway.

And that should be that. The GUI menu entry for the vodafone package you can find at Applications > Internet.

Good Luck!

---

### Post by tomliw on 2010-04-01
Hey there. thanks to all who spent valuable time on this problem. i appreciate it. i haven't posted for some time due to working all over the country. so i finally decended on my parents house and connected to router. finally got online with the vodafone k3520 mobile broadband dongle. thanks again.
however....new problems have arrisen. i couldn't download the majority of the updates. a dialogue appeared stating i only had a small amount of space and needed to get rid of junk using sudo apt-get clean.........or something like that. i have no idea why. there is about 100MB left apparently so pretty damn useless. please help if you can. thank you

---

### Post by coffeecat on 2010-04-02
The problem you describe is because, when you installed, you made the root partition too small. About 4GB I would imagine. Unless you've saved an **enormous** amount of personal data in your home folder.

Anyway - part of the answer is in your post, but I'll let you work that one out. :wink: I suggest you start a new thread. This is a different problem from your OP and is irrelevant to the thread title, which will put off people who may be able to help.

One piece of advice. When you start a new thread, avoid comments like:

> **tomliw said:**
> pretty damn useless.

I'm sure you meant that the 100MB is pretty useless, but some people will interpret that as an attack on their favourite OS and react accordingly. Regrettable, to be sure, but even the fanboys may have something useful to contribute.

Good luck!

---

### Post by tomliw on 2010-04-03
thank you.

---

### Post by Peterfc on 2010-04-13
Hi Guys

Just got my "Vodafone (Huawei K3565) mobile broadband dongle" working but when i load Firefox all i get is   " Server not found "

Check address for typing errors

If you are unable to load any pages check your computers network

If your computer or network is protected by a firewall or proxy make sure that Firefox is permitted to access the web

Try again

I have followed the advice form information i found after using search options. I have connected via another network connection and completed a full update and my laptop is now up to date as of midday today. 

Thanks for reading

Peter

---

