---
title: "2013 VOIP Poll"
date: 2013-02-07
forum: Multimedia Software
---

### Post by grashdur on 2013-02-07
Dear All,

Perhaps I&#8217;m a silly, stubborn, fool, wanting to rely heavily on VOIP instead of just buying a telephone, putting it on my desk, and signing up for landline service again with AT&T. But I like the convenience of VOIP, when it works. For six years now, I&#8217;ve often been frustrated with VOIP on Ubuntu. 

It all started when I began using Skype on Windows (before starting to use Ubuntu). It worked great, and I loved the convenience of using a headset and of being able to copy and paste phone numbers, and save them to an address book, instead of pushing those buttons all the time.

It got difficult after I switched to using Ubuntu, because of sound issues, especially with a headset. And each time I installed a new version of Ubuntu, the problems started over again. Usually I succeeding in making it all work after spending many hours tweaking it and reading online forums including this one. Sometimes I had to revert back again to the previous version of Ubuntu. My repeated frustration drove me to find alternatives.

I basically tried every softphone out there, and several different VOIP providers. In a nutshell, what I&#8217;ve discovered is that no softphone program works reliably and consistently over time. I tried only a few of the many providers out there, and steered clear of most of them based on very bad stories I read about them online. Interestingly, there are lots of websites offering ratings of VOIP providers, but they all seem to be phony sites funded by various VOIP companies. 

Originally I would have assumed that someone having problems like mine would probably have some soundcard driver issues. But I used one Gateway desktop computer, a Sony Vaio laptop, and now use a ZaReason desktop computer designed for Linux, that came with Ubuntu preinstalled. So I no longer think my problems are unique to a particular computer. And to make matters worse, sometimes I&#8217;ve tried making minor tweaks, such as switching the output device in Ubuntu&#8217;s Sound utility, and that has sometimes majorly messed up all sound on my computer for weeks or months afterwards&#8212;even though I switched the settings back to their former values. I wonder if maybe someone is playing a cruel joke on all of us with these sound problems. But more likely, it&#8217;s simply that there are only a handful of people who use VOIP on Linux, so even with the wide variety of software and service providers, bugs don&#8217;t tend to get found and resolved. And at the same time, I think there are some fundamental problems with sound in Ubuntu that have never been addressed.

My main findings so far:

**_Softphones:_**

**Bria:** I paid $50, and downloaded and installed it yesterday.
GOOD:  *It basically works all right and has plenty of features  *I was able to set it up for both Diamondcard and CallCentric.
BAD: *Sound is crackly with frequent pops and cut-outs (but apparently the outgoing sound is okay)  *Sends all sound to the speakers, not the headset&#8212;it sets all sound devices to PulseAudio so they can&#8217;t be altered (Skype does this too&#8212;in earlier versions of Ubuntu I was able to use the Sound utility to then set the program correctly for speakers/headset, but not since Unity came along)   *So far I&#8217;m not getting any response to my help request on their forum  *No notification of voicemails  [workaround: just have my VOIP providers send all voicemails as file attachments to my email]

