---
title: "USA Pinnacle PCTV HD 800i PCI - no channels, no scan, wtf!"
date: 2008-08-29
forum: Mythbuntu
---

### Post by slickware on 2008-08-29
Alright. So, I have no idea what I am doing.
I just set up the alpha release of mythbuntu, and I have a PCI 800i (pinnacle PCTV HD) card.
I'm in the USA, and I have Comcast cable - my TV can tune into regular (digital) channels, as well as a few HD channels.
I am assuming I want to watch digital cable with my 800i card, so I have the capture card set to be DVB.
Here's my cap card settings:
[I]card type: DVB DTV capture card v3x
device number: 0
fontend ID: Samsung S5H1409 QAM/Subtype: ATSC
timeout: 3000
tune timeout: 5500[/I]

Now, every time I do a channel scan in the Input Options, I get NOTHING. I have it set to use EIT or ScheduleDirect.
On the Scan Configuration page, I have:
[I]Video source: EIT
Input: DVB:0 (DVB Input)
Scan Type: Full SCan
Freq Table: Broadcast
Modulation: Terrestrial 8-vsb
ATSC Chan separator: 5_1
channel treatment: minimal updates.[/I]

When I run this scan, I get:
[I]Status:Scanning ATSC channel X
No Lock
SignalStrength: 0%
Signal Noise: 0%
Scan: %(fills slowly)[/I]

No matter what options I choose on the previous page, I seem to always end up with 0% signal. I've tried the QAM options and everything. I even tried running the scan in Kaffeine, but the scan button just goes grey once I press it, and it hangs.

WTF!? Can anyone help, seriously? I have no idea what my settngs are supposed to be, and I can't find documentation of anyone having any issues getting signal!

---

### Post by slickware on 2008-08-29
Update:
I found an input scan that actually produces results.
I set it to Cable-IRC-High and QAM128, and it scans channels 76 through 118.
I wasn't even aware I had those channels... and apparently I don't, really, because when I tune in to them, 95% of the time, the frontend will crash or give an "error with display" notice before blackscreening.

I can't seem to get any channels below 76.

---

### Post by slickware on 2008-08-30
Really? Nothing?
Isn't there anyone from the US who has this card, and got a channel scan to work using digital cable?

---

### Post by jmore9 on 2008-08-31
I used me-tv and the regular cable-Qam preload that is in dvb-utils in the repos.  It scanned the channels and displayed what it found.  Never was able to get kaffeine to work .  Me-tv will do its own scan using the preloads included with dvb-utils.
Hope this helps

---

### Post by zarshmogon on 2008-08-31
Hey Slick - I am having similar problems getting the same card to install on fedora 9 with MythTV. Got some analogue channels to tune but no luck with anything digital yet...

In my travels I did notice this thread that might be of more use to an ubuntu user. 

[http://www.avsforum.com/avs-vb/showthread.php?p=13774831&posted=1#post13774831](http://www.avsforum.com/avs-vb/showthread.php?p=13774831&posted=1#post13774831)

Continued here ... 

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/220857](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/220857)

Hard to say if this will help you.

Thanks for the idea on setting the card to DVB and so on - I'm giving that a shot right now. 

-Z

---

### Post by zarshmogon on 2008-09-02
Thought I'd leave another update. I'm having a hell of a time scanning and finding channels with this Pinnacle PCTV HD 800i card. I am using Comcast Digital Atlanta. Scanning with the built in MythTV scanner is pretty hopeless on this card (or I am doing something completely wrong). I found mention of a linuxtv app called dvb-apps which includes a scan utility. I am now trying that to find channels. I'll let you know how it goes. 

How are you supposed to figure out if your provider has QAM64, QAM128 or QAM256? Or even VSB-8 or whatever? 

Then there's the question of how I get access to digital AND analogue channels. 

I tried grounding my feet and sticking my tongue on the end of the cable but the clue meter is still reading zero :-)

-Z

---

### Post by slickware on 2008-09-02
> **zarshmogon said:**
> 

How are you supposed to figure out if your provider has QAM64, QAM128 or QAM256? Or even VSB-8 or whatever? 

Then there's the question of how I get access to digital AND analogue channels. 

