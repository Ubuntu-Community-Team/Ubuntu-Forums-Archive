---
title: "Probably dumb post of the day, Mythstream not working"
date: 2009-09-16
forum: Mythbuntu
---

### Post by drifting on 2009-09-16
For a while now Mythstream has not worked, not a show stopper,just meant I fired up something else to listen to smooth jazz on SKY.FM.

So does it work in 9.04 is the burning question? And the other point I always wanted to ask, does it use the back end for anything? Thought it was all being done on the frontend?

Regards

---

### Post by azmyth on 2009-09-16
I have mythstream working on 9.04. I had it working under 0.21 and now trunk. You have to watch the mythstream page as parsers change.

---

### Post by drifting on 2009-10-04
Ok, to follow on from this, I was messing with a new install, and Mythstream does not appear to work right from the word go, so am I right in assuming that the Mythbuntu current release is broke too ?  

Paul.

---

### Post by rickyble on 2009-10-05
Yes it is broken from the get go.  I worked on it for about 2 weeks making all sorts of changes but I finally got it to work.  You will find a lot of posts with "definitive"  answers for what is broken but I dont think that there is one single problem but multiples.  I am out of town right now but if you would like I can work with you when I get back and tell you exactly what I have done and tell you my settings.  Its a real shame it keeps breaking but it is what it is and just another reason mythbuntu and mythtv are not really ready for prime time mainstream.  I love it but you really have to work at it to keep it all running.I dont mind but thats just me.  The new parser is the first step so download it and copy it into your usr/share/mythtv/mythstream/parser subdirectory(not sure about the exact directory names but you can browse to find it).  Also I went to the mythstream page for mythtv and I think it was there I found a suggestion to drop a table and let it rebuild in mythtv.  That was the last step and it worked after that.  I play the streams on a backend with multiple frontends.  I had the same problems with mythweather and have just got it working.

---

### Post by tgm4883 on 2009-10-05
> **rickyble said:**
> Yes it is broken from the get go.  I worked on it for about 2 weeks making all sorts of changes but I finally got it to work.  You will find a lot of posts with "definitive"  answers for what is broken but I dont think that there is one single problem but multiples.  I am out of town right now but if you would like I can work with you when I get back and tell you exactly what I have done and tell you my settings.  Its a real shame it keeps breaking but it is what it is and just another reason mythbuntu and mythtv are not really ready for prime time mainstream.  I love it but you really have to work at it to keep it all running.I dont mind but thats just me.  The new parser is the first step so download it and copy it into your usr/share/mythtv/mythstream/parser subdirectory(not sure about the exact directory names but you can browse to find it).  Also I went to the mythstream page for mythtv and I think it was there I found a suggestion to drop a table and let it rebuild in mythtv.  That was the last step and it worked after that.  I play the streams on a backend with multiple frontends.  I had the same problems with mythweather and have just got it working.

Yea, blame Mythbuntu and MythTV for a 3rd party plugin. I think I'll blame Toyota for my after market stereo I put in.

---

### Post by rickyble on 2009-10-05
Its part of it.  Its listed in the configuration console.  If it doesnt work it should be removed.  Its the same thing as everyone complains about with Windows.  No difference.  And if I buy an aftermarket radio for my car that is suppose to work and is made for it then yes I would blame someone.  Im just saying most people who want to have and use something like this dont have the know how to dig around.  Thats what makes it main stream or just a novelty.  Until the average person can download it and install it then its not ready for primetime no matter whether people can admit or not.

---

### Post by tgm4883 on 2009-10-05
> **rickyble said:**
> Its part of it.  Its listed in the configuration console.  If it doesnt work it should be removed.  Its the same thing as everyone complains about with Windows.  No difference.  And if I buy an aftermarket radio for my car that is suppose to work and is made for it then yes I would blame someone.  Im just saying most people who want to have and use something like this dont have the know how to dig around.  Thats what makes it main stream or just a novelty.  Until the average person can download it and install it then its not ready for primetime no matter whether people can admit or not.

Guess what, Mythstream support dropped from Mythbuntu 9.10. Your wish is granted.

---

### Post by joshoekstra on 2009-10-06
Bummer :S
I liked it, but I don't have enough programming experience to make it work :S
The original author is rewriting mythstream as I can gather from: [http://home.kabelfoon.nl/~moongies/streamtuned.html](http://home.kabelfoon.nl/~moongies/streamtuned.html)
Seeing that it's pretty close to release I won't expect any change, but maybe there's an option to make it available after realease? Via a ppa or something?

---

### Post by tgm4883 on 2009-10-06
> **joshoekstra said:**
> Bummer :S
I liked it, but I don't have enough programming experience to make it work :S
The original author is rewriting mythstream as I can gather from: [http://home.kabelfoon.nl/~moongies/streamtuned.html](http://home.kabelfoon.nl/~moongies/streamtuned.html)
Seeing that it's pretty close to release I won't expect any change, but maybe there's an option to make it available after realease? Via a ppa or something?

We could put it on the -testing PPA, but don't count on it if we are going to be blamed for it's shortcomings.

:EDIT:

I take that back, it can't live on the -testing PPA because it needs to be built every time MythTV is built. So if it's on a PPA, the PPA also has to have MythTV on there as well.

---

### Post by joshoekstra on 2009-10-06
hmmm :s
I can see your point, maybe later then.
Hopefully halfway .22 or sooner it's up2date...

---

### Post by drifting on 2009-11-23
> **tgm4883 said:**
> Yea, blame Mythbuntu and MythTV for a 3rd party plugin. I think I'll blame Toyota for my after market stereo I put in.

Laugh out loud, what a gem of a reply, nearly fell off my chair.

Well I got it going fine by just adding the parsers, I love Mythbuntu to bits, would be lost without it, and the shortcomings are a problem that happens with age ;-) 

Paul

---

### Post by drifting on 2009-11-23
> **tgm4883 said:**
> Guess what, Mythstream support dropped from Mythbuntu 9.10. Your wish is granted.

Oh bugger, that was one of my favourite things! Oh well, cling on to the old version of Myth for now.

Paul.

---

### Post by azmyth on 2009-11-23
Someone fixed the code to make it work for 0.22. The patches can be found over at google code. I just use it for shoutcast so I only applied those patches. This'll mean that you'll have to compile mythstream.

---

