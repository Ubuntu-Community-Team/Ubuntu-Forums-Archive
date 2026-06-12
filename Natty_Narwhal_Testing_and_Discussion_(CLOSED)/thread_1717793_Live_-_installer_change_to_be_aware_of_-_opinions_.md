---
title: "Live - installer change to be aware of - opinions needed"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-03-30
Some of you undoubtedly know that I've been trying to tackle bugs in the new ubiquity for some time:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I screamed, whined, and shouted to little avail. Then I posted this at Ayatana:

[COLOR="Red"][Killing ourselves softly with our own song?]("http://www.mail-archive.com/ayatana@lists.launchpad.net/msg04586.html")[/COLOR]

That finally got a response :)

So work began to get rid of the deceptive buttons, that was complete in Alpha3, and I was promised that the "use largest free space" would be returned by Beta1.

Well it is, sort of. Here I need feedback from others, and comments at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

What happens now is that if ubiquity decides you have adequate free space and you click on "Install Ubuntu alongside them" the installation process just starts! No chance at all to view what it's doing!

I'm not sure what an adequate amount of free space is other than what I've posted at the bug report :)

I'd really appreciate some help on this one if you have the time.

Edit: corrected title.

---

### Post by ronacc on 2011-03-30
the only time I trust ubiquity to partition or format my drive is if it is the first install on that drive , it has screwed me too many times in the past . I now use a standalone gparted cd to do the preparation and just pray that ubuqiuty will actually put the install where I tell it to .

---

### Post by cariboo on 2011-03-30
I have to agree with ronacc, the only time I've used the automatic partitioning of any sort is on a bare drive, other wise I always use manual partitioning.

---

### Post by jerrylamos on 2011-03-30
> **cariboo907 said:**
> I have to agree with ronacc, the only time I've used the automatic partitioning of any sort is on a bare drive, other wise I always use manual partitioning.

Having been burnt to a crisp and at the stake by ubiquity over the years, I almost always run

sudo gparted

so I know what is where what the labels and bytes used are and can partition and format making my own mistakes, not those made by ubiquity.

Now at the moment the 29 March .iso hangs on my Acer Aspire one netbook.  The hang occurs just at the point ubiquity is trying to determine the partitions.  Yes there's a launchpad bug written.

Somebody else can test "automatic" screw ups by ubiquity.

Jerry

---

### Post by kansasnoob on 2011-03-30
Based on the first three comments should we just eliminate the live installer altogether?

The alternate is truly a modified Debian installer.

I'd had no problems at all with the live installer (ubiquity) since I began with Gutsy until they changed things in Maverick.

---

### Post by ronacc on 2011-03-30
unfortunately Ubuntu is determined to make the install process as interactionless and as mindless as possible so we will just have to continue to tiptoe around ubiquity as best we can .

---

### Post by coffeecat on 2011-03-30
There's quite an irony here. :) Experienced users are avoiding anything but the manual/advanced option of ubiquity because of earlier bad experiences. But it needs experienced users to test those options likely to be used by newcomers and the less-experienced to make sure there is nothing that will bite them. Like the notorious Maverick install-alongside-let's-nuke-Windows-while-we're-about-it option.

And for getting the devs to actually do something about that, I think the Ubuntu community owes kansasnoob an eternal debt of gratitude. Let's hear it for him! =D>=D>=D>

---

### Post by cariboo on 2011-03-30
The only reason I use the live installer, is so that I can continue doing things while the install is in progress, I've installed a Linux distribution so many times, that I get bored silly watching it. 

Once you've entered the info needed to do the install, there is no need to watch it, I normally fire up Firefox, and check the forums while the install is in progress.

---

### Post by ronacc on 2011-03-30
I do salute kansasnoob for goading the devs into doing something . but what discourages many of us who have been around for awhile is that any fix will be short lived , they just can't resist "improving it " a little more as they have every other time that they had the installer working right .

---

### Post by ranch hand on 2011-03-30
> **coffeecat said:**
> There's quite an irony here. :) Experienced users are avoiding anything but the manual/advanced option of ubiquity because of earlier bad experiences. But it needs experienced users to test those options likely to be used by newcomers and the less-experienced to make sure there is nothing that will bite them. Like the notorious Maverick install-alongside-let's-nuke-Windows-while-we're-about-it option.

And for getting the devs to actually do something about that, I think the Ubuntu community owes kansasnoob an eternal debt of gratitude. Let's hear it for him! =D>=D>=D>
You are right on the dot there.

I will not, on my setup, even think about auto installing.   I have too many things on here to risk.

