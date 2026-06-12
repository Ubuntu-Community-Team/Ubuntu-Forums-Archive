---
title: "Best Long Range USB Wireless Adapter for 9.04"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by scifilens on 2009-07-11
Hi all,

So I have had some experience (read: trials and tribulations) with getting various adapters to work in various versions of Ubuntu, but after reading through these forums and either downloading this driver or updating that kernel, or using ndiswrapper - I have had some varied success.  

However, when it comes to the Alfa AWUS036H long range adapter (with the rtl8187 chipset), I have the same problem that a few of you have had with the dropped signal, etc. in jaunty.  So far, none of the suggested fixes (ndiswrapper, stop/disable Network manager, blacklist various other drivers, etc) have solved this problem for me (whereas it works fine on the same box with Vista).  And yes, I know I could post a proper ticket and try to see if anyone can help me fix it... but I'm kinda done playing around with it at this point.  I feel like far too many have tried it already.

Hence, I am now trying to identify a more suitable long range and high power (500mW/20bD+) adapter, something that has a proven, known range of at least 300 feet, preferably more [feel free to school me in the ways of the wifi maths].  Could it be easier to go backwards and find out which is the best chipset (is it RT73?) or chipsets for compatibility with 9.04 (btw I'm using the i386 architecture) and is there a long range adapter out there with one of those chipsets?

And I do know (well) the list of [supported wireless devices]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), but it is an evolving document and so has its limitations, also it does not identify which are useful for long range/wardriving-type applications.  (But don't get me wrong, it's an amazing document - HIGHLY useful...)

So, if anyone has any tips or advice on my query above, I would greatly appreciate it.  I can also pass on what I have learned so far to anyone who asks.  I just don't want to hog the list with any further ramblings from myself.  :)

Shiny.

~Sci

"No problem is too small or too trivial if we can really do something about it." - Richard Feynman, 1966

---

### Post by Ultra Cronic on 2011-11-12
> **scifilens said:**
> Hi all,

So I have had some experience (read: trials and tribulations) with getting various adapters to work in various versions of Ubuntu, but after reading through these forums and either downloading this driver or updating that kernel, or using ndiswrapper - I have had some varied success.  

However, when it comes to the Alfa AWUS036H long range adapter (with the rtl8187 chipset), I have the same problem that a few of you have had with the dropped signal, etc. in jaunty.  So far, none of the suggested fixes (ndiswrapper, stop/disable Network manager, blacklist various other drivers, etc) have solved this problem for me (whereas it works fine on the same box with Vista).  And yes, I know I could post a proper ticket and try to see if anyone can help me fix it... but I'm kinda done playing around with it at this point.  I feel like far too many have tried it already.

Hence, I am now trying to identify a more suitable long range and high power (500mW/20bD+) adapter, something that has a proven, known range of at least 300 feet, preferably more [feel free to school me in the ways of the wifi maths].  Could it be easier to go backwards and find out which is the best chipset (is it RT73?) or chipsets for compatibility with 9.04 (btw I'm using the i386 architecture) and is there a long range adapter out there with one of those chipsets?

And I do know (well) the list of [supported wireless devices]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), but it is an evolving document and so has its limitations, also it does not identify which are useful for long range/wardriving-type applications.  (But don't get me wrong, it's an amazing document - HIGHLY useful...)

So, if anyone has any tips or advice on my query above, I would greatly appreciate it.  I can also pass on what I have learned so far to anyone who asks.  I just don't want to hog the list with any further ramblings from myself.  :)

Shiny.

~Sci

"No problem is too small or too trivial if we can really do something about it." - Richard Feynman, 1966

Reply------>
I can&#8217;t help myself when I hear about &#8220;RANGE&#8221; concerns.

