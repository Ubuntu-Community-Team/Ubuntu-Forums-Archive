---
title: "Reminder: help the noobs and everyday users!"
date: 2010-05-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-05-08
I've been trying, really hard, to keep up with threads at Installation & Upgrades, and a bit at Absolute Beginner Talk, but I get overcome sometimes.

Many of us here at testing have learned certain skills, and they vary greatly, so let's not forget when we knew nothing! This is an opportunity to not only show our support for Ubuntu but also give others the gift of a Windows free world :)

Spread the love! Help wherever you can!

Oh, and anyone that's encountered challenges with "grub installation" please look here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

I'm "Jonesing" for iso-testing :p

---

### Post by ranch hand on 2010-05-08
Now see, that is not a bug it is a feature to help have a Windows free world.

---

### Post by hikaricore on 2010-05-09
I always knew everything..

---

### Post by arpanaut on 2010-05-09
> **ranch hand said:**
> Now see, that is not a bug it is a feature to help have a Windows free world.

Now Now  

We want them to throw windows out of their PC's

Not their PC's out the window...:roll:

---

### Post by plun on 2010-05-09
I can confirm observations from Ubuntu Sweden and severe dual-boot trouble from a handful of users.

This is not good for Ubuntu and must be resolved.


But maybe its a feature  :P

---

### Post by wilee-nilee on 2010-05-09
Help those with needs; I agree. ;)

---

### Post by kansasnoob on 2010-05-09
> **arpanaut said:**
> Now Now  

We want them to throw windows out of their PC's

Not their PC's out the window...:roll:

That would make a great sig :)

---

### Post by KdotJ on 2010-05-10
> **kansasnoob said:**
> That would make a great sig :)


lol +1

---

### Post by ranch hand on 2010-05-23
> **kansasnoob said:**
> I've been trying, really hard, to keep up with threads at Installation & Upgrades, and a bit at Absolute Beginner Talk, but I get overcome sometimes.

Many of us here at testing have learned certain skills, and they vary greatly, so let's not forget when we knew nothing! This is an opportunity to not only show our support for Ubuntu but also give others the gift of a Windows free world :)

Spread the love! Help wherever you can!

Oh, and anyone that's encountered challenges with "grub installation" please look here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

I'm "Jonesing" for iso-testing :p
Well, I know that I still have a lot to learn.

There are some things that I am unlikely to learn.  How to really rescue MS is one.  I think you probably should use MS to learn about it and I am not going to.

However, this feller here;

[http://ubuntuforums.org/showthread.php?t=1491232](http://ubuntuforums.org/showthread.php?t=1491232)

seems to have a very interesting problem that is crying out for someone with a clue.

I hope some one will take the time to look at this.  The boot script is there.  I think W7 is still there.  The partition scheme seems strange to me.  The readout for sda3 strikes me as having something to do with wubi.

I have no idea where to even start.

---

### Post by fedexnman on 2010-05-23
lol thats funny ranchhand , i keep my windows on a seperate hd and when i up grade or do a clean install of ubuntu i unplug the sata cord on the windows drive, then plug it in later after install and then do sudo update-grub. thats playin it safe for me.

---

### Post by ranch hand on 2010-05-24
Gee, thanks.

I believe I can still find the Dell Vista install disk that came installed on this box.

I took it off after 3 weeks of dealing with that and installed Hardy.  I did use a different drive.  Vista stayed on that drive for another 3 weeks until I realized I could have a back up OS by simply dual booting with Hardy.

That drive now is in a single external enclosure with three Ubuntus installed on it in both 32  bit and 64bit making for 6 installs.  I loan it to folks who want to try Ubuntu out.  

I don't do windows.

This poor guy really needs some help from someone who does.

---

### Post by kansasnoob on 2010-05-24
> **ranch hand said:**
> Well, I know that I still have a lot to learn.

There are some things that I am unlikely to learn.  How to really rescue MS is one.  I think you probably should use MS to learn about it and I am not going to.

However, this feller here;

[http://ubuntuforums.org/showthread.php?t=1491232](http://ubuntuforums.org/showthread.php?t=1491232)

seems to have a very interesting problem that is crying out for someone with a clue.

I hope some one will take the time to look at this.  The boot script is there.  I think W7 is still there.  The partition scheme seems strange to me.  The readout for sda3 strikes me as having something to do with wubi.

I have no idea where to even start.

I had a look over there. It's a mess. Oldfred already suggested changing the boot flag and that should be the next step.

But that was a horrible set up! It looks like the OP had 3 primaries which was no problem. You can stuff ALL of an Ubuntu inside logicals created within one extended partition.

Then, given the Ubuntu wireless problem, I'll bet the OP lost the wireless at some point during the install so Ubuntu is probably just borked which explains why not even the shutdown or restart buttons work.

In other words the problem was between the chair and the keypad :)

---

### Post by ranch hand on 2010-05-24
It is a mess and I am not even sure how he got there.

I hope he listens to oldfred.

I certainly haven't got a clue.   Well I have a way to fix it but the OP seems to actually want W7 on his box.  My cure would be to format the drive and install Ubuntu.

---

### Post by kansasnoob on 2010-05-24
> It is a mess and I am not even sure how he got there.


Reading that thread it's obvious how the OP painted him/herself into a corner, user "mbzn" convinced the OP to delete a partition with the misguided logic that Ubuntu's "root" partition must be a primary!

I've sometimes received bad advice on the forums. I've also sometimes given bad advice to others here on the forums. More often than not it's a matter of misunderstanding, or thinking that I know more than I actually know.

I've made a habit of clicking on user's names and checking some previous posts of theirs before taking their advice. Sometimes people come across as quite knowledgeable but a quick search tells you otherwise :)

