---
title: "Natty will only run on 1 of my 4 PC's!"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2011-03-29
Hello everyone, after a long absence from testing here, I am back again, Last Night I tried to install Natty Alpha 3 on 3 PC's (A Dell Inspiron 1012 Mini Netbook, A Dell Inspiron Zino 400 HD, and A Dell Dimension 8400) and on 1 Apple Mac Mini 2010 Edition PC. 2 my surprise the only PC that I could get the Alpha 3 software 2 run on was the Dell Ispiron 1012 Netbook PC! The Mac completed the install just fine but would NOT boot up. The Dell Inspiron Zino 400 HD ran the CD but locked up as soon as the Hard Drive Partisioner started up. The Dell Dimension 8400 would NOTeven read the CD! Today I tried out the Latest Alternate Install Daily Build, same results!

---

### Post by NCLI on 2011-03-29
Report bugs for the machines that don't work, remember to mark the bugs as regressions if 10.10 worked.

---

### Post by dino99 on 2011-03-30
you should read & post on special DELL subforum

---

### Post by PaulW2U on 2011-03-30
> **kevpan815 said:**
> The Dell Dimension 8400 would NOTeven read the CD! Today I tried out the Latest Alternate Install Daily Build, same results!
I'be been running Ubuntu on a Dell 8400 for almost a year now. I haven't had one CD failure in that time and I have run alpha, beta and daily builds in addition to full releases. I think I've loaded Natty three or four times now without any installation problems. I still have the original CD and DVD drives installed although other items have been replaced. Of course, there may be slight variations in the components used in our machines as I'm in the UK but I think the problem must be something specific to your PC rather than the 8400 model in general. As suggested posting in the Dell forum, if you haven't already, may yield some answers.

I hope you get it sorted as my 8400 has served me well and running Ubuntu means I probably still have a few years use of it before I need to buy a replacement.

---

### Post by jerrylamos on 2011-03-30
Natty 29 March .iso Unity running on three of my four test pc's.  Unity 3D on my latest desktop, Unity 2D on the older desktop and laptop.

Acer Aspire netbook won't install because Ubiquity hangs endlessly trying to figure out the partitions.  There's a launchpad bug written.  Natty 3D does run on it by installing onto a USB hard drive using a desktop, then moving the USB hard drive to the Aspire and running grub again.

Jerry

---

### Post by kevpan815 on 2011-03-30
> **kevpan815 said:**
> Hello everyone, after a long absence from testing here, I am back again, Last Night I tried to install Natty Alpha 3 on 3 PC's (A Dell Inspiron 1012 Mini Netbook, A Dell Inspiron Zino 400 HD, and A Dell Dimension 8400) and on 1 Apple Mac Mini 2010 Edition PC. 2 my surprise the only PC that I could get the Alpha 3 software 2 run on was the Dell Ispiron 1012 Netbook PC! The Mac completed the install just fine but would NOT boot up. The Dell Inspiron Zino 400 HD ran the CD but locked up as soon as the Hard Drive Partisioner started up. The Dell Dimension 8400 would NOTeven read the CD! Today I tried out the Latest Alternate Install Daily Build, same results!

Just noticed Bug number #745960 (in the ISO Tracker) which may be why Natty will Install but NOT run on my Mid 2010 Intel Mac Mini.

---

### Post by kevpan815 on 2011-03-30
> **dino99 said:**
> you should read & post on special DELL subforum

Keep in mind that I am having trouble getting Natty up and running on a 2010 Mid Year Mac Mini as well although that may be because of Bug Number #745960. Also just to let you guys know that Dell forum both here and on Dell.com is 4 released versions of Ubuntu only.

---

### Post by kevpan815 on 2011-03-30
> **kevpan815 said:**
> Keep in mind that I am having trouble getting Natty up and running on a 2010 Mid Year Mac Mini as well although that may be because of Bug Number #745960. Also just to let you guys know that Dell forum both here and on Dell.com is 4 released versions of Ubuntu only.

