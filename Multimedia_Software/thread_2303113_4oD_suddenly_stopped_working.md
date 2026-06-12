---
title: "4oD suddenly stopped working"
date: 2015-11-16
forum: Multimedia Software
---

### Post by Ddamia on 2015-11-16
Hello,
I'm on a fairly new (month-old) install of 14.04. I installed HAL and everything was working fine until about a week ago, when I last watched 4oD. Went to watch something yesterday, nothing. The player itself won't even load. I just get the grey background. It is also impossible to access the flash player settings on the macromedia site. I just get the background and an endlessly loading page. 

Nevertheless, I've followed other guides of wiping the adobe cache -- which for some people seem to solve the problem -- but in this case, nothing doing. 

Has anyone got any ideas?

Cheers!

---

### Post by ueter on 2015-11-17
Hi,
I'm having identical issues with Debian & Arch.  Grey image, Flash not even loading.
 
 
 Trailer clips work (including Flash settings)
 [http://www.channel4.com/programmes/homeland](http://www.channel4.com/programmes/homeland)
 
 but main episodes do not
 [http://www.channel4.com/programmes/homeland/on-demand/61766-006](http://www.channel4.com/programmes/homeland/on-demand/61766-006)
 
 This was working fine about a week ago.
 
 
 Channel4 say  
 “Some of our Flash video (mainly short-form clips on All4.ccom and E4.com) is delivered using the Brightcove platform...”
 
 I guess the Brightcove stuff maybe OK, but whatever the other platform is, Channel4 just broke it (again!). ](*,)
 
 
 Upgrading to the latest Flash 11.2.202.548 from .540 made no difference.
 
 Peter

---

### Post by Ddamia on 2015-11-17
Wow, you're right. The trailer clip works. It hadn't occurred to me to try them.

But the macromedia Adobe site still isn't working for me. So I can only assume something's wrong with flash on my end too. It does something very strange. It shows the background and seems to be constantly loading, but sometimes, if I hit enter again to reload the page, for a moment the full page appears and then disappears again, because obviously I told it to reload. This only happens sometimes, however.

---

### Post by ueter on 2015-11-17
This should be working
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html)

