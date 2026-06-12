---
title: "DVD upconverting software"
date: 2008-12-28
forum: Multimedia Software
---

### Post by slapshots on 2008-12-28
Hey, I'm primarily using my computer as a HTPC right now, and was wondering if there was any software out there that could "upconvert" avi files or DVDs. Basically I want my computer to work like one of those DVD upconverting players that cost way to much money at bestbuy. Something that works as the movies is playing would be preferred, but something that works through the movie and saves it in HD would work too.

---

### Post by cariboo on 2008-12-28
You can never make your source better than it already is. If you have a decent LCD or Plasma TV you will see how bad the picture quality is just converting an avi file to dvd. The reason it doens't look to bad on your computer is the small screen size, as screen size goes up picture quality gets worse.

Now that price of a dvd player that upconverts is less than $80.00 Cdn, I'm thinking about trying one, and if it doesn't work as expected, it can't be any worse than the dvd palyer I have now.

Jim

---

### Post by scoobymad555 on 2008-12-28
Just my opinion based on what i've seen and heard ....

Could be wrong but i think you're referring to "upscaling" technology rather than "upconverting". If you try to convert / enlarge a source like for example a standard dvd which sits at a resolution of 720x576 to a resolution like 1080p which is 1920x1080 what you actually get is to all intense and purposes a 'pixel zoom' effect. Results being that it normally looks blocky and mostly naff in bad cases or just annoyingly poor quality in good cases. Also, the bigger the screen you fire it onto, the worse it will appear.

Quite a lot of the sources from 720p upwards usually carry more data than is actually required by the player and generally gets ditched rather than displayed though. "Upscaling" technology makes use of that unwanted data plus 'intelligent' software and specific hardware to try and fill in the missing bits of data by effectively guessing at what colour the pixel next to it should be. It's essentially attempting to re-encode on the fly at the same time as guess what the missing bits are for want of a better description.

So far the only hardware i've used that's made a reasonable effort at upscaling a low quality source (420p satellite feed) onto a decent sized screen (50" pioneer) was a yamaha a/v amp but, 1) it won't upscale from an hdmi source so don't plan on upscaling dvd's from it lol and 2) at the time of purchase (about 8 months ago now) it retailed at £3200 so certainly wasn't cheap! Wouldn't have a clue what the lower priced ones are capable of at the moment but tbh i don't think i'd hold my breath for a winning result .... always nice to be proven wrong on things like that though! ;)

Personally i'm not sure i'd even attempt to upscale via a pc without a decent spec graphics card that had its own gpu's on it at the moment though since i suspect you'd struggle to get a decent data throughput with a software and core cpu solution. I'd expect the results in playback to be either extremely "stop/start glitchy" or possibly even chunks missing as it dropped frames to try and keep up with the required output speed. (remember that a 1080p output is 3x or more bigger than a dvd one in terms of actual data)

As far as i'm aware the new generation of graphics cards with gpu's on them aren't supported under linux yet though since they seem to have been developed with m/s's new directX technology in mind so might be a while yet for that unfortunately :( That said, there doesn't seem to be anything that can't be done with linux (least not that i've found so far lol!) so one of the other guys on here may be able to point you in the direction of some software that will do what you want .... if there is some out there i'd certainly expect it to be pretty resource intense on your system though :S

Personally, my tactics currently are get as higher quality source as i can in the first place and then basically live with the results from there. One thing you can try doing to make the picture look a little better if you're using a pc plugged into the screen as a playback device is lower the pc's output resolution to something like 1024x768 which is only slightly above a dvd's native resolution (it's not perfect but i've had reasonable results by doing that). Does of course mean you have to raise the resolution back up again if you want to watch an hd source though.

---

### Post by slapshots on 2008-12-30
Ahh, found out that VLC has a "sharpen" feature that works in much the same way an upconverting player does. 

-I find a new feature in VLC everyday

---

### Post by scoobymad555 on 2008-12-31
Good find! lol! Had a quick look at it - it actually increases the contrast levels of adjcent pixels so the visual effect would probably in most cases appear like an upscaled image. Only thing you may find is some frames may look a little "funny" around the edges of focused detail in them but i guess that'll also depend on how aggressive you configure the filter to work :)

There was also a feature in 0.86a of vlc called swscale that was an upscaling filter working on nearest neighbour principles intended to be used in transcoding processes but i think it was removed due to being unreliable .... don't know if it's been reintroduced yet though as i don't really use vlc "in anger" that much :S

---

