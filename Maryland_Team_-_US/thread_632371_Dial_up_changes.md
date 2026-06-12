---
title: "Dial up changes"
date: 2007-12-05
forum: Maryland Team - US
---

### Post by Oceola on 2007-12-05
Most of the folks in Maryland using dial-up received letters from Verizon as to access number changes. Since Verizon has been somewhat uncooperative in support of Linux it might be good to keep tabs on this here as far as what numbers are working and any DNS Server numbers which seem to function.

I looked for some support on the web site as per the letter's suggestion but there was none.

Calling Verizon Tech support, they seem to have added an "Other Operating Systems" mention in the robot voice choices but it goes to someone who doesn't know other operating systems and doesn't know ifnthe DNS server numbers are changing.

I tried 5 of the local numbers the online robot picked, all went through but with an unfamiliar initial beep, a pause, then the computer tones. In some cases I heard a distant pinging but with loads of static in the line. None would allow me on line with the current DNS server numbers. When I queried the Verizon Tech about this she told me all were under constructions and none would be available until after the fifteenth when the current number I use no longer grants access. This strikes me as working without a net, not being able to pretest and work out the bugs.

There's no support or help for FIOS or DSL or I'd use one or the other. DSL has workarounds but the software router is one way blocking so once something's in there's no way to stop the out unless you use another software firewall. FIOS is unsupported for Linux completely and parts of the package for MAC as well.

Any comments or suggestions or disagreements would be welcomed. Might be nice to have this stuff ironed out befoer the Ides of December.:confused:

---

### Post by parma1 on 2007-12-05
> There's no support or help for FIOS or DSL

Hmmm. That doesn't sound right.  I know of several people using Verizon DSL with Ubuntu, and having no problems.

Also this site

[http://www.freesoftwaremagazine.com/node/1875](http://www.freesoftwaremagazine.com/node/1875)

seems to indicate the same for FIOS.

-J.

---

### Post by Oceola on 2007-12-06
You took the remark out of context. Verizon Tech support will offer no help whatsoever for Linux. For Dial-up, DSL or for FIOS. I've seen the third party workarounds and you have to be fairly savvy in order to make them happen plus the expense is over several hundred dollars for an additional router on the client end. Add the couple of hundred more for the FIOS service and each individual computer hookup. It also is a non reversible commitment. Once you commit to FIOS you cannot get your copper pair back. I know it seems retarded to go on when things like wireless exist but wireless is unsafe and insecure in my area.

FIOS also requires some form of compatible Microsoft software which Verizon needs to place on your system. I spoke with the installation engineers when they were installing the systems and they had no issues, but getting assistance from marketing/tech support people who do not have the engineering experience is or at least seems impossible. It also appears they have been told not to help Linux systems. There's an option with the phone robot for help "For other operating system" but it sends you to the same tech support personnel who do not support Linux.

Your magazine link didn't work properly at first but eventually I got through. I went through the cacophony of responses beneath and it's the same confusion I see in all of the "suggested" attempts or "it works without effort" troll remarks. Mostly the Northeast US has access to tech support personnel who are in their region and not working from a script in a distant land. It may also be because of system purchases by Verizon in one area works better with being compatible to other systems than some others due to remaining personnel who haven't been dumped yet. Bell Atlantic was my previous provider and there was never an issue as far as DNS information, PPP configuration or anything else. Most Linux systems use the same connection values outside of specific hardware issues and these are no longer provided willingly. The FCC will not help either as they seem to be part of either Microsoft or Verizon, haven't figured out who owns who there yet.

---

### Post by ChuckFrain on 2007-12-06
I really cannot comment on the dialup aspect of Verizon as I have never used that.

However with Verizon DSL and FIOS I have not had any issues. I put a WRT54G running DD-WRT on the front of both of these connections just fine. I have FIOS at home and relatives have DSL. I've also used an [IPCop ]("http://www.ipcop.org")box on the connections for testing purposes, again without any issue. 

FIOS directly to the PC should only need a PPPoE client on the software side as that is how I configure the routers. So if you use a PPPoE package from Ubuntu it should, in theory, work for the desktop. The question becomes why would you not put a router/firewall between you and the internet? Verizon provided a D-Link router during the install of my FIOS.

---

### Post by Oceola on 2007-12-07
Do not take this as condescending or arrogant but most folks seem to miss the simplicity of what I'm looking for here. Simply put the Primary and Secondary DNS to place in pppconfig or in "Network." Each Verizon access telephone number, which is changing after December 15th, has what appears to be committed Primary and Secondary DNS xxx.xx.0.xxx and xxx.xx.1.xxx. It's a simple thing in a static modem setup. Two numbers is all I've been requesting and they are not available, or at least not provided to the scripted tech support personnel. At the same time there's no access if the DNS numbers are wrong for that telephone number, no information exchange of your password or account information if I'm on target with this..

@Chuck - Thanks for the DSL and FIOS input but FIOS leaves you a prisoner of Verizon and is not reversible, so if you discontinue (with ISPs unreasonable termination penalties) you're left without a telephone or internet unless you get a wireless uplink or some other provider takes over the copper network in your area and runs new wire to your location (There's also the question if they will cooperate at that time with Linux). This is without the normal service fees, which double on a monthly basis, the cost of the added hardware and my illiterate attempts at making it work without someone leading me by the nose or doing it for me, consider me a twit. There's also the installation fees per computer. They will hook up one computer as part of the initial deal but each additional one has a separate fee. $100 at last review, can't leave the wife by the wayside. Also I don't need to download movies or Pay to watch commercial television, which seems somewhat lacking in common sense and a grand time wasting scenario.
DSL would be OK if I could have a two-way Firewall on a hardware router on the Linux system and not a Windows one-way firewall only software router provided by the ISP. DSL looked the easier method until the issue of ISP access and single direction firewall came into play. Adding a second router was suggested but seems more of the same "work around" complications plus additional costs which should be unnecessary. .

