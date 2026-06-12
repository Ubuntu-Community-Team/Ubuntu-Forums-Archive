---
title: "Dapper Drake 6.06: &quot;Improved Wireless Support&quot;"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Sasquatch2000 on 2006-06-07
Says so right here, about 3/4 of the way to the bottom:

[Improved Wireless support](http://www.ubuntu.com/testing/dapperbeta?highlight=%28wireless%29)

---

### Post by matthew on 2006-06-07
Network Manager found my ethernet as well as my ipw2200b/g wireless card and let me set up WPA within minutes. It was a great improvement.

---

### Post by brt on 2006-06-07
well, it did work well with breezy using ndwrapper+xp-driver with WEP, so it did with dapper, but i am still messing around with wpa(_supplicant)   :...

---

### Post by Lambert on 2006-06-07
There have been improvements but I guess that's relative to everyone as there are still many who have problems with wireless.

Linux in general has had some strong points in wireless but also many (and arguably more) weak points. Each year there have been improvements and there are many more to come. 

One of the bigger ones I believe is not on an individual distribution release such as ubuntu but on a macro linux level.

[http://www.linuxdevices.com/news/NS1977847793.html](http://www.linuxdevices.com/news/NS1977847793.html)

I know this can be annoying and difficult for many as it's a key function of users (access to the WWW network). But there has been improvement and there is much more to come. It's just been a little late (mostly due to vendor support of their devices) but that's looking to continue to improve and change.

---

### Post by fxgogo on 2006-06-08
My wireless worked beautifully in Warty, Hoary and Breezy and now it is broken in Dapper. From my investigations, it seems to be a kernel thing, but this is not good. Not good at all.

---

### Post by mozetti on 2006-06-08
[QUOTE=fxgogo]My wireless worked beautifully in Warty, Hoary and Breezy and now it is broken in Dapper. From my investigations, it seems to be a kernel thing, but this is not good. Not good at all.[/QUOTE]

Similar problem here -- my SMC 2632W Atmel chipset WiFi card 'just worked' in Breezy, but it doesn't in Dapper. From all the posts I've seen, this isn't a chipset specific problem. I'm not experienced enough to do testing on beta distros, so I have to wonder if this was happening during the Dapper testing? If so, then why wasn't it ironed out, or at least made known? If not, then what happened?

---

### Post by boneman1 on 2006-06-08
My wireless card worked fine in Hoary and Breezy and it's working fine in Fedora Core 5.  I'd really like to use Ubuntu on my laptop, but until they get the wireless problem fixed that's not an option for me.  One of the big reasons I liked Ubuntu was ease of use.  If I'm going to have to spend hours tweaking things to get it working it's not worth my while.

---

### Post by Sasquatch2000 on 2006-06-08
P.S. I started this poll because the answers from [BEST / Recommended wireless card for Ubuntu](http://ubuntuforums.org/showthread.php?t=189940&page=2) were not all positive.


***SO***, if this is *supposed to be* so ***_"improved"_***, what happened?

---

### Post by Monarchos on 2006-06-08
Dapper did not do jack sh*t for my wireless.  Now its getting to the point of its so frusterating, I don't even enjoy using Ubuntu now because im always programming or fixing something, that i never have time to actually take advantage of the features.  Whats especially frusterating is when you spend four hours getting your wireless to work and it finally does, only to wake up the next morning to find it not working, and not having any idea where to start so I can get it to work.  Ubuntu needs better wireless support.  Its lies that Dapper makes wireless easier, all it does is make it more complicated and I'm sick of messing with it.  I may get rid of Ubuntu if I have to re-program my wireless card every f*ing day.

---

### Post by Sasquatch2000 on 2006-06-08
21 to 13 so far saying it makes things worse.

Should the developers be pointed to see this thread? If so, I wonder what the answer is. I'm assuming there are open bugs on these issues. Anybody know if these are in some sort of [COLOR="Red"]**high priority**[/COLOR] area to be done this or next week or at least before anything else?

---

### Post by sarutv on 2006-06-08
I wish I had did some research before upgrading to Dapper. My Belkin F5D6020 card 'Just Worked' in Hoary and Breezy using the atmel drivers. I was so proud that I recommended them to my friends. I even boasted saying in Windows, I had to install drivers and in Ubuntu it worked out of the box.

But I am totally disappointed with Dapper. Now I am forced to use windows until this problem is resolved :(

---

### Post by Sasquatch2000 on 2006-06-09
Can this post be made a "sticky" post, meaning it "sticks" to the top?

Seems more than appropriate.

---

### Post by awaldram on 2006-06-09
Actualy guys this was brought up it was generaly broke 2 weeks prior to release when we had massive backports into the kernel.

Numerous issues were reported and the community generaly sugested that Dapper should be delayed before it got a bad repertation.

We were overuled and the release even though I pointed out that about 50% of wireless hardware would be broke on Dapper.

You have my sympathy.

It works like this 

If you need WPA and can use ndis wrapper then Network Manager should work

If you have An Prism 2.5 PCI then use the hoatap_pci instead of orrinoco the force manual connection using wpa_supplicant afterwards Network Manager should function.

If you need an open/WEP connection the manual edit /etc/networks should work.

If you require roaming accross multiple different enviroment then unless you have mulitple cards (as I have) the your scrXXed.

It's a real mess hostap_cs produces and WLAN0 interface hostap_pci produces and eth0 interface there is no consistency in how the kernel handles wireless interfaces which appears to hopless break userland tools.

---

### Post by awaldram on 2006-06-09
The kernels nearly as bad as my spelling ;-)

---

### Post by nocturn on 2006-06-09
I'm disappointed that NM does not support fixed IP's.  It would be really nice to have my fixed IP (like now in interfaces), but to be able to roam when I take the laptop out.

Another issue with NM is that it does not activate interfaces at boot, but after login.  I have an LDAP+Kerberos directory server for authentication info....

---

### Post by nocturn on 2006-06-09
to answer the question though, for me
Dapper.wireless == Breezy.wireless == Hoary.wireless

---

### Post by Linuxpunk on 2006-06-09
Well I got a intel 2200b/g in my itronix ix260+ GoBook3. It work fine with breezy, then I upgraded to dapper. No change. Seems I can only use WEP. Would like to get WPA working tho. But as for speed and connectivity I can't complain. Still getting fast downloads like in windows. Tho sometimes I will lose connection. Not to concerned with it at the moment.

---

### Post by polo_step on 2006-06-09
[QUOTE=Sasquatch2000]Can this post be made a "sticky" post, meaning it "sticks" to the top?

Seems more than appropriate.[/QUOTE]
[FONT="Courier New"]I agree.[/FONT]

---

### Post by NinjitsuStylee on 2006-06-09
It's posts like this that are preventing me from clicking that lil' upgrade button in the update manager! :sad:

---

### Post by Mr. Picklesworth on 2006-06-09
I can see where they tried to improve things, but it didn't end up being easier for me.
An example of unfortunate failures in easiness is with the Asus WL-138g card, where a driver (or something) for my wireless card is burried deep in the filesystem and has to be manually deleted to allow ndiswrapper to do its thing without being interfered with.

It's understandable that wireless support is a difficult thing to pull off. For example, I was just thinking it would be cool if there was an online repository of wireless setup programs for different wireless cards in case files had to be edited/removed... then I remembered that that would need Internet access to do!

---

### Post by pssl220 on 2006-06-09
I still have problems with setting up WPA.  In openSuse 10.1 it was very easy to set this up. With Breazy this was a problem. I read in these forums that lots of people had a problem getting WPA to work. I thought, certainly by the Drapper release this would be fixed. What is a higher priority than secure wireless?  Its not like I have some rare wireless card. I have the ipw2200 intel chips. 

I guess I will stick with SUSE which had no problem with WPA right from the start. Even Knoppix had no problem with WPA and that was with an older version. 

Ubuntu works well with WEP, but who wants to use WEP?

I am disappointed because the Ubuntu communtity seems to be very active and working to wants to make this a great distrubution.

---

### Post by MetalMusicAddict on 2006-06-09
[QUOTE=nocturn]I'm disappointed that NM does not support fixed IP's.  It would be really nice to have my fixed IP (like now in interfaces), but to be able to roam when I take the laptop out.

Another issue with NM is that it does not activate interfaces at boot, but after login.  I have an LDAP+Kerberos directory server for authentication info....[/QUOTE]
These were my 2 big complaints.

---

### Post by zxee on 2006-06-09
I've been following threads in the networking section of the hardware forum, I'm somewhat discouraged to find so many problems after what seemed like a good show in previous releases. I've even learned something about ethernet, but I'm a dial up user (ok, cue Bronx cheer) but while I'm a lowly user of phone line connection, at least at home, we do have something in common.  The means to dial up internet connection that worked admirably in hoary and breezy no longer work in dapper, and there are several posts to that effect here. Also I've filed a bug which has been languishing. It makes me wonder how such a significant area of the operating system could have A) Gone from working to DOA, and B) How this problem could be so ignored.

---

### Post by Nrvnqsr on 2006-06-10
I'm sorry to say this but this bcm43xx driver is crap for my laptop, that it suddenly shut down my laptop, blacklist won't do it, I feel very comfortable with ndiswrapper but yet ndiswrapper is being a *** now for me

improved wireless support? I'm sorry but I give it a 2 thumbs down.[-(

---

### Post by supermarchino on 2006-06-10
[QUOTE=fxgogo]My wireless worked beautifully in Warty, Hoary and Breezy and now it is broken in Dapper. From my investigations, it seems to be a kernel thing, but this is not good. Not good at all.[/QUOTE]


same here! old dlink dwl-650! it works with dapper just with older 2.6.12 kernel!

---

### Post by Shonkin57 on 2006-06-10
It was at least better than SuSE 10.1, which had my Hawking wireless pcmcia card's driver *removed* from it without warning. 10.0 had it (the rt2500 chip driver). Anyway, I did 2 installs of Ubuntu. The first was a mess. The Network managment tool worked on and off, but would suddenly lock my system up as tight as a drum. I mean, no keybaord, no mouse, and no way to get out of Xwindows. I had to repeatedly hard reset the computer (a Compaq 2545US Presario laptop). Not a linux kind of experience!

Second try. I wiped the drive, updated from my only Ubuntu disk (a Breezy DVD), installed a minimal gnome-only system to start. And made sure NOT to install the network manager. Card came up like a champ, and has been working great ever since, even after I gingerly began feeding in KDE base and apps. 

I hated seeing Linux work worse than Windows, but after my SuSE 10.1 experience (which involved an unfortunately long wrestling match with ndiswrapper--yes, it works, but for HOW LONG!?!) I was glad to find Ubuntu's native rt2500 chip support acting so friendly with my laptop. 

A tech note for other poor slobs like me out there, who know just enough to hack their way into cyber-hell... My laptop also has a real loser of a wireless card, a Broadcom, built right into it. It barely works at all even in Windows w/ windows-native drivers. But I did note Ubuntu actually finds the card when reporting wireless cards to me, and that may be yet another wrinkle in my personal difficulties getting my wireless NIC to work.

Oh, my wired NIC (an inbuilt card of some sort, forget right now) worked just fine when I bothered to hook it up. But I have it disabled right now -- the less confusion the better.

Hope this helps someone...
Shonkin

---
Yes, I'm an evangelical. No, I didn't vote for Bush. Either time.

---

### Post by ferenczi on 2006-06-12
I gave up installing my D-Link DWL-G630 with Ralink RT61 chipset on a breezy on a compaq armada e500 and used ethernet

in dapper, I activated the wireless, deactivated the ethernet, and then never again could start 'Network' from the System menu. It won't start!!! Neither will Synaptic, for that matter. 

and make it a sticky post, yes!

---

### Post by dicecca112 on 2006-06-12
still have to compile ndiswrapper 1.16 on my own to get my wireless to work 100% of the time.  The default cause it to freeze randomly

---

### Post by Jeff250 on 2006-06-13
[quote="Sasquatch2000"]21 to 13 so far saying it makes things worse.[/quote]
Nope, according to the poll, the only thing you can conlude is that 21 to 13 (or now 75 to 35) say that Dapper does not make things better, not that it makes things worse.  There is an enormous difference between a regression for a user and just a lack of improvement!

Only a number of wireless chipsets have the driver maturity to support WPA + NetworkManager, Intel having the most mature and other drivers like madwifi also having very mature support for a lot of users.  Unfortunately, many wireless companies make no effort to release linux drivers, leaving users with unpopular and unsupported chipsets in a rut.  Wireless cards CAN work excellently with Ubuntu, but they are simply something that should ALWAYS be researched before purchasing a laptop or wireless NIC.

---

### Post by Sasquatch2000 on 2006-06-13
[QUOTE=Sasquatch2000]Can this post be made a "sticky" post, meaning it "sticks" to the top?

Seems more than appropriate.[/QUOTE]

Please?

---

### Post by Sasquatch2000 on 2006-06-13
[QUOTE=awaldram]Actualy guys this was brought up it was generaly broke 2 weeks prior to release when we had massive backports into the kernel.

Numerous issues were reported and the community generaly sugested that Dapper should be delayed before it got a bad repertation.
...[/QUOTE]

So, is a new version with the fixes coming this week? If not, soon? Are you one of the developers?




[QUOTE=awaldram]...
We were overuled and the release even though I pointed out that about 50% of wireless hardware would be broke on Dapper.

You have my sympathy...

It's a real mess hostap_cs produces and WLAN0 interface hostap_pci produces and eth0 interface there is no consistency in how the kernel handles wireless interfaces which appears to hopless break userland tools.[/QUOTE]

So, why do they claim it makes wireless easier?

---

### Post by Sasquatch2000 on 2006-06-13
[QUOTE=Jeff250]Nope, according to the poll, the only thing you can conlude is that 21 to 13 (or now 75 to 35) say that Dapper does not make things better, not that it makes things worse.  There is an enormous difference between a regression for a user and just a lack of improvement!

Only a number of wireless chipsets have the driver maturity to support WPA + NetworkManager, Intel having the most mature and other drivers like madwifi also having very mature support for a lot of users.  Unfortunately, many wireless companies make no effort to release linux drivers, leaving users with unpopular and unsupported chipsets in a rut.  Wireless cards CAN work excellently with Ubuntu, but they are simply something that should ALWAYS be researched before purchasing a laptop or wireless NIC.[/QUOTE]

Good point on the semantics of the poll.

Again, they CLAIM it makes things easier, which is overwhelmingly NOT the case according to this poll. 

The answer to your second paragraph comes in my post [[wireless] Ubuntu 6.06 - BEST / Recommended wireless card for Ubuntu](http://www.ubuntuforums.org/showthread.php?t=189940&page=2)

---

### Post by Shonkin57 on 2006-06-13
I am at work, so must be short w/ this.

In a nutshell, I had to install Dapper twice. The wireless card -- I think -- caused all my difficulties the first time out. But I also learned. I'd had to upgrade from a Breezy Badger to Dapper, and before I upgraded to it I had updated Breezy. BAD move. At least, so I at last decided--after the desktop locked up about every second or third time I did anything remotely to do with the network. 

So I went back (this after an absolutely DISASTEROUS SuSE 10.1 install, which turned out not to support my card -- oh, the card was a Hawking wireless based on the Rt2500 chip set, and had been supported in 10.0). And this time I installed a minimal breezy from the DVD I had. I set up the wireless NIC through the native ralink linux driver it auto-detected (hallelujia!) and installed up to Dapper via that card.

Problems have cropped up since, but not with the wireless. It has worked like a champ each and every time I rebooted, reinstalled bits of Dapper, and so on and so forth.

That is why I voted in the mid-range opinions re Dapper and wireless. And perhaps without going through the Breezy intermediate steps--for instance, usuing a DVD/CD w/ Dapper on it from the git-go, it would have been more painless.

Regardless, it is well worth it. Ubuntu. I like it very much, thank you.

Shonkin57 ~ who sez when we get to Ubuntu's "G" flavor, can it be called "Grinning Gopher?" So a Montanan speaks.

---

### Post by e*clipse on 2006-06-13
I'm a noobe to Ubuntu and Linux in general, so my comments may not be that helpful.  On the other hand, I have been configuring computers before Windows 3.1 and I do have some historical context.

System recognizing my unsupported card (Trendnet TEW-423PI)   GOOD!

Needing to research to find out the ndiswrapper workaround ... a more general purpose solution would be better, but there is a solution.

Needing to install drivers from terminal using ndiswrapper:  Not user-friendly (not a "grandma" job)

Not being able to run WPA > huh?

Needing to install network-manager-gnome and other packages:  Ridiculous!

---

### Post by Sasquatch2000 on 2006-06-13
[QUOTE=e*clipse]I'm a noobe to Ubuntu and Linux in general, so my comments may not be that helpful.  On the other hand, I have been configuring computers before Windows 3.1 and I do have some historical context.

System recognizing my unsupported card (Trendnet TEW-423PI)   GOOD!

Needing to research to find out the ndiswrapper workaround ... a more general purpose solution would be better, but there is a solution.

Needing to install drivers from terminal using ndiswrapper:  Not user-friendly (not a "grandma" job)

Not being able to run WPA > huh?

Needing to install network-manager-gnome and other packages:  Ridiculous![/QUOTE]

[B]"Improved Wireless Support":

[SIZE="5"][COLOR="Red"]PRICELESS![/COLOR][/SIZE][/B]

---

### Post by MarinaraOfDeath on 2006-06-13
[QUOTE=Shonkin57] (which involved an unfortunately long wrestling match with ndiswrapper--yes, it works, but for HOW LONG!?!) [/QUOTE]

This is precisely my problem right now. If I keep losing a half hour every day just to fighting with getting networking working (wireless ***and/or*** ethernet), then Linux becomes a thing I can't afford to spend time on. At least in FC5, once I figured it out an arcane 3-step procedure I knew it would work (everytime, no less). In Dapper, no such luck -- I have to boot into XP to get my work done more than half the time. I love the rest of it, so much "just works", but dammit, I'm not willing to put up with this bu****it until I'm getting paid for it.

I wish linux was good enough I could move my friends and family over, but if I, who've been maintaining various computers since 1992, can't keep ,my own system running the way I need it, it simply is not going to happen. What are they going to say when I tell them it's good but if wireless is needed they're utterly screwed if using linux? Wireless is absolutely to dealbreaker, for pretty much every single laptop owner I know.

---

### Post by dyssident on 2006-06-13
ive got a new laptop and everything works EXCEPT a wifi gui.

my Atheros card was recognized (good) and i can connect to anything with iwconfig (blah). NetworkManager doesnt work at all, gtkwifi wont correctly set the connection mode and wifi-radar didnt seem to do much of anything, so im out of luck for a wifi gui.

aparently dapper comes with the madwifi-old drivers, so ill soon be trying [this]("http://www.ubuntuforums.org/showthread.php?p=703020") tutorial in hopes that NetworkManager will work with madwifi-ng.

---

### Post by Sasquatch2000 on 2006-06-13
dyssident and MarinaraOfDeath, I don't see that either of you voted in the poll.

Care to weigh in with your vote? Thanks.

---

### Post by steev on 2006-06-14
I am a Gentoo developer, so I am coming into this with a bit more in-depth perspective (being the person who is considered the maintainer for NetworkManager in Gentoo.)  For me, I hadn't used Debian since 2001, so I gotta say that I was quite impressed with the installation.  My boss suggested I check out EasyUbuntu, so that was what I did, and at the time, it offered NetworkManager (I don't recall seeing it in the latest release.) While attempting to find a 0.6.3 (which fixes a lot of the issues that I have on my other laptop) I decided to try out edgy, but then perl was broken complaining about the locale, and nothing I could do to fix it.  So, I reinstalled, sticking with Dapper, and just hoping that eventually (soon I hope anyways) 0.6.3 would be added to Dapper.  While Gentoo and Ubuntu handle NetworkManager very differently, it is those slight differences that I think annoy me the most about it.  On my Gentoo box, I can plug in random network card, and boom, NetworkManager sees it and starts to use it, here in Ubuntu, I have to restart NetworkManager (which took me a while to wrap my head around the way Ubuntu runs apps from /etc/dbus-1/event.d (although its basically just an initscript in a different directory.)  That for me, is a HUGE show stopper.  Restarting NetworkManager every time I pop a new network card into my laptop (I have around 10 that I am testing at any given time) requires I restart NM... yeah... that's not making it easier...  I don't know if the issue is hal, or NetworkManager in Ubuntu, but its definitely not as smooth as it could be.

The other thing is, if the device isn't plugged in at boot time... restart again....  The whole point of Utopia was to get away from having to start/stop/restart services I had believed.  Perhaps someone more familiar with Ubuntu can tell me where I may be going wrong, as I said at the beginning, I am first and foremost a Gentoo developer (and I gotta say that I *am* *very* impressed with Ubuntu, so I am not trying to put it down, this is really a very nice and easy install and maintenance, just wishing I knew how to generate the .debs myself so I could pop out a 0.6.3 release of NetworkManager.

One other thing, does anyone know where the vpn plugins for NM are?  Do they not exist for Debian/Ubuntu?  Thanks

---

### Post by MarinaraOfDeath on 2006-06-14
Oh, sorry about that Sasquatch. I thought about voting, but it didn't seem a fair comparison voting when I wasn't sure what you wanted a comparison against? I was thinking that I never ran Ubuntu before Dapper, so it could be either and I didn't really know. Did you want a more general comparison, against other flavors of linux?

When it works, it's like magic -- as quick and easy to get online as it is in XP. Othertimes I want to cry cause everything else works so well but with my research and my blog habits are not possible.

---

### Post by MarinaraOfDeath on 2006-06-14
Wait, you have to have the NIC running at boot time for GUI network configuration to have an effect? Dammit, that's a recipe for bad juju, maybe why I've been having such a wretched time trying to connect. 

I change network environments ***a lot***. LAN in office, various wireless or ethernet connections on campus or around town. Per the ::cough:: wisdom ::cough:: of the internet I usually turn the wireless adapter off if I have a LAN port availalbe. Save battery life (don't know if it really does since I haven't obsessively tracked time to drain the battery), prevent DHCP problems, feels like consistently faster connection (average, not necessarily peak). Now I have to start tracking and see if I can figure it out, starting with NEVER turning off the wireless. More work before being justified in shooting my mouth off...

---

### Post by mattotoole on 2006-06-14
Well, I'm not sure what they did, but it certainly hasn't improved things for me.  I upgraded from Breezy to Dapper, which hosed my networking completely -- neither my ethernet nor wireless cards would work, while they were working perfectly before.  Rather than spend hours troubleshooting, I simply wiped and reinstalled Breezy, which was the quickest way to a functioning system.  I think I'll stay with Breezy 'til they sort all this stuff out. 

IMO the Network Manager is pretty lame to begin with anyway.

---

### Post by Sasquatch2000 on 2006-06-14
mattotoole and marinaraofdeath: Please vote. 

This is comparing the current version to the previous version. The current version claims to be easier than the previous version.

---

### Post by gbw69 on 2006-06-14
i'm also frustrated by not being able to understand why i can't my wireless to work.
All the forums say its easy, bang it should just work, with a few tweaks here and there. After following posts, reading and reading and not getting anywhere i feel that we need more hands on support instead of just hoping someone is going to reply to your thread and come to your rescue.
I like ubuntu and i'll keep plugging at it untill i get it done. I would like to spend some time getting to know the rest of the features aswell. :rolleyes:

---

### Post by Sasquatch2000 on 2006-06-14
More than 2 to 1 disagree that with the statement about "Improved Wireless Support" for Dapper Drake 6.06 as of this post. Perhaps the Ubuntu people should pull down that description as one of its "selling points".

Disagree =95
Agree =42

---

### Post by javaJake on 2006-06-14
[QUOTE=fxgogo]My wireless worked beautifully in Warty, Hoary and Breezy and now it is broken in Dapper. From my investigations, it seems to be a kernel thing, but this is not good. Not good at all.[/QUOTE]
Same here... whoever did the supposed "fix" should probably try to see what went wrong...

---

### Post by OpelBlitz on 2006-06-14
My Dell TrueMobile 1150 wireless worked right out of the box, just had to point it to my SSID and I was set.  Then again, it did in Badger too.  I never had Warty or Hoary on this laptop.  Everyone who votes/posts should mention what their wireless NIC is. :)

---

### Post by Sasquatch2000 on 2006-06-15
bump

---

### Post by steev on 2006-06-15
My wireless nic's are...

**Cisco Aironet PCM-352** (airo_cs) - works spectacularly
**Orinoco Gold** - (orinoco) - again, works spectacularly
**Dell 1450** - 2 different drivers here - islsm_usb and ndiswrapper - with islsm_usb i get a connection, but cannot use it (i blame the drivers, not Ubuntu - it is the same on Gentoo) and ndiswrapper, well, it worked with NM ONE time, and since, refuses to.  Works fine if I iwconfig wlan0 essid $ESSID; dhclient wlan0
**Netgear MA101** - Untested
**Belkin F5D7050 (or is it 5070)** - (rt2x00/rt2570) - Untested - heard this driver was dropped as it has problems (it does in Gentoo as well, although, that is with 2.6.{16,17} rt2570 works fine with 2.6.15
**Dlink DWL-G650** - (madwifi) - Untested (friend borrowing)
Buffalo Airsomething ( rlt8180) - works just fine as far as I have tested.

The only real complaint I have is needing to restart NetworkManager whenever I pop in a network card - I thought the point of HAL and NetworkManager was for things to "Just Work"

---

### Post by BaffledMollusc on 2006-06-16
I have an acx111 chipset, and initially I thought it was a wash; Breezy == Dapper. 

Breezy: During the install it detected and configured my wireless connection providing I wasn't using WEP. As soon as I booted in I could surf the net. If I wanted to use WEP, however, I had to install ndiswrapper, which did the job.

Dapper: On the minus side, Dapper did not detect and set up the wireless connection; I had to do it manually. On the plus side, support for the acx111 chipset with WEP appeared to be compiled directly into the kernel - I didn't need ndiswrapper.

Today, however, I've just downloaded an huge load of updates, and promptly lost my network. Since one of the updates was a new kernel (2.6.15-25-amd64-k8 ) I went back to the old one (2.6.15-23-amd64-k8 ) and immediately had internet connectivity again. I still don't know why.

This latest annoyance tilted me to ticking the "worse support in Dapper" box.

---

### Post by RobertH on 2006-06-16
Well wireless worked straight off the bat but for wpa it was harder because the configuration was different from breezy if I had know about the difference then the configuration would have been much easier.

---

### Post by Nrvnqsr on 2006-06-16
[QUOTE=BaffledMollusc]

Today, however, I've just downloaded an huge load of updates, and promptly lost my network. Since one of the updates was a new kernel (2.6.15-25-amd64-k8 ) I went back to the old one (2.6.15-23-amd64-k8 ) and immediately had internet connectivity again. I still don't know why.

This latest annoyance tilted me to ticking the "worse support in Dapper" box.[/QUOTE]

your not the only one, the 2.6.15-25-x also broke my wifi and some other stuff, just when I have finally got a functional wifi through ndiswrapper.....I already having a strong feeling to go back to Breezy =/

---

### Post by Mr. Picklesworth on 2006-06-16
Oh, so it wasn't just the replaced unworking built-in driver followed by me being dumb?
I hope that whole thing can be simplified some day.

Sorry for the odd (and probably easily found answered) question: How do I revert to an older kernel?
Edit:
Oh, I restart the computer :S
I'll leave that dumb question there so you can laugh at me... It's good for your health.
Oh well, booting with the old kernel solved the problem, so it's not too painful.
Better question: How do I remove the newer kernel so I don't feel like there's a lot of space being wasted?

---

### Post by auberginepop on 2006-06-18
Look at various forums it appears I have had a common experience:

Wireless networking that had been achieved at some difficulty uder Breezy (due to having Broadcom card) dissapeared after an upgrade to Dapper.

After some effort I got wireless working again only to lose it again after installing the kernel to 2.6.15-25.

I have got it all working again (although I'm not entirely sure how).

I'll be very careful in future when upgradeing.

---

### Post by ferenczi on 2006-06-18
improved or not, I finally found the way to get my RT61 chipset card to work on an old Compaq Armada with Dapper: see the howto [here]("http://www.ubuntuforums.org/showthread.php?t=132980") but unlike it states, DO go on to step (h) even in Dapper.

---

### Post by Princey on 2006-06-18
Can't complain here. My D-Link DWL G510 worked perfectly. One caveat was that it only showed WEP in the Wireless Network manager. Read a few posts, modified it to suit my needs and upon installing knetworkmanager, my WPA is active and working. Didn't had to go around tweaking kernels and drivers. Not even after the kernel update which seems to be causing problems for a lot of folks, not just with wireless as stated here. Have to give thumbs up as my breezy box had spotty wireless connections. Posting now using wireless.

---

### Post by christian.convey on 2006-06-19
[quote=Sasquatch2000]Says so right here, about 3/4 of the way to the bottom:

[Improved Wireless support]("http://www.ubuntu.com/testing/dapperbeta?highlight=%28wireless%29")[/quote] 
[quote=fritz_monroe]I haven't had any problems with my Wifi.  I use a Sony Vaio and upgraded from 5.10 to 6.06.  My home network uses WEP and after the upgrade it worked just fine.  I have not tried to connect to other networks, though.  I use it mainly at home, and since it's been just a couple days since the upgrade, I have not had the chance to connect anywhere else.

I will attempt to get WPA running in the next couple days, so I may end up breaking it then.  Hopefully not.[/quote] 
I too had a regression.  My Intel 2200BG works on unencrypted networks, but doesn't seem to work on the encrypted network at my favorite cafe.  It worked fine with Breezy.

I think there's a lesson here:
(1) We (me included) need to be proactive and actually try out the early flights of a Ubuntu release, and write bug reports when we have problems.
(2) Mark Shuttleworth needs to get serious about holding up any stability-oriented release when that release's goals apparently haven't been met.  I.e., when many of us WiFi users are facing regressions.

I promise to do (1) if Mark will promise to do (2).

---

### Post by ssmaxss on 2006-06-19
NetworkManager didn't even find my wireless card ( that is shown by iwconfig). So definetly Disagree.

---

### Post by ngeren on 2006-06-20
Does anyone know if a bug report has been created regarding the new "updated" kernel (.25) and the lack of wireless cards working with it? I'm half determined to go build my own, but that kinda defeats the purpose in why I switched from Slackware to Ubuntu.

---

### Post by spier on 2006-06-20
[QUOTE=matthew]Network Manager found my ethernet as well as my ipw2200b/g wireless card and let me set up WPA within minutes. It was a great improvement.[/QUOTE]

"Within minutes"? Nah, just the time to type the key! ;)

---

### Post by undy on 2006-06-21
Not improved. Gone from working in Hoary & Breezy to not working in Dapper. 

Very disappointed that this appears to have been an anticipated problem. Not sure if I'll put in the effort to work around the problem, switch to an Ethernet connection, or just revert to Breezy.

:( 

Andy

---

### Post by reefland on 2006-06-22
Running Kubuntu Dapper here.  Under System Settings, Network Settings, it autodetected my wireless card.  wlan0 was configured and enabled.  I just had to set network security information.

Using Trendnet TEW-228PI PCI Adapter in a Dell OptiPlex GX260.

---

### Post by afilonov on 2006-06-23
Upgraded from Breezy to Dapper, don't see any difference. I have Thinkpad T41 with Atheros chip. Worked perfect with 5.10, don't see any changes in 6.06. I had problem with 686 kernel, needed to install restricted modules.

---

### Post by Sasquatch2000 on 2006-06-23
174 to 83.

It is still over 2 to 1 in disagreement.

---

### Post by schneo on 2006-06-24
I have a dexlan wifi PCMCIA card wich worked fine with warty, hoary, breezy.

Ifconfig sees it but impossible to activate it with the Network Manager.

I always thought Ubuntu/Linux was improving fast but I guess I was wrong, after reading threads and threads it seems that :

- no Ubuntu dev seem to care about this problem (no answer = I ignore you)
- no ubunutu modo want to make a sticky of this despite all the people reporting problems 

Oh .. I forgot maketing really improved ! Everything is fine even if it's not :mrgreen:

Now I'm back on WinXP, students seem puzzled ...

---

### Post by schneo on 2006-06-24
I have a dexlan wifi PCMCIA card wich worked fine with warty, hoary, breezy.

Ifconfig sees it but impossible to activate it.

I always thought Ubuntu/Linux was improving fast but I guess I was wrong, after reading threads and threads it seems that :

- no Ubuntu dev care about this problem (no answer = I ignore you)
- no ubunutu modo want to make a sticky of this despite all the people reporting problems 

Oh .. I forgot maketing really improved ! Everything is fine even if it's not :mrgreen:

---

### Post by Stinger on 2006-06-27
I have a Asus WL-138g , in Breezy it works with ndiswrapper , it  does so in Dapper too , BUT NOT OUT OF THE BOX !
In Dapper you have "Improved Wireless Support" , meaning some additional wireless kernel modules which for some lucky users will improve wireless support , but for the rest of us will do the exact opposite !
I my case Dapper loaded the mrv8k.ko module , unfortuanally it doesn't support my wireless card.
The result is a frozen boot screen !! 

If you can't boot , how are you suppose to use the system at all !! ](*,)

Ndiswrapper wont work as long as the mrv8k.ko module is loaded , a typical catch-22. 

I was lucky I have a onboard ethernet device aswell , but for those with wireless only , you are sh:-#  out of luck !

Admins , please , please show some guts and make this a sticky !

Now this doesn't mean that Dapper hasn't improved in other areas , it certainly has !! 
But wireless ? Outch!

You can see how i solved my trouble on the [ndiswrapper stuff]("http://ubuntuforums.org/showthread.php?t=190726") thread [#10]("http://ubuntuforums.org/showpost.php?p=1147777&postcount=10").

---

### Post by Sasquatch2000 on 2006-06-30
bump (please make sticky)

---

### Post by vayu on 2006-07-02
[QUOTE=RobertH]Well wireless worked straight off the bat but for wpa it was harder because the configuration was different from breezy if I had know about the difference then the configuration would have been much easier.[/QUOTE]

WPA is broken for me in Dapper as well (was working great in Breezy).  Would you mind describing what configuration differences allowed it to work for you?

(I have an ipw2200, card and a static IP network)

---

### Post by osaeris on 2006-07-05
My D-Link GW650 worked on Breezy coaxed by a session startup script which restarted networking on login. The same isn't true in Dapper I have to open a terminal window and restart networking. For some reason the script won't work I've tried all with sudoers / chmods and the like to no avail. I would say dapper is a faster OS but wireless wise it's a step back for me.

---

### Post by Paloseco on 2006-07-05
Then network manager drops wpa-eap connections few times a minute. :mad:

---

### Post by ddossot on 2006-07-05
> [Using Intel(R) PRO/Wireless 3945ABG on Dell Precision M90]

Yes it improved :p  but only until I applied the post install upgrades #-o 

Then: gone, no more wireless, back to Windoze whenever I am not pluged in the router. Yuck! :mad: 

Somebody: help :confused:

Joy to the world! After the recent updates, it rocks! Ubuntu rules, good bye M$.

Love to all,
David

---

### Post by cracker on 2006-07-05
I have an older Linksys WPC54G card using the TI ACX111 chipset. In both Breezy and Dapper, I had to manually disable the 'acx' kernel module and use ndiswrapper, but with Breezy my card would not work properly on bootup. I had to disable and re-enable it. It would also break after a long period of time, and need to be re-enabled. In Dapper, it works much better, as I have not had to re-enable it at all.

---

### Post by Tamihania on 2006-07-06
Hi all,

I am relatively new to Ubuntu as well as to Linux. But I voted "Agree" here and that's why:

My experience with Linux has begun with Breezy - wireless connectivity was what I describe as nightmare for newbie - so, I've changed to Kanotix...lol which simply worked "out of the box" at the beginning but was too difficult for me to maintain. Anyway I've learned a lot and I am still grateful for it to Community...

To make long story short - I changed to Ubuntu again for few months ago - running testing version of Dapper - wireless worked (sometimes better sometimes worse - but - WORKED!)

After fresh install of Dapper (1ST OF jUNE ;) ) I decided to make my wireless connection working permanently (at the boot) - and it could be done thanks to this thread:

[URL="http://ubuntuforums.org/showthread.php?p=1093961#post1093961"]http://ubuntuforums.org/showthread.php?p=1093961#post1093961
[/URL]
special thanks to [mchs3d]("http://ubuntuforums.org/member.php?u=117578") :)

My specs are:
> description: Notebook
    product: EasyNote
    vendor: Packard Bell NEC
    version: PB07400007
wireless card: MICRO-STAR INT'L CO.,LTD. 802.11b CardBus Wireless Card
Wireless interface product: Wireless PCI Adpator RT2400 / RT2460
          vendor: RaLink

Those specs were working either through line command: 

> # iwconfig ra0 essid "MY ESSID" key "MY KEY"
# dhclient ra0

or - through gui (System->Administration->Networking) - deactivate ra0, activate ra0 (WAIT...), connect (WAIT...).

After adding those lines:

> modprobe rt2400

iwconfig ra0 essid "MYESSID" key "MYKEY"

to the /etc/init.d/bootmisc.sh (at the end but before exit:0) - my laptop connects me wireless to the net at the boot time :)

I hope that this long story:
1. explains why I'm happy with Dapper wireless
2. would be of a help for at least some of the frustrated...

tami

PS. My /etc/network/interfaces file looks as follows:

>  #This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface ra0 inet dhcp
wireless-essid MYESSID
key MYKEY



auto ra0




---

### Post by transm on 2006-07-06
I've tried many different solutions on this board and still can't get my Dell e1705s 1390 to work.   6 hours gone... I still really like the distribution, but wireless is a necessity for so many computer users nowadays.  This does not make a good impression especially given what the distro says are its strong points.  Why release it early if it will just leave a bad impression for so many users?

With so many people having wireless problems, and with the release having been rushed, why isn't there a page up in the meantime where people can post their exact configurations and solutions until the developers do their thing? Or maybe there is one and I'm just bad at searching?

---

### Post by Rocker452 on 2006-07-08
I have a Linksys card and router setup with WPA and I had it working in the last version, which was Breezy i think, but I can't get it to work at all in Dapper. The network Manager that they keep talking about doesn't even see the network or says networking not active. As far as WPA is concerned i haven't even found where You can configure the WPA supplicant in Dapper.It has never been easy to setup wireless in Ubuntu but it's worse now.

---

### Post by Tux+ on 2006-07-08
I disagree. I'm using a Dlink g520+ rev b card that uses the acx drivers. Although it is included like in breezy, ithe new version seemed to be broken and you have to roll back to the previous version.

The older drivers work perfectly and even better than breezy with less drop outs, I had to search around to find out what was the problem and how to fix it which was frustrating as I could not get on the net on the same computer.

---

### Post by mech7 on 2006-07-08
I dont even see a setting for WPA i am new to Ubuntu but really common only WEP [-X  So i voted No, its not easy

---

### Post by erganondorf on 2006-07-08
> **supermarchino said:**
> same here! old dlink dwl-650! it works with dapper just with older 2.6.12 kernel!

Same happened to me, besides dist-upgrade destroying Gnome, icons, etc, my 3Com Office Connect wifi PCMCIA adapter,that used to work with all Ubuntu distros since Warty, out of the box, is just useless with 6.06. After several unsuccessful attemts to find a reason, with much regret I must conclude that Dapper Drake is a failure, a real loser. Switching back to Window$. snif! :(

---

### Post by bensexson on 2006-07-08
My wireless is working flawlessly, but it was NOT easier than Warty or Hoary(I skipped Breezy).  I have not been able to use NM sucessfully and had to revert to my custom interfaces scripts and a LOT of work to get them to work.  I am using a Broadcom 4306 with ndiswrapper.  I tried bcm43xx but the inability to use 54 Mbps was not acceptable for me.  It was not harder but it was NOT easier than previous versions.

---

### Post by bazza on 2006-07-09
I voted disagee because switching to the Ubuntu 6.06 686 kernel from the 386 kernel broke my wlan Dlink-650+ connection. As a new Ubuntu user I did not know that I had to install the restricted kernel modules to get it to work. However a look-see in these forums gave me some hints (once I realised that "restricted kernel" meant kernel and restricted modules)

---

### Post by erganondorf on 2006-07-17
> **Sasquatch2000 said:**
> 21 to 13 so far saying it makes things worse.

Should the developers be pointed to see this thread? If so, I wonder what the answer is. I'm assuming there are open bugs on these issues. Anybody know if these are in some sort of [COLOR="Red"]**high priority**[/COLOR] area to be done this or next week or at least before anything else?
The purpose of an axe is not to be honed all the time. The beauty of pre-Dapper Ubuntu distros was that they were easy to install and maintain, leaving plenty of time to use them for production work. So, if Dapper does not get fixed ***at once***, that will mean that Ubuntu has ceased to exist. Pity.

---

### Post by christian.convey on 2006-07-17
> **erganondorf said:**
> The purpose of an axe is not to be honed all the time. The beauty of pre-Dapper Ubuntu distros was that they were easy to install and maintain, leaving plenty of time to use them for production work. So, if Dapper does not get fixed ***at once***, that will mean that Ubuntu has ceased to exist. Pity.
Sadly, I must agree.  With Breezy I was ready to recommend Ubuntu to just about anyone.  With Dapper, I'm not.  I got the Dapper CD's in the mail today.  I was going to bring them to a local cafe for people to take, but then I paused.  Dapper just hasn't been very stable for me.  I hate to say it, but I don't want Dapper to be peoples' first impression of Linux.  I'm just going to wait for Edgy and *hope* it's something I want to bet my reputation on.  I.e., something I'm willing to recommend to non-techies.

---

### Post by javaJake on 2006-07-17
> **christian.convey said:**
> Sadly, I must agree.  With Breezy I was ready to recommend Ubuntu to just about anyone.  With Dapper, I'm not.  I got the Dapper CD's in the mail today.  I was going to bring them to a local cafe for people to take, but then I paused.  Dapper just hasn't been very stable for me.  I hate to say it, but I don't want Dapper to be peoples' first impression of Linux.  I'm just going to wait for Edgy and *hope* it's something I want to bet my reputation on.  I.e., something I'm willing to recommend to non-techies.

I do not agree. The wireless drivers have actually improved! The drivers for my card didn't work at first, but now they do (devs took notice). As long as people don't use proprietary junk *AHEM* they'll be fine. ;)

---

### Post by Sasquatch2000 on 2006-07-17
> **christian.convey said:**
> Sadly, I must agree.  With Breezy I was ready to recommend Ubuntu to just about anyone.  With Dapper, I'm not.  ...

Same here. It isn't ready for prime time.




> **javaJake said:**
> I do not agree. The wireless drivers have actually improved! The drivers for my card didn't work at first, but now they do (devs took notice). As long as people don't use proprietary junk *AHEM* they'll be fine. ;)

Then how come there were no real answers to the question posed here?

[BEST / Recommended wireless card for Ubuntu](http://ubuntuforums.org/showthread.php?t=189940)

---

### Post by christian.convey on 2006-07-17
> **javaJake said:**
> I do not agree. The wireless drivers have actually improved! The drivers for my card didn't work at first, but now they do (devs took notice). As long as people don't use proprietary junk *AHEM* they'll be fine. ;)
I never said that Dapper was a worse distro for everyone.  I'm very happy that Ubuntu got better for you with Dapper - seriously.

It's just that I've seen enough regressions that I won't recommend it to most people.  I've seen the regressions, filed the bug reports, seen the reports not even be triaged yet, etc.  I'm a Ubuntu fan-boy, but Dapper's wireless just isn't doing it for me.  Maybe Edgy.  I certainly hope so.

---

### Post by javaJake on 2006-07-18
The only thing pissing me off so far is the SMB/HAL bug. No one's seemed to take notice despite the fact it was confirmed as a bug and affects everyone. :mad:

---

### Post by zba78 on 2006-07-27
Well my ubuntu/kubuntu experience only started from dapper flight 2 onwards so I can’t comment on weather dapper is better then hoary/breezy (before I was an avid ARCH linux user).

Kubuntu found my Intel 2200BG out of the box, installed knetworkmanager, which found the network card (using ipw2200 driver) straight away and configured it to work with WPA-PSK in a few seconds.

Only annoying thing is what has been mention before:

- Have to type Kwallet/Gnome Keyring password after logging in to authenticate network manager.
- No option for fixed IP address

---

### Post by Sasquatch2000 on 2006-07-27
Does the new version of Ubuntu do any better?

[Ubuntu team gets "edgy" with latest test release](http://www.desktoplinux.com/news/NS4828732453.html)

---

### Post by mkp on 2006-07-30
I'm sitting here with an ethernet cable snaked across the floor, my wireless connection dead.  Thanks, Dapper.

---

### Post by Stinger on 2006-07-30
> **mkp said:**
> I'm sitting here with an ethernet cable snaked across the floor, my wireless connection dead.  Thanks, Dapper.

I am familiar with your situation , I feel for you , that was how 
Dapper left me too.](*,) 

If I can help you in any way just say the word ;-)

---

### Post by jimmymac on 2006-07-30
Mine worked like a dream with ndiswrapper on 5.10.
Having a few minor issues in Dapper but I'm sure I'll get through them with some help from you guys!!

Cheers,

Jimmy

---

### Post by javaJake on 2006-08-01
> **mkp said:**
> I'm sitting here with an ethernet cable snaked across the floor, my wireless connection dead.  Thanks, Dapper.

Well, maybe we can help you out. :)

---

### Post by schneo on 2006-08-01
Well I guess Zdnet is voting against the *improved" wireless support. 

[http://blogs.zdnet.com/Bott/?p=105](http://blogs.zdnet.com/Bott/?p=105)

Worth reading but I still don't uderstand why no modo here wants to make this thread/poll a sticky to tackle the problems (I guess mainstream media are doing the job then) ...#-o 


> After a restart, I was ready to tackle wireless networking. And that’s where the fun stopped. I began in the Networking control panel, where I was happy to see that the system had detected my wireless adapter. But it couldn’t see my access point, and a quick bit of Googling confirmed that I needed to download a whole bunch of packages to get up and running. Catch-22: I needed a network connection to run apt-get, but the notebook didn’t have a built-in Ethernet adapter. I tried downloading packages from ubuntu.com and transferring them to the notebook via a USB flash drive, but each download I tried to install balked, complaining of dependencies and telling me I needed to install several other packages first. After more than an hour of this I gave up and plugged in a USB Ethernet adapter (add $30 to the hardware upgrade cost). Ubuntu recognized the new adapter immediately and I was able to begin installing 100+ security updates and then try to get the wireless adapter working.

The good news? In fairly short order I was able to see the wireless access point from the notebook. The bad news? It still wouldn’t connect, because my access point is configured for WPA encryption, and the networking components I downloaded only support the horribly insecure WEP encryption. I’m not about to lower the security of my wireless network, especially when every other computer on this network is able to use the full-strength encryption.

I spent the better part of an afternoon Googling and reading in search of the secret to getting WPA encryption working on this notebook. Turns out I’m not the only one with this problem (see the tales of woe here and here and here and just try to follow the MEGO-inducing instructions here). This page promised “seven steps to WPA encrypted Wifi with Ubuntu Dapper Drake” but alas, after following the instructions to the letter and rebooting, I got a couple baffling error messages and yet another prompt for a WEP key that results in no network access.

And that’s where it stands. This computer is destined to sit on a desk in a guest room where no wired connection is available, so wireless access is the only option. Windows XP works perfectly; Ubuntu Linux won’t connect to my secure wireless network. It’s no contest.

---

### Post by Sasquatch2000 on 2006-08-10
bump (since not a sticky)

---

### Post by lynxus on 2006-08-10
This version certaining helped.

I have 2x ( Some model, Linksys PCMCIA cards ) and 1 x centrino thingy.

NONE worked before, ( Fedora or alike )

This detects all now and works fine.

The Automatix script is GREAT and the Network manager helped PERFECTLY!


Infact, Windows doesnt even do the networking better IMO

---

### Post by schneo on 2006-08-10
> 
I have 2x ( Some model, Linksys PCMCIA cards ) and 1 x centrino thingy.

NONE worked before, ( Fedora or alike )

This detects all now and works fine.

The Automatix script is GREAT and the Network manager helped PERFECTLY!

Can you tell me exactly which models of Linksys PCMCIA cards ?

Do you manage to use WPA with it ? (WEP should be forbidden)

Did you have to install anything apart from Automatrix (which is not in the 'standard' distro by the way). It doesn't look like it installs wifi drivers just the ndisgtk frontend.

---

### Post by bensexson on 2006-08-10
I posted here earlier that the wireless support in Dapper is not better (no worse though).  It seems I was wrong.  It is better because of improvements made to Debian Etch that were also added to Dapper.  Debian added wpa_supplicant support to the networking subsystem.  This means wpa_supplicant can be configured and started from the /etc/network/interfaces file.  This means I can use WPA with my network scanning scripts.  If bcm43xx was ready yet It would probably be perfect.  Network Manager is NOT ready yet.  Is the version used in FC5 any better yet?  Also I think wifiradar is the more promising app and should get more support.

---

### Post by erganondorf on 2006-08-13
> **mkp said:**
> I'm sitting here with an ethernet cable snaked across the floor, my wireless connection dead.  Thanks, Dapper.

You are lucky. That is where Dapper Drake left me when I updated my laptop. Then I thougth wire-hooked boxes could be updated safely... Wrong!. This time I got several errors. Gnome just died in the process, losing most of common icons. Had to rebuild the system manually. It seems just like if M$ had something to do with Dapper.

---

### Post by jruschme on 2006-08-13
No complaints here. I've had no problems using my one Atheros-based card (Aterm WL54AG) or three of four PrismII-based cards (two v1. Linksys WPC11 and a D-Link DWL-650, all updated to latest available firmware).

The only problem has been one obscure PrismII-based card, an OEM variant of the Zcomax XI-300 which has a different PCMCIA product ID. Under breezy and earlier, I could add an entry to /etc/pcmcia/config and everything would work find. With the change to pcmcia-cs in dapper, though, I can't find the right place to add the entry and my request for help elsewhere in this forum has gone unanswered.

The only other card giving me trouble is my Atmel-based 3CRSHPW196 which is detected, but won't connect. I gather, though, that this is a problematic card, so I'm not really concerned about it.

John

---

### Post by Ay Deverrick on 2006-08-13
Ubuntu detected the wrong card upon installation, so I had to do everything by hand once I got the installation over and done with.  The only difference this time was that I had to comment out a line in the modules file that loaded the wrong driver on boot up.

---

### Post by cookfromfrozen on 2006-08-14
I don't see why WPA support isn't integrated into the standard network GUI without having to manually configure wpasupplicant or install network-manager-gnome (which didn't work for me).

If it's so easy to configure WPA in Ubuntu, why isn't it integrated into the UI?

I think it's shameful that WEP is the main option in the UI at the moment -- why are the Ubuntu devs prominently displaying such an insecure technology?

Anyone know of any distros that support WPA without having to mess with wpasupplicant?

---

### Post by fazofazo on 2006-08-14
ok thank you good think

---

### Post by garrye on 2006-08-14
I did not try wireless with breezy so I can't comment on the "improved" part.  Everything on my Acer Aspire 3003 WLCI works like a charm with the exception of the Broadcom 4318 wireless and standby/hibernation.

To get the wireless working I had to do an immense amount of reading and trying things, which is fine since I've learned a lot about how Linux/Ubuntu works.  This is something I've been wanting to do for quite a while.  Attempts with the built-in bcm43xx failed totally.  Had to blacklist it and use ndiswrapper.  Attempts at getting Network Manager to work also totally failed.  All I got was a hot and overloaded CPU for my troubles.  I did however keep wpa_supplicant from that install and am using it to run WPA-PSK with AES-CCMP.  I've developed a nice tidy .conf file for that and have inserted a stanza into /etc/network/interfaces to invoke the suppicant at bootup and that has everything working nicely now!  Just this morning I took a walk with my lappy and wandering among the trees at my neighbours I managed a working wifi up to 100 meters from my house before I noticed significant drops in sustained data transfer rates.  That's BETTER than I could ever manage with the co-installed windows xp!!

Improved wireless support?  I voted no.  Nonetheless given that this is a cheep crappy laptop with a cheep crappy SiS chipset and wireless silicon KNOWN NOT to play nice with the Linux community I'd say **_GREAT JOB UBUNTU TEAM!!!_** still a work in progress but then so is the best of Billy's.

I look forward to testing devicescape's Wifi stack or what ever the Ubuntu team has up their sleeve!

---

### Post by erganondorf on 2006-08-20
Dear mkp and all others affected by Dapper 6.06 "improved" wi-fi stuff, your networking problems (and mine) are about to come to an end. Just get and install Ubuntu 6.06.1. This is my boy!. Thanks, Canonical.

---

### Post by oyvindaa on 2006-08-20
I never got to try wireless on Breezy so I can't say. But it works flawlessly on Dapper my end. Out of the box actually, which I'd never thought it would.

---

### Post by zwz on 2006-08-23
Wireless in breezy used to work well on ThinkPad which has an Intel PRO/Wireless 2200BG (rev 05). After upgrading to dapper, it no longer works. For details, please check the second post on 
[http://www.ubuntuforums.org/showthread.php?t=232349](http://www.ubuntuforums.org/showthread.php?t=232349)

---

### Post by Sasquatch2000 on 2006-08-23
> **erganondorf said:**
> Dear mkp and all others affected by Dapper 6.06 "improved" wi-fi stuff, your networking problems (and mine) are about to come to an end. Just get and install Ubuntu 6.06.1. This is my boy!. Thanks, Canonical.

I see nothing anywhere about this 6.06.1 version on the Ubuntu web site. I do see it on download, but no actual textual description anywhere. Can you clue me in what has changed here? 

Thanks.

---

### Post by domib on 2006-08-23
My bitsa desktop with a no-name ralink rt2500 card is 100% reliable running WPA-PSK in Breezy, and I configured it in about half an hour from a standing start by looking up the correct way to edit /etc/network/interfaces.

I have a spanky new HP8372ea laptop with centrino wireless, and the Breezy live cd won't load because it can't cope with the widescreen display (X fails with "no display devices").

Dapper desktop boots perfectly, and it seems to recognise the wireless as the network manager gui thing lists eth1 as a wireless device. It only has space for a WEP key, not a WPA key.

So I tried editing /etc/network/interfaces, but the live cd won't let me. I'm not going to install Dapper properly until I'm sure it's going to work reliably. Particularly since the Win XP Home that came with my laptop didn't come with disks (there's a restore partition on the hd - what a rip off).

Will editing /etc/network/interfaces do it in Dapper? How come it lists lo, eth0, eth1, eth2, wlan0 and I think I remember some other device too. Network manager said my wireless was eth1. My Breezy rt2500 card was ra0. Whats wlan0?

Anyway I'll ask my questions again as they seem to be lost in a sea of moans:

 - in Dapper, can I get my wireless working by editing /etc/network/interfaces?

 - which of the listed interfaces is my interface?

I'm voting no, btw

---

### Post by zwz on 2006-08-23
I found a workaround [http://ubuntuforums.org/showpost.php?p=1415042&postcount=4]("http://ubuntuforums.org/showpost.php?p=1415042&postcount=4").

---

### Post by schneo on 2006-08-27
>  Originally Posted by erganondorf  View Post
Dear mkp and all others affected by Dapper 6.06 "improved" wi-fi stuff, your networking problems (and mine) are about to come to an end. Just get and install Ubuntu 6.06.1. This is my boy!. Thanks, Canonical.

Something new for WPA in this version ?  :-k

---

### Post by ousooner919 on 2006-08-27
> **matthew said:**
> Network Manager found my ethernet as well as my ipw2200b/g wireless card and let me set up WPA within minutes. It was a great improvement.

Maybe it did for you, but NetworkManager and its various components have yet to find mine consistently. I did much better with the wpasupplicant HOWTO in Breezy than I have yet to do in Dapper. In fact, because NetworkManager never seems to find my ipw2200 card, I just went back to standard 128-bit WEP until this somehow gets fixed, because everyone just says "use NetworkManager". It's just not working for me. It's not like I'm using unusual hardware; I have a stock Dell Latitude D610.

SUSE has had WPA figured out and built in for a while, so it's odd that this somehow continues to be such a problem within Ubuntu.

---

### Post by domib on 2006-08-30
> **domib said:**
> 
 - in Dapper, can I get my wireless working by editing /etc/network/interfaces?


turns out the answer is no - rt2500 is configured for WPA-PSK with iwpriv private driver commands, which i think is a brilliant idea but not available in my intel3945

> **domib said:**
> 
 - which of the listed interfaces is my interface?


i learned that iwconfig with no parameters tells me it's eth1

And I've installed network-manager and network-manager-gnome and they see my card, and iwlist eth1 scan sees the WPA protected network i want to connect to, and network-manager-gnome applet lets me enter the "Network Name" and "Password" for WPA-Personal, by which I assume it means the ESSID and PSK, but it won't connect even though my breezy box is still connecting fine.

---

### Post by Sasquatch2000 on 2006-09-27
> **erganondorf said:**
> Dear mkp and all others affected by Dapper 6.06 "improved" wi-fi stuff, your networking problems (and mine) are about to come to an end. Just get and install Ubuntu 6.06.1. This is my boy!. Thanks, Canonical.

Oh, really. 

Where does one find this version? How come it isn't announced on the main home page? Does it work with any of these out of the box?


[Linksys Wireless-N Products](http://www.linksys.com/servlet/Satellite?c=L_Promotion_C2&childpagename=US%2FLayout&cid=1144421946975&pagename=Linksys%2FCommon%2FVisitorWrapper)

[RangeMax NEXT](http://www.netgear.com/Products/Adapters/RangeMaxNextWirelessAdapters.aspx)

[Share your Internet wider and faster](http://catalog.belkin.com/IWCatSectionView.process?Section_Id=202570)

---

### Post by Fitzcarraldo on 2006-10-07
*Sasquatch2000*,

My brother had terrible trouble installing a Belkin 54g Notebook Wireless Card (model no. F5D7010) in a Dell notebook PC. The saga is documented in the following thread:

[http://ubuntuforums.org/showthread.php?p=1589311](http://ubuntuforums.org/showthread.php?p=1589311)

This was his first experience with ubuntu and it was a dreadful introduction to the world of ubuntu/Linux/Unix.

---

### Post by javaJake on 2006-10-07
> **Fitzcarraldo said:**
> *Sasquatch2000*,

My brother had terrible trouble installing a Belkin 54g Notebook Wireless Card (model no. F5D7010) in a Dell notebook PC. The saga is documented in the following thread:

[http://ubuntuforums.org/showthread.php?p=1589311](http://ubuntuforums.org/showthread.php?p=1589311)

This was his first experience with ubuntu and it was a dreadful introduction to the world of ubuntu/Linux/Unix.

Our documents could've helped you reduce your time making this work. There are two important facts you could've gleaned:

1) When using ndiswrapper, always unload the wireless driver that comes with Ubuntu.
2) If your card isn't on the list, you'll have to use ndiswrapper (and the friendly instructions that are there as well).

So, as we **always** say, do some searching first. :D

**Edit:** Sorry... I was getting mad a bit in that post. It gets frustrating when someone comes up to us saying how aweful Ubuntu when they didn't even try searching. Anyway, I edited my post above to be less... agitated.

---

### Post by Fitzcarraldo on 2006-10-07
Thanks for the reply, *javaJake*. I can promise you that my brother and I read through many Web pages and posts on this and other forums over the past three days. We thought we were on to a winner several times when we found threads such as the following:

[http://ubuntuforums.org/showthread.php?t=187004](http://ubuntuforums.org/showthread.php?t=187004)

to name but one example. My brother followed that procedure and it didn't work. He followed others and they didn't work either. You just have to look at the number of posts about the Belkin 54g Wireless Notebook PCMCIA (Model No. F5D7010) in these forums to know that there appear to be quite a few people having a lot of trouble installing (or failing to install) that wireless card with ubuntu.

He tried to follow the official ubuntu instructions, too, but still could not get it to work. Hence his very detailed step-by-step procedure in the thread I posted earlier:

[http://ubuntuforums.org/showthread.php?p=1589311](http://ubuntuforums.org/showthread.php?p=1589311)

I should point out that my brother is no rookie, being very familiar with computers and networking equipment (albeit not with Unix and the various flavours of Linux). He has over 20 years technical experience in the telecommunications industry and is a former Cisco Certified Internetwork Expert and Juniper Networks Certified Internet Specialist and has jointly authored a book in the networking field. I'm saying this not to brag but just to try and demonstrate that, if he found it difficult to install the Belkin wireless PCMCIA card with ubuntu after searching and reading through all these forums and Web pages, then it must be even more confusing for someone who is a beginner and coming to Linux/ubuntu for the first time.

On a much simpler installation than the above -- software configuration only, this time -- I myself have found that the ubuntu documentation does not always work. For example, I followed the instructions here:

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

and they did not work. Fortunately I found a cached page from someone's blog on the Web (the original page no longer exists) here:

[http://72.14.253.104/search?q=cache:6ajIFW4Ng9UJ:www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/](http://72.14.253.104/search?q=cache:6ajIFW4Ng9UJ:www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/)

which got the remote printer working straight away with my ubuntu PC on a Windows network.

I have been using and programming computers of various types (micro, mini and mainframe) since 1977 all the way up to present, with operating systems such as MSDOS, CP/M, MP/M, Unix, VMS and others) and I find several of the procedures needed to (try and) get things working under ubuntu (and other flavours of Linux) complicated and/or complex in some cases. I have to admit that I've also 'broken my head' a few times with the various versions of MS Windows and its GUI and non-GUI predecessors, but with Windows it has never been as complicated as the procedures that some people have had to go through, as posted in these forums, to install some variants of those Belkin wireless cards.

Please don't take the above as a rant, but I wanted you to understand that we did search and read (and not from the position of total beginners, either).

I hope that you will be able to advise me in future if I come across any problems with my ubuntu installation using a wired Ethernet Cardbus card. So far I'm very pleased with *my* first ubuntu installation (on an old Gateway Solo 9300 notebook), to the extent that I will be trying an install on one of my newer PCs which is due for replacement shortly.

'See' you in the forums. :)

---

### Post by Melcar on 2006-10-07
Unfortunately, some cards plain out refuse to work.  The instructions for installing drivers for ndiswrapper are very simple to follow, and what's more, actually make sense (this coming from a long time Windows user).  I have gotten several wireless devices working with ndiswrapper.  However, as I wrote earlier, some cards just don't play nice; I was never able to get my WPC54G working.

---

### Post by Sasquatch2000 on 2006-10-07
> **javaJake said:**
> Our documents could've helped you reduce your time making this work. There are two important facts you could've gleaned:

1) When using ndiswrapper, always unload the wireless driver that comes with Ubuntu.
2) If your card isn't on the list, you'll have to use ndiswrapper (and the friendly instructions that are there as well).

So, as we **always** say, do some searching first. :D

**Edit:** Sorry... I was getting mad a bit in that post. It gets frustrating when someone comes up to us saying how aweful Ubuntu when they didn't even try searching. Anyway, I edited my post above to be less... agitated.


I think the point here is people shouldn't HAVE TO SEARCH AROUND for anything. They want it to be automatic. If it isn't automatic, there should be some clear instructions on how to find answers without necessitating a "search" for the information. That is just going to turn people away in hordes.

They should come out with a list of recommended network and recommended video cards to make it real easy what hardware to use. I didn't see that anywhere when installing. It should be the first step in the installation process. Call it "hardware verification" for lack of a better description.

---

### Post by lyceum on 2006-10-07
My wireless is built in, and Broadcom, the company that makes the hardware, has Linux drivers, but I have to run them from source, as Ubuntu could not find the hardware. Other than that, I am just learning about Networking, so I am not sure. All I can say is that I took my laptop to class and everyone with Windows logged on to the net without knowing how they did it. I plugged in an external WiFi that did work and Ubuntu (Gnome) kept asking me for the network info, and I did not know what it was talking about ](*,) . (I am new to networking) After 4 weeks of bragging about how great Ubuntu was to the class, I looked kind of dumb being the only one not on the web. But hey, what doesn't kill us makes us stronger, right? :-k

---

### Post by ckonrad on 2006-10-07
> **matthew said:**
> Network Manager found my ethernet as well as my ipw2200b/g wireless card and let me set up WPA within minutes. It was a great improvement.

wish i could say the same thing i have been trying to get wireless working for about 3 months, i usually work on it and ask people here in the forum for  a few days and then take a break for awhile.

---

### Post by oyvindaa on 2006-10-08
Works great here. Now I'm just curious how it'll work/not work on Edgy.

---

### Post by Fitzcarraldo on 2006-10-08
> **ckonrad said:**
> wish i could say the same thing i have been trying to get wireless working for about 3 months, i usually work on it and ask people here in the forum for  a few days and then take a break for awhile.

Are you using the same card (ipw2200b/g wireless) as *matthew*, *ckonrad*?

---

### Post by finite9 on 2006-10-13
Dapper does improve wireless for me in that I can now use a native driver instead of ndiswrapper like I had to in Breezy.  I have a bcm43xx chipset and it all works dandy with custom scripts in the shell.  Forget about roaming or manual connections without having to drop to shell though.

Network manager for me just refuses to play ball.  I have WPA, which should be the de facto, not second best to WEP!  Cannot believe that more peolpe using Linux tend to stick with WEP/nothing whereas even my non-techie Dad knows he has to use WPA on WinXP.  I thought Linux was the security-conscious geek toy, and thereby Linux users would automatically favour WPA?  Guessed wrong.

NM doesn't like bcm43xx + WPA combination.  This is as of 6 months ago when I installed 6.06.  Times change fast though and I would love for it to start working with an update like so many other things have since installing :)

---

### Post by Sasquatch2000 on 2006-11-28
So, have we come any closer to improving wireless support with 6.10? Someone want to do a new poll? (-:

---

### Post by javaJake on 2006-11-28
> **Sasquatch2000 said:**
> So, have we come any closer to improving wireless support with 6.10? Someone want to do a new poll? (-:

Yes, but clarify the fact that we are to vote whether or not wireless support is **better then pre-Dapper distributions**, and **not if it works**.

Also, clarify things **directly related to network support**. For instance, my wireless USB device doesn't work without a line of code because of a new USB-power-limiting feature. This "feature" isn't related to network support, and almost is a seperate issue. Beyond that, it works beautifully!!!

---