Update on my situation: I was able to get the Latest Ubuntu AMD64 Nightly Build Alternate CD 2 run on my 2005 Dell Diminsion 8400 after switching 2 a Different Monitor (It did NOT like the 19' Vizio HD TV that I had it connected 2) however it (the install) locked up just as soon as the Hard Disk Drive Partisioner started up, just like on the 2010 Dell Inspiron 400 Zino HD which did the same exact thing. The Mid 2010 Mac Mini is still failing to install even without Encryption enabled.

---

### Post by kevpan815 on 2011-03-31
> **kevpan815 said:**
> Update on my situation: I was able to get the Latest Ubuntu AMD64 Nightly Build Alternate CD 2 run on my 2005 Dell Diminsion 8400 after switching 2 a Different Monitor (It did NOT like the 19' Vizio HD TV that I had it connected 2) however it (the install) locked up just as soon as the Hard Disk Drive Partisioner started up, just like on the 2010 Dell Inspiron 400 Zino HD which did the same exact thing. The Mid 2010 Mac Mini is still failing to install even without Encryption enabled.

Further Update on my situation: I tried out yesterday's Live CD Build on the 3 computers, since there was no new Build yesterday 4 the Alternate Installer, still NO GO.

---

### Post by jdwhite87 on 2011-03-31
> **kevpan815 said:**
> Further Update on my situation: I tried out yesterday's Live CD Build on the 3 computers, since there was no new Build yesterday 4 the Alternate Installer, still NO GO.
 
I was trying to run natty alpha 3 from a USB stick last night on a Dell Mini 1012 and it wouldn't work for me either. I am still VERY new to all this (just installed Ubuntu about a week ago) so I assumed I did something wrong. But when the screen pops up and you can choose "Try Ubuntu" or "install Ubuntu" I click try and it sits there and loads for about 5 minutes then it goes away and there is nothing but the wallpaper. I waited another couple minutes and started impatiently pressing keys (CTRL+ALT+T, ALT+F2, etc...) but nothing happened. But if I pressed the volume or brightness keys the pop-up would show for those and it would change.
 
EDIT: I seem to remember a box popping up saying compiz had crashed too. What is compiz?

---

### Post by kevpan815 on 2011-04-01
> **jdwhite87 said:**
> I was trying to run natty alpha 3 from a USB stick last night on a Dell Mini 1012 and it wouldn't work for me either. I am still VERY new to all this (just installed Ubuntu about a week ago) so I assumed I did something wrong. But when the screen pops up and you can choose "Try Ubuntu" or "install Ubuntu" I click try and it sits there and loads for about 5 minutes then it goes away and there is nothing but the wallpaper. I waited another couple minutes and started impatiently pressing keys (CTRL+ALT+T, ALT+F2, etc...) but nothing happened. But if I pressed the volume or brightness keys the pop-up would show for those and it would change.
 
EDIT: I seem to remember a box popping up saying compiz had crashed too. What is compiz?

I actually ran Alpha 3 and now Beta 1 off a DVD on all 4 computers (I have the Official Dell External Hard Disk Drive 4 the 1012). The Beta 1 install is successful on the 1012 for me (using a DVD instead of a USB Memory Stick). It still fails on my 3 other PC's.

---

### Post by kevpan815 on 2011-04-01
> **PaulW2U said:**
> I'be been running Ubuntu on a Dell 8400 for almost a year now. I haven't had one CD failure in that time and I have run alpha, beta and daily builds in addition to full releases. I think I've loaded Natty three or four times now without any installation problems. I still have the original CD and DVD drives installed although other items have been replaced. Of course, there may be slight variations in the components used in our machines as I'm in the UK but I think the problem must be something specific to your PC rather than the 8400 model in general. As suggested posting in the Dell forum, if you haven't already, may yield some answers.

I hope you get it sorted as my 8400 has served me well and running Ubuntu means I probably still have a few years use of it before I need to buy a replacement.

That is very different hardware then what is on my 8400, no upgrades have been made to it since I bought it. The Pentium 4 Processor does run at 3 GHz, but everything else is different. ATI 300 Series Graphics Card. Hard Drive is only 160 GB and there is only one of them. Last but not least the Memory is only 2 GB and not 4 like in your system.

---

### Post by jdwhite87 on 2011-04-01
> **kevpan815 said:**
> I actually ran Alpha 3 and now Beta 1 off a DVD on all 4 computers (I have the Official Dell External Hard Disk Drive 4 the 1012). The Beta 1 install is successful on the 1012 for me (using a DVD instead of a USB Memory Stick). It still fails on my 3 other PC's.
 
Ok I'm gonna have to try it with a DVD drive then. Next Friday after I get paid :P Thanks!

---