I've been using Linux without crutches or Windows for a couple of years now from Hoary through Gutsy. Each upgrade the internet access system has gotten better and easier. With the EU Courts making the MS server information available to other Operating systems I figured it wouldn't be too long before a dedicated Linux access was available in the US as well. I don't use Webb TV or radio, play net games,watch movies or listen to music on the computer, I removed all the Realmedia and Shockwave software. It's a simple email and search tool.

In any case, dial-up with two phone lines, complete, costs me about $80 a month with no extra expenses or equipment replacement . I don't have cable TV nor do I want it.

---

### Post by Oceola on 2007-12-08
None of the  5 offered phone numbers in the area accept any transfer as of yet. Tried them all seperately in pppconfig using the same primary and secondary server number .
Dec 8. in the early a.m., five attempts.

---

### Post by parma1 on 2007-12-11
> DSL would be OK if I could have a two-way Firewall on a hardware router on the Linux system and not a Windows one-way firewall only software router provided by the ISP. DSL looked the easier method until the issue of ISP access and single direction firewall came into play. Adding a second router was suggested but seems more of the same "work around" complications plus additional costs which should be unnecessary. .

Hold on a second. If a hardware firewall is your concern, why not buy an inexpensive router at WalMart (~$35), and put that right behind your DSL modem? (That'd also solve your second PC connection.)  As you said earlier, you are not asking for the world here; your requirements seem quite modest.

I've set two elderly people up with Ubuntu and Verizon DSL, and the setup is quick, easy and stable.  Costs each of them $17/month.  $80/month seems way out of line unless you have a lot of long distance charges.

---

### Post by Oceola on 2007-12-13
Thanks for the input, I will find out if the Dynamic setup in Ubuntu works after December 15th, if not I'll be looking for another provider and canceling Verizon or possibly just go offline completely. The rest of Ubuntu software works just fine for me as it is and I will miss the research capability but it may be better to just buy the books and do without all the advertising detritus and spoofed sites which seems to pervade each search, 

The second router is one of those work-a-rounds which seems feasible and it would allow me to keep my copper pair, That way I could, if I wanted go to another provider. If I were going to commit to DSL I found I can use my own hardware router with a two way firewall with some ISPs. I necessarily don't want to move to DSL because of some marketing weasel's techno extortion on the part of Verizon by not providing the Primary and Secondary DNS numbers in order to satisfy some backroom deal between Microsoft and Verizon. The modem/router you suggest is a one way software router, easily borked. I've been looking and investigated these possiblities over a year ago when the FIOS setup fell through after Verizon's marketing/technical support people lied about the Microsoft requirements and Linux not working with FIOS and how MS crapware had to be on the computer. I don't buy retort that level one scripted techs are dumb. It's deliberate forced marketing and a form of criminal racketeering.

The $81 a month cost is for two phone lines (separate numbers) and the $25 a month unlimited dial-up. DSL is only cheap right now to get folks to switch, once a sufficient number switch and dial up goes the way of the Dodo it will increase substantially.
If I go offline I'll save about $60 a month and keep one single land line so the telemarketers can annoy the answering machine.
:lolflag:

---

### Post by parma1 on 2007-12-14
Well, maybe it's me, but I'm still puzzled at your apparent obstacles. The router behind the dsl modem is not a software firewall, and I've never heard of one being breached. (I know, never is a dangerous word, but just the same.)

You could always switch to cable for less than $81/month and enjoy download speeds *way* in excess of dsl. You can get a Comcast internet only account for around $50/month, I think.  The router behind the cable modem works well here also.

And Comcast plays very nicely with Ubuntu.

Also, depending on where you live, other dsl providers are available like Covad, Embarq, and one other whose name escapes me just now.

I just can't see why you seem to be without more than one or two options. Not for that kind of outlay per month.

---

### Post by Oceola on 2007-12-14
@parma1 - There's fewer options locally than you might think. Some of the ISPs represent they are Ubuntu or Linux compatible but are not supporting in anyway. I found several ISPs which are apparently without issue, Covad is one in consideration, and the DSL issue seems to be resolved with a D-Link router.

When I investigated and actually committed to Verizon's DSL they were offering two routers. One required Windows or Microsoft software to be placed on your computer the other was a hardware router. Both had internal fiirewalls but the firewalls were one way. The hardware modem router is no longer offered with only the MS Crapware modem/router being available ,Outbound signals to urls not part of your operations when on line can be for a number of reasons, from simple signaling your presence on line to Bug reports, loggers or spyware shipping out your personal information. The other part of the issue is some of the providers want to put their crapware on your system and are not flexible enough to allow by-pass and just provide values and IP numbers for access by dial up. I do have solutions and most of the folks here and at other sites have been very helpful. Part of the issue is I'm getting tired of the Microsoft big corporate business politics and other issues which impede a decent uncomplicated internet access. Like you noted my needs are simple.

Comcast is a no go in my area as they restrict Point to Point, which seems to be the next great internet issue, and have  a less than stellar record. Everyone I know who has Comcast says to stay away from them due to their poor service and failure to support Linux plus they limit downloads and this is a recent condition which they are not rectifying. Maybe it's an area by area thing like with Verizon. Folks in Vermont have no problems hooking up Linux to Verizon FIOS and but here  FIOS is difficult due to Verizon's lack of cooperation, tech support and cost, plus they state they have to put the MS crapware on your system or you are on your own much like Chuck Frain's setup, a little too complicated for the average user. I can't even begin to talk to my wife about the preference settings for her screensaver with out her eyes going blank, imagine what it would be like to explain something more complicated, all folks don't want to fiddle with things preferring to keep them simple.  Even the Mac support service is limited and the premium packages are restricted to Microsoft users only. Clearly a restraint of trade and racketeering issue. Then there's the little issue of reversion to another provider after a FIOS installation, not available. Verizon will not replace the copper pair so you can change to DSL or other system. It would almost be less costly to run dedicated ISDN lines than to get another pair installed from another provider.

All this is moot as of tomorrow or the day after when I change the phone number, as directed in a recent mailing, and maybe get on line without a great deal of problems, unlikely at this point. Which was the initial point of the post, now wandered off into the world of options.

Maybe I'm just tired after 30 some years using a computer and have lost faith in the technology and some of those who promote it as the "be all, end all."

---

### Post by parma1 on 2007-12-14
Well, many of your arguments are political, not technical, as far as I can tell. (Not that political arguments are not important.)  From a support standpoint, I guess I've never assumed I'd get any *help* from my ISP, only *non-hinderance*. That's what I consider support. While that might not work for Aunt Tilly, all the Aunt Tilly's in my life call me for support anyway, not their ISP.  And I don't help them unless they are running linux. Too much hassle.

I think you'll wait a good long time before ISPs actually *help* you with a linux problem, and that is primarily a cost issue from their standpoint, which I understand, not necessarily a racketeering one. But that doesn't bother me as long as they don't take actions that impede my linux use.

I've used Comcast cable, Earthlink dsl, Covad dsl, and Verizon dsl here in Baltimore and have never had an ISP actively impede my use. None required any Windows software on my machines (which is a good thing, since I don't have any).