kansasnoob has gotten impressive results and there is certainly some improvement.  Reverting to the old style seems to me to be the best thing they could do,

As a total Linux noob I had no trouble at all installing 8.04.  I really have never seen the problem that these improvements are meant to correct.

---

### Post by VastOne on 2011-03-30
> **coffeecat said:**
> There's quite an irony here. :) Experienced users are avoiding anything but the manual/advanced option of ubiquity because of earlier bad experiences. But it needs experienced users to test those options likely to be used by newcomers and the less-experienced to make sure there is nothing that will bite them. Like the notorious Maverick install-alongside-let's-nuke-Windows-while-we're-about-it option.

And for getting the devs to actually do something about that, I think the Ubuntu community owes kansasnoob an eternal debt of gratitude. Let's hear it for him! =D>=D>=D>

> **ranch hand said:**
> You are right on the dot there.

I will not, on my setup, even think about auto installing.   I have too many things on here to risk.

kansasnoob has gotten impressive results and there is certainly some improvement.  Reverting to the old style seems to me to be the best thing they could do,

As a total Linux noob I had no trouble at all installing 8.04.  I really have never seen the problem that these improvements are meant to correct.

Agree on both... and well done kansasnoob

The ideal solution from a user perspective, especially a new user is the fundamental understanding of partition manager and partitions in general, especially the sdX layout.  The sooner a user understands these fundamental things about their own hardware, the easier it is to use the manual process and take it out of the hands of ubiquity...

I am sure there are how to videos already setup, but if there is not a worthy one, _we_ should create one and that could/should be a part of the LiveCD sitting on the desktop with a MUST WATCH flag... 

Training before installing, a novel approach at little cost or footprint...

All my 2 cents, and it ain't worth much...

---

### Post by kansasnoob on 2011-03-30
From my interaction with several devs I believe most of them test with VM's.

And, for sure, most of us that know what we're doing will use manual partitioning to work on production machines.

But shortly before iso-tesing begins I always back up anything really important to me and go forward trying very hard to NOT remember how to do things :D

I like to call it "putting my noob shoes on" which ticks some people off, but I then point out my own forum moniker.

My goal is to make everyones first Ubuntu experience as pleasant as mine was with Gutsy.

So, since not many others are willing to really put their hardware/data to the test, I have a "trade-off" in the works ;)

Explain to me **step-by-step** how to record a screencast using nothing but tools in the repos so I can show everyone what the process looks like :D

BTW is this hard for others to read:

[ATTACH]187581[/ATTACH]

I think the sub-text is incredibly hard to read but I'm legally blind so I'm a darn poor judge.

---

### Post by kansasnoob on 2011-03-30
> **VastOne said:**
> Agree on both... and well done kansasnoob

The ideal solution from a user perspective, especially a new user is the fundamental understanding of partition manager and partitions in general, especially the sdX layout.  The sooner a user understands these fundamental things about their own hardware, the easier it is to use the manual process and take it out of the hands of ubiquity...

I am sure there are how to videos already setup, but if there is not a worthy one, _we_ should create one and that could/should be a part of the LiveCD sitting on the desktop with a MUST WATCH flag... 

Training before installing, a novel approach at little cost or footprint...

All my 2 cents, and it ain't worth much...

One of the greatest initial challenges I've faced trying to explain things to noobs is device designations which I've just always found simple. I did collaborate with Herman on this:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Of course it's soon to be out-of-date again :(

I learned how to deal with legacy grub and how to multi-boot reading his guide :)

Now I tend to get carried away:

[ATTACH]187585[/ATTACH]

---

### Post by ronacc on 2011-03-30
legally blind has nothing to do with it . the person who chose very light gray and small text for important information is a freaking idiot who should never again be allowed near the interface .

---

### Post by cariboo on 2011-03-30
This is a bit off-topic, but I was playing with Debian wheezy on my Apple G4 the other day, and they now have an option, at least on the ppc version to automagically create a separate home partition when using the guided partitioning option. Might we see something like this in future versions?

---

### Post by VastOne on 2011-03-30
> **kansasnoob said:**
> From my interaction with several devs I believe most of them test with VM's.

And, for sure, most of us that know what we're doing will use manual partitioning to work on production machines.

But shortly before iso-tesing begins I always back up anything really important to me and go forward trying very hard to NOT remember how to do things :D

I like to call it "putting my noob shoes on" which ticks some people off, but I then point out my own forum moniker.

My goal is to make everyones first Ubuntu experience as pleasant as mine was with Gutsy.

