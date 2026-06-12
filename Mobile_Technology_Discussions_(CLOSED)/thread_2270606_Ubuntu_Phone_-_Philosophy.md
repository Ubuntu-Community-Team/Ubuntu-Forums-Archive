---
title: "Ubuntu Phone - Philosophy?"
date: 2015-03-24
forum: Mobile Technology Discussions (CLOSED)
---

### Post by rupertbear2 on 2015-03-24
[SIZE=2][FONT=arial]I am new here, I have joined because I have purchased a BQ Aquaris E4.5 Ubuntu Edition smartphone.

I have little experience with Linux, what I have largely from using the Raspberry Pi, but I think that I do have some understanding of the general philosophy behind it.

I have previously owned Android phones and, whilst enjoying the facilities, have always loathed the intrusive nature of the OS, the total lack of privacy, the inability to configure the phone and all the other factors associated with the 'ecosystem' philosophy. The alternatives, iOS and Windows Phone, appear no better if not worse.

The Ubuntu Phone seemed to offer a way out and a real alternative. Now that I have bought it I'm afraid it's a great disappointment. Google Mail? Sign in with your Google Account? How do I change the configuration - a couple of quick examples might be to use an alternative provider of weather forecasts or restrict a Search to the device rather than automatically including (sections of) the internet? Where is apt-get or its equivalent? Will I be able to install Firefox, Adblock, Ghostery etc, etc?

[/FONT][/SIZE]I'm aware that these are early days and that the OS is being rapidly developed. It's possible that the things I am unhappy about will be rectified in time. I would, though, like to be reassured that this is the case and that this is the direction that development will take. If Ubuntu for phones is going to share the  iOS and Windows Phone 'ecosystem' philosophy then I shall be very unhappy and the phone will be sold.

Surely the biggest, if not the only, gap in the smartphone OS market in today's climate has to be one where the user can feel in complete control of the device and its behaviour? Privacy and security are not available elsewhere.

The fault is, I'm sure, mine in making presumptions before purchase. I did expect, though, that any form of Linux would embrace the philosophy of configurability, security and privacy.

I look forward to hearing others' opinions.

---

### Post by ockelz on 2015-03-24
It's still early as you mentioned. I bought the BQ Aquaris too out of  curiosity and by supporting the brave steps of a minority,  but with in mind the limitations and bugs of this first real hardware  edition. I knew i couldn't compare it to the Big Two (maybe three if you  count windows mobile). Things will change in time, and i'm almost  certain that the community will pick the missing pieces up. Just as they  did when i installed ubuntu 6.06  years ago for the first time. I then  felt unhappy too, struggling with the lack of control, bugs, crashes and  missing programs. I tried to compare everything from my old rusted  point of view. As time passed, and linux evolved, i realized that i  could do almost everything whith linux, and at the moment of writing i  have all my hardware and now eventually my Phone running on some form of  free linux.

---

### Post by grahammechanical on 2015-03-24
It is my understanding that before being allowed to buy one of these ubuntu phones a person had to go through a process that made them familiar with what it could and could not do. Did this not happen? Please post a link to any advertising that caused you to think that the Ubuntu phone provided features that are not actually present.

The BQ Ubuntu phone and any other Ubuntu device that comes on the market will be first and foremost a commercial product. Even if Canonical had the funds to pay a manufacturer to make devices after the fashion of Apple any Ubuntu mobile device would still have to be a commercial product. Canonical is a software company and has no plans to become a hardware maker. Therefore, Canonical needs partners (OEMs) who will take the commercial risk in producing Ubuntu mobile devices. Canonical and its partners need to make a profit. This is just a fact of life. Philosophy does not put bread on the table of the workers.

Canonical engineers have evolved the Debian packaging system into what they call Click packaging. It makes it very easy for application developers to get their apps accepted into the app store. Click packaging makes sure that the apps in the app store do not contain malicious code. All apps run in their own container and apps are not allowed to access data on the phone without authorisation. The file system is read only. This makes it next to impossible for malicous code to change the system. When an app is not on screen it is no longer uses system resources. Thus prolonging  battery life.