And, it never occurred to me to get a router from an ISP. Too many good, less-expensive choices to be had elsewhere. Even a cable modem is cheaper at Best Buy than it is if you buy one from Comcast.

---

### Post by ChuckFrain on 2007-12-14
I do agree with the points you make about the lack of support for Linux from ISPs. If the Linux distributions were more standardized with the tools and utilities they provided, I would argue more to get their support. The P2P issues with Comcast and other providers with their restrictions on traffic will be corrected by the market long term. These are bumps in the road as far as I'm concerned, a learning curve if you will.

As for the 'complicated' setup I have at home, it is actually a rather simple setup *for me*. I would not suggest that someone not technically inclined set that up.

---

### Post by Oceola on 2007-12-17
I finally "got off the pot" and made a commitment to a provider for a dedicated DSL line. I'll be able to dump one phone line and the dialup from Verizon once it's installed and the costs will be similar or slightly less than I pay now.  Also, and I'm at a loss on this, I haven't changed the dial in number but am still getting on line making me wonder if it was some form of marketing ploy. If so it backfired since they'll eventually lose me as a customer altogether, not something they seem concerned with.

@Parma - Impeding the access was never the issue, though a bit complicated for the average dullard like my self, it was more having a simple installation and setup. Not really politics but more ease of access without the intrusive software requirements and failed support. You stated you never had any access issues with a few ISPs, my point exactly, having looked at this from a number of perspectives. Cost of support is a lie as defense by a provider since a sheet of paper is a sheet of paper when you have scripted tech support and the values are the same for all systems.