And some drm tips here
[https://helpx.adobe.com/flash-player/kb/protected-video-content-play.html](https://helpx.adobe.com/flash-player/kb/protected-video-content-play.html)

But even with all that working (I can see the Getty steam train video), something definitely broken now at 4oD.

---

### Post by Ddamia on 2015-11-17
The macromedia site managed to load after *literally* around 10 minutes.

I followed the instructions in the second link and the Getty train video works fine. 4oD still doesn't work, though, as you said.

---

### Post by MZ250Supa5 on 2015-11-21
I'm also having issues with this, and Demand 5 too - I even e-mailed 4od and complained, only to receive an assurance that they do take Linux users into consideration... Yeah, right!  Once again it's the whole paranoia thing that means they foul up things with DRM software etc, all in a pretty vain attempt to stop people downloading their content.  Heck, the BBC are under exactly the same constraints, but don't seem to make any real effort to thwart users of get_iplayer, which they don't seem to help either, as every once in a while that stops working, but due to it being a community thing is never really disabled for more than a few days before a fix is issued.

I'm guessing that the logic is that if it's fine for users of Windoze and Mac, then all is fine, and stuff the saner types who use Linux systems. Perhaps we all need to write to Channel 4 and make our feelings known. Much of the problem is that Flash is still used, as these sites haven't yet upgraded to H.264 or more modern, open media standards due to the DRM issue, as open standards seem to be less friendly to the use of DRM.  Eventually they'll probably have to take a very different stance, rather like iTunes had to do with DRM protected content.

---

### Post by Ddamia on 2015-11-22
> **MZ250Supa5 said:**
> I'm also having issues with this, and Demand 5 too - I even e-mailed 4od and complained, only to receive an assurance that they do take Linux users into consideration... Yeah, right!  Once again it's the whole paranoia thing that means they foul up things with DRM software etc, all in a pretty vain attempt to stop people downloading their content.

Did they actually admit that there's something wrong? Any indication that they might fix it? Or did they just assert that they take Linux users into consideration, without any actual evidence for this?

> **MZ250Supa5 said:**
> Perhaps we all need to write to Channel 4 and make our feelings known. Much of the problem is that Flash is still used, as these sites haven't yet upgraded to H.264 or more modern, open media standards due to the DRM issue, as open standards seem to be less friendly to the use of DRM.

However, even DRM protected Flash does work for us, as long as we have HAL installed. It just suddenly stopped working for 4oD. (I haven't even tried Demand 5, since I don't watch it).

---

### Post by ueter on 2015-11-23
> **Ddamia said:**
> (I haven't even tried Demand 5, since I don't watch it).

Don't bother!  Demand5 needs Flash minimum version 15, so is Windows/Mac only I'm afraid:(

---

### Post by Ddamia on 2015-11-23
> **ueter said:**
> Don't bother!  Demand5 needs Flash minimum version 15, so is Windows/Mac only I'm afraid:(

Fabulous. (Though we're not missing much, that's not the point).

---

### Post by davdo2004-yahoo on 2015-11-28
TVPlayer is still working ok which has most of the freeview channels on. [https://tvplayer.com/watch/](https://tvplayer.com/watch/)

---

### Post by Ddamia on 2015-11-30
Unfortunately that's only good for watching live. There's no catch-up/on demand. And I only watch catch-up. 

I can only assume no one's found a way to sort this yet, eh?

---

### Post by MZ250Supa5 on 2015-12-02
The reply from Channel 4 was a little indignant that I dare suggest that they are not supporting users of Linux. I think it was just the default kind of **** covering that happens when someone dares to suggest that they don't take their user base seriously.  Perhaps if more government agencies started to use Linux on their desktops, (and save the taxpayer huge sums in M$ licence fees) Linux OSes might be better known and less easy to ignore.  

@ davdo2004-yahoo - TVPlayer might be a great thing, (if live TV is your thing) but we are talking about online catch-up services that you don't (at present) need a licence to watch. I haven't really watched live TV as it is broadcast for about 4 years, and I particularly liked to watch online as I can usually find a way of blocking most of the advertising which I find both irritating and pointless - if capitalism is going to rely on people like me it's truly doomed!

It may well be that Demand 5 isn't much of a miss, (but then neither is 50% + of BBC output) and the decision to start using Flash 15 must surely have something to do with the unhealthy obession that broadcasters seem to have with DRM, which probably causes more problems than it solves. Approach Demand 5 and they seem to suggest that I'm somehow lacking somewhere because I don't use a 'mainstream' operating system on my computer - but I bet they run all their streaming service servers on Linux! The BBC seems content to ignore the existence of get-iplayer, but then I guess that the fact that it's command line driven will put off 95%+ of people out there - Mac and Windoze users in the main. I don't actually regard 4OD as being that much better than Demand 5, as they seem to take an equally sensationalist, (as well as slanted, and incorrect)  approach to social security recipients, which is the main reason why I want access to those channels.  Looks like I'm going to have to boot up my only system that has Windows on it... still, it does need the cobwebs blowing out, so that might actually be a good thing!

---

### Post by ueter on 2015-12-08
> **Ddamia said:**
> I can only assume no one's found a way to sort this yet, eh?

I gather it may be possible via Windows Firefox under Wine, but I have not tried this myself. Has anyone else here?

From a 'Homeland' page source
[http://www.channel4.com/programmes/homeland/on-demand/61766-008](http://www.channel4.com/programmes/homeland/on-demand/61766-008)
[http://www.channel4.com/static/programmes-bips-flash/flashVersion.js](http://www.channel4.com/static/programmes-bips-flash/flashVersion.js)

I find
var flashVersion = '12.35.0';

As Flash for linux is stuck at version 11, this is probably the issue.

---