So, since not many others are willing to really put their hardware/data to the test, I have a "trade-off" in the works ;)

Explain to me **step-by-step** how to record a screencast using nothing but tools in the repos so I can show everyone what the process looks like :D

BTW is this hard for others to read:

[ATTACH]187581[/ATTACH]

I think the sub-text is incredibly hard to read but I'm legally blind so I'm a darn poor judge.

I use Desktop Recorder, it does the job in a very straight forward process.. Nothing too difficult to master...

As far as the attachment... sight is not an issue for me, but I think it could be better explained than what is there... There is room for more info or at least a pop up when hovered over... 

This choice is the most critical step in the install process, why not elaborate more so that it is clearer... 

Again, IMHO, nothing more or less...

---

### Post by VastOne on 2011-03-30
> **cariboo907 said:**
> This is a bit off-topic, but I was playing with Debian wheezy on my Apple G4 the other day, and they now have an option, at least on the ppc version to automagically create a separate home partition when using the guided partitioning option. Might we see something like this in future versions?

Yet another absolute IMHO,  having a separate partition for home is easily the best thing I have ever done with Ubuntu/Linux...

---

### Post by VastOne on 2011-03-30
> **kansasnoob said:**
> One of the greatest initial challenges I've faced trying to explain things to noobs is device designations which I've just always found simple. I did collaborate with Herman on this:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Of course it's soon to be out-of-date again :(

I learned how to deal with legacy grub and how to multi-boot reading his guide :)

Now I tend to get carried away:

[ATTACH]187585[/ATTACH]

That is a great site full of very very useful information... 

What are the chances of Noob's seeing it before a first install?  Again, something on the LiveCD desktop is a great place to encourage a new user to learn before leaping..

---

### Post by cariboo on 2011-03-30
> **VastOne said:**
> Yet another absolute IMHO,  having a separate partition for home is easily the best thing I have ever done with Ubuntu/Linux...

UDS-O is from May 9 - 13, should we start lobbying now? :)

---

### Post by VastOne on 2011-03-30
> **cariboo907 said:**
> UDS-O is from May 9 - 13, should we start lobbying now? :)

I am in... Sign me up, point me in the direction.. 

Whatever you/we need

---

### Post by cariboo on 2011-03-30
To address kansasnoobs question, I'm trying the install along side option as I type this. The system already had a Natty install using 3 partitions.

I have to say the intial partitioning screen, does look a lot more newbie freindly, with four pretty clear options. 

[LIST=1]
[*]Install along side
[*]Update to Natty
[*]Wipe the hard drive and install
[*]Manual partitioning
[/LIST]

When I clicked the install alongside option, I got the option screen to resize the partitions, then I had to click the next/continue button to start resizing the partitions, and the install continued on from there.

All in all it was a pretty painless installation, both installations boot with no problem. This was an i386 install with no internet, as the system has a Broadcom pci wireless card.

Two bugs that I did find, were:

[LIST]
[*]Sound muted on start up
[*]Wireless device not detected by additional drivers
[/LIST]

---

### Post by Quackers on 2011-03-30
Credit is indeed due to kansasnoob and his tireless efforts to get ubiquity changed. In fact, the changes that have now been made are a major improvement, imho.
I have just one concern with the resizing slider option, and that is that a lot of the less experienced users will be installing side by side with a Windows version. As we have seen many times in forum help requests, it seems that Windows does not like to be resized by anything other than Windows Disk Management console.
It remains to be seen whether problems will arise in the future.

---

### Post by ranch hand on 2011-03-30
> **cariboo907 said:**
> This is a bit off-topic, but I was playing with Debian wheezy on my Apple G4 the other day, and they now have an option, at least on the ppc version to automagically create a separate home partition when using the guided partitioning option. Might we see something like this in future versions?
I am sure that it will be included in the Ubuntu installer.  It is part of the Debian installer so it will be in the Alt Install disk.  No reason to think it would not be on the Live as well.

---

### Post by ranch hand on 2011-03-30
> **cariboo907 said:**
> To address kansasnoobs question, I'm trying the install along side option as I type this. The system already had a Natty install using 3 partitions.

I have to say the intial partitioning screen, does look a lot more newbie freindly, with four pretty clear options. 

[LIST=1]
[*]Install along side
[*]Update to Natty
[*]Wipe the hard drive and install
[*]Manual partitioning
[/LIST]

When I clicked the install alongside option, I got the option screen to resize the partitions, then I had to click the next/continue button to start resizing the partitions, and the install continued on from there.

