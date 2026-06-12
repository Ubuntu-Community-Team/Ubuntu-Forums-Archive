---
title: "Motorola DCH3200 - firewire - myth backend"
date: 2007-11-29
forum: Mythbuntu
---

### Post by stiev3 on 2007-11-29
My set top HD box is a Motorola DCH-3200's.  I'm trying to come to a conclusion about whether I should give up the idea that  I could have myth watch HD content through its firewire ports.

Following this guide [https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire) ,
[LIST]
[*]my plugreport checks out(its output matches the tutorial).
[*]my set-top's diagnostic test (holding ok/select after i press power) shows that the firewire port is enabled.  But Active: no.
[*]my ./firewire_tester tests and has 5 failures consistently when connected to one port on the STB.  
[*]The STB's other port results in a test that runs > 10 minutes that I ctrl-c out of (it's never finished).
[*]An AVS forum member who works for the cable company says all boxes are firewire enabled.
[*]Myth doesn't recognize it either.
[/LIST]

What do I do next?  Purchase an OTA card and a fancy antenna?

---

### Post by mbrocketry on 2007-11-29
> **stiev3 said:**
> 
[*]An AVS forum member who works for the cable company says all boxes are firewire enabled.


Not necessarily, I happen to work for a major cable company and the firewire port  is not usually enabled. It depends on the headend (local cable company system) but most systems have the fireware port disabled. Otherwise it would be real easy for you to record digital content direct from the hard drive from the settop box. This is a real issue with content providers so most cable companies have it disabled to reduce risk. I know this is a catch 22 since you and easily record with a tuner card or to a vcr directly through the output ports (composite, s-video etc.) on the back of a settop.

---

### Post by stiev3 on 2007-11-29
Is there a way to easily tell whether it's active or not?  Google leads me to believe this isn't a popular mythtv capable set-top.  In other words, how would I test whether the box's firewire is doing what it's supposed to do on a set-top that might not be supported by the various fire-wire testing scripts in that tutorial?

The representative I spoke to said "If it's enabled but inactive, whatever you're connecting to it isn't working"... which is vague, but a huge possibility because I'm fairly new at MythTV.

The ideal case is one where I can say "Ok this box is working, so it's a problem on my end."  Or "This box isn't working because the cable company hasn't activated it in an effort to make this process a real pain".

---

### Post by mbrocketry on 2007-11-29
If you get Comcast cable, I can almost guarantee that the firewire port is disabled. Motorola settops use either NAS (National access storage) or a DAC (Digital access control) to turn on or off access to services like whether or not you get HBO, Showtime, etc. One of the settings which in Comcast access control is defaulted off is firewire. It must be enabled from this AC device in the headend. This also includes the other ports like the serial interface in which we do diagnostics with when we are testing new services on settops or the usb connector etc. Good chance that it is not enabled unless there was a reason to in the first place.

---

### Post by murchball on 2007-11-30
I have an SA 3250HD and found that firewire_tester failed every time unless I tuner the STB to an unencrypted channel first. In the end, I decided to abandon firewire after realizing that the only channels that were unencrypted were the ones that I could get over the air.

---

### Post by stiev3 on 2007-11-30
So I finally got it working.  I ended up switching to the weekly mythbuntu build, and using the tutorial linked above, so I'm not exactly sure which is responsible for it working.  I may have had the wrong nodes and ports while trying to follow the tutorial.

I was assuming the cable box telling me "Firewire Enabled: Yes Active: No" meant that the company was intentionally blocking this application of their boxes somehow.  But, I guess it means "the firewire is working, just not connected to a properly configured HTPC".

I'm still a n00b, but for whatever it's worth I'll explain what I was doing wrong:

If the box is on an unavailable channel, you need to pick up its remote and flip to a channel you know you have.  Otherwise, I'm assuming it's trying to show its menu, and that may not be available over firewire.

So upon flipping to a channel I know I had, my firewire_tester command started getting responses (via P2P, not broadcast).

After that, I was careful to set my "start channel" in myth to something I know I had.  The one it defaulted to was no good.

Furthermore, if I flipped to an unavailable channel, my frontend would lose its stream.  I would then have to go through the backend and fix where it left off (myth defaults to saving its last used channel - which saves a bad channel should you tune in to one), and I'd have to pick up the set top remote and switch to that channel as well.

So my next task is to go through and remove all the channels I don't have off the list... still reading up on that heh.

---

### Post by newlinux on 2007-12-01
Firewire works for me on all my comcast boxes. I have found over time more and more channels are 5c protected, but I can still get a most of the ones I want...

---

### Post by tgm4883 on 2007-12-01
If you live in the US, then cable companies are required by law to give you a functional firewire port on HD boxes.  Keep in mind that there are other limiting factors like copy-control and such for specific channels (ie, HBO, etc)

From [http://www.mythtv.org/wiki/index.php/FireWire#FCC_regulations](http://www.mythtv.org/wiki/index.php/FireWire#FCC_regulations)
> The FCC has passed a regulation that if you are in the United States, and you have a HD subscription and a HD cable box, they have to on your request replace or upgrade your cable box with working FireWire.

See: Image:Pdf.gif [http://hraunfoss.fcc.gov/edocs_public/attachmatch/FCC-03-225A1.pdf](http://hraunfoss.fcc.gov/edocs_public/attachmatch/FCC-03-225A1.pdf)

Page 50, section 4

(4) Cable operators shall:

(i) Effective April 1, 2004, upon request of a customer, replace any leased high definition set-top box, which does not include a functional IEEE 1394 interface, with one that includes a functional IEEE 1394 interface or upgrade the customer's set-top box by download or other means to ensure that the IEEE 1394 interface is functional. 

:EDIT:

I also noticed that I am able to receive local HD channels with my pcHDTV 5500 over the cable.  No antenna needed.

---