Once the new system is up I'll pass back any helpful information, the new bunch has Linux tech support personnel and no software restrictions. Even if you disagreed with me on any of thiis, thanks anyway. Hopefully it's resolved, I will learn a bit more and will help to encourage more use of Ubuntu. Least my updates of the kernel and Open Office should take less than a day.:)

---

### Post by Oceola on 2008-01-21
Looks like the DSL didn't pan out either but I did find an ISP not afraid of Linux or it's implications. Can't use their "speed up" package as it's MS but it's still slightly faster than the old dial up.

One thing I haven't been able to resolve completely is the re-occurrence of the Verizon Business office IP constantly showing up in the resolv.conf file. I''ve removed and re-edited all the /etc files and networking files but cannot find how this changes back to the Verizon business office in Virginia. 

Worst part is the Primary and Secondary for my ISP are changed to this business office IP. Past few times I've been able to hold my ISPs ip but there's a bog down and then a DOS and the IP for Verizon has replaced the proper IP.

Any thoughts?

---

### Post by Benanov on 2008-01-23
> Comcast is a no go in my area as they restrict Point to Point, which seems to be the next great internet issue, and have a less than stellar record. Everyone I know who has Comcast says to stay away from them due to their poor service and failure to support Linux plus they limit downloads and this is a recent condition which they are not rectifying.

