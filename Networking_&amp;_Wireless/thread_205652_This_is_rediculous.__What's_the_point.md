---
title: "This is rediculous.  What's the point?"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by DownTribe on 2006-06-28
What's the point of using Ubuntu, if you CANNOT ACCESS THE FREAKING INTERNET?  :mad: 

Before I get flamed for that, let me just say that i've spent the past two weeks searching these forums, other forums, and dozens of places around the net.  I'm not looking for a replacement for Windows, I'm looking for something better.  I've tried Mepis and SUSE in the past.  So far, Ubuntu seems to be the best for me and my needs.  I love the interface and the bundled software.  One problem, actually it's more of a question:  How come nobody can figure out a universal fix for the Linksys WMP54G wireless card?  I've read every post on this forum that had the phrase "WMP54G" in it, and tried every mentioned fix.  Nothing, still no internet at all.

Another question, why is there absolutely ZERO support (read: auto configuration) for today's most popular wireless cards?  When I installed this card in Windows, I was up and running in less than 5 minutes.

Again, I'm trying to avoid comparing Ubuntu to Windows...I know they are entirely different beasts.  I guess my only solution at this point is to use Ubuntu for...well...nothing actually.  If I can't connect to the internet to get updates, it's useless to me.

OK, I just had to get that off my chest.  Rant over, LOL.  :wink:

---

### Post by matthew on 2006-06-28
[quote=DownTribe]How come nobody can figure out a universal fix for the Linksys WMP54G wireless card?[/quote]Because Linksys hasn't produced a Linux driver nor have they released the specs so an open source driver can be written easily.

I hate to say it, but if hardware isn't supported you will have to either make do with kludgy hacks (if you can get them to work) or you're just out of luck. For those already running Linux, this reemphasized the necessity of research before buying.

---

### Post by MetalMusicAddict on 2006-06-28
[QUOTE=DownTribe]If I can't connect to the internet to get updates, it's useless to me.[/QUOTE]
Bye.

---

### Post by az on 2006-06-28
It's chicken and egg.  The manufacturers don't pay a lot of attention to linux because of the low market share.  People like you are turned away because the resulting hardware does not work easily.

Be it know that a lot of (most?) cards actually work out-of-the-box with no tweaking needed.

---

### Post by TOPPEL on 2006-06-28
i had the same problem with the same wifi card.  it would never connect !  not only that originally i needed wpa-psk support which wasn't included either.  we had a multifunction printer configured on wireless lan and now its down because i had to downgrade to WEP because there was no native support for this.  well, WEP didn't work either.  even though the linksys card is alleged to work out of the box (i had the version 4 of the card) it would not connect to my router.  now i'm having problems because i swapped nics with my dads windows machine and because i read that someone had no problems with the NETGEAR 311T working out of the box despite "rumors" well, i'm having the same issue and the AP is in my room so that can't be the problem.  

btw, because of all this the brother wlan printer is now a usb printer the family can't share.

---

### Post by TOPPEL on 2006-06-28
[QUOTE=MetalMusicAddict]Bye.[/QUOTE]

uh, d00d, the card uses the Ralink 2500 driver.  its native.  

WMP54G by Linksys does anyway.

---

### Post by DownTribe on 2006-06-28
[QUOTE=MetalMusicAddict]Bye.[/QUOTE]

Thank you for your interesting, helpful, thought-provoking post.  :roll:

---

### Post by DownTribe on 2006-06-28
I'm going to continue to keep Ubuntu on a 30GB partition, and learn as much about it as I can.  I'd like to participate and contribute as much as I can to the platform.  When it works, I like it.

I've also sent out an e-mail to Linksys inquiring about their practices.  I'll post their response when i get it...

---

### Post by MetalMusicAddict on 2006-06-28
[QUOTE=DownTribe]This is rediculous. What's the point?[/QUOTE]
Thank you for your pointless attention grabbing thread. Instead of resorting to whining couldnt you have at least asked for help first? Posting threads with inflamitory topics to get help is not the way to get it.

---