All in all it was a pretty painless installation, both installations boot with no problem. This was an i386 install with no internet, as the system has a Broadcom pci wireless card.

Two bugs that I did find, were:

[LIST]
[*]Sound muted on start up
[*]Wireless device not detected by additional drivers
[/LIST]

I would not call the sound muted on start up a bug.  it should, I admit, just make sure that the SB analog/digital output jack is off.

Muted is better than having sound that either comes garbled and/or very, VERY loud.  The very loud is what I am getting on the Xubuntu disk at any rate.  I am sure the neighbors can hear it if I forget to turn the sound system off.

This was fixed for 9.04, by the way, so I am not sure why it has come back starting with that great 10.04 release.

---

### Post by Hedgehog1 on 2011-03-30
> **Quackers said:**
> As we have seen many times in forum help requests, it seems that Windows does not like to be resized by anything other than Windows Disk Management console.
It remains to be seen whether problems will arise in the future.

I would like to add a 'Hear! Hear!' to this.  The resize can take a very long time on an non-defragged NTFS partition.  I too have been helping folks muddle through the 'The install was hung so I rebooted' when really 'parted' was busy shrinking the NTFS partition.

I was thinking a 'pre-install check list' icon on the LiveCD that fires up an HTML page (located on the CD); it would mention the need to defragment the NTFS partiton and show pictures of the before/after of typical partitions. This would be very helpful to new users.

Few things will sour a new user on Ubuntu faster than destroying their Windows install when they thought they were getting an Ubuntu 'alongside' Windows install.

***The Hedge***

:KS

---

### Post by ronacc on 2011-03-30
2 other things need to be done on a windows system before resizing with linux . Turn off the windows swap partition and run disk cleanup then defrag and things will go ok .

---

### Post by ranch hand on 2011-03-31
> **ronacc said:**
> 2 other things need to be done on a windows system before resizing with linux . Turn off the windows swap partition and run disk cleanup then defrag and things will go ok .
Much easier to simply delete the MS partitions and start over with a real OS.

---

### Post by Hedgehog1 on 2011-03-31
> **ronacc said:**
> 2 other things need to be done on a windows system before resizing with linux . Turn off the windows swap partition and run disk cleanup then defrag and things will go ok .

See why a check list is needed?  If folks like me don't remember all the steps, how are average users supposed to know? :D

***The Hedge***

:KS

---

### Post by ronacc on 2011-03-31
> **ranch hand said:**
> Much easier to simply delete the MS partitions and start over with a real OS.

I haven't had anything from MS in this house in 12 years now . Unfortunately I have friends who think I can fix anything  .

---

### Post by kansasnoob on 2011-03-31
> **cariboo907 said:**
> To address kansasnoobs question, I'm trying the install along side option as I type this. The system already had a Natty install using 3 partitions.

I have to say the intial partitioning screen, does look a lot more newbie freindly, with four pretty clear options. 

[LIST=1]
[*]Install along side
[*]Update to Natty
[*]Wipe the hard drive and install
[*]Manual partitioning
[/LIST]

When I clicked the install alongside option, I got the option screen to resize the partitions, then I had to click the next/continue button to start resizing the partitions, and the install continued on from there.

All in all it was a pretty painless installation, both installations boot with no problem. This was an i386 install with no internet, as the system has a Broadcom pci wireless card.

Two bugs that I did find, were:

[LIST]
[*]Sound muted on start up
[*]Wireless device not detected by additional drivers
[/LIST]

I hadn't seen the "update to Natty option". No doubt due to my conglomerated partitioning mess :)

