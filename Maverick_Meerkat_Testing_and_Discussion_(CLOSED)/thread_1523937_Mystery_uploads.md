---
title: "Mystery: uploads"
date: 2010-07-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by chrismine on 2010-07-04
I found that on Meerkat the computer is permanently busy with uploading something to 174.129.241.144 via port 443. The site seems to belong to Amazon.com

Attached screenshot of nast running.

Can somebody give me any pointers, I cannot find out why this happens.

---

### Post by MadMan2k on 2010-07-04
Ubuntu made a deal with Amazon. They scan your home folder for "interesting" keywords, so that Amazon can send you personilized offers and in turn Ubuntu may use the Amazon servers for Ubuntu One.

---

### Post by hikaricore on 2010-07-04
> **MadMan2k said:**
> Ubuntu made a deal with Amazon. They scan your home folder for "interesting" keywords, so that Amazon can send you personilized offers and in turn Ubuntu may use the Amazon servers for Ubuntu One.

With this kind of statement you really need to cite a source..
I'm 100% sure that any such nonsense would be on an opt-in ONLY basis, sounds like rubbish to me.

---

### Post by chrismine on 2010-07-04
Thanks for that, the problem is that it uploads at maximum speed and makes my Internet unusable. It has also uploaded about 160MB this afternoon which is unacceptable.

How does one stop this?

---

### Post by crjackson on 2010-07-04
Wow, that's not good.  I'm not seeing this at all.  Have you tried to block that i.p to see what happens?

---

### Post by Jeroensum on 2010-07-04
> **hikaricore said:**
> With this kind of statement you really need to cite a source..
I'm 100% sure that any such nonsense would be on an opt-in ONLY basis, sounds like rubbish to me.

No need for that, just whois the IP and you'll see that it belongs to amazon...

To troubleshoot this, do a: *sudo netstat -tulpen* and look for the IP, at the end of the line you'll see the program responsible for the upload. Simply kill it with *killall -9 <process name>*
The next step would be to see how this process is started, */etc/init/* , */etc/crontab* and the *Startup Applications* menu item would be good places to start.

---

### Post by hikaricore on 2010-07-04
No need for telling people not to spread FUD?  I think there's plenty of need for it.
People are going to get pissed off and paranoid about Ubuntu over a misunderstanding or outright lie.

"it's scanning your home directory"  IS NOT something to be announced so lightly.

---

### Post by jrothwell97 on 2010-07-04
Either that or a badly-timed sarcastic joke went over someone's head.

---

### Post by belkinsa on 2010-07-04
Amazon = Google, Google does the same with your e-mail;s if you use Gmail.

---

### Post by hikaricore on 2010-07-04
> **Mechafish said:**
> Amazon = Google, Google does the same with your e-mail;s if you use Gmail.

Which are stored on their servers and you agree to when you sign up.
You're comparing apples to oranges here.

---

### Post by Jeroensum on 2010-07-04
> **hikaricore said:**
> No need for telling people not to spread FUD?  I think there's plenty of need for it.
People are going to get pissed off and paranoid about Ubuntu over a misunderstanding or outright lie.

"it's scanning your home directory"  IS NOT something to be announced so lightly.

LOL, I just misread your post, I thought the first line referred to checking the source as in the IP. Always funny to see how fast some people get agitated on forums these days... Just take a breath there dewd ;-)

---

### Post by hikaricore on 2010-07-04
> **Jeroensum said:**
> Always funny to see how fast some people get agitated on forums these days... Just take a breath there dewd ;-)

Bite me hippie.

---

### Post by ranch hand on 2010-07-04
> **Jeroensum said:**
> LOL, I just misread your post, I thought the first line referred to checking the source as in the IP. Always funny to see how fast some people get agitated on forums these days... Just take a breath there dewd ;-)
Take a breath?  You are implying that for an OS to auto connect you to some server that is mining information is all right.  I would say that MS has trained you real well.

I want the source of this possible security hole in my OS as soon as possible.