A different method of updating is now used. It is possible for app developers to use the app store to update their apps independently from an update to the OS. And Ubuntu is updated independantly of the apps and the OEM, unlike Android. The method used on the desktop requires the upgraded package to be downloaded in it entirety. On the Ubujntu phone it is only the code differences that are downloaded. Thus, reducing data download costs to the user.

 Canonical has taken responsibilty for updating the OS and anyone who has a Ubuntu phone will have an up to date version of Ubuntu all the time. The present phone code base is built on the Ubuntu 14.10 code base. Work is being done to base the phone code on the 15.04 code base and all Ubuntu phones will be updated. So, the Ubuntu phone does not have the limited support life that desktop Ubuntu has. If these BQ Ubuntu phones are still working in 5 years time they will have the latest Ubuntu OS. You will not need to buy a new phone to get the newest OS.

Ubuntu phone and tablet users will have a choice. Use what Canonical calls Transactional updates or use developer mode and use apt-get but once we use apt-get we break the method for using translational updates. And I would expect that the warranty would be broken as well. 

Android is a form of Linux and yet you clearly are concerned about Google and your privacy. So, it is not logical to expect Linux and privacy to be hand in hand all the time.

You do not know it but I am sure that Firefox is present in the OS. It is just not usable on the phone. It is not designed for a phone UI. But I am sure it will be useable on the tablet. The Ubuntu phone does not use the X windowing system. It use Mir but applications like Firefox and LibreOffice are built to run on X. A way needs to be found to get these applications running on Mir. This is a work in progress and it was not necessary for the phone and it would have delayed the release of Ubuntu phones. It may be availble for Ubuntu tablet devices. I have seen videos of Libreoffice running on Unity 8 on an Intel and Nexus tablet. So, progess is being made but each step at a time and without rushing.

Regards.

---

### Post by rupertbear2 on 2015-03-27
> **grahammechanical said:**
> It is my understanding that before being allowed to buy one of these ubuntu phones a person had to go through a process that made them familiar with what it could and could not do. Did this not happen? Please post a link to any advertising that caused you to think that the Ubuntu phone provided features that are not actually present.

Thanks for the reply.

I was aware of no 'process'. I simply learned that BQ were doing a batch sale and ordered one. However, I stated in my original post *'The fault is, I'm sure, mine in making presumptions before purchase'* and I am not complaining of any misrepresentation.

> The BQ Ubuntu phone and any other Ubuntu device that comes on the market will be first and foremost a commercial product. Even if Canonical had the funds to pay a manufacturer to make devices after the fashion of Apple any Ubuntu mobile device would still have to be a commercial product. Canonical is a software company and has no plans to become a hardware maker. Therefore, Canonical needs partners (OEMs) who will take the commercial risk in producing Ubuntu mobile devices. Canonical and its partners need to make a profit. This is just a fact of life. Philosophy does not put bread on the table of the workers.

Agreed. Therefore, the more phones sold, the better. I would suggest that the best (only?) way of selling any significant quantity would have been to market it as a smartphone with privacy and security built in, rather than following the business model of the giants.

> Android is a form of Linux and yet you clearly are concerned about Google and your privacy. So, it is not logical to expect Linux and privacy to be hand in hand all the time.

I'm sorry but I don't follow your argument here. Android, whilst being based on Linux, was given a new name and was created by a particular entity which was known for behaving in certain ways. Nobody was surprised, therefore, by what they got. Ubuntu Phone, on the other hand, comes from one of the major strands of Linux and continues to carry its name but the product seems to share its philosophy more with the creator of Android than with previous Ubuntu offerings. I was surprised by what I got.

> You do not know it but I am sure that Firefox is present in the OS. It is just not usable on the phone. It is not designed for a phone UI.

I'm afraid that my technical knowledge doesn't run to understanding windowing but thank you for the explanation. In a general sense, though, I have been running Firefox on my last two Android phones which must be for three years or so.

I have not yet decided whether I will persevere with the phone or whether it will be on ebay. I suspect the latter. I would like to reiterate that I am not blaming anyone for anything, the error was completely mine. I do very much feel that an opportunity has been missed.