This is no doubt going to be interesting also considering the [[COLOR="Red"]wubi default if partition table full[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1702733") option.

And I don't think the use largest free space option is complete yet based on what I'm seeing and what Colin Watson said [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852/comments/35").

> If there is more space free in a partition that could be resized than is available in unallocated space, then the unallocated-space option is dropped. I'm guessing that the theory here may be that you can just use the "Install alongside" option and leave the other OS' size unchanged, thereby reducing the number of automatic partitioning options we need to present. However, the "Install alongside" option doesn't actually let you use unallocated space - it always resizes. I think we should present unallocated space, as people may well prefer not to reduce the amount of space available to their other OS.

Another problem I notice is that if the only other partitions present are data partitions - that is, os-prober outputs nothing - then you get neither the unallocated-space option nor the resize option. This seems like a bug, as resizing is perfectly possible here. Perhaps the 'if os_count == 0:' branch in calculate_autopartitioning_options needs to consider resize options.

I'll ask Evan to comment on this, and reopen or spin off a new bug report as necessary.


So, as it stands, the "use largest free space" is integrated with "install alongside". I'm not so sure that's a good situation, and in the following comments I said (in agreement with a couple other posters):

> Daniel and Martin make a very point. It's quite likely that a person with a very large disc might still allocate only a small bit, say 20GB out of a 1TB disc, for Ubuntu.

And it appears that Colin Watson agrees:

> I think a careful reading of my comment will reveal that I agree with you.

And AFAIK Colin is the lead ubuntu-installer dev, although the changelogs and my experience with ubiquity bugs, would indicate that Evan Dandrea does the lions share of ubiquity development.

It's important also to remember that the devs, at least to some degree, have to bow to the design team :D

And, in my experience, some of the design team members are very, very hard to sway :(

---

### Post by kansasnoob on 2011-03-31
> **ronacc said:**
> I haven't had anything from MS in this house in 12 years now . **Unfortunately I have friends who think I can fix anything**  .

I get that all the time but it's becoming easier all the time to just say, "I don't mess with Windows anymore" ;)

I quite honestly don't need the aggravation.

---

### Post by kansasnoob on 2011-03-31
> **ranch hand said:**
> You are right on the dot there.

I will not, on my setup, even think about auto installing.   I have too many things on here to risk.

kansasnoob has gotten impressive results and there is certainly some improvement.  **[COLOR="Red"]Reverting to the old style seems to me to be the best thing they could do,[/COLOR]**

As a total Linux noob I had no trouble at all installing 8.04.  I really have never seen the problem that these improvements are meant to correct.

It was explained to me that the UI had to change for several reasons. Most were beyond my comprehension, but one I did understand was the anticipated elimination of a specific netbook edition.

It's all a part of progress and it can be difficult at times :)

---

### Post by kansasnoob on 2011-03-31
> **ronacc said:**
> legally blind has nothing to do with it . the person who chose very light gray and small text for important information is a freaking idiot who should never again be allowed near the interface .

OK, I'll file a new bug regarding that to try and get the explanatory text darkened. Thank you :)

---

### Post by ezsit on 2011-03-31
I have used ubiquity on occasion, and even then I do my  partitioning beforehand with **cfdisk** and my formatting with **mkfs** in a terminal. Most installs I use the alternate discs since that installer allows for greater options.

I think the only true fix to all the problems mentioned is to eliminate all the preset partitioning schemes and only provide for manual partitioning and "use entire drive". Give the user some information in a little self-paced slide show beforehand (and a SKIP button for those who know what we are doing). Unless the user wants to use the entire drive, manual partitioning is the only true way for every user to get exactly what they want every time.

---

### Post by VastOne on 2011-03-31
> **ronacc said:**
> I haven't had anything from MS in this house in 12 years now . Unfortunately I have friends who think I can fix anything  .

lol.. 6 years for me and I am in the same boat...

---

### Post by kansasnoob on 2011-04-04
Following up here as it's too nasty outside to work and I hate cleaning the house (what's left of it), so I got a tiny bit busy.

I added to this (about the number of device options displayed during a manual install) post #4:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/726740](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/726740)

I'm debating about the need to file a new bug report regarding that because it shows fix released. IMHO it's partly fixed so hopefully I can just follow up with Beta 2 iso-testing :)

About that horrifically light font used displaying installation options someone beat me to the punch so I added a comment (#2), and confirmed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748384](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748384)

Comments at both are welcome but please remember the code of conduct. Always be considerate of others!

---

### Post by kansasnoob on 2011-04-04
Adding, this is going to be interesting!

I noticed in this thread that the option to upgrade an existing Ubuntu exists under the proper circumstances. While searching ubiquity bugs I noticed someone mentioning the option to **replace** an existing Linux installation ......... wow!

I'm really going to need some feedback about exactly what triggers these options :confused:

This should be fun :)

---

### Post by VastOne on 2011-04-04
> **kansasnoob said:**
> Following up here as it's too nasty outside to work and I hate cleaning the house (what's left of it), so I got a tiny bit busy.

I added to this (about the number of device options displayed during a manual install) post #4:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/726740](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/726740)

I'm debating about the need to file a new bug report regarding that because it shows fix released. IMHO it's partly fixed so hopefully I can just follow up with Beta 2 iso-testing :)