Point to Point? I can run OpenVPN just fine over my Comcast link, but perhaps that's not the same.

To be honest, the best way to get Comcast to support Linux *is to outsmart them.* After that they'll do the things you need to do, as long as you can demonstrate basic skills.*

You only "need" a Windows or Mac for provisioning, but what no one tells you is that you can call in and have tech support do it.

(Don't tell them you have a Windows machine if you do. They wasted 45 minutes of my life trying to get my SO's box to work.)

**"Madam, I have thirteen linux computers in this house, and a Wii.  Which machine do you want me to put your software CD in?"****

**"That's what I thought."**

Other than that Comcast "just works" and there's no fee for multiple machines (as long as you pull the router out when you're having problems, and use a direct connection, they don't care really.) Yes, BT is blocked, jidgo seems to not work very well (it may just be that I'm running Dapper)...their customer service track record is horrible, but if you outsmart them they will listen. Comcast is only the best because everything else is so terrible, but they do work.

--BK




*sudo dhclient eth0
** I got rid of most of them afterward. I'm down to about 8.

---

### Post by Oceola on 2008-01-24
Thanks Benanov.
I have an ISP (dial up) and it's faster than verizon was. Issue I have now is I think when they turned off the dial up number I used they needed it for the FIOS and I'm getting a constant signal from their servers in Loudon Virgina (formerly MCI ips) now DBA Verizon. I can't block the signal no matter what I try and it keeps replacing my new providers primary and secondary ips with the ones in Virgina. Stupid thing is it all works, albeit with the increase in hits from mainland China, railway and shipyard on the MSN network (tinfoil hat is growing in leaps and bounds on this one) I'm going to go shopping for a hardware router but if the folks at Verizon have placed my phone connection in the FIOS system it may not work either. I can't seem to get anyone past a scripted customer support individual and last check, even with a cancellation confirmation number from some guy in Bombay the charges are still showing up on my bill. Everyone has gone sort of blank on this one. I think I just threw my ISP for a loop in trying to explain it. We'll have to see. Wonder if this means I now have free internet if somehow they borked the FIOS. Nah! This is too visible for stealth mode. Damn signal is coming in UDP right towards my ISP assigned IP.](*,)

---

### Post by Oceola on 2008-01-25
OK I believe I may have found the source of the redirect and the lock on to the former provider's signal. It looks as if the dhcp3 was detecting the other IP signal on my phone pair and since it may have been a stronger signal, used that for the dial up. This may be peculiar to my situation since they are installing FIOS in my area and it may be there was no complete closure of the former account or maybe they've piggybacked a neighbors line or whatever.
I also did some digging and in the backups found some other files with former passwords and user names plus I double disabled a couple of "generic" lines. I also didn't use the Network manager auto dialer to access, which as it uses the dhcp I believe to be the culprit which changes the primary and secondary DNS by detecting a signal and using that, even with the other proper primary and secondary DNS in the system.

Anyway all my internal effort seems to be OK so far. iptraf shows no more lock down to the improperly accessed level3 servers.
For Now.:lolflag:

---

### Post by Oceola on 2008-01-28
Removing the Network Manager resolved this issue but "resolv.conf" files still need to be edited to remove the unwanted former Primary and Secondary (detected) IPs. You'll need to find your backups and edit them as well. 
There is also less closure of your Firestarter and you can add ranges and the firewall will hold. Works for both Feisty and Gutsy.

---