Any other views? Is there a better forum where I might take this discussion?

---

### Post by howefield on 2015-03-27
> **rupertbear2 said:**
> Is there a better forum where I might take this discussion?

Not so much a forum, but if you are serious about finding out more (as opposed to simply wanting a whinge) you could hang out at #ubuntu-touch (ubuntu-phone and tablet Discussion and Support channel) on Freenode.

---

### Post by DuckHook on 2015-03-28
Fellow Entities,

I did not get the sense that the OP was trying to whinge. Methoughts OP was asking for reassurance that Ubuntu phone would not turn into a walled jail, and while we in this forum cannot provide such reassurance, my sympathies are with the OP.

@rupertbear2

I have no idea whether Ubuntu will eventually build jail walls around its phone. It may sadly turn out that this is the only way to survive in the mobile marketplace. I concur with you that some of the strongest points that drew me to Linux in general and Ubuntu in particular were their philosophies of freedom, open source and user control, and their commitments at the time to privacy and security. I also believe that some of these philosophies and practices have eroded somewhat in the last few years, but not yet to such an extent that I am soured on Ubuntu. In the event that Ubuntu is compromised to a point that I find offensive, I shall switch to another distro that I feel to be closer to the aforementioned ideals. You and I will always have this choice so long as the Linux-sphere remains healthy.

However, I do know that Ubuntu is trying to do something that other distros are not: because while those others may have remained more faithful to the purity of the Linux vision, they have also confined themselves to a desktop paradigm that gets narrower with each passing day and offers no hope of being relevant in the biggest and most important part of our evolving IT world: the mobile space. For this, I give Ubuntu immense credit, and am willing to forgive them an awful lot of big stumbles as they struggle to bang together an alternative to the jailed behemoths that are currently crushing everything else underfoot. Remember: Canonical is a small fry in an ocean of sharks. You can't expect them to turn out a perfect alternative on their first try. In fact, it's going to be a long and gruelling process with all sorts of fair-weather-friends jumping off the bandwagon. Get used to that. Be prepared for it. And if they succeed&#8213;which is by no means certain&#8213;you can some day take a quiet pride in knowing that you were one of the original pilgrims that stuck with them through those first fierce winters.

PS

If you do decide to sell your phone, PM me. I would be willing to buy it.

---

### Post by Jordan_Roberts on 2015-03-30
> **grahammechanical said:**
> 
Android is a form of Linux and yet you clearly are concerned about Google and your privacy. So, it is not logical to expect Linux and privacy to be hand in hand all the time. 

Here I have to respectfully disagree. To me, "linux" means (among other things) user control, and control is method for (among other things) taking your privacy back from those systems, corporations and organizations that actively threaten it. This is especially relevant in Mobile Technology because - as the OP already pointed out - in mobile systems we find ourselves locked into all these closed ecosystems, within the shackles of which it is more difficult to protect your privacy than it is on the desktop. On the linux desktop at least, we can freely install hundreds of privacy tools; we can more easily take control over our data; we can more easily employ anonymization and obfuscation technologies; etc.

For that reason, Android is a contradiction to me. Google supports linux development, but at the very same time, Google is a threat to the human right of privacy (possibly the biggest threat there is). In my opinion at least, Google has been using linux for highly nefarious and suspect purposes, which is one of the reasons why we need alternativemobile linux systems - such as Ubuntu.

And I am indifferent to wether the market likes the latter concept or not. I support linux development with financial donations, so that we can eventually have mobile linux systems that can be more of an asset to us in terms of protecting our individual and collective privacy from various rising threats to it.

---

### Post by chris-burmajster on 2015-03-31
I bought an Ubuntu Phone too and I'm generally pleased with it. However,  I'm disappointed with the lack of support for it a) because it's a new  product and needs more support than usual and b) because, unlike the desktop OS,  you have to pay for it. With previous phones that I have bought, if I  had any problems I could go back to the shop or the carrier, but none of  that seems to apply to the Ubuntu Phone.

