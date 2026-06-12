---
title: "To upgrade to 10.10? or wait for LTS?"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by polardude1983 on 2010-09-09
No I know that Ubuntu 10.10 is now dropping 32bit support and is now only going with 64bit.

Question is should I upgrade to 10.10? or should i just stay at 10.04 LTS and wait for another LTS edition?

Is there a way to only upgrade LTS editions so that i dont have to upgrade to the others? I thought i read that there was some way where it doesn't ask you to update until another LTS edition comes out. Anyways responses would be great

---

### Post by ezsit on 2010-09-09
Where did you hear that Ubuntu was dropping 32bit support? If that were the case, the news should be all over the net by now.

---

### Post by cj.surrusco on 2010-09-09
I seriously doubt that they are dropping 32-bit support. I mean, 64-bit is the *default* download on ubuntu.com, but I can't imagine them dropping 32-bit. I'd be willing to bet that over a third of Ubuntu users run 32-bit.

---

### Post by philinux on 2010-09-09
> **polardude1983 said:**
> No I know that Ubuntu 10.10 is now dropping 32bit support and is now only going with 64bit.



Not at all. No idea where that FUD came from.. [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

---

### Post by polardude1983 on 2010-09-09
Something said its dropping i386 or so. isnt that 32bit support?

> If you're planning on using Ubuntu 10.10 Maverick Meerkat on a computer with a processor older than i686, well... you can't.

Ubuntu 10.10 will be dropping support for i386-i586 processors so it can take advantage of the i686 optimizations. Apparently this has been discussed and confirmed at UDS-M.

---

### Post by 98cwitr on 2010-09-09
^^^no, x86 is the microarchitecture, it's just diff generations of Intel design...it doesn't coin 32-bit or 64-bit...there's x86-32 (IA32) and x86-64 (IA64), thus designating the _memory addresses_

by them dropping i386 support, it only means they will not support i386 processors (old *** processors from the 80s and 90s), but i686 are both found in IA32 and IA64 forms

[http://en.wikipedia.org/wiki/Intel_80386](http://en.wikipedia.org/wiki/Intel_80386)

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

go 10.10...screw LTS

---

### Post by QIII on 2010-09-09
I'm not at my Ubuntu machine right now, but I think you can limit the upgrade from LTS to LTS something like this (if memory serves):

Software Sources > Updates > Release Upgrade > Long term support releases only

(If someone else knows different, please feel free to jump in!)

Don't upgrade to Maverick right now unless you intend to test and are willing to take the risks associated with upgrades borking your system as things are readied for the RC.

I used to go with the Beta every time if my Alpha testing made me happy, but my primary machine has ATI graphics.  AMD typically gets the latest driver in the repo for the RC.  Since I want to use the driver, I wait on my primary machine until the RC now.

I will tell you, however, that on my test machine Maverick has been working brilliantly, with few burps.  It loads very fast!

---

### Post by philinux on 2010-09-09
> **polardude1983 said:**
> Something said its dropping i386 or so. isnt that 32bit support?

> If you're planning on using Ubuntu 10.10 Maverick Meerkat on a computer with a processor older than i686, well... you can't.

Ubuntu 10.10 will be dropping support for i386-i586 processors so it can take advantage of the i686 optimizations. Apparently this has been discussed and confirmed at UDS-M. 

Thats dropping support for certain older **hardware** going forward with 10.10. Maverick will still have a 32 bit version.

---

### Post by bodhi.zazen on 2010-09-09
> **polardude1983 said:**
> No I know that Ubuntu 10.10 is now dropping 32bit support and is now only going with 64bit.

Question is should I upgrade to 10.10? or should i just stay at 10.04 LTS and wait for another LTS edition?

Is there a way to only upgrade LTS editions so that i dont have to upgrade to the others? I thought i read that there was some way where it doesn't ask you to update until another LTS edition comes out. Anyways responses would be great

You should only upgrade to a pre-release if you are willing to test and report bugs. Expect bugs ranging from minor to major.

If you do not wish to participate in testing and debugging, wait for the final release.

---

### Post by polardude1983 on 2010-09-09
Well I didn't mean I would upgrade to the beta, I meant when the final release comes. I'm not against upgrading to 10.10 but there seems to be nothing for me to upgrade besides updated softwares which I could do in 10.04.

Why do some people only upgrade from lts to lts? I'm not sure. Maybe I wil or not. Some direction would be nice.

---

### Post by bodhi.zazen on 2010-09-09
> **polardude1983 said:**
> Well I didn't mean I would upgrade to the beta, I meant when the final release comes. I'm not against upgrading to 10.10 but there seems to be nothing for me to upgrade besides updated softwares which I could do in 10.04.

Why do some people only upgrade from lts to lts? I'm not sure. Maybe I wil or not. Some direction would be nice.

lts is for, well, lts (long term support).

Some people prefer stability, others the newest, latest, greatest, your choice.

Personally I prefer a newer release, if it is not broken, tweak it some more =)

My wife is happy with working software and she does not care about age, so she uses LTS to avoid the hassles and potential carnage of an upgrade.

---

### Post by ranch hand on 2010-09-09
I like to have, on my main drive, 2 installs.  One is the LTS that is set up on large partitions, very secure and used for business on the internet.  The other is set up on about 1/3 as much room and is usually the current release.

That is not real secure so it is easier to play with and I admit to spending more time on it.  That kind of release is supported for 18 months instead of the 3 years for the LTS.

With the long support you do not have to update right away to the next LTS but can wait for it to be rock solid.  You have a year of overlapping support for the LTS releases.  That is pretty nice.

---

### Post by uRock on 2010-09-09
I am not even pondering anything before the next LTS comes out. Lucid does the job and does it well. As for newer applications, installing tarballs gets easier with every install.

---

### Post by bodhi.zazen on 2010-09-09
> **uRock said:**
> I am not even pondering anything before the next LTS comes out. Lucid does the job and does it well. As for newer applications, installing tarballs gets easier with every install.

Personally, I try to run the alphas in a VM (they do not always work with KVM). Dual boot the beta. Upgrade when the prerelease is available.

---

### Post by uRock on 2010-09-09
> **bodhi.zazen said:**
> Personally, I try to run the alphas in a VM (they do not always work with KVM). Dual boot the beta. Upgrade when the prerelease is available.
I play with them in VMs. I love watching them grow.

---

### Post by polardude1983 on 2010-09-09
I think I will always just upgrade :)

