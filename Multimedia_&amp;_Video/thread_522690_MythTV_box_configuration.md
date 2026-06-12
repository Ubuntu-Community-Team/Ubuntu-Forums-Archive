---
title: "MythTV box configuration"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by n3x on 2007-08-10
Hi everyone!

I'm trying to build a mythTV backend/frontend box out of some stuff I have lying around. I wish I could afford to build a quiet and small frontend, but I can't. Here's what I have:

- 2.8ghz P4
- 512mb RAM
- 120gb HD
- ATI radeon 9800 pro

I used linux (gentoo) regularly a few years ago, but OS X has stolen my heart recently (:oops:) so I have some experience, but none whatsoever building a mythTV-like system (on any OS). My multimedia knowledge is seriously lacking. I've done a lot of reading and lurking and I hope I have this right! So I figure I should buy the following:

- 500gb HD
- Hauppage PVR 150
- some kind of remote/receiver? (need some help here, I think)

Am I missing anything? I'm afraid I'm missing something big, but I don't think so. Again, I can't afford the really good stuff, I just want something basic. This will be used in Canada (that's not an issue with TV listings, right?). So please, any comments, suggestions or criticisms would be greatly appreciated. I'm very excited to get back into linux.

Thanks,
James

---

### Post by balleyne on 2007-08-11
I'm a Canadian using MythTV. I've got it working with standard cable now, haven't ventured into trying digital cable yet. Listings for Canada should be fine (though the current free service provided by Zap2It Labs is ending in September, but MythTV developers have established another organization which will provide listing services for a small fee (read the article: [http://www.linux.com/feature/118505](http://www.linux.com/feature/118505)) - they do mention Canada).

In terms of hardware... I'm running a MythTV server on an old AMD Athlon 1.0 Ghz machine that's 7 years old (replaced Windows 98 with Ubuntu a few months back). It's been working fine for me, though I'm not using it heavily. As a front end machine on one of my televisions, I recently converted an old Pentium III machine which has been doing the trick as well. Haven't bought a remote yet (though I've heard the StreamZap USB remote mentioned - haven't done the research yet though), but what I've found a wireless keyboard very useful on the front end TV I set up. I'd certainly recommend considering it. It might be a good short term option even if you decide to try the remote later on. (It takes zero setup time and I had one available, which is why I haven't looked into a remote yet.)

In terms of a TV tuner, the Hauppage PVR 150 works well. Though I bought the PVR 500, which is essentially the same card but it has two TV tuners. That way two people in the house can be using MythTV at once to watch live television, or one person can watch live TV while something is recording on the other tuner. There's also picture-in-picture. Might be worth considering the 500 for that extra flexibility, but you can always buy additional tuners later on.

500 GB hard drive sounds good too. I'm still running off a 120 GB hard drive right now, though it's been mostly a pilot project so far. I'm planning to buy a 500 GB drive. You can certainly start using it with 120 GB though, you just can't be recording a ton of material, but it's find for some casual use, testing, etc..


Here's something you need to consider though. Are you hooking up the display to a television or a computer screen? The TV I have the front end on right now is our fancy new widescreen HD etc etc TV, so it has a "PC in" at the back. But the only other way, as far as I've found, to really hook up a computer to a television screen is to get a video card that has an s-video out (and a TV that has an s-video in). Just something to keep in mind.

---

### Post by n3x on 2007-08-11
Thanks for the input!  I think my 9800pro has S-video out, I will double check. I just have analog cable so I'm not worried about the whole digital cable complications. I will definitely look into the PVR500, it would be really helpful to be able to watch and record at the same time... I will look into getting a wireless keyboard, that sounds like a really good idea. 

I have some videos that I've downloaded (torrents) which is part of the reason I want a big HD. I assume I'll have to use something like VLC to play these - is that hard to set up? Is this another good reason to have a wireless keyboard/mouse? What keyboard are you using/do you suggest? 

I see you're in TO - I'm studying at Queen's in Kingston.

---

### Post by Scorpuk on 2007-08-11
If the videos are of a format that MythTV supports then you can add them to the MythTV database as a recording.