Gee, I think this is something to get upset about.  I realize that MS mines for info under the guise of improving your "experience".  This is a major reason that it is not allowed in my house.

If this is true, Ubuntu can go the same way.

---

### Post by MCVenom on 2010-07-04
What the hell people? No, Amazon is NOT scanning your home directory (or at least not as part of some deal with Canonical)! :lolflag:

That's not something to say lightly, what is wrong with people? :P

---

### Post by ranch hand on 2010-07-04
> **BlackOtaku said:**
> What the hell people? No, Amazon is NOT scanning your home directory (or at least not as part of some deal with Canonical)! :lolflag:

That's not something to say lightly, what is wrong with people? :P
I surely hope you are correct.

If this was a joke it was a damned bad one.

---

### Post by ronacc on 2010-07-04
it it possible that he had some transaction with amazon that caused/allowed them to scan his sys , I am NOT seeing this here and I keep a pretty close eye on my traffic , especially outbound .

---

### Post by mc4man on 2010-07-04
> If this was a joke it was a damned bad oneI'd think the debian fanboy who mentioned this is getting a bit of a laugh from it all..

---

### Post by questioning on 2010-07-04
> **ranch hand said:**
>  I realize that MS mines for info under the guise of improving your "experience".  

this is exactly the same FUD, whenever MS really does that, it asks you first, has been like that since windows xp days (before that i cant really remember)

paranoid bullshit, nothing more.

---

### Post by jfernyhough on 2010-07-04
Ubuntu One uses Amazon S3 for storage.

This will be why you are uploading data to an Amazon server.

---

### Post by lisati on 2010-07-04
Thread closed so we can all take a breather and calm down. There are tools available to help track down what's happened. The "netstat" and "whois" options might have some merit, and a big bouquet of "[tulpen]("http://de.wikipedia.org/wiki/Tulpen")" (tulips) to someone who comes up with a practical solution.

---

### Post by lisati on 2010-07-04
Thread reopened after PM from OP

---

### Post by chrismine on 2010-07-04
Hello I am the original poster of the thread, in the meantime I have  found out (by accident) when I kill the ubuntusync-daemon the uploads  stops.

I have no problem that it is checking from time to time but at the  moment it is constantly uploading something at the maximum upload rate  my ADSL line is capable of, that it has uploaded about 160MB of data in  the span of an afternoon on a 384 Kbps ADSL connection. It takes over  the line so that I cannot get into websites etc, downloads erratic and  slow


This is the contents of my PM - I do not have a permanent solution but a least we now know the culprit...

---

### Post by ranch hand on 2010-07-04
> **questioning said:**
> this is exactly the same FUD, whenever MS really does that, it asks you first, has been like that since windows xp days (before that i cant really remember)

paranoid bullshit, nothing more.
Well, this may be what you think.  I, however, spent 3 days digging around in Vista ferreting out the auto reporting "features" and turning them off when we bought this box.

When you are on dial up you notice very small activities on your modem (we could, on a good day get 4.4KB/sec).  There was a very regular upload of something about every 6 hours.  After turning all that stuff off it quit doing that.  We changed nothing else.  We had not had the thing long enough to do any business with it.  I think that pretty well show where it was going.

Some of the info being gathered made some sense even.  Some of it was just not right.  Internet usage was one of the things I turned off.

I hope that they have stopped doing this with 7 but I do not know.

---

### Post by mcphargus on 2010-07-04
If you've set up Ubuntu One, and you place a large file in your UbuntuOne folder, it will sync. This sync will take a long time. UbuntuOne is also in your home directory, so I can see where the misunderstanding happened.

---

### Post by sgosnell on 2010-07-04
If you have Ubuntu One enabled, and tell it to store your data, then it should be uploading the data to the Ubuntu One servers.  If you disable Ubuntu One, the uploads should stop.  I see no benefit at all in Ubuntu One, and removed it long ago.

---