I tried grounding my feet and sticking my tongue on the end of the cable but the clue meter is still reading zero :-)


OH. MY. GOD.
I have been wondering the same thing, and finding the answer to those questions is like searching for the holy frigging grail. If you figure this out, not only are you my hero, but you're a mastergoogler as well.

Also, try blowing and huffing alternatively on the card. It used to work for NES games, back in like 1988.

I am giving this issue about one more day, and then I am buying a HomeRun thing, because apparently that just works, out of the box.

---

### Post by bmwman on 2008-09-02
> **slickware said:**
> OH. MY. GOD.
I am giving this issue about one more day, and then I am buying a HomeRun thing, because apparently that just works, out of the box.

Not to discourage you but certain TV tuners just have issues and not really easy to get em to work. I was having issues with Hauppage HVR 1800 which was supposed to work but it didn't and after few days i just gave up and returned it. I'm really happy with my HDhomeRun now which of coarse cost twice as much but it's a dual tuner so it's still the same after all if you're looking to have 2 tuners.

Have you tried loading the mercurial drivers? That supposed to be the latest and greatest driver? It may work.

---

### Post by slickware on 2008-09-02
I tried mercurial on the current stable version of Mythbuntu, and after installing that and updating to the newest kernel, the machine would hang at boot. 
Tried 3 times, same results.

---

### Post by zarshmogon on 2008-09-04
I'm having better luck finding channels following the instructions on [this site]("http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards"). 

I did get a couple of channels to work when I used the MYTHTV scan (QAM256 and CABLEHRC) but it also found a lot of duff channels that crashed MythTV frontend. I found far more with the above procedure. Now I just need to make the channels.conf file and import that into Myth. 

BTW to import a channels.conf file you have to hit the "scan for channels button" then change the scan type to import channels.conf. If they had been really trying they'd have put it under the "This button will melt your hard drives and kill your dog" button. 
Then I finally have to figure out how I get both digital AND analogue channels working together. 

Then I can watch TV..... weeeellll there's never really anything on anyway is there .....

---

### Post by zarshmogon on 2008-09-06
Last Word: 
I got a few digital channels working as I said above. I then added the 800i a second time as an analogue card [v4l] and scanned seventy or so channels successfully. I discovered I could not tune into all channels successfully until I deleted the digital [dvb] capture card OR deleted the analogue capture card. So I am in an either-or situation, all analogue or all digital..... but MythTV is working and to celebrate I recorded and watched The Usual Suspects last night. 

Perhaps there is a way to get both digital and analogue channels with the 800i in MythTV but I don't know how and nobody is telling. Perhaps [Keyser Söze]("http://www.google.com/url?sa=t&source=web&ct=res&cd=3&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FThe_Usual_Suspects&ei=CW7CSOyWJ4mKgwT5ys3SBg&usg=AFQjCNEKKbUWvFg0C2J1bx2QyqfJLErPgg&sig2=sBuXP_K4IQY-bGjVp1Vafg") has threatened them with a fate worse than death. Of course trying for two weeks to get the digital and analogue channels to play together was similar but lacked the peace I always assume you get with death.

---

### Post by Cruton502 on 2008-09-07
I'm working with the same video card trying to get MythTV working for over-the-air broadcasting.  I however am a complete noob at linux and don't really know what I am doing.  Is it possible for me to get this working or should I just stick with pinnacle's TV program through Win XP?

I would need help on how to properly install the drivers and firmware update because I have no clue on how to do that.

---

### Post by zarshmogon on 2008-09-19
MythTV is definitely worth it once you get it running. Picture quality seems as good on Linux as on Winxp for sure. Then of course there a lot of very nice features in MythTV that the Pinnacle software doesn't touch. Once you get the tv schedules working there are some very powerful record-on-keyword functions. There's also a great "show me every movie coming up in the next two weeks" feature. Great! 

The Ad skipping works fairly well. I seem to remember it didn't even really work at all on Pinnacle software. Then there's a _really_ nice edit feature that takes all the ads out of movies you've recorded. 

I would suggest installing Linux as a dual boot with winxp for now so you can switch back to a working system when you are tired of figuring things out on Linux for the day. 

