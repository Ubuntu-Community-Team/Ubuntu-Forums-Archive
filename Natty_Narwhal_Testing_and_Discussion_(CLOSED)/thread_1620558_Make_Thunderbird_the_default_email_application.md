---
title: "Make Thunderbird the default email application"
date: 2010-11-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Toxicbits on 2010-11-13
Hi,

In my opinion Thunderbird is much more user friendly than Evolution and several polls showed that the majority prefers TB, too. 
So I wonder whether for this or the next release TB could be installed by default, supporting Ubuntu One flawlessly.

How do you think about this?

Toxicbits

---

### Post by Starks on 2010-11-13
From what I've heard, it's planned for 11.10

---

### Post by plun on 2010-11-13
> **Toxicbits said:**
> Hi,

In my opinion Thunderbird is much more user friendly than Evolution and several polls showed that the majority prefers TB, too. 
So I wonder whether for this or the next release TB could be installed by default, supporting Ubuntu One flawlessly.

How do you think about this?

Toxicbits

Yep.... but now at Natty-UDS they decided to stick with Evolution.... just a sad decision, IMHO...

Linux Mint 10 uses Thunderbird as default mail-client !

---

### Post by cpmman on 2010-11-13
Thunderbirds is go
Gwibber is gone
Empathy is pathetic
Evolution has happened

Wake up to the world outside your machine.

---

### Post by Toxicbits on 2010-11-13
Does anyone know who developed the Ubuntu One integration for Evolution?

---

### Post by chrisccoulson on 2010-11-13
> **plun said:**
> Yep.... but now at Natty-UDS they decided to stick with Evolution.... just a sad decision, IMHO...

I was one of those in the session at UDS. We decided to stick with Evolution this cycle mainly because most people are going to be focused on making the switch to Unity rock.

There are also issues we need to resolve in Thunderbird, primarily integration with the messaging menu and global menu in Unity (which is an issue in Firefox too)

---

### Post by Toxicbits on 2010-11-13
Is the indicator applet integration actually coded in Evolution or some kind of add on? Because for Thunderbird there is an extension which adds support for TB:

[Indicators for Thunderbird :: Add-ons for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/")

Wouldn't this delivered by default be enough regarding the Indicator applet?

---

### Post by castrojo on 2010-11-13
> **Toxicbits said:**
> Wouldn't this delivered by default be enough regarding the Indicator applet?

Yeah unfortunately there are some bugs with that so far and we don't have the time to look into that this cycle. We were however able to sit down with the Thunderbird developers and hash out some things we need to work on before this is doable.

Here are some blueprints with notes from the sessions:

[https://blueprints.launchpad.net/ubuntu/+spec/packageselection-desktop-n-thunderbird-messaging-indicator](https://blueprints.launchpad.net/ubuntu/+spec/packageselection-desktop-n-thunderbird-messaging-indicator)

[https://blueprints.launchpad.net/ubuntu/+spec/packageselection-desktop-n-thunderbird-on-ubuntu](https://blueprints.launchpad.net/ubuntu/+spec/packageselection-desktop-n-thunderbird-on-ubuntu)

---

### Post by chrisccoulson on 2010-11-13
> **Toxicbits said:**
> Is the indicator applet integration actually coded in Evolution or some kind of add on? Because for Thunderbird there is an extension which adds support for TB:

[Indicators for Thunderbird :: Add-ons for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/")

Wouldn't this delivered by default be enough regarding the Indicator applet?

I've already considered this extension, but there are currently some architectural problems which mean we can't ship it by default in it's current form (the main problem being is that it only allows communication from the mail client to the indicator, and not back in the other direction. This means it isn't possible to raise Thunderbird from the indicator, let alone raise it on the right mailbox).

I'm planning to implement a native (C++) extension, which would make it possible to integrate it much more nicely in to the indicator (avoiding the limitations of writing extensions in pure Javascript), and do other cool things like change how we present notifications based on your presence. Whether it will be a new extension or changing the existing one is not decided yet though, and I've got other things to work on before that ;)

---

### Post by plun on 2010-11-13
Really strange when also Fedora uses Thunderbird as default mail app....

Still a really sad discussion...  I don't understand it...8-[

---

### Post by chrisccoulson on 2010-11-13
We've just explained the decision to you, which bit don't you understand? :/

---

### Post by plun on 2010-11-13
> **chrisccoulson said:**
> We've just explained the decision to you, which bit don't you understand? :/

Nope, I did not understand it....

Everything works just fine for me including the indicator and Lightning !!

[http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-the-ubuntu-messaging-menu/](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-the-ubuntu-messaging-menu/)

[http://www.omgubuntu.co.uk/2010/09/thunderbird-ubuntu-notification-applet/](http://www.omgubuntu.co.uk/2010/09/thunderbird-ubuntu-notification-applet/)

Thats it !

---

### Post by chrisccoulson on 2010-11-13
> **plun said:**
> Nope, I did not understand it....

Everything works just fine for me including the indicator and Lightning !!

[http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-the-ubuntu-messaging-menu/](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-the-ubuntu-messaging-menu/)

[http://www.omgubuntu.co.uk/2010/09/thunderbird-ubuntu-notification-applet/](http://www.omgubuntu.co.uk/2010/09/thunderbird-ubuntu-notification-applet/)

Thats it !

No, the indicator doesn't work to a level which is acceptable to ship by default. When I click on an inbox in the indicator, I expect Thunderbird to raise, on the correct mailbox. It doesn't do that now, and it won't do that at all with the current architecture. In addition to that, Thunderbird doesn't use the global menu, and the lightning calendar isn't integrated with the panel clock etc.

It might be *ok* for you, but we need to fix those issues before we could ship it by default to the rest of our users.

If you don't understand now, then I give up...

---

### Post by plun on 2010-11-13
> **chrisccoulson said:**
> No, the indicator doesn't work to a level which is acceptable to ship by default. When I click on an inbox in the indicator, I expect Thunderbird to raise, on the correct mailbox. It doesn't do that now, and it won't do that at all with the current architecture. In addition to that, Thunderbird doesn't use the global menu, and the lightning calendar isn't integrated with the panel clock etc.

It might be *ok* for you, but we need to fix those issues before we could ship it by default to the rest of our users.

If you don't understand now, then I give up...

Well...I do believe that if Ubuntu wants it everything is possible.....;-)

As shown in OMGUbuntu url everything is possible but now some developers wants to stick with Evolution and thats just deeply sad...

Then maybe its a "language barrier"):P but  I don't understand this decision.... just confusing but I dont care because for me this is not a problem..... just to use Thunderbird including Lightning and the indicator....

---

### Post by chrisccoulson on 2010-11-13
> **plun said:**
> Well...I do believe that if Ubuntu wants it everything is possible.....;-)

As shown in OMGUbuntu url everything is possible but now some developers wants to stick with Evolution and thats just deeply sad...

Then maybe its a "language barrier"):P but  I don't understand this decision.... just confusing but I dont care because for me this is not a problem..... just to use Thunderbird including Lightning and the indicator....

We all ultimately want the same thing - which is Thunderbird by default, but I want it to be done properly, and I've explained why that's not possible this cycle. I'm not sure what else to say.

Note, that I will be doing some of the work for it this cycle. As long as nothing else comes up, I'm going to be starting to implement support for the global menu bar in the next week or so. And then I hope I can get the messaging menu stuff working well, and an implementation of that in Natty.

---

### Post by plun on 2010-11-13
> **chrisccoulson said:**
> We all ultimately want the same thing - which is Thunderbird by default, but I want it to be done properly, and I've explained why that's not possible this cycle. I'm not sure what else to say.

Note, that I will be doing some of the work for it this cycle. As long as nothing else comes up, I'm going to be starting to implement support for the global menu bar in the next week or so. And then I hope I can get the messaging menu stuff working well, and an implementation of that in Natty.

OK....!!

I must thank you for answering and for good arguments... much appreciated

=D>

---