I would like to see  Canonical add a page to their website for the Ubuntu Phone with up to  date news about developments, FAQ's, and to be able to sign up for  notifications when new software is released and what the changes are. It  would also be good for owners to be able to ask questions about their  phone. At present, so many things are unfinished and it would be good to  know when they will be done. For example, the GPS on my phone doesn't  seem to work. Is this because the software is not finished or because  the phone is faulty? This is why it would be good to get some answers  from Canonical.

I fear that if something is not done, then owners will feel abandoned and the phone will not progress as much as we all want it to.

Chris

---

### Post by Lutz_Fechner on 2015-03-31
> **chris-burmajster said:**
> I would like to see  Canonical add a page to their website for the Ubuntu Phone with up to  date news about developments, FAQ's, and to be able to sign up for  notifications when new software is released and what the changes are. It  would also be good for owners to be able to ask questions about their  phone. At present, so many things are unfinished and it would be good to  know when they will be done. 


100% agree to that statement. Somehow I'm missing some commutiy management for the new Phone OS. SO far this forum seems to be the best stop. But the content here still is rather thin.

---

### Post by daplan on 2015-03-31
> **Lutz_Fechner said:**
> 100% agree to that statement. Somehow I'm missing some commutiy management for the new Phone OS. SO far this forum seems to be the best stop. But the content here still is rather thin.