---

### Post by KegHead on 2010-09-10
Hi!

As much as I would love to test out 10.10, I don't have the knowledge or expertise.

I'll wait for the RC.

KegHead

---

### Post by uRock on 2010-09-10
> **KegHead said:**
> Hi!

As much as I would love to test out 10.10, I don't have the knowledge or expertise.

I'll wait for the RC.

KegHead
I have it in a vbox and it is looking great, but the bug reports are rampant like popups in an unprotected XP machine. I am sure that this will clear up in a near futured update.

---

### Post by feardotcom on 2010-09-11
I think im installing 10.04 back on my machine in the morning. I'm just having way to many issues with 10.10 at the moment.

---

### Post by ELD on 2010-09-11
A question - What would be the best/easiest VM to test Maverick in?

---

### Post by uRock on 2010-09-11
[Oracle VirtualBox]("http://www.virtualbox.org/") works great for me.

---

### Post by bodhi.zazen on 2010-09-11
If you have the hardware, KVM

---

### Post by ktp on 2010-09-11
kvm is what i use and like

---

### Post by ELD on 2010-09-11
I actually ended up using testdrive, seemed to work okay.

---

### Post by feardotcom on 2010-09-11
I like virtualbox, even if it can be slloooowww, especially when downloading/installing, like the visual studio 2010 express edition, it almost freezes up virtualbox.

---

### Post by cj.surrusco on 2010-09-11
I've always found Virtualbox to be very smooth and fast. It is definitely my favorite.

---

### Post by feardotcom on 2010-09-17
Then i must have something set wrong, cause virtualbox freezes randomly. Esp when downloading/installing, like updates. It just semi freezes with a like a 2 min delay. Here latly i cant even get it to install any distros, i was gonna test out slackware and slackware freezes on installation, same thing with fedora. Kubuntu installed fine, but it skips every few minutes. Idk of anymore free vm's so i guess im stuck with virtualbox

---

### Post by borth92 on 2010-09-17
i am very satisfied with Lucid and not that interested in any clean installs so I ask the question, when Maverick comes out, will it be worth the pain involved with upgrading?

---

### Post by sikander3786 on 2010-09-17
To be honest, upgrading has never been smooth for me. I always end up in breaking one thing or another. On the other hand, it does work well for many others. Might be "distribution-upgrade" dislikes me :-)

If you want to test out all the releases, put your /home on a seperate partition and go on upgrading from one release to the other.

I won't upgrade to Maverick even if I am assured of success because 10.04 is LTS and I will stay with it for at least 2 years.

---

### Post by borth92 on 2010-09-17
ill give it a go...maybe, i just want to hear some testers tell me that there's gonna be a significant upgrade in something to make it worth my while

---

### Post by perspectoff on 2010-09-17
> **sikander3786 said:**
> To be honest, upgrading has never been smooth for me. I always end up in breaking one thing or another. On the other hand, it does work well for many others. Might be "distribution-upgrade" dislikes me :-)

If you want to test out all the releases, put your /home on a seperate partition and go on upgrading from one release to the other.

I won't upgrade to Maverick even if I am assured of success because 10.04 is LTS and I will stay with it for at least 2 years.