### Post by mcphargus on 2010-07-04
> **sgosnell said:**
> If you have Ubuntu One enabled, and tell it to store your data, then it should be uploading the data to the Ubuntu One servers.  If you disable Ubuntu One, the uploads should stop.  I see no benefit at all in Ubuntu One, and removed it long ago.

That's not to say UbuntuOne is totally worthless. This is a to-each-his/her-own scenario. I'm personally a fan of UbuntuOne; I've multiple machines, and note synchronization and some file sync (little stuff, like projects I'm working on, stuff I wanna share amongst teams that don't quite warrant a whole PPA in launchpad, etc.) make UbuntuOne a pretty nice little app. I'm excited about its development and that it really does integrate nicely into Ubuntu with very little setup. Not everyone wants to fart around hacking rsync and cron-jobs and the like to get things to synchronize.

+1 to ubuntuone, but it ain't everyones cup 'o coffee.

---

### Post by sgosnell on 2010-07-04
Oh, I'm not claiming UbuntuOne is totally worthless, it's just worthless to me.  Dropbox is far more useful to me, so that's what I use.  If I could use only Linux, I would probably use UbuntuOne, but I have to use Windows at work, and need to sync files between my Ubuntu system and my work computer.  Different people have different requirements, and so use different tools.  That's life.

---

### Post by chrismine on 2010-07-05
What I don't understand is all the megabytes of uploads - I have only two folders flaggend and it is only about 3MB in total.

---

### Post by hikaricore on 2010-07-05
Either the service is highly unreasonable with its checking and rechecking and syncing, or you flagged more that you realize.
I suggest disabling ubuntu one if you don't need it and using the web interface to store backups and such for the time being.

---

### Post by chrismine on 2010-07-05
It started uploading my Downloads folder which I have not flagged for Ubuntu One, so part of the mystery has been cleared. Why that specific folder is shared I don't know,I will mot share it because it is 9 gigabytes in size and too big to fit into my free account.

I do find value in Ubuntu One, to store some small commands and files that may get lost when I reinstall.

---

### Post by philinux on 2010-07-05
You can set the bandwidth limit. System>prefs>ubuntu one. Devices tab.

---

### Post by andrewabc on 2010-07-05
With ubuntu one do you need launchpad account?

Or can any random person install ubuntu, enable ubuntu one and it can auto upload your stuff without needing any login information? How does it know which computer is yours? If you switch from say desktop to laptop, you would sync data between them? So you must give ubuntu one login info correct?

---

### Post by hikaricore on 2010-07-05
Yes you need to sign up for a launchpad account.

---

### Post by andrewabc on 2010-07-05
> **hikaricore said:**
> Yes you need to sign up for a launchpad account.

Ok, so the original poster, must have at some point put in login information to ubuntu one. Then at some point enabled it. Then it uploaded at full speed.

Yet original poster had no idea what was going on.

If I am in nautilus and it asks to enable it (like it currently does), if you click enable or whatever it can't auto start uploading if you've never input your launchpad account info, can it? Does it ask for this info if you click enable in nautlius?

I'm not currently at my 10.10 computer so can't try any of this.

---

### Post by chrismine on 2010-07-05
> **philinux said:**
> You can set the bandwidth limit. System>prefs>ubuntu one. Devices tab.
Thanks for that I have set an upload limit. I now know what happened and will mark as solved, albeit I still do not know how my Downloads folder got flagged.

---

### Post by philinux on 2010-07-05
PEBKAC lol

---

### Post by hikaricore on 2010-07-05
Either you set it that way originally or...it's possible the downloads folder is flagged by default.
Glad you figured it out either way.

---

### Post by chrismine on 2010-07-06
> **philinux said:**
> PEBKAC lol

:redface: And i am suppose to be a computer technician!

Rub it in!

---

### Post by chrismine on 2010-07-08
> **Chauncellor said:**
> Hey! Let's spend three more pages going completely ape-**** over an obvious sarcastic joke that someone planted!

Don't worry i'll tike it in my stride...

---