My biggest problem was following  other  folks "howtos". When you don't know what you are doing and say step 7 leaves you out in the weeds then you are just stumped. I'm sure a lot of places I got stuck would be easy for a real linux jock to figure out but I just don't have the fundamentals. I guess that's how you learn though. I never did find anywhere that really explained the fundamentals. Lots of stuff on how the desktop works but not much on how the low level stuff works. Commands like dmesg & /sbin/service that look like you just hit the keyboard with a dead cat. What do they all mean. I know some bearded guy in a cable knit sweater will refer me to the MAN pages ...... yeah that explains it.

Anyway if you fancy having a go at it these are the links that helped me the most.


[http://www.linuxtv.org/](http://www.linuxtv.org/)

[http://www.tweaktown.com/articles/1022/1](http://www.tweaktown.com/articles/1022/1)
[http://www.avsforum.com/avs-vb/showthread.php?t=1025170](http://www.avsforum.com/avs-vb/showthread.php?t=1025170)

[http://linuxtv.org/hg/v4l-dvb/file/5e73425c1968/linux/Documentation/video4linux/CARDLIST.cx88](http://linuxtv.org/hg/v4l-dvb/file/5e73425c1968/linux/Documentation/video4linux/CARDLIST.cx88)

[http://wilsonet.com/mythtv/](http://wilsonet.com/mythtv/)

[http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards](http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards)

[http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers](http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers) 


I was setting up on Linux Fedora 9 BTW. Why am I on Ubuntu? Wherever I hang my hat mate, know what I mean?

---

### Post by Twintop on 2008-10-12
Hi everyone. I'm having similar problems with my MythBuntu box (currently 8.10 32-bit beta). I'm having similar luck as zarshmogon did initially: I have gotten it so that my card will scan some digital channels with QAM256 and CABLEHRC, but no matter what I do I can't scan any analog channels (which is what I am most interested in doing). Does anyone have any suggestions as to what I might try? Thanks in advance!

---

### Post by Twintop on 2008-10-16
Bumping this thread in case anyone has any ideas. Thanks!

---

### Post by agamotto on 2008-10-16
You are most likely running into the problem of Comcast scrambling all of their digital channels.  I am not sure about analog, but they scramble all digital to force you to rent the set-top box.  In scanning for channels, try:

freq-table:  cable-high (no irc,hrc, etc)
modulation:  qam-256


This may give you some of the pass-through channels, but I wouldn't be surprised that Comcast is scrambling them.

---

### Post by Twintop on 2008-10-17
> **agamotto said:**
> You are most likely running into the problem of Comcast scrambling all of their digital channels.  I am not sure about analog, but they scramble all digital to force you to rent the set-top box.  In scanning for channels, try:
 
freq-table:  cable-high (no irc,hrc, etc)
modulation:  qam-256
 
 
This may give you some of the pass-through channels, but I wouldn't be surprised that Comcast is scrambling them.
 
Yeah, Charter here in Northern Nevada does the scrambling of all digital channels that aren't the broadcadt channels. The settings you suggested are the same as I was using (with limited success) for digital.I'm not paying for Digital with Charter though, just the expanded basic that comes with my Cable Internet (~70 channels) which is why analog would be perferred.I'm thinking about trying a CVS Trunk build of 0.22 next to see if there are any improvements...any thoughts/ideas are welcome still! Thanks!

---

### Post by Twintop on 2008-10-28
Just an update for anyone watching. I tried trunk builds of MythTV 0.22 but had no luck. I did some more searching/probing and found people had out of the box success with openSUSE 11.0 where all that was needed was firmware and drivers. I ran in to some more snags getting it to work on openSUSE 11.0, but was eventually successful. I've detailed the steps [here ]("http://twintopsoft.blogspot.com/2008/10/opensuse-110-on-my-mythtv-box.html")if anyone else is still fighting with getting Analog tuning working.

---

### Post by bobpaul on 2008-11-29
> **zarshmogon said:**
> I'm having better luck finding channels following the instructions on [this site]("http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards").  

BTW to import a channels.conf file you have to hit the "scan for channels button" then change the scan type to import channels.conf.

Grr.. I can do this and watch using mplayer (mplayer dvb://"channel name") but when I point mythtv to my channels.conf, it comes up with no signal. Anyone have this issue?

---