See this post for details on how to do that: [http://ubuntuforums.org/showthread.php?t=515225]("http://ubuntuforums.org/showthread.php?t=515225")

Try it with one of your downloaded films to see how it copes then add the rest if it works. ;)



(I have yet to try this out myself, but by the end of the month I will be transferring MythTV to a server and will import my currently recorded shows into a blank database to start afresh.)

Its far simpler to keep MythVideo for DVD images than to have a mixture of formats in there. :)



Hope this helped.

---

### Post by balleyne on 2007-08-11
The wireless keyboard I've been using is a Logitech infrared mouse/keyboard pair. It retails for $25-30 I think. I also looked into bluetooth offerings from Logitech (because that way you wouldn't have to point the keyboard at the infrared receiver) and they retailed around $90. I haven't done a lot of resesarch though, just checked a local place that sells cheap hardware, so there might be better deals out there. Bluetooth seems ideal, except I'm not convinced that it's worth the price to serve as a MythTV remote (seeing as standard remote controls are infrared anyways), so I think I'm just going to stick with my infrared keyboard.

One of the other reasons I like the wireless keyboard/mouse idea is for making use of other applications besides MythTV. In MythTV, the mouse isn't necessary and you can just use the keyboard. But when I first setting the machine up, my sister used it to pull up pictures from a trip to Europe on Facebook to show my girlfriend. I'd never really thought about it, but we might get some use out of a fully functional PC on our television (Facebook, youtube, checking the weather, etc etc...). If there was just a USB remote set up, I'm not sure it'd be very useful in Firefox or other applications.


As for downloaded videos, I haven't tried watching any other formats through MythTV, but Scorpuk seems to be pointing you in the right direction there.


I have a ton of friends at Queen's! A lot of people from my high school (De La Salle) ended up going there, most of them are heading into third year now.

---

### Post by n3x on 2007-08-12
I found a Logitech RF remote that I think I'll get -- thanks for the input. It never really occurred to me to use it as a "real" computer either. I think this might  end up being even more useful than I had imagined.

Do you just need the right cables to run sound from the sound card to the TV? Or is it better to hook up computer speakers to the sound card? 

I'm going into my third year (computing, biomed option)! I bet we know some of the same people.

---

### Post by balleyne on 2007-08-13
For sound, my TV has a 3.5 mm headphone jack input for "PC in", so I was able to just use a male-to-male headphone cable to go from line out on my computer to the input on the TV. If you're using s-video, you'll probably have red/white audio inputs, and you can just buy a cable from a RadioShack type place to go line out from your computer to the audio inputs on your TV. (Hope that makes sense, as you can tell I'm not expert on the terminology for these types of cables and inputs)

I think that using the TV inputs would be better than setting up computer speakers, in terms of not complicating the setup unnecessarily. But if you've got some nice computer speakers, that option could certainly work too.

Do you have a Facebook account? You should be able to check my profile to see if we have any mutual friends - [http://facebook.com/profile.php?id=28107284](http://facebook.com/profile.php?id=28107284)

---

### Post by loudestnoise on 2007-08-14
> **balleyne said:**
> In terms of a TV tuner, the Hauppage PVR 150 works well. Though I bought the PVR 500, which is essentially the same card but it has two TV tuners.

How has the picture quality been with the PVR-500? I just built my first MythTV box on Sunday with a PVR-150 and love it, but desire the ability to watch/record two channels at the same time.  I have read on various forums and on the MythTV wiki that the different tuners Hauppauge used on the 500 had some issues. The Phillips' tuners were apparently good, while the Samsung weren't so hot.  Other reports say that with new version of MythTV and newer kernels seem to work much better. Just was wondering what your experience has been. Having paid $120 for my 150 at Fry's I'm gonna return it and get the 500 for $130 on Amazon.

---

### Post by balleyne on 2007-08-23
The picture quality has been fine with the PVR-500. As far as I understand actually, it's using the exact same hardware as the PVR-150, it's just that there are two tuners on the card. So there should be no difference in quality.

And in terms of performance, the card does hardware MPEG encoding (like the PVR-150), so having two tuners still doesn't require much more from the CPU *shrugs*

It's worked well in my experience, but I haven't tried any other cards.

---

