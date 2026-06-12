---
title: "Netflix issues - Xubuntu 14.04 w/latest Chrome"
date: 2015-04-19
forum: Multimedia Software
---

### Post by RallyDarkstrike on 2015-04-19
Hi all!

Now, this could just be the computer itself, but I wanted to make sure there wasn't something I was missing that was affecting it. I have an old desktop here at home running Ubuntu 14.04 and the latest version of Google Chrome downloaded from Google's website.

The computer is an older one, so not great, but it surpasses the Silverlight minimum system requirements for running Netflix on Windows (1.6ghz, 512mbs RAM), so I assumed it SHOULD be able to run Netflix on Linux through Chrome. I KNOW it can't do HD, as it is an older system, but it should be able to stream normal-def just fine. The system is a 2.8GHZ single-core Pentium 4 with 2GB of RAM and a 128MB ATi Radeon 9250 video card, so, like I said, not great, but ok enough for most stuff.

I have a 20mbps Download speed on my internet connection, and a 2.0mbps Upload - I can stream HD fine from other sites on my other computer, so I know it's not my internet connection.

When trying to run Netflix in Chrome, video is REALLY choppy/laggy. Sound is fine. Previously video was set to 'Auto' in my Netflix account settings, but I forced it to 'Medium', then to 'Low', thinking it would play a little bit better. Oddly, it plays EXACTLY the same on any of the settings, the same amount of choppiness and glitchiness. This is what makes me wonder what the issue is...? If it were just the fact it's older, less capable hardware, I would think lower settings would let it run at least a little better, but the settings seem to make no difference.

Any other Linux Netflix users out there have any suggestions. As I mentioned, I KNOW it can't do HD, and I don't care if it can, just curious why it can't seem to steam normal-def through Chrome ok.

Thanks for any ideas or suggestions! :)

---

### Post by kerry_s on 2015-04-19
did you try additional drivers ?

---

### Post by RallyDarkstrike on 2015-04-19
Hi - thanks for the reply. There are no proprietary drivers in use, and search doesn't find any available when I click on "Additional Drivers." A quick web search says that there are no newer drivers for this vid card in later versions of Linux...?

---

### Post by kerry_s on 2015-04-19
you try disabling the composting under window tweak ?

---

### Post by RallyDarkstrike on 2015-04-19
Just did, disabling it makes no difference, sadly :(

---

### Post by mc4man on 2015-04-19
Don't have netflix but am curious - 
You mention another (better?) pc, does netflix work ok on it?
Can the pc in question play streams ok from other sites like youtube, ect?  ?And if so at what point rez/bitrate does it begin to not be ok?

Does this netflix 'vid' show you anything useful?
[http://www.netflix.com/WiMovie/70136810?trkid=439131](http://www.netflix.com/WiMovie/70136810?trkid=439131)

---

### Post by RallyDarkstrike on 2015-04-19
My other computer plays it fine. The other computer is my personal  Windows 7 desktop. (To show that I am Linux faithful, my netbook runs  Mint 17.1 MATE and all my other computers run Xubuntu 14.04! ;) ) Truth be told, the system in question I am trying  to see if Netflix works on it's an old system I had around that I know  is fine for a basic computer use and I was using it as a spare for  awhile. This all started but I put it up on a local classified site to  sell it and a lady contacted me asking if it can handle Netflix. I KNOW  it can't do HD, but as I've never had a Netflix account, I thought I'd  create a 30-Day Trial and see if it can handle it before I told her yes  or no. I didn't really think it could, but after looking at the sysreqs  for Silverlight on Windows which are quite a bit lower than this  computer's specs (as mentioned above 1.6ghz, 512mb RAM for Silverlight  while the comp in question is 2.8ghz, 2GB RAM), I thought, I may as well  try.

The PC in question can play streams from Youtube fine on  normal resolution in Firefox - anything higher than 480p and it starts to get  choppy on Youtube - that's why I thought it should be able to do  normal-res streams of Netflix half-decent. However, Netflix doesn't work  on any other browser in Linux than Chrome because apparently Netflix  won't support anything else I guess. I had Firefox on the comp as the  main browser as it is my preference but trying to select a video to play  in Netflix in Firefox leads to it just loading some sort of "These are  the minimum requirements to watch Netflix" page instead of playing the  video. I tried installing Chrome just to see if Netflix would work - I  think my problem may be partially some rendering issue with Chrome,  because loading any webpage, there seems to be weird "choppy" rendering  issues. Like, you can sort-of notice it even if a basic webpage like  Google is loading. It loads quickly, as it normally would, it's just the  way it looks as it loads over the few seconds is odd....hard to  describe unless you see it...things that fade in, for example, aren't  smooth....that sort of thing. For the record, everything in Firefox,  like fade effects, etc, are smooth. Youtube videos on Chrome on the  machine are choppy as well, but run fine in Firefox? Definitely thinking  it's some sort of Chrome issue...?

Would Chromium make a difference instead?

---

### Post by kerry_s on 2015-04-20
only chrome can do netflix, chromium can not.
it should be able to do netflix easy, your specs are higher than mine & i can do netflix fine.
it has to be some issue with the pc itself, my moneys on the vid driver.

i just got this netbook from mom, the hd gave out, so i just traded her my laptop, got the upgrades on order.

---

### Post by mc4man on 2015-04-20
Sounds like something in chrome. Maybe it doesn't work well with older hardware. Again I hardly ever use it (even in android, Dolphin is better). Maybe look in or compare with others - 
chrome://flags/
chrome://gpu/

---

### Post by monkeybrain20122 on 2015-04-21
I think Chrome uses html5 for netflix. If your system is old hardware acceleration is not available html5 is not great. As a test you can go to Vimeo and see how it performs.

---