Allot of people are in here working their butts off trying to make the Alfa 
AWUS0&&H Wifi dongles work. And I admit if your a power monger like me 
They are one sweet wifi transmitter for the price. However.
	You may want to consider the biggest and baddest upgrade anyone can do for their range especially if your 2 miles or even 5 miles away from a nearest &#8220;Free Legally&#8221; wifi spot. 
	The short and simple theory here is multiply your power [in db units] times 4 to gain one lousy db at the receivers end. YUK!!! You would have to run an illegal 100 watt 2000 dollar transceiver to gain 5 db units on the other end. and still you can&#8217;t receive any better so you connection goes toast. 
	Short story; I use a 150 dollar 30 db gain Microwave WIFI dish tuned for 2.4  Wifi band, they are easy to find google it. Now get this you get a 30 db gain transmitting and a 30 db gain RECEIVING!!  So now your TWO way has been boosted instead of just a one way cloud warmer.  I used to use whats called an alligator wifi dongle to use the net an alligator has ALL mouth and NO ears and my results where deplorable with the alfa hooked up to the sad excuse of a 1/4 wave [-8 db gain] antenna that it came with.  Most the antenna you guys are using are built in and have negative gains another words LOSSES costing you performance. I went from my liksys pcmcia wifi to the alfa once I got it to work after literally compiling the driver to kernel method I found out here to force the install, blowing up my kernel twice thank god for hard drive imaging I could get back up in 2 hours with everything setup. 
	Lets rap it up;
The bottom line is GAIN on receiving as well as transmitting is the only thing that will &#8220;Get You Out&#8221; further. The AMPLIFIER method is useless as it does no good on the receiving end as also to often it is illegal for those that care hehe he. The antenna method is legal up to the total of one watt combined amplifier and antenna gain, rest assured a half watt dongle and a 30 db gain dish is over the limit, no will or time here to post the math, google it. 
	End result? my Linksys 1/3 watt hooked up to the microwave dish gave me 4 bars in my wifi net monitor. Now all this trouble to connect a 1/2 watt alfa to the same antenna gave me the same 4 bars!!!   %$$##!##$%!!!! 2 total system meltdowns and 4 days hammering out driver code for what? NOTHING. 

	The 30db wifi dish antenna minus 8db in line losses of connectivity cable [keep that short by the way] is what is already giving me the edge of over 20 db gain. 
Did I fail to mention I am using [with permission from the owner] a free wifi spot 4 miles away from here? YUP that&#8217;s right , and the cheap pcmcia linksys did just as good a job. I&#8217;m on McDonald&#8217;s wifi spot with a dish on the roof, easily removable of course for my war driving polka runs.  The only advantage to the alfa dongle is; unlike the linksys the alfa supports promiscuous and monitoring modes and is a preferred dongle to the hacking community for that reason. The linksys [that I have] is only good for normal use surfing the net no injection or mac addy change spoofing and such.

	 Big and bulky you say? Well my antenna dish is, but there are 5 to 12 db gain models you can fold up in a suitcase or even a brief case!! remember you are probably running a negative 8 db loss right now as your reading this. Your negative -8 db going up to a positive +8 db [small dish about 12&#8220;] will yield you a net gain of 16 db over what you have now, that&#8217;s about three bars on a wifi monitor software widget.
      Even indoors a dish shows the same gain in comparison.

           Even a patch antenna will fit in your pocket and give 6 to 8 db gain.

RAP-UP: This is just a peek at the topic. There is allot I left out, such as Gain from what?  a benchmark gain starts at zero. A user situation gain starts from the negative -8 db gain [loss] at the point of just before improvement. Actually I am gaining 28 db total if You started at the -8 db gain my alfa radio came with. The other magor topic not mentioned is directional versus non directional [uni-directional]  and why you should be using directional beam antennas. Witch "Reject" unwanted RF packets from your neighbors behind your antenna. The less unwanted packets the higher the speed of downloads you get with the same signal. Your radio and software has less Space-Junk to filter through just to find your packets.
Best lesson on this subject, Google the cringles can wifi antenna. It's zero gain but delivers 4 times the download speeds with the same lousy 2 bar connection and they list the reasons why.

Moderators feel free to use this as a topic starter , I noticed most people using the wrong approach to boosting their signal.

---