### Post by caryb on 2010-11-13
Looking a little more globally this would be great to be the default in Kubuntu as well (all *buntu flavours) I think concentrating our efforts on best of breed applications will cut down on double handling. For example apps like K3B & synaptic would make good global defaults across all *buntu flavours:confused:


Cary

---

### Post by simpleblue on 2010-11-13
> **plun said:**
> Really strange when also Fedora uses Thunderbird as default mail app....

Still a really sad discussion...  I don't understand it...8-[

I'm running Fedora 14 and it's using Evolution as the default mail app. Tbird is not installed. I cannot speak for previous versions of Fedora though.

As a side note, I find that Evolution is MUCH faster with loading emails in Fedora then Ubuntu. It's a difference between loading in 2-4 seconds in Fedora and hanging for 10 to 20 seconds in Ubuntu. I've tried this with several installs, and I only use the default setup on both.

---

### Post by SeijiSensei on 2010-11-13
IMAP? POP? Encryption?  Local servers over an intranet?  Remote servers on the Internet?  I think speeds will depend a lot on your choice of servers and protocols.

I don't experience any delays with opening my inbox in Thunderbird which I've been using for as long as it has existed.  Version 3 does spend a bit of time indexing the mail folders (I have lot of them) the first time it's installed, but after that it's pretty fast.

In the past I've thought Evolution was largely an effort by RedHat, Novell and the GNOME developers to create a Linux application that worked similarly to Microsoft Outlook.  Since I have no need or desire to integrate with Exchange or any other Microsoft products, I've not used Evolution in years.  The absence of calendaring functions in earlier versions of Thunderbird was a major obstacle to getting it established on corporate networks.  Nowadays there are many methods of creating shared calendars, including "cloud" services like Google Calendar, and the fact that they've finally integrated Lightning just adds to the options.

---

### Post by dext on 2010-11-14
> **plun said:**
> Really strange when also Fedora uses Thunderbird as default mail app....

Still a really sad discussion...  I don't understand it...8-[

Fedora doesnt use TB as default, dunno where you get that from.

---

### Post by plun on 2010-11-14
> **dext said:**
> Fedora doesnt use TB as default, dunno where you get that from.

OK.... sorry I read this Url and missed it.;)

[http://fedoraproject.org/wiki/Features/Thunderbird_3](http://fedoraproject.org/wiki/Features/Thunderbird_3)

---

### Post by dext on 2010-11-14
> **plun said:**
> OK.... sorry I read this Url and missed it.;)