---

### Post by phillw on 2010-05-24
I've asked on one the IRC channels if someone could help out / suggest, there is one of them with Win7 experience in its worst cases, he's concerned over the loss of the backup partition but has updated the thread.

/kansasnoob, you have better knowledge of Win7 systems, I hope his input is of use to you and oldfred.

Regards,

Phill.

---

### Post by ranch hand on 2010-05-24
> **kansasnoob said:**
> Reading that thread it's obvious how the OP painted him/herself into a corner, user "mbzn" convinced the OP to delete a partition with the misguided logic that Ubuntu's "root" partition must be a primary!

I've sometimes received bad advice on the forums. I've also sometimes given bad advice to others here on the forums. More often than not it's a matter of misunderstanding, or thinking that I know more than I actually know.

I've made a habit of clicking on user's names and checking some previous posts of theirs before taking their advice. Sometimes people come across as quite knowledgeable but a quick search tells you otherwise :)
It would also be really great if folks would read the first post in the thread BEFORE they give advice.  It really is not that hard and, sometimes, it helps to know the actual problem.

---

### Post by kansasnoob on 2010-05-24
> **phillw said:**
> I've asked on one the IRC channels if someone could help out / suggest, there is one of them with Win7 experience in its worst cases, he's concerned over the loss of the backup partition but has updated the thread.

/kansasnoob, you have better knowledge of Win7 systems, I hope his input is of use to you and oldfred.

Regards,

Phill.

AFAIK the OP is hosed other than possibly recovering data and then reinstalling everything.

And they should chalk this up to a lack of research!

In what world do you ask a question on an open forum and just jump on the first advice with no research?

I never run any "unknown" command without a bit of research, and to think that someone would delete a partition with hardly any thought ......... WOW!

---

### Post by ranch hand on 2010-05-24
I bet he doesn't do it again.

---

### Post by wilee-nilee on 2010-05-24
> **ranch hand said:**
> I bet he doesn't do it again.

He seems to recognize that it is probably not fixable, and is willing to do a reinstall, since there is nothing to lose.

It might be that oldfreds advice works, but personally I would reinstall to get it setup correctly. I would put it in one partition, except fore the auto 100mb boot partition that is automatically built.

---

### Post by ronacc on 2010-05-24
scenes like that are why I am always very careful when I to try to help noobs , you aren't there , you don't really know anything about their skill level, you have only a second hand assessment of the situation and something simple that you could handle in person easily can spin out of control very quickly when trying to work "long distance ".

---

### Post by wayneericgouin on 2010-05-27
Quick off-topic question if ya'll dont mind. Is it possible to boot the Daily alternate builds from a usb drive similar to how unetbootin works for the live-cds?

---

### Post by cariboo on 2010-05-27
You should be able to do it with **Startup Disk Creator** utility.

---

### Post by wayneericgouin on 2010-05-27
I tried that as well but it left me at the command line asking for a cd, which prompted me to google it then left me wondering if perhaps i should have googled first.

---