### Post by Squid_blk on 2008-02-16
I have been with Verizon DSL for about since 2002. Besides a minor password corruption issue that took 10 minutes to resolve more than four years ago and not having power during Tropical Storm Isabel, I have never had an outage or any problems with DSL.  I was using Vonage for my home office from Nov 2005 to last month and I was using the router when I switched my home PC to Linux and Ubuntu last Summer.  I think having the router makes all the difference because it has the login information stored in it and all you need is to connect your PC to it and it works.  I did not have to install or configure anything when I installed Ubuntu or when I used the trial live CDs.  My work laptop can go wireless and the IT folks have it set up to work with about anything.  Last night I installed XP Pro on my girlfriend's refurbished laptop and I plugged in LAN cable from my work laptop even XP was able to get online with it and without any configuring, wizards or install programs. I have not tried to connect the DSL to my Ubuntu computer without the router since I have no need to but I figure why mess with something that already is not broken. Not sure if this helps but DSL is great and I switched to it from Cable and I will never go back to cable. I got tired of being pinged by offsite users and I got tried of the bandwith moodswings which would go from fast to a crawl depending on the time of day.

---

### Post by Oceola on 2008-02-18
If things had been as simple as you were able to find them I more than likely would have had the Fios or DSL by now. The routers they provide are one way, not two way so blocking outbound signals has to be managed another way. Buying your own router is OK but you need the network values to set them up.  Unfortunately if you mention Linux to Verizon's people they go dumb on you. They say simply they don't support Linux, end of technical support. I have been using Linux as a standalone for two years and had no difficulties with the new provider once the broadband creep below was dealt with. 

There's also the unresolved signal "discovery" on Verizon phone lines. After changing from Verizon dial up to another provider the Network Manager kept discovering the 65.0.0.0 range of servers in Virginia instead of the servers I was directing the modem too. In reviewing this with an IT expert I was informed it's one of Verizon's insecure, dirty little secrets. Call it Broadband creep or whatever it's their fault the system is borked. I had to remove the Network manager and the DHCP system entirely to prevent access from IPs which had managed to breach the security on the Verizon servers. Something they won't admit to nor fix since it's a known MS hole.

Most of these hits come from IP ranges which target the remote access ports and administrative ports. Some hits to the old Microsoft Messenger ports and other Microsoft package ports. What I have now is working for my simple needs, Maybe when Verizon decides to dump all phone service in lieu of their new role as "Mr. Entertainment" I'll have to find a new copper pair provider.

PS: Has anyone ever heard that it's illegal for "Coppernet" to provide technical support to Linux?

---

### Post by shouden on 2008-02-22
I have been using Verizon for years, Dialup, DSL, and now FIOS. I have never had any issues running Ubuntu (or any other distro) and getting access, provided I used the router they gave me during installation. I of course upgraded to a Linksys running DD_WRT but I could easily have stuck with the one they provided.

For broadband they don't really care what OS you have, as long as you are able to configure it for DHCP, but they will not guarantee it will work (as it is not officially supported) Each time the tech came out for the install, even though he has confused with the OS presented to him, all he asked for was a browser window so he could connect to and configure the router. 

As long as the Linux boxes could DHCP an address from the router(which is configured for you) everything works well. The tech will even make certain WEP is enabled if you are provided with a wireless router. 

I also used Comcast briefly, before they began their traffic shaping crusade soto speak, and even though I had no issues with them and Linux I can't recommend their service at all. It worked fine for a few months, then they sent out some kind of auto update to the cablespeed modems, and apparently my modem failed during its update process, effectively making it a brick on my desk. It took Comcast 33 days to send out a tech to fix it, I called Verizon on day 7 to install DSL and their tech was there on day 9.

---