### Post by tturrisi on 2006-06-28
some versions of that linksys card have a broadcom chipset, howto:
[http://linux-wireless.org/Install-HOWTO/LinkSys.WMP54G/](http://linux-wireless.org/Install-HOWTO/LinkSys.WMP54G/)

---

### Post by DownTribe on 2006-06-28
[QUOTE=MetalMusicAddict]Thank you for your pointless attention grabbing thread. Instead of resorting to whining couldnt you have at least asked for help first? Posting threads with inflamitory topics to get help is not the way to get it.[/QUOTE]


Wasn't whining. Not an inflammatory post.  (Apparently dictionary & spell check don't work either.)  I asked legitimate questions that others have graciously given me answers to.  I didn't ask for help with the WMP54G, because I actually SEARCHED for previous help threads on the subject.

Please take your trolling to another thread.  :rolleyes:

---

### Post by TOPPEL on 2006-06-28
i would not assume however that if you had that card that you had broadcom off the bat though.  there was a ralink wiki for compiling the latest drivers that needs revisioning.  i followed the link from the Ubuntu certification start pages as mentioned in the mailing list of Ubuntu.  i thought i was free -- i was not.

but first find your chipset :)

---

### Post by MetalMusicAddict on 2006-06-28
[QUOTE=DownTribe]Please take your trolling to another thread.  :rolleyes:[/QUOTE]
You expected to get flamed. So as I see it Im just meeting expectation. :)

Better title for your thread "Will someone help me one on one with my WMP54G wireless card? Ive tried everything."

Threads like this happen 10 times a day. Just 1 too many for me today. ;)

**EDIT:** Sorry. Im just pissy. Dont mind me.

---

### Post by kaaredyret on 2006-06-28
[QUOTE=MetalMusicAddict]Bye.[/QUOTE]

If this is all you can come up with, then I suggest you don't answer him. Really, imagine how many like him that are struggling with configuring his ubuntu with a wireless NIC. 

This guy has a point! The most important thing I an think of, is not that my software is open source, free, made by liberalists or followers of a religion, but that it bloody works! If it is so hard to find a computer with hardware that is supported by Linux, just to discover that it still doesnt support WPA2 encryption unless you monkey around with classic Linux configuration, then why bother? I bought Windows XP, and used almost zero hours on configuring it. I installed Linux and could use an eternity on trying to get it working. Some people dont use their computer as their hobby, but to get work DONE! Or to have fun with it, but NOT to configure it forever, or whatever you guys do in front of you computers.

YOU, MetalMusicAddict, failed to see the point: that this makes many people say BYE to Linux. Look at the market shares, lad.  

I sense that many like you defend their closed linux society/cult ("you are either with us or against us" attitude) but fine. A childish attitude like that will only limit the progress of Linux and the number of new users. Microsoft send their greetings to guys like you.

The majority of users here provide kind and extremely helpful feedback and help. The rest is a cult of freaks, that just dont get the point of CRITISISM. Blah blah whining, blah blah flaming blah blah dont talk negative about Ubuntu blah blah. You GUYS (!) ... Linux is far from perfect, far from good enough, far from the goal... so EXPECT critisism, "customers" who had bad experiences... expect it all! End users expect hardware support, whatever the excuse for lack of it will be. Wireless networking is the big thing now, so no poor support for it will be noticed. If it hurts your feelings to read about peoples bad experiences with Linux here, or to experience that they dont sing it to you, praising Linux on every second line, then turn OFF you computers and go to bed, or watch a feel good movie. Or embrace the REAL WORLD! 

All the WHINING from your type just gives us an impression of a little fragile cult, defending their ideology, with little or poor contact with the real world.

And now I will unplug this network cable (so 1996), reboot into Microsoft Windows XP and see my wireless card connect as it always did: immidiately and perfectly. As it does everywhere I go with my laptop. So 2006.

---

### Post by Handssolow on 2006-06-29
I'm sorry that I too have been very disappointed with my my lack of progress at getting my installed Kubuntu to access my router and the internet and I've got a Belkin ra2500 card that's supposed to have the drivers already installed. Forgetting WPA for the moment, why for example is there's no option in the Network GUI for setting the WiFi channel? Anyway I found the The Network Settings GUI to be unreliable. My settings seem to disappear. I can only assume there are bugs in the software. 