[http://fedoraproject.org/wiki/Features/Thunderbird_3](http://fedoraproject.org/wiki/Features/Thunderbird_3)

TB doesnt have a decent Calenda etc in it yet to be made Default, maybe when its complete it maybe made default in Fedora And or Ubuntu  if you dont like Evolution i suggest you try out claws mail [http://www.claws-mail.org/downloads.php?section=downloads](http://www.claws-mail.org/downloads.php?section=downloads)

---

### Post by plun on 2010-11-14
> **dext said:**
> TB doesnt have a decent Calenda etc in it yet to be made Default, maybe when its complete it maybe made default in Fedora And or Ubuntu  if you dont like Evolution i suggest you try out claws mail [http://www.claws-mail.org/downloads.php?section=downloads](http://www.claws-mail.org/downloads.php?section=downloads)

Thunderbird and Lightning works just fine...... including Google Calendar integration.

[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

Indicator solution:
[https://addons.mozilla.org/en-US/thunderbird/addon/223374/](https://addons.mozilla.org/en-US/thunderbird/addon/223374/)

---

### Post by Toxicbits on 2010-11-14
Do you know whether they are planning to actually integrate Lightning into Thunderbird, not as extension, but actually coded natively?

Lets all hope this will be working for 11.10

---

### Post by plun on 2010-11-14
> **Toxicbits said:**
> Do you know whether they are planning to actually integrate Lightning into Thunderbird, not as extension, but actually coded natively?

Lets all hope this will be working for 11.10

Nope... but they have had an "never-ending discussion" about this at Mozilla upstream..... lightning devs wants to run their own project....as I understands it.  Thunderbird devs wants to include Lightning....

---

### Post by chrisccoulson on 2010-11-14
> **Toxicbits said:**
> Do you know whether they are planning to actually integrate Lightning into Thunderbird, not as extension, but actually coded natively?

Lets all hope this will be working for 11.10

I'm not sure what you mean by "coded natively", but it's already about as native as you will get - it's even hosted in the same Mercurial tree as Thunderbird, and is coded in XUL, Javascript and C++ (exactly the same technologies as Thunderbird).

It's just built as an extension rather than being shipped with Thunderbird.

In fact, if you grab the source of our lightning package in Ubuntu - you'll see it's basically just Thunderbird, but built with "--enable-application=calendar" instead.

---

### Post by ronacc on 2010-11-14
I have a revolutionary idea , why not let people choose the Email client/PIM/IM app/chat client they want instaead of hardcoding someone elses choice so that it makes it a PITA to get rid of them and install your choices .

---

### Post by plun on 2010-11-14
> **chrisccoulson said:**
> 
It's just built as an extension rather than being shipped with Thunderbird.

In fact, if you grab the source of our lightning package in Ubuntu - you'll see it's basically just Thunderbird, but built with "--enable-application=calendar" instead.

Well.... I have missed this package....

[http://packages.ubuntu.com/natty/xul-ext-lightning](http://packages.ubuntu.com/natty/xul-ext-lightning)

I then cannot find any package for Google Calendar provider ??

I just uploads stinking MS Outlook calendar files to Google Calendar from a Windooze-machine at my work....

After that I am free at home and uses Ubuntu/Thunderbird with Google sync and a Android phone, also synchronized with Google...

---

### Post by chrisccoulson on 2010-11-14
> **plun said:**
> Well.... I have missed this package....

[http://packages.ubuntu.com/natty/xul-ext-lightning](http://packages.ubuntu.com/natty/xul-ext-lightning)

I then cannot find any package for Google Calendar provider ??

I just uploads stinking MS Outlook calendar files to Google Calendar from a Windooze-machine at my work....

After that I am free at home and uses Ubuntu/Thunderbird with Google sync and a Android phone, also synchronized with Google...

The Google Calendar integration is provided by xul-ext-gdata-provider

---

### Post by plun on 2010-11-14
> **chrisccoulson said:**
> The Google Calendar integration is provided by xul-ext-gdata-provider

Great !!  and thanks !

Testing....;)


Package info
[http://packages.ubuntu.com/natty/xul-ext-gdata-provider](http://packages.ubuntu.com/natty/xul-ext-gdata-provider)

---

### Post by Mr. Picklesworth on 2010-11-14
> **ronacc said:**
> I have a revolutionary idea , why not let people choose the Email client/PIM/IM app/chat client they want instaead of hardcoding someone elses choice so that it makes it a PITA to get rid of them and install your choices .

We gain a lot from having a centralized PIM system that other applications can talk to, for example to manage contacts. Over here, that's Evolution's database. Unfortunately, nothing has taken advantage of it except the clock applet, so the point is moot.
(Meego could change that though, especially if it wants to compete with Google's various offerings).

Of course, at this point, since it isn't really used, it can still be replaced with something better. That particular feature of a database anything else can access should really be kept, though.

---

### Post by ronacc on 2010-11-14
I understand the THEORY about having a centralized PIM I also know that the reality is that the choice they make( any choice they make) will not be the one that a large segment of users prefer and the further insult of embedding it in Ubuntu Desktop just makes matters worse , That is why my default position is always on the side of user choice .

---

### Post by bikeboy on 2010-11-14
Not sure if it's too early to answer these question, but here goes:

- If we switch to TB, are we likely to ship with Lightning/Sunbird by default?
- Along those lines, nicely integrated alarm and appointment notifications to replace what Evolution provides? (I guess that'd fit into messaging menu integration)
- Clock/Calendar applet integration or replacement? Without that, much of the current applet becomes useless so we'd maybe want to consider a different clock that doesn't show a calendar with no highlights.
- Does Lightning have task lists to replace that feature in Evolution? (currently shown in Calendar applet)

---