### Post by Oceola on 2008-03-31
@shoudon - I never had any problems with Bell Atlantic before the numbskulls at Verizon Corporate got a hold of it. Nice when you're the big gorilla in the cage, damn shame they don't have as much common sense as the monkey. There was never an installation issue with Verizon to begin with for FIOS except when I went to order it. Before it was installed in my area (6 months before) I spoke to the engineers doing the installation, they also said no issues but when I spoke to the business side to get it installed they wanted a crapload of money and Linux would not work since MS crapware had to be installed for "Control and Maintenance" (so they stated at the time) and as usual they did not support it.
I originally started to use DSL but the issue with that (prior to the FIOS considerations) was the piece of crap oneway router they supplied which allowed them access to my system with no way to block outbound information to unwanted IP ranges. Two routers were offered one a hardware router and the other a WinRouter which required MS both were one way and the blocking of signals outbound was impossible without another firewall. Most folks know the Gutsy Network manager is broken and I wound up removing most of the DHCP service in an effort to keep the constant hits from Verizons poorly secured Microsoft server installations. As evidence of the failure of the DHCP manager after I cancelled the Verizon On line service, which took several attempts, the DHCP functions were picking up a signal from Virginia based Verizon signals and logging me in there using old pppconfig user name and password. I played hell trying to get the detritus out of this system. 

You paint a pretty picture but the truth of it is you need more than a "Yes please do" to make things work and even after Verizon has been removed from my system and another ISP found to replace them there's still the interference from their contractors in Virginia and elsewhere. There's also the cost which Slashdot reported on over a year ago that the average cost of this kind of service would be $150 a month or more. It's already nearing that. I still can't figure why I should pay someone for TV with commercials. Bad enough the nitwits here support the digital TV standard causing most of the nation to buy some kind of Orwellian system.

I still have a dial up phone system and the new ISP has been pretty good, particularly when I get a couple more KB/sec download speeds when updating my Ubuntu. It would be even better if there wasn't constant attempts by Verizons system to put a "robot speed governor" on the connections. It's not quite DOS but damned near it at times.

---

### Post by phr0ze on 2008-04-01
I've had Comcast and FIOS. I also know this will work with DSL.

1. I think you talk too much to the sales people. You confuse them and they end up saying they can't help you. Its almost like you want to prove to them that they can't help you.

2. All cheapie routers are one way. You are asking for too much here. If you want a decent router then buy a used WRT54G v2 router off ebay or craigslist and put DD-WRT on it. And no, there really is nothing secret to punch into a 3rd party router. Generally it's plug and play with maybe a reboot of the modem.

3. Installation is simple, the tech people come out and use their own windows computer to register the line. You don't need windows.

4. Support SOFTWARE, I wouldn't let them put this stuff on my computer if they paid me. This stuff is crap and it gives them access to your machine. Thats how they use it to support you. I used to run windows with comcast and I never installed the software. I tell even the newbies not to install this software. 

5. Support SERVICE, Is lousy anyways. They will not tell you what you want to hear. I don't call them. In general if your line goes down, they tell you to reboot everything (the modem, router, and computer.) Then they have you check your settings (They should be DHCP or Automatic.) There I told you everything they can ever tell you.

6. DNS settings. I stopped using their DNS a while ago. It's slow and it often fails. I switched to OpenDNS which is free and blazing fast. All you have to do is put the two numbers in the DNS spot. Here they are:  208.67.222.222
208.67.220.220. If you register with open DNS for free you can even see all your history, and you can block sites such as adult, political, high bandwidth, etc. It's very cool.

I think you worry for nothing or you are just trying to see how long you can keep this conversation going. Some of the things you have said just don't make sense.

Good luck

---

### Post by Oceola on 2008-04-22
I looked at the OpenDNS and it has been suggested before. I don't understand it completely and there seems to be some privacy issues. 
Maybe you're right, this dialogue has gone on too long without any real resolution and just continues to show me for what I really am, a technological inept imbecile. Doesn't matter now, problem has been resolved. No need to say how everything works anymore, I wouldn't use Comcast or Verizon for On line anything because of their marketing practices, the lack of support and the lies. You can add the extortion level fees as another reason, but then what the heck, one guy like me can't matter.

---