I still hoping for some helpful replies to my requests for forum help to enable me to set up my wireless connection to my router. It's a mystery to me why it doesn't link with the router and next with the internet. Yet the strange thing is that sometimes sudo iwconfig reports that the link with my router has been established, though not for many hours.
I've been briefly connected to Google a couple of times but I didn't expect this "now you see it now you don't, now it works now it doesn't".

It's such a pity because I can hardly recommend linux and Ubuntu/Kubuntu to anyone when I'm not able to access the internet.

This posting comes to you from my XP machine over my WLAN, I only wish it didn't.

---

### Post by rai4shu2 on 2006-06-29
[QUOTE=kaaredyret]And now I will unplug this network cable (so 1996), reboot into Microsoft Windows XP and see my wireless card connect as it always did: immidiately and perfectly. As it does everywhere I go with my laptop. So 2006.[/QUOTE]

And immediately shut down by WGA. :p 

Wireless in my experience is unreliable *hardware* that suckers use. I've had more trouble using wireless in XP than Linux.

Why is it that you people think we are threatened when you stop using Linux? Your Microsoft cult propaganda and FUD machine has no equivalent in the Linux world.

---

### Post by DownTribe on 2006-06-29
[QUOTE=rai4shu2]

Wireless in my experience is unreliable *hardware* that suckers use. I've had more trouble using wireless in XP than Linux.

[COLOR="Red"]
Bwahahahahahahaha.  Tell that to just about every Ivy League, State, and Private University, who provide it free & flawlessly to their students and faculty on a daily basis.  Not to mention all the workplaces and coffee houses around the world...[/COLOR]

Why is it that you people think we are threatened when you stop using Linux? Your Microsoft cult propaganda and FUD machine has no equivalent in the Linux world.

[COLOR="Red"]First, read my post #8 in this thread.  I'm no Microsoft cultist.  I continue to use Ubuntu (and SUSE). Second, I refuse to resort to petty personal attacks over the internet, unlike you, but lets just say...if you can't connect to your wireless router via WinXP, then I'm surprised you are able to pull your pants up in the morning...[/COLOR]

[/QUOTE]

:confused:

---

### Post by rai4shu2 on 2006-06-30
Flame bait. Welcome to my ignore list, you troll.

---

### Post by Lord Illidan on 2006-06-30
Calm down and no name calling, or a mod will close this thread.
Either help this guy or don't post.

---

### Post by matthew on 2006-06-30
[quote=Lord Illidan]Calm down and no name calling, or a mod will close this thread.
Either help this guy or don't post.[/quote]This is an absolutely true statement. Please moderate yourselves or one of us will do it for you.

---

### Post by elemental666 on 2006-06-30
So did you figure out which chipset your dealing with?  Post the results of running lspci here if you need help.

---

### Post by amanda on 2006-06-30
I am with you. 

Having recently spent a slightly infuriating week at my parent's house, where my fiancee's WinXP PDA was able to connect to an unsecured access point just fine, but I could not connect, and where the only other computer available has 64 Megs of RAM and a dialup modem (a P III with 64Megs of RAM. that is a problem that is easy to solve ...), I think I actually hollered outloud. 

There are a few things missing from the Ubuntu install that are pretty key to at least inching towards an OS that "just works."

* Some general wireless tools help: it took me forever to stumble upon iwlist and iwconfig. A "networking" help page that had a rundown of the commands you can use when the gui doesn't work, and how to use them to connect to an accesspoint--that would be really helpful. 

* Some modem help. I know it isn't very 21st Century of me, but when I couldn't connect to wireless, I tried my modem. Not only did it take me forever and a day to find wvdial commands, but I had a very hard time figuring out that I don't have any modem drivers installed. Getting the drivers is one thing, but getting a help page that says "If you are trying to use your modem, look here to see whether any drivers are installed, or try this command or that to test ..." would have been a godsend.

A lot of things are available online, but explanations of connectivity issues ought to be available offline, in the help files. That would be helpful, because networking in Ubuntu *is* difficult.

---

