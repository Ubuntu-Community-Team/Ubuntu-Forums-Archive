---
title: "Sony Ericsson GC89 GRPS/EDGE/WLAN"
date: 2005-12-20
forum: Networking &amp; Wireless
---

### Post by psyguy92 on 2005-12-20
Hi.  This is a nice card, but I'd like to know if anyone has been able to get it to work with Ubuntu, before I buy it at $200 and $50 / month access plan.  I don't want to be resigned to using windows for this!  Traditional broadband isn't available where I'm at now, so this looks like a good option.

Someone asked about this some months ago [here]("http://ubuntuforums.org/showpost.php?p=361953&postcount=1"),  but there were no replys.

---

### Post by psyguy92 on 2005-12-31
[QUOTE=psyguy92]
Someone asked about this some months ago [here]("http://ubuntuforums.org/showpost.php?p=361953&postcount=1"),  but there were no replys.[/QUOTE]

Those who cannot learn from history are doomed to repeat it.

Anyway... In case someone else is searching for this info, it seems that a similar card works under ndiswrapper.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("ndiswrapper.sourceforge.net/mediawiki/index.php/List")

---

### Post by psyguy92 on 2006-08-03
Hi me. I would like to introduce you to myself and I.

In case anyone is interested, I've no *nix partition anymore :(
I'm using the EDGE/GPRS network as a connection to the internet, and still haven't found a way to make it work under Ubuntu. I miss Ubuntu. 

I looked for info on this again and came up with this: [http://www.network-builders.com/t58652-gprs-card-connected-to-the-gprs-network-in-linux-2615-can-send-sms-messages-but-still-no-internet.html](http://www.network-builders.com/t58652-gprs-card-connected-to-the-gprs-network-in-linux-2615-can-send-sms-messages-but-still-no-internet.html)

A little bit of that makes sense to me, but not a lot of it.  I'm wondering if anyone else here on the forum has this card, or wants it to work.  Alas... Maybe later.

---

### Post by bnyrbl on 2006-09-21
I have this card recently given to me by my employer, and I'm pretty antsy to get it working too.

It shouldn't be so much an issue of obtaining/creating a driver for the card.  When I hotplug it into the PCMCIA slot, it does appear as serial port ttys04.  According to other forum posts on the web, someone was able to get this working on Cingular with the proper init/dial string, but this would be specific to the provider.  I am on a Canadian cellular network, which provides an 'Install CD' with Windows drivers and a dialer component.  The connection settings would probably be hard-coded into this dialer component, as there is no documentation delivered with the card on setting this up manually.  Either that or the network has everything it needs from your provider's SIM card installed in the back.

This card also has a wireless b/g functionality, and you would be able to use ndiswrapper with the windows driver definition (I believe it's a Broadcom based chipset, but I already have built-in wireless on my laptop so getting this working hasn't been a priority).

So basically, I'm going to set it up in Windows, sniff the com port while it's connecting and try and get the proper init string and dial settings, if any.  Once you have that, just create a pppd profile and it should work, I'll let you know what I find.

---

### Post by squinky on 2006-10-09
I picked up a GC89 last winter with the intent of making it work one way or the other.  I wound up getting it working, though not at the full speed the thing's capable of.  I wrote a little HOWTO here:

[http://erikstambaugh.com/gprshowto.html]("http://erikstambaugh.com/gprshowto.html")

The project wasn't able to keep my full attention beyond the ability to simply connect, which I did.  If anyone can improve on it, I'd be quite happy.

Mine is written for T-Mobile's US GPRS/EDGE network.  Other networks will require different phone numbers, authentication, and context strings, which you will probably need to get from your provider, if you can get past the low-tier "try rebooting Windows XP again" support people.

As for the card's 802.11 capabilities, Edgy seems to detect it, though I haven't used it, so I can't confirm if it works.

Good luck!

---

### Post by new_foo on 2006-10-19
I've tried SQUINKY's technique, and it works on my GC83.  Thanks.

One question, I disconnect by pressing ctrl-C with the terminal that I ran the script with still open.  Once I accidentally closed that terminal without disconnecting.  I ended up rebooting to disconnect.  Is there a way to get in there and disconnect without rebooting?

Thanks in advance.

---

### Post by squinky on 2006-10-19
Should be able to connect to the same /dev/ttyS(something) using minicom and try typing things (I suspect something like +++ATH might work).  I've had many problems with it, and at worst I'll pull the card out of the slot and hope it'll work when I plug it back in without requiring a reboot.  I've also had things stop working and start again after a few minutes' timeout.

It's kind of been a black art making this thing work in the first place, so I don't really have any elegant solutions that make it function the way hardware is supposed to.  I hope someone else can, though!

---

### Post by new_foo on 2006-10-22
squinky,

do you have problems with the conection stalling?

I only got this working earlier this week and it worked fine for a day or two, then I didn't have time to play with it.  On friday, it kept "stalling."  It's not the tmobile connection.  When I run the card in windows, it works good.  in fact ever since the earthquake/blackout on sunday, the connection has been extra good.  

I first thought it was tmobile, but it's not, then I thought linux was doing the windows thing and trying to download something big in the background, but I could find no evidence of that.  Then I realized a process had kept the port after I quit the script, and the prompt didn't return to the terminal.  I traced it to the pppd process holding up the works.  Any idea on the cause?  I guess I'll go download that sony ericsson manual.

Thanks

---

### Post by squinky on 2006-10-30
I wonder if, when the data comes off the wireless at a higher rate than the DTE rate, it simply flushes it, causing the pppd to freak out.

I don't know beyond that.  All I can do is guess.

---

### Post by psyguy92 on 2007-05-02
SQUINKY!
You are my new HERO!!! :) :) :)