About that horrifically light font used displaying installation options someone beat me to the punch so I added a comment (#2), and confirmed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748384](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748384)

Comments at both are welcome but please remember the code of conduct. Always be considerate of others!

I think Beta2 ISO testing is your best bet..

OTOH, Ubiquity is broke yet again from the last 3 dailies, unplugging from the network was the only way to install any flavor of Ubuntu... And just like before, it did not affect everyone

---

### Post by kansasnoob on 2011-04-04
> **VastOne said:**
> I think Beta2 ISO testing is your best bet..

OTOH, Ubiquity is broke yet again from the last 3 dailies, unplugging from the network was the only way to install any flavor of Ubuntu... And just like before, it did not affect everyone

I haven't tried a new daily build yet. I just try to update every day and then I check the changelog for ubiquity in synaptic.

BTW ubiquity upgrades silently :)

---

### Post by VastOne on 2011-04-04
> **kansasnoob said:**
> I haven't tried a new daily build yet. I just try to update every day and then I check the changelog for ubiquity in synaptic.

BTW ubiquity upgrades silently :)

I do that perfectly on one partition, but on another I continue the testing of Daily ISO installs

---

### Post by kansasnoob on 2011-04-10
I did a few test installs today after noticing ubiquity hit 2.6.0:

[https://launchpad.net/ubuntu/natty/+source/ubiquity/2.6.0](https://launchpad.net/ubuntu/natty/+source/ubiquity/2.6.0)

I'm still a bit disappointed with a few things regarding the UI. Like too darn light of a font explaining installation options, too much garbage eating space on the manual partitioning screen so you only see 3 1/2 lines of devices, etc.

But I've beat my brains out on this and I guess the devs won't listen. That and they are superficial, so I'm done with the UI part of it.

That includes not clearly defining "install alongside" from "use largest free space". They disagree and I've been arguing with the devs for far too long!

As it stands the "install alongside" option will use free space if the installer decides it's appropriate - PERIOD! It just does it with no ability to say, "NO THAT"S NOT WHAT I WANTED"!

OTOH if it still appears to the installer that there is more room in an existing partition than the free space you created you'll still get the "resize" option.

AFAIC it's still a bloody mess :(

And I really am tired of fighting with these guys.

They have however added both a Wubi default and an upgrade default if the installer determines that's best. That does sound cool, but ATM I'd be scared to use anything other than manual partitioning, which they now call "Something Else" followed by a nearly unreadable explanation.

Sigh ..........................

---

### Post by VastOne on 2011-04-10
You tried Kansasnoob and for that I say bravo...

The Something Else part is the kicker... Someone suggested url links that could be implemented that could give real value in explaining the importance of the decisions placed upon the user, especially a new user. Easy to implement with incredible long range value

FWIW, I am going to miss the crowd here, it will seem like a part of my day missing... I would never have believed that there would be such a division of the Ubuntu community... The levels of disrespect at some of the trusted sites (OMG, Web Upd8..) bordered on hate. I got pretty well roasted questioning the Canonical decision making process..and the risks involved... 

For the life of me, in just a span of 4 days, would ever have thought I would be saying goodbye to a trusted friend in Ubuntu

I was told enough times to accept the changes or get out.. and I did just that... And in making a decision to use Fedora 15 and Gnome 3, I was then ostracized and told that I was dumb...  So much for the overall Linux community and any vision of a brotherhood 

I wish you the best..and good luck in your continued efforts.

---

### Post by kansasnoob on 2011-04-10
> **VastOne said:**
> You tried Kansasnoob and for that I say bravo...

The Something Else part is the kicker... Someone suggested url links that could be implemented that could give real value in explaining the importance of the decisions placed upon the user, especially a new user. Easy to implement with incredible long range value

FWIW, I am going to miss the crowd here, it will seem like a part of my day missing... I would never have believed that there would be such a division of the Ubuntu community... The levels of disrespect at some of the trusted sites (OMG, Web Upd8..) bordered on hate. I got pretty well roasted questioning the Canonical decision making process..and the risks involved... 

For the life of me, in just a span of 4 days, would ever have thought I would be saying goodbye to a trusted friend in Ubuntu

I was told enough times to accept the changes or get out.. and I did just that... And in making a decision to use Fedora 15 and Gnome 3, I was then ostracized and told that I was dumb...  So much for the overall Linux community and any vision of a brotherhood 

I wish you the best..and good luck in your continued efforts.

I'd seen a post from you about how much you loved Fedora 15. That's OK, but I'm not anywhere near giving up on Ubuntu. I want to make it better.

Regarding ubiquity/the live-installer I'm almost done. Ubuntu and it's devs will have to just deal with it.

I'll complete the Natty iso-testing cycle with ubiquity and if I see no improvement I'm just going to switch to testing the alternate, which is a modified debian-installer.

I'm certainly not giving up on Ubuntu :D

---

### Post by ranch hand on 2011-04-10
> **VastOne said:**
> You tried Kansasnoob and for that I say bravo...

The Something Else part is the kicker... Someone suggested url links that could be implemented that could give real value in explaining the importance of the decisions placed upon the user, especially a new user. Easy to implement with incredible long range value

FWIW, I am going to miss the crowd here, it will seem like a part of my day missing... I would never have believed that there would be such a division of the Ubuntu community... The levels of disrespect at some of the trusted sites (OMG, Web Upd8..) bordered on hate. I got pretty well roasted questioning the Canonical decision making process..and the risks involved... 

For the life of me, in just a span of 4 days, would ever have thought I would be saying goodbye to a trusted friend in Ubuntu

I was told enough times to accept the changes or get out.. and I did just that... And in making a decision to use Fedora 15 and Gnome 3, I was then ostracized and told that I was dumb...  So much for the overall Linux community and any vision of a brotherhood 

I wish you the best..and good luck in your continued efforts.
Sorry to hear that .  You gotta do what you gotta do.

I have never liked the RH branch of Linux.  RPMs and the package managers that go with them drive me up the wall.  Other than that they are pretty damned nice.  I really think that Mandriva is very nice.  Fedora doesn't work well for me (Plymouth again).

Come visit over at [http://www.linuxquestions.org/](http://www.linuxquestions.org/).  There are some familiar folks over there.

---

### Post by VastOne on 2011-04-11
> **kansasnoob said:**
> I'd seen a post from you about how much you loved Fedora 15. That's OK, but I'm not anywhere near giving up on Ubuntu. I want to make it better.

Regarding ubiquity/the live-installer I'm almost done. Ubuntu and it's devs will have to just deal with it.

I'll complete the Natty iso-testing cycle with ubiquity and if I see no improvement I'm just going to switch to testing the alternate, which is a modified debian-installer.

I'm certainly not giving up on Ubuntu :D

I do not recall expressing a love for Fedora 15.  What I did say was that I am shocked at how polished Gnome 3 is in Fedora 15, and appreciation that there is a choice.  

I get in enough trouble with what I say without someone speaking for me... :)

---

### Post by dino99 on 2011-04-11
really cant trust this ubiquity blackbox working as closed source. Even with huge efforts made by our tireless friend Kansasnoob, these devs continue their non understandable design and snub the whole community.

on my side, i never use it, i prefer preparing the partitions with partedmagic then install the "alternate" iso; its less scary and i know what its done.

[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

---

### Post by kansasnoob on 2011-04-11
> **VastOne said:**
> I do not recall expressing a love for Fedora 15.  What I did say was that I am shocked at how polished Gnome 3 is in Fedora 15, and appreciation that there is a choice.  

**I get in enough trouble with what I say without someone speaking for me**... :)

Sorry about that :(

But when someone says, "I was told enough times to accept the changes or get out.. and I did just that...", I assume they mean an alternative has been found and they're truly giving up on Ubuntu.

Regarding Unity, I also don't understand the "love or leave it" attitude. I've always thought that being able to customize an OS to ones own liking was one of the greatest strengths of Linux.

---

### Post by kansasnoob on 2011-04-11
Oh, something I forgot to mention in that post last night, twice while using the Live CD I had the installer .......... err, actually the whole live desktop, completely freeze after the installation had begun.

But both times I started the install from the Unity desktop, and after the install began rather than watch the slide-show I opened another workspace to use Firefox and things would just completely freeze.

Repeating the same steps beginning from the Classic w/o effects DE things worked fine. But this is not a huge surprise, this hardware has never run compiz well.

---

### Post by kansasnoob on 2011-04-12
Color me impatient :oops:

Lots of changes still coming:

[https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065](https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065)

If that makes your brain nearly explode then you're in the same boat I am :D

Lots and lots of stuff for my old noggin to absorb.

---

### Post by coffeecat on 2011-04-12
> **kansasnoob said:**
> 
[https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065](https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065)


I'm glad to see four options, but I hope they proof-read the Ubiquity window before Natty goes final.

> You can re-install Ubuntu without loosing any of your precious data or settings."Loosing" (sic), grrr. It's losing, losing, losing. :(

---

### Post by VastOne on 2011-04-12
> **coffeecat said:**
> I'm glad to see four options, but I hope they proof-read the Ubiquity window before Natty goes final.

"Loosing" (sic), grrr. It's losing, losing, losing. :(

+1

I am sure kansasnoob will point this out..  Good catch..

---

### Post by ranch hand on 2011-04-12
> **coffeecat said:**
> I'm glad to see four options, but I hope they proof-read the Ubiquity window before Natty goes final.

"Loosing" (sic), grrr. It's losing, losing, losing. :(
Now now, they may have reason to worry about the buggers getting loose.  You are "working" your OS.  Could be be like working a bunch of cows.  You don't want them getting out the gate.

---

### Post by coffeecat on 2011-04-12
> **ranch hand said:**
> Now now, they may have reason to worry about the buggers getting loose.  You are "working" your OS.  Could be be like working a bunch of cows.  You don't want them getting out the gate.

:lol:

---

### Post by seeker5528 on 2011-04-13
> **dino99 said:**
> really cant trust this ubiquity blackbox working as closed source.

[http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.dsc](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.dsc)

[http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.tar.xz](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.tar.xz)

> The original Guadalinex source can be found at:
	[http://ws314.juntadeandalucia.es/guadalinex2005/live_installer/](http://ws314.juntadeandalucia.es/guadalinex2005/live_installer/)

and Ubiquity is developed at:
	[http://bazaar.launchpad.net/~ubuntu-installer/ubiquity/trunk/](http://bazaar.launchpad.net/~ubuntu-installer/ubiquity/trunk/)

Copyright (C) 2005  Javier Carranza
Copyright (C) 2005, 2006, 2007, 2008, 2009, 2010  Canonical Ltd.

Ubiquity has been adapted for usage by the Mythbuntu
team for the purposes of a Ubuntu derivative focused
upon setting up a standalone MythTV box.

Portions copyright (C) 2007 Mario Limonciello

oem-config was written by Colin Watson <cjwatson@ubuntu.com>.
It is:
  Copyright (C) 2005, 2006, 2007, 2008 Canonical Ltd.
  Copyright (C) 2006, 2007 Anirudh Ramesh

Some code in oem-config is borrowed from base-config, whose copyright
declaration is as follows:

  This package is copyright 2000-2004 by Joey Hess <joeyh@debian.org>.
  Portions are also copyright by Bruce Perens <bruce@hams.com>, Enrique
  Zanardi <ezanard@debian.org>, Sven Rudolph, Luis Francisco Gonzalez
  <luisgh@debian.org>, Ben Collins <bcollins@debian.org>, Matt Kraai
  <kraai@debian.org>, Petter Reinholdtsen <pere@debian.org>, VA Linux
  Systems, and Software in the Public Interest.

License:

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 2 of the License, or
  (at your option) any later version.

Yep, too bad. :twisted:

Later, Seeker

---

### Post by kansasnoob on 2011-04-13
> **ranch hand said:**
> Now now, they may have reason to worry about the buggers getting loose.  You are "working" your OS.  Could be be like working a bunch of cows.  You don't want them getting out the gate.

If we all start nit-picking about spelling and such, look at the title of this thread. It was supposed to be:

Live installer - change to be aware of - opinions needed

With the "-" in the wrong place it just looks stupid.

My point is that the devs are human too :)

---

### Post by kansasnoob on 2011-04-13
> **seeker5528 said:**
> [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.dsc](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.dsc)

[http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.tar.xz](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.6.5.tar.xz)



Yep, too bad. :twisted:

Later, Seeker

Are you just pointing out the difference between open source and closed source?

Somehow I'm missing your point :confused:

Apologies in advance, after 3 rounds of iso-testing my brain is 90% fried.

---

### Post by seeker5528 on 2011-04-13
> **kansasnoob said:**
> Are you just pointing out the difference between open source and closed source?

Somehow I'm missing your point :confused:

I was responding to "really cant trust this ubiquity blackbox working as closed source."

With a link to the .dsc and source tarball in the repository, which you should be able to get with 'apt-get source ubiquity' if you have the src lines enabled in your sources.list, and quoting from the copyright file which includes a link to the bazaar tree for ubiquity and seems to indicate, as near as I can figure, the source code is GPL.

And being a little sarcastic with the... "Yep, too bad. :twisted:"

> Apologies in advance, after 3 rounds of iso-testing my brain is 90% fried.

Not a problem, I start to feel a little cross eyed myself at times between the updating/testing, verifying behavior, and deciphering forum posts, more verifying behavior, etc...

Doesn't help any that my memory is like swiss cheese and the older I gut the more I swear I must be dyslexic. :neutral:

Later, Seeker

---