I have never, ever had a smooth upgrade. Every version upgrades a myriad of things, from databases (MySQL or PostgreSQL), scripting languages (PHP, Python, Perl), and applications (groupware, web servers) to intrinsic hardware and OS processes (splashscreen managers, networking managers, wirless card drivers, temperature monitoring utilities).

I have learned never to upgrade for about 2-3 months after a release at the earliest. For my Drupal websites, for example, I ended up not going to Lucid because the upgrades were incompatible (PHP was updated to a version that Drupal didn't yet recognize). Upgrading from Jaunty to Karmic caused a mish-mash of the Grub bootloader files. The Plymouth splashscreen manager doesn't work in any of my computers, although after 4 months I have at least figured out how to get them all to boot up in Lucid (finally). 

If your version is working for you, I absolutely do not recommend upgrades. It is never smooth.

On the other hand, the upgrade process is a good time to clear out the deadwood of your system. It makes you concentrate on what you really want to carry forward.

But I now set up a parallel installation and always install fresh, then move my databases one by one and make sure the applications, databases, and hardware still work with the new version. 

Obviously, if you don't have a production system and use your computer only for Internet access, some games, or other trivial stuff, it is not as critical. 

I have to say that I still have a few old computers using Hardy that are some of the most reliable, fastest, stable computers I have, and the interface is quite streamlined. I am not compelled to change those to Lucid at all (Lucid still has a number of serious quirks that take a lot of time to tweak). 

The Ubuntu MOTU are focusing on a lot of cutting-edge things, these days, such as mobile computing and cloud computing. Some desktop basics and database-application-OS compatibilities that the rest of us rely upon daily are often not priorities in cutting-edge updates and the newest version. I can not imagine the problems in Maverick awaiting me.

Never be the first nor the last to adopt a new technology.

---

### Post by bodhi.zazen on 2010-09-17
> **feardotcom said:**
> Idk of anymore free vm's so i guess im stuck with virtualbox

KVM
QEMU - qemu will be slow, but may be faster then a broken vBox.
VMWare - both player and server.

Probably not what you want, but there is also LXC (linux containers), Xen, and Openvz.

With that said, it sounds as if there is a problem with your VBox, especially networking stack, you should ask on the VBox forums (be sure to post your hardware and network configuration).

---

### Post by mxboy15u on 2010-09-17
There is nothing significant about this release as far as I can tell. It works pretty much the same as 10.04 for me. I just enjoy being on the bleeding edge, otherwise I would be with 10.04.

---

### Post by VastOne on 2010-09-17
> **borth92 said:**
> ill give it a go...maybe, i just want to hear some testers tell me that there's gonna be a significant upgrade in something to make it worth my while

It is too subjective of a subject to answer to any one users specific needs. I can tell you that I have been running Maverick since Alpha 2 and it meets or exceeds everything I want and need and I now have Beta on all my machines (6).  As was posted, having your /home on a separate partition and using tools to backup your installed packages and source.list for easy restore, you could have a clean install alongside your current one in no time at all, thus know firsthand if you want Maverick or not.

---

### Post by 23meg on 2010-09-17
Merged with the other thread on the same topic.

> **VastOne said:**
> It is too subjective of a subject to answer to any one users specific needs.

That's the bottom line. It's impossible for people to give good advice without knowing your needs, goals and hardware.

---

### Post by borth92 on 2010-09-17
> **VastOne said:**
> It is too subjective of a subject to answer to any one users specific needs. I can tell you that I have been running Maverick since Alpha 2 and it meets or exceeds everything I want and need and I now have Beta on all my machines (6).  As was posted, having your /home on a separate partition and using tools to backup your installed packages and source.list for easy restore, you could have a clean install alongside your current one in no time at all, thus know firsthand if you want Maverick or not.
  im just asking for things like, "hey i noticed a speed increase in the boot time" or maybe "i have experienced more bugs than most beta releases. It is not that subjective of a subject.

Dell XPS M1330
4 GB RAM
2.2 gHz processor

---

### Post by xebian on 2010-09-17
> **borth92 said:**
> im just asking for things like, "hey i noticed a speed increase in the boot time" or maybe "i have experienced more bugs than most beta releases. It is not that subjective of a subject.

Dell XPS M1330
4 GB RAM
2.2 gHz processor

If that's what you want then read all the posts here.  You can see everything from useless to the best and sloow to fastest.

Why is it so hard to understand that you alone and your hardware can gauge it if it's worth it or not?

---

### Post by VastOne on 2010-09-17
> **borth92 said:**
> im just asking for things like, "hey i noticed a speed increase in the boot time" or maybe "i have experienced more bugs than most beta releases. It is not that subjective of a subject.

Dell XPS M1330
4 GB RAM
2.2 gHz processor

Going to 6 production machines with a Beta release is IMHO about the best answer I can give you telling you that everything I run and want to accomplish is doable right now. Of course, this is my environment and comfort level which is again subjective. If you really want to know just build yourself a test environment either with a virtual environment or a separate machine or separate partitions.

---

### Post by borth92 on 2010-09-17
> **xebian said:**
> If that's what you want then read all the posts here.  You can see everything from useless to the best and sloow to fastest.

Why is it so hard to understand that you alone and your hardware can gauge it if it's worth it or not?

Because I want a persons overall opinion, not a compilation of random  opinions about random issues. Plus they may know of an issue that has  not been posted in a couple days, which i would not run into scanning  the forums.

---

### Post by prettyboy85712 on 2010-09-17
Will it be possible to upgrade from the beta directly to the LTS? Or, will it be necessary to start from scratch again?

---

### Post by VastOne on 2010-09-17
> **borth92 said:**
> Because I want a persons overall opinion, not a compilation of random  opinions about random issues. Plus they may know of an issue that has  not been posted in a couple days, which i would not run into scanning  the forums.

The beauty of these forums is the layout and the teaching of users to post what they are looking for in the title, and from my observations at least 90% of the users do a great job of that.  You can also tweak your settings to show 50 posts per page which cuts down on how many times you would have to click to the next page.

It really is just an investment of your time and effort to see what is going on right now in Maverick from my fellow peers living on the edge.

---

### Post by VastOne on 2010-09-17
> **prettyboy85712 said:**
> Will it be possible to upgrade from the beta directly to the LTS? Or, will it be necessary to start from scratch again?

It's detailed in the stickies.. Read those ):P

---

### Post by cariboo on 2010-09-17
It's pretty hard to give you an opinion, that will satisfy you because everybody's hardware is different, I have maverick installed on four different systems, three that are sort of the same except for different model processors, different model motherboards, different graphics cards and different amounts of ram. All three have AMD processors, MSI motherboards and Nvidia graphics cards, but the all have different issues. The fourth is a netbook and again there are different issues there because it's running Unity.

---

### Post by crjackson on 2010-09-17
> **borth92 said:**
> im just asking for things like, "hey i noticed a speed increase in the boot time" or maybe "i have experienced more bugs than most beta releases. It is not that subjective of a subject.

Dell XPS M1330
4 GB RAM
2.2 gHz processor

It's a little slower on my INTEL x2 core laptop with Intel graphics, but works fine otherwise.  I expect the release to be faster.  **It's worth it on THIS machine.**

It's a little slower on my AMD x2 core desktop with nVidia graphics, but works fine otherwise.  I expect the release to be faster.  **It's worth it on this machine.**

It won't boot on my AMD64 laptop with ATI graphics.  The Beta worked fine but after updates, or by installing fresh with the daily build, it won't boot. ** It's _not_ worth it on this machine.**

---

### Post by ranch hand on 2010-09-17
10.10 is NOT a LTS.

10.04 is the LTS.

The next LTS is 12.04.  It is not available at this time, hard as that may be to believe.

---

### Post by bodhi.zazen on 2010-09-17
> **ranch hand said:**
> The next LTS is 12.04.  It is not available at this time, hard as that may be to believe.


LOL !!!!!

:lolflag:

---

### Post by VastOne on 2010-09-17
> **ranch hand said:**
> 10.10 is NOT a LTS.

10.04 is the LTS.

The next LTS is 12.04.  It is not available at this time, hard as that may be to believe.

> **bodhi.zazen said:**
> LOL !!!!!

:lolflag:

I know..Good ole Ranch Hand's cynicism knows no bounds, you have to admire the mans brilliance..!

---

### Post by ktp on 2010-09-17
> **VastOne said:**
> I know..Good ole Ranch Hand's cynicism knows no bounds, you have to admire the mans brilliance..!

yes, you have to.

---

### Post by VMC on 2010-09-17
> **VastOne said:**
> I know..Good ole Ranch Hand's cynicism knows no bounds, you have to admire the mans brilliance..!
> Originally Posted by ranch hand  
10.10 is NOT a LTS.

10.04 is the LTS.

The next LTS is 12.04. It is not available at this time, hard as that may be to believe.
> Originally Posted by bodhi.zazen  
LOL !!!!!

Did you noticed, both of them ol' boys are from Montana. They're probably neighbors.

---

### Post by ranch hand on 2010-09-17
Yup we sure are.  I think it is less than 500 miles apart anyway.

---

### Post by VastOne on 2010-09-17
> **ranch hand said:**
> Yup we sure are.  I think it is less than 500 miles apart anyway.

Wow, you really are close neighbors.  Bet you pass each other on your ranch fence repairs and branding runs every day.

---

### Post by ranch hand on 2010-09-18
Nope, got to be at least nine or ten outfits between us.

---

