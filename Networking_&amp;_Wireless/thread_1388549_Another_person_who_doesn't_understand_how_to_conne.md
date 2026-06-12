---
title: "Another person who doesn't understand how to connect to the internet"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by terrasears on 2010-01-23
I am in the process of switching computers and have always wanted to try ubuntu so I thought this would be a great time. Normally I think of myself as pretty good at researching and finding how to do things (note: with the research not with me by myself.) However, the difference here (from windows) makes it so I am not sure how to look this stuff up even (terminology?)

So I have went to the prompt thing (as directed on one research attempt) and entered in the sudo pppoeconf and it didn't result in anything but a response of sorry something or other. 

I downloaded the latest ubuntu (9 something?) installed via a flash drive and have been trying to figure out the internet since, have half way given up because I just don't understand.

I connect through an ethernet cord, have a static IP address, in windows I always had to edit the subnet and DNS server. (The connection is technically ADSL, A through the phone line as it is that or dial up in my middle of nowhere location.)

I also saw information that said to go to System - Admin - network, but unless that network is supposed to say network tools rather than just network I don't have it.

Step by step keeping in mind that my terminology is way different would be greatly appriciated. :)

TS

---

### Post by pricetech on 2010-01-23
A search of the forums will reveal that you are not alone.  I've seen numerous posts describing network issues with Karmic that seem to have no solution no matter what is tried.

If you were a seasoned Linux user, I'd say hang with it until you sort it out, but as a newcomer you're probably better off to install an earlier version such as Jaunty or the current LTS, Hardy.

I'll probably get flamed for suggesting that, but that's my opinion and advise.

If you're bound and determined to make it work no matter what, I wish you infinite success.

---

### Post by GregBrannon on 2010-01-23
Taking Pricetech's comments in a different direction:

Yes, many have blazed the trail before you and successfully come through the forest.  Read the Stickies in this section, search for and read networking tutorials, and search the forum for similar hardware or symptoms to see if there are parallels in the experiences and advice that you can use.  Perhaps that will bring you to a new starting point for another question, but it should be a starting point somewhere along the path through the forest rather at the trail head.

You'll find help here in this community that comes from an honest desire to make your experience successful unlike that available any other place.

Don't give up and good luck!

---

### Post by terrasears on 2010-01-23
ROFL

So I am to keep researching (no one knows for sure)

and/or

go back to windows / try an early version?

Very helpful thanks

---

### Post by darkod on 2010-01-23
> **terrasears said:**
> ROFL

So I am to keep researching (no one knows for sure)

and/or

go back to windows / try an early version?

Very helpful thanks

I didn't understand quite well do you know how do you connect to the internet at all. You said you use ethernet cable so if all you need is manual (static) IP, do this:
Right-click the network manager icon on top right on the screen. Select Edit Connections.
Select the Wired tab. Then the tab Internet Protocol ipv4 (or similar, can't remember the exact name of everything right now, look around).
Select Manual in the drop down list. Click under IP Address and enter your static IP. DON'T FORGET to hit enter after that. Do the same for netmask and gateway.
Under that you have the DNS field, enter one or more dns servers addreses with ; between them (if using more than one). Click on close and that should be it.

PS. I wouldn't agree that 9.10 is difficult for networking. If you have a specific situation where you need to use static IP etc, you would have to do it manually in windows too, and most likely any other OS. As for wi-fi support and similar, also don't forget that it is up to the hardware manufacturers to create drivers for linux and not the linux community. Unfortunately, manufacturers scramble to create drivers for windows and it's up to the linux community usually to create drivers for linux.

---

### Post by Iowan on 2010-01-23
There are a lot of possibilities - most of which are beyond me. I have DSL - my modem acts like a router, it handles all the PPPOE stuff. I set it up via the "Auto eth0" instead of the DSL option. I presume your (local) network is working properly?

---

### Post by terrasears on 2010-01-23
Thank you [darkod]("http://ubuntuforums.org/member.php?u=946366")! My internet connection now works! And I agree I always had to configure my IP in windows as well, in fact now that I know how to do this it is easier than the windows application (just a matter of finding it.)

A few things for people coming over for windows (for the things that had me a bit lost);

netmask = subnet  (amazing what a small difference does for understanding this quickly)

I never had to get my gateway before so this took me a minute - but I found it on the computer I have with Vista (but not on XP). It was under the DNS server settings in vista. Although I am sure your network administrator could also help with this.

When he says right click on an icon on the top, he means that icon is IN the bar at the top. (This took me a minute to figure out as I am used to things that are referred to in this way as being on the active middle part of the desktop.)

Anyway, thank you much... :)

---

### Post by darkod on 2010-01-23
Glad you got it working. :)
Sorry, I wasn't at my ubuntu and I rarely go into that menu so I can't remember how exactly everything is called. And you're right, the term actually is Subnet Mask, don't know how I came up with netmask. :)

---

### Post by terrasears on 2010-01-23
LOL

It is called one name on windows and the other name on ubuntu, which is where my confusion came from you said it exactly right for ubuntu... I was just used to the name it has on windows :)

---

### Post by pricetech on 2010-01-24
> **terrasears said:**
> ROFL

So I am to keep researching (no one knows for sure)

and/or

go back to windows / try an early version?

Very helpful thanks

Definitely NOT go back to winders.  I'd never suggest that.

I'm glad you got the issue solved and that it turned out to be a simple solution.

I feel kinda silly having assumed it would be one of those "head scratching / hair pulling" problems.

My bad.

---