I think Launchpad is a good place to hang around, to get the latest news. [https://lists.launchpad.net/ubuntu-phone/](https://lists.launchpad.net/ubuntu-phone/)

---

### Post by buzzingrobot on 2015-03-31
> **rupertbear2 said:**
> [SIZE=2][FONT=arial]...
I have previously owned Android phones and, whilst enjoying the facilities, have always loathed the intrusive nature of the OS... iOS and Windows Phone, appear no better if not worse...

The Ubuntu Phone seemed to offer a way out and a real alternative. Now that I have bought it I'm afraid it's a great disappointment.[/FONT][/SIZE]

It's not the operating system on the phone.  It's the applications that are annoying you. 

You, as a user, don't interact directly with iOS or Windows or Android.  You interact with the applications running on them. 

As I'm sure you know, the reason apps collect/massage/interpret the data we generate when we use them is to generate revenue.  Historically, it's been almost impossible to convince consumers to pay for online services.  We expect them to be free. Yet we complain when the businesses that provide those services try to figure out how to turn a profit. No profit = no business = no online services.

Add to that the overriding fact that the basic architecture of the internet was not designed with privacy in mind. No one anticipated, 30 years ago, that it would blossom into the pervasive global thing that it is.

So... if you don't want App X or App Y messing with your privacy, delete them.

---

### Post by Lutz_Fechner on 2015-03-31
> **daplan said:**
> I think Launchpad is a good place to hang around, to get the latest news. [https://lists.launchpad.net/ubuntu-phone/](https://lists.launchpad.net/ubuntu-phone/)

Subscribed to the mailing group.

Found some issues so far that I wanted to report (or check for solutions):
- JDK installations was a bit harder than I expected. Package dependecies in general seem to be in questionable condition.
- Had some crashes so far.
- Bluetooth keyboard not connecting but visible.
- Some stalled network conditions where turning network off and on resolved the issue.

---

### Post by ockelz on 2015-03-31
> **Lutz_Fechner said:**
> 100% agree to that statement. Somehow I'm  missing some commutiy management for the new Phone OS. SO far this forum  seems to be the best stop. But the content here still is rather  thin.

I agree too. I'm looking for some kind of (community) support  too, but i haven't found the right place. I just peeked at 

[https://answers.launchpad.net/~ubuntu-phone](https://answers.launchpad.net/~ubuntu-phone)

But I can't report a bug or ask a question like i can for the Ubuntu launchpad.
Subscribing  to the mailing list seems cluttered and does not suit my way of finding  answers, asking questions or providing feedback.

A few things that i wanted to report, regarding to the core os (not the apps):

- Wifi connection with WPA2-Enterprise with AES (CCMP) encryption / EAP(PEAP) cannot be set up
- Bluetooth keyboard cannot connect (can be seen but is  greyed out)
- Music player scope (preview button) occaisonally kept playing and could not be shut down (only a reboot).
- Random freezing lock screen when trying to unlock (hard reset solves only, or device reboots itself after a few seconds)
- Personal suggestion: On the homescreen, hide what NOT has been done, for example it says: No messages sent today, no video's recorded. Just message the things that happened.

In general i'm happy with my phone, and i'm curious about it's future.

---

### Post by Olivia_Zane on 2015-04-13
i wish ubuntu could buy out Cyanogen and base their mobile os on the great work these guys have been doing

---

### Post by chris-burmajster on 2015-04-13
> **Olivia_Zane said:**
> i wish ubuntu could buy out Cyanogen and base their mobile os on the great work these guys have been doing But then it wouldn't be an Ubuntu phone! That's why I bought one, because it runs Ubuntu as its OS. I'm sure that, once the teething troubles are over it'll be a great OS, as great for phones as it is for laptops / desktops.

---

### Post by Sprint21 on 2015-04-18
> **buzzingrobot said:**
> It's not the operating system on the phone.  It's the applications that are annoying you. 

snip

So... if you don't want App X or App Y messing with your privacy, delete them.

Any hints on how to do that, or where to go for advice?  I don't use Twitter or many of the other apps and I'd like to get that junk off my phone

---

### Post by howefield on 2015-04-18
> **Sprint21 said:**
> Any hints on how to do that, or where to go for advice?  I don't use Twitter or many of the other apps and I'd like to get that junk off my phone

You can try uninstalling from the app store, according to the user manual, there may be some that cannot be removed.

> Deleting (Uninstalling) Scopes and Apps You can’t delete the main Scopes and apps that were on your phone when you took it out of the box. All the others – the ones you have downloaded and installed yourself – can be deleted (or uninstalled) by visiting the Ubuntu Store and searching for your app or Scope. In the preview screen for the Scope or app you want to delete, you will see options to either update or uninstall it. Tap ‘Uninstall’ and let Ubuntu do the rest. The quickest way to access the preview screen for an app is to give a long press on the icon in the Apps Scope.

---

### Post by chris-burmajster on 2015-04-18
> Any hints on how to do that, or where to go for advice?  I don't use  Twitter or many of the other apps and I'd like to get that junk off my  phone

I got Twitter, Facebook at al off my phone simply by pressing and holding on the relevant icon in APPS. After a few seconds a menu pops up. Select DELETE and you're done. I was able to do this with every app I didn't want - and there were quite a few I didn't want.

Chris

---

### Post by Sprint21 on 2015-04-18
Chris, you are a genius!!!  Thank you so much :D:D:D

---

### Post by chris-burmajster on 2015-04-19
Pleasure! Nice that I've been able to help somebody, as I'm usually the one asking for help on these forums.

Chris

---

### Post by lgd on 2015-05-10
> **Lutz_Fechner said:**
> 100% agree to that statement. Somehow I'm  missing some commutiy management for the new Phone OS. SO far this forum  seems to be the best stop. But the content here still is rather  thin.
Take notice of this new project question: [Ubuntu Touch into help.ubuntu.com/community]("http://ubuntuforums.org/showthread.php?t=2277572")                 Maybe you are interested in helping.

And by the way, now you can start Ubuntu pc programs on the phone by following this guide there.

> **ockelz said:**
> I agree too. I'm looking for some kind of (community) support  too, but i haven't found the right place. I just peeked at 

[https://answers.launchpad.net/~ubuntu-phone](https://answers.launchpad.net/~ubuntu-phone)

But I can't report a bug or ask a question like i can for the Ubuntu launchpad.

Here you can report or sign bugs: [https://bugs.launchpad.net/canonical-devices-system-image/+bugs](https://bugs.launchpad.net/canonical-devices-system-image/+bugs)

Greetings, lgd

---

### Post by Jaxilian on 2015-05-12
I am also greatly disappointed in this phone. I have the phone, but can't use it. I would cripple myself if I did...I would go back in time like 6 years of phone development

---