I, with great sadness, deleted my Ubuntu partition over a year ago because I couldn't connect to the internet with this card. I saw the new Feisty Fawn version come out, and thought I'd give it a try.

I found your howto and gave it a shot. It seems minicom is not installed by default, so I downloaded a .deb from the debian site using WinXP, transfered it to a USB Keychain, installed it on Ubuntu, and couldn't get it to do jack (I really don't know how to use it). I thought I was going to be beating my head against the wall, but went ahead and created the 3 files you listed, and here I am happily posting to the forum using the gc89 card.  I haven't had a chance to see anything about it's stability or ease of disconnect/reconnect yet, but I'm thrilled to have it connected!

Thanks so much Squinky !!!

:popcorn:

---

### Post by squinky on 2007-05-02
> **psyguy92 said:**
> SQUINKY!
You are my new HERO!!! :) :) :)


Aww, shucks.  I'm glad to help.

Unfortunately, I only use the card as a last resort when I'm out traveling, so there hasn't been much incentive for me to puzzle out how to get it running faster.  Still, it beats not having it work at all!

---

### Post by PhenixPhyre on 2007-05-05
Hey  this post have helped me quite a bit. But I am still not able to able to use my Tmobile Sony Ericsson GC89 network card. I run the "tail -n 3 /var/log/messages" command and this is what comes up.