**Ekiga:** {2008}
BAD: *No phone-to-PC calling available *Not user-friendly  *Very few options and settings available
GOOD: *It works well with my USB headset  *I was able to set up a working account on ekiga.net by going to the website  *[on Windows: The program can&#8217;t reach its network.]  

**QuteCom:** {2013}
BAD: *Sound usually shuts off for no apparent reason except for the program&#8217;s internal sounds such as rings  *No notification of voicemails  *Can&#8217;t save a number from call history directly into contacts  *Apparently missing a lot of the settings that are available in Twinkle such as assigning a SIP port  *Doesn&#8217;t seem to allow connection to more than one SIP provider at a time
GOOD: *Mostly works well overall now  *Allows individual selection of headset vs. speakers  *Worked with Diamondcard with no technical setup whatsoever (can&#8217;t be configured for CallCentric because it can only prioritize codecs and not disable them)

**SFLPhone:** {2012, 2013}
GOOD: *Worked right off with Diamondcard, with no technical setup (except disabling sound codecs other than PCMU/8000, and maybe turning off noise cancellation)  *Easy to specify sound devices  *Fast
BAD: *I'm having sound problems in other programs since I started using SFLPhone--perhaps because I opted to circumvent PulseAudio in order to select devices individually?
NOTE: In order to have contacts (a phonebook) in this program, you need a plugin that you can install with Synaptic Package Manager (but not in the Software Store): &#8220;sflphone-evolution&#8221;. You need to have Evolution already installed, with your contacts there. (I don't normally use Evolution, so I just imported a copy of my contacts from a vcf file.)

**Jitsi (formerly SIP Communicator):**  {2009, 2010}
GOOD: *Easy to install  *Very clean and clear user interface  *It allows selecting input and output devices  *Lots of nice features
BAD: *I can't get it to work with Diamondcard, in spite of Diamondcard's own instuctions for configuring it  *No sound

**Skype:** {2006-1013}
GOOD:  *Good sound quality  *Reliable  *Portable synchronized address book shows up wherever you log in  *Chat/IM is built-in  *Automatic encryption of calls without any need for setup  *Conference calls can be set up immediately without having to first visit a website
BAD: *No customer support available, and their user forums are not necessarily helpful  *Can&#8217;t call to regular SIP services  *Voicemails are hidden away in a format not accessible to any other program so you can&#8217;t save them on your computer  *Nobody knows how long Microsoft (Skype&#8217;s new owner) will offer a Linux version  *Difficult and time-consuming sound problems when I install a new version of Ubuntu 

**Twinkle:** {2009-2013}
GOOD: *The most reliable program other than Skype, until recently  *Vast numbers of settings available  *Works well with both CallCentric and Diamondcard  *Automatically finds and connects with any installed Kontact address book (if you&#8217;re into KDE)  
BAD lately: I just stopped using it due to increasing bugs: *It keeps failing to find the headset (about half the time I have to solve this by re-selecting them manually in the audio settings after starting the program; sometimes it still fails after I&#8217;ve done this, so I can&#8217;t use it&#8212;rebooting does not usually solve this)  *Sometimes it fails to make a call, saying that service is unavailable, even though incoming calls are working fine (when it fails to connect to one VOIP service, it also fails to connect to the other; sometimes this can be solved by restarting the program or rebooting)  
BAD all along: *Main-screen user interface is a bit clunky, for my taste

**_Providers:_**

**Axvoice:**  {2012}
Here&#8217;s one I haven&#8217;t tried yet. I haven&#8217;t heard anything bad about them yet so I&#8217;ve left them on my list of potential providers. Apparently they can port a number in. Axvoice: This is one I might try later if I end up not liking Diamondcard at some point. &#8220;We.. provide a free VoIP phone adapter that connects to your router. There&#8217;s a one-time porting fee of $15.&#8221; 

**CallCentric:**  {2008-2013}
GOOD: *Excellent customer service *Great online menus offer simple access to lots of features  *Can port in an existing phone number for call-in service *Voicemail can be accessed either in the program, or as a listenable, downloadable mp3 file from their website, or forwarded to you as email attachments
BAD: *Call quality was inferior to Skype when I compared them in 2008, especially on international calls  *Softphone options are more limited since most don&#8217;t offer all the settings they require  *Call quality is not good enough (choppy and repeatedly cutting out), intermittently but especially on calls to/from non-urban areas or organizations with special internal phone systems

**Diamondcard:**  {2012-2013}
GOOD: *Call quality is better than CallCentric (sound doesn&#8217;t repeatedly cut out while talking to someone in a non-urban location)  *Reliable
BAD: *Website is not well organized so features and information can be hard to find  *Some people online say they&#8217;re a little weird/paranoid (for example, restrictive monthly limits on credit card purchases)--but if you seem like a decent person they can be helpful  *Can&#8217;t dial in/out with users of other SIP providers  *Call quality is occasionally horrible &#8212; mainly when calling people on cheap mobile phone carriers  *They had some difficulty porting my old phone number in--but now that's fixed

**Nextiva:** I haven&#8217;t tried them yet for VOIP.
GOOD: *They can port numbers in and offer new local phone numbers  *They&#8217;re reputed to have good sound quality  *I&#8217;ve been using their web-based fax service and have found it to be very reliable and easy to use
BAD: *More expensive (their least-expensive service starts @ $35/month; there&#8217;s apparently also a $20/month service, but that&#8217;s only only at high volume (dozens of lines); they offer another service (&#8220;Talk In&#8221;?) starting at $16/month, that requires a physical VOIP phone connected to the computer  
QUESTIONS I&#8217;ll ask before signing up: *What do I get for that $35/month? How about international calls?  *Can I make SIP calls in addition to calling landlines?

**Skype:** 
GOOD: *Good sound quality  *Reliable  *Portable address book shows up wherever you log in  *Chat/IM is built-in
BAD: *No customer support is available; user forums often not useful  *Can&#8217;t call to/from regular SIP services  *Can&#8217;t port your phone numbers in or out

**VOIPo:** This is one I might try later if I end up not liking Diamondcard at some point. They send some sort of adapter to connect the computer to a router. Porting a number in: no charge. Doesn&#8217;t require a separate phone line as Vonage does.  voipo.com {2012}

**Vonage:**  {2012}
BAD: *They require a user to have not only a high-speed internet connection, but also a physical phone landline  *They don&#8217;t have the Linux version of their soft phone ready yet
GOOD: They can port numbers in and offer new local phone numbers  *They&#8217;re reputed to have good sound quality, and they&#8217;re fairly inexpensive now

Right now I&#8217;m using the provider Diamondcard, with the SFLPhone. I'm keeping the Bria softphone, the provider CallCentric, and Skype, as my backup options. I might buy a decent desktop microphone to avoid the difficulties of using a headset in Ubuntu

By the way: I'm calling this a poll to invite insights from others out there. It doesn't look like there's a way any more to put a votable poll up on Ubuntu Forums, so I'll just leave it like this.

---

### Post by grashdur on 2013-05-17
One more new phone to add:

**Yate:** (2013)
GOOD: *It works (which is a huge plus, compared to most of the others)  *Simple interface & easy to set up  *Compatible with both of my VOIP providers
BAD: *There's a glitch that makes audio fail whenever you answer an incoming call -- the workaround is that you can press the hold (pause) button twice, and then it works fine
OTHER NOTES: Don't bother with the old versions, which don't work and have ridiculous features (contacts not sorted; no way to close the program). Get the latest version by adding the appropriate repository lines to your Update Manager (as shown on their website), and then find the program again in the Ubuntu Software Center and install it from there.

---

### Post by broomie on 2013-07-15
I struggled with all of teh above with Ubuntu 13.04 with exception of Jitsi whichwas easy to set up and seems to have 

a) working mic (Qutcom - no mic) (SFLphone -souded like dalek)

b) decent mic quality!

Paul

---

### Post by VanillaMozilla on 2013-07-15
Twinkle with DiamondCard has worked fine for outgoing calls for years, but we don't use Twinkle much except mostly to connect to DiamondCard.  No one knows how to call us on VOIP, so we don't even try.  Mostly we use DiamondCard, accessing through their 800 number.  Occasionally they have made a mistake and changed a phone number or something, but we've always gotten in, and they always fix it promptly when I e-mail them the documentation.  Very cheap and highly recommended.  But technically we're not using VOIP much.

Software is easy to use.  Remember to quit if you don't want Twinkle to stay running in memory.

Sound quality on DiamondCard has been consistently very good for international or domestic calls.  Also very good on Twinkle when I have used it.  You may have to pay attention to microphone and speaker gain.  (That's in your system, not Twinkle's fault.  You could occasionally get it very wrong.)  Twinkle has some extras that make it very practical -- feedback control or stuff like that -- I don't remember exactly.

I tried some other programs a few years ago, but Twinkle was the only one that was flawless and reliable.

All of them are just a little too complicated.  All I really want in a phone is the following:  dial, ring, answer, hang up, speak here, and listen here.  Plus maybe a phone book and recharge the account.  They all have a lot of technical choices, unfortunately.

---