May  5 14:10:27 laptop kernel: [75219.332000] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
May  5 14:10:27 laptop kernel: [75219.332000] ACPI: PCI Interrupt 0000:02:00.1[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
May  5 14:10:27 laptop kernel: [75219.332000] Couldn't register serial port 0000:02:00.1: -28

Any help that anyone can give me would be great.

Thanks

---

### Post by psyguy92 on 2007-05-06
Hey there. Did you try Squinky's guide? [http://erikstambaugh.com/gprshowto.html]("http://erikstambaugh.com/gprshowto.html")

I did this on a Feisty fresh install - don't know if that would matter or not.  The only thing I really had to change was /dev/ttyS0. For the life of me, I can't remember now how I figured out that it was at S0, but I did :confused: 

Are you using the T-mobile network, and not Cingular or something else? It may be important, because this line:
```
OK AT+CGDCONT=1,"IP","internet2.voicestream.com"
```
is specific to T-mobile. It probably wouldn't work for another network.

I'm far from an expert here, but hope these ideas help a bit, and good luck! :)

---

### Post by PhenixPhyre on 2007-05-06
I was going by that guide but I am stuck on the step where I see if the hardware works. I check /var/log/messages and I just see the line that the card couldn't register. But I will try to just use /dev/ttyS0 and see i that works. And to answer your other question, I am using Tmobile as my carrier. Also the install that I am using is prety fresh. it hasn't been on my laptop for maybe a week.

---

### Post by psyguy92 on 2007-05-07
Let me/us know how it goes. I wouldn't think that trial and error incrementing it by 1 each time would hurt anything. S0, S1, S2... S14 (or so).  As I said in a previous post, I wasn't able to get minicom to do squat either as far as detection/testing goes, but that's probably user error on my part :)

---

### Post by Matoso on 2007-05-18
I want to use the SE GC89 to manipulate SMS that it receives. Does anyone have a idea on how I can do it? or some doc that I can read to do that automated.

Thanks for the attention

---

### Post by alex_mayorga on 2007-10-23
> **Matoso said:**
> I want to use the SE GC89 to manipulate SMS that it receives. Does anyone have a idea on how I can do it? or some doc that I can read to do that automated.

Thanks for the attention

Matoso,

I'm also interested on this. I plan to hack an ancient laptop and a GC82 card so it works as a "Twitter bridge" of sorts, in network SMS are unlimited for me, but Twitter is a international $$$ SMS away so this would be definitely of value.

Any info you've might found would be of value, so I can keep annoying everyone via Twitter :lolflag:

Best luck,
Alex

---

### Post by mimsmall on 2007-10-23
What connection speed do you get? Some other how to's for this card say it must be set at 57600. They also set the connection string to: OK AT+CGDCONT=1,"IP","wap.voicestream.com"  and you say OK AT+CGDCONT=1,"IP","internet2.voicestream.com"  
For 57600 only, I don't think it is worth the money and trouble. IMO

---

### Post by TapocoL on 2008-04-12
I have tried squinky's how-to, however I have run into one problem. It seems like I am connecting the card properly, but I have no idea how to connect to T-Mobile's internet.

Here is the tail-end of the pppd call tmobile.
[PHP]Cannot determine ethernet address for proxy ARP
local IP address ##.###.##.##
remote IP address ##.###.##.#
primary DNS address ##.##.#.###
secondary DNS address ##.##.##.###
Script /etc/ppp/ip-up started (pid 6511)
Script /etc/ppp/ip-up finished (pid 6511), status = 0x0[/PHP]

I opened up another terminal window to run the ifconfig at the same time, and here is what I get for the PPP section.
[PHP]ppp0  Link encap:Point-to-Point Protocol
      inet addr:##.###.##.##  P-t-P:##.###.##.#  Mask:###.###.###.###
      UP POINTTOPOINT RUNNING NO ARP MULTICAST  MTU:1500  Metric:1
      RX packets:3 errors:0 dropped:0 overruns:0 frame:0
      TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:3
      RX bytes:66 (66.0 b)  TX bytes:87 (87.0 b)[/PHP]

Hopefully, I have given enough information that someone can help me. I had to use wap.voicestream.com because internet2.voicestream.com was giving me +CME ERROR: 10 and internet3.voicestream.com was getting an auto disconnect when I tried it.

I am another one of those newbies, so I do not know too much about what these commands are doing. Thanks for any help.

Craig

---

### Post by TapocoL on 2008-04-12
I found the problem, I had a weak connection on a wifi line. I believe requests were trying to be sent through that communication instead of the Cardbus, so now I am posting with the GC89. Thanks squinky for the how-to.

---

### Post by linxuser14 on 2008-04-15
Hi, first thanks for what you've done researching gc89. I just got one a couple weeks ago. Couldn't get anything with it in kubuntu. kppp just intialized and debug window showed ATZ followed by ERROR. I copy/pasted squinky's 3 files and did the pppd call tmobile but system log showed it running throught script ending with hang up and after a time it repeats. But afterward kppp was able to communicate with gc89 and connect after I changed its number to *99***1# , it was previously *99# last year that worked for a while on my sierra aircard. anyway now every 2 minutes kppp hangs up and reconnects. but it works and here I am writting this. Any idea what I've done? And it hard to see if the original pppd script is still repeating in there. I definately don't follow whats happening. but connect is connect. do you think it needs to see 57600 to work?  maybe using what it does regardless? I had to set the modem to 57600 or the debug window in kppp showed it transmiting jibberish to gc89 with no response. I'm just finding questions to my questions with this. Anyway thats input that I can think of on my gc89 experience thus far.
:popcorn:

---

### Post by linxuser14 on 2008-04-16
I originally couldn't get kppp to access gc89 till I set the modem speed to 57600. Otherwise it 

communicated jiberish to gc89 and no response. Then it did ATZ to gc89 with response of ERROR. 

After reading Squinky's how to I copy/pasted his /etc/ppp/peers/tmobile , gc89chat files it was 3 files. 

Ran pppd call tmobile and it didn't connect. But after that kppp can communicate with gc89. Setting 

dialing # to *99***1# enabled it to connect. Then...

        -next is copy/paste from my kate-

In /etc/ppp/options I commented out lcp-echo-failure 4 and removed the comment-out (#) from the 

line -vj (something about jacobson compression) I think it disabled it but I did (#lcp-echo-failure 4) to 

disable it I think. Anyway kppp no longer hangs up and reconnects every 2 minutes. there was a line 

saying lcp-echo-interval 30 that I left unchanged. i guess that explains the 2 minute hang 

up/reconnect time. Anyway it works fine. Just speed is maybe not at optimal. speedtest shows 40 

kb/s using LAX and Mpls,Mn servers. 50 kb/s doing Scottsdale.AZ server. But it works. Anyone know 

specifically what files contain settings I've stumbled on that make it work, request and I'll be glad to 

post em. I'm not sure if my other problem where kppp couldn't communicate with gc89 till after I do a 

pppd call tmobile is still an issue till I halt and try again another day. But yeah! Internet in kubuntu. 

p.s. I'm running 6.06 I think.

---

### Post by linxuser14 on 2008-04-16
> **psyguy92 said:**
> Hi.  This is a nice card, but I'd like to know if anyone has been able to get it to work with Ubuntu, before I buy it at $200 and $50 / month access plan.  I don't want to be resigned to using windows for this!  Traditional broadband isn't available where I'm at now, so this looks like a good option.

Someone asked about this some months ago [here]("http://ubuntuforums.org/showpost.php?p=361953&postcount=1"),  but there were no replys.
see my posts in  T-Mobile Sony-Ericsson GC89  maybe something will help.

---

