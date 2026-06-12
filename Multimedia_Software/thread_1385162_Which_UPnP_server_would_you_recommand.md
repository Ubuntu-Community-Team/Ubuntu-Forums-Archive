---
title: "Which UPnP server would you recommand ?"
date: 2010-01-19
forum: Multimedia Software
---

### Post by emma_peel on 2010-01-19
Hello forum !

I'd like to start a discussion around the UPnP servers. Which server would you recommand for ubuntu ?

Based on the wikipedia page ([http://en.wikipedia.org/wiki/Comparison_of_UPnP_AV_MediaServers](http://en.wikipedia.org/wiki/Comparison_of_UPnP_AV_MediaServers)), I have short listed the following ones :
- Coherence
- FUPPES : unfortunatly does not seem to be available on the repositories
- MediaTomb
- MythTV : but in the UPnP sever is only a small part of the whole package
- Serviio

Do you see any additional options ?

Thank a lot for your feedback.

---

### Post by Shhnap on 2010-01-19
Um can I state that as a developer of fuppes who has currently packaged fuppes that It might be on the repositories sooner than you think. :) So don't discount fuppes just because of that. If you want to know more about packaged fuppes see my post on the matter: [http://massaioli.homelinux.com/wordpress/?p=7]("http://massaioli.homelinux.com/wordpress/?p=7")

And obviously I say use fuppes. :) It's awesome. I liked it so much that I now help develop it.

Edit: Though, in the spirit of debate, you did forget 'PS3 Media Server' and a few minors. Still, give fuppes a try if you have not already.
Edit2: Normally I would give reasons for my statements, but it seems a bit biased (and vain) for me to be pumping my own development up. I'll let somebody without bias talk about fuppes though if no-one does then I will weigh it's pro's and cons.

---

### Post by emma_peel on 2010-01-25
I'm currently testing FUPPES and it clearly looks promising. I will let you know after a couple of days of use.

I have seen that you are very active on the threat explaining how to install it on the Ubuntu karmic Koala 9.10.

If the application could be one day available using the package manager, that would be terrific, even if the howto, it has been a piece of cake.

I did not select UPnP server with "PS3" or "XBOX" in the name, as I wanted to evaluate only general server. Even if I assume those program will stream media for any kind of terminal.

---

### Post by emoguitarist06 on 2010-01-25
How do I install Fuppes? I want to stream videos to my xbox360. And I don't know anything about compiling.

---

### Post by emma_peel on 2010-01-26
> **emoguitarist06 said:**
> How do I install Fuppes? I want to stream videos to my xbox360. And I don't know anything about compiling.

I have followed the how-to described in this thread :

[http://ubuntuforums.org/showthread.php?t=1310511](http://ubuntuforums.org/showthread.php?t=1310511)

It worked at the first time. The howto is excellent, but the installation is somehow complicated, more complicated than a simple aptitude install.

---

### Post by Shhnap on 2010-01-26
Yes we are working on making it a simple aptitude install. That's what you can read about if you click the link I provided above.

---

### Post by sjhupp on 2010-01-26
A friendly install would be great.
Also, the wiki has some feature requests including resizing (as part of transcoding).  Is this likely to be implemented?
I have in our house a few devices (xbox1, xbox360, PSP, iphone etc) and would love to be able to stream to each with different profiles.  If I read correctly I can based on IP address (fine), but some (like a PSP) require transcoding as well as a specific res.  If Fuppes could do this it could serve almost any device, and be fantastic.

---

### Post by emma_peel on 2010-01-27
> **sjhupp said:**
> A friendly install would be great.
Also, the wiki has some feature requests including resizing (as part of transcoding).  Is this likely to be implemented?
I have in our house a few devices (xbox1, xbox360, PSP, iphone etc) and would love to be able to stream to each with different profiles.  If I read correctly I can based on IP address (fine), but some (like a PSP) require transcoding as well as a specific res.  If Fuppes could do this it could serve almost any device, and be fantastic.

Looks possible :

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Device_specific_settings](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Device_specific_settings)

---

### Post by sjhupp on 2010-01-27
Yeah, looks like different devices is supported, and if fuppes just calls ffmpeg to transcode, I assume it can resize also (have an ffmpeg line to encode for psp already that I sometimes use!).
Sure there's more to it than that though :p

---

### Post by Zerauskire on 2010-02-01
I currently use Mediatomb which is awesome by the way. Fuppes sounds really cool though. My main problem with Mediatomb right now is the fact that I can't get it to work with my Xbox 360 but my ps3 works just fine with it. It's also a little spotty with transcoding. If you guys could get your stuff in the repositories then I would probably switch.

I didn't see anything on your site that specifically says it but I was wondering if Fuppes can stream over WAN or just over LAN? Right now with Mediatomb I don't believe I can stream to my Laptop while i'm at work from my server at home. I would like to be able to do this. I can do this with TVersity but that requires a Windows server and I no longer have one.

Also another REALLY great idea that I brought up to the Mediatomb devs but they seem to have just ignored me was this. I think it would be VERY user friendly and awesome if you guys made a config wizard on your site. Something with like boxes you fill in and drop downs etc. It would ask things like do you want to transcode? Then what file types? Then will you be streaming to an XBOX 360, PS3 etc... What's your local IP. Blah blah blah etc etc etc... Then once all that is complete it compiles a config file for you and you just download it and drop it in your fuppes directory. This would make things so much easier and I know everyone would love it.

I got the idea because i've had to do this at work before for customers to create config files for their routers. I just made a PHP based site that customer's went to and filled out all of the things they wanted such as port fowarding etc and then when they were done it created a file for them, saved it in their directory and allowed them to download it. Now I made it store the file for them just for backup purposes incase something went wrong down the line. You wouldn't need to do this. You guys could just make it spit out text to the page and people copy and paste it. You could also go a whole other route and not even do it web based. I only suggest web based because it would be easier for you to maintain and no approval process would be needed to update it for repositories.

I'm telling you, one of the biggest issues aside from not being in the repositories for people is the config files. To a lot of people they can be very confusing. Take this out of the mix and you're easily a step ahead of the rest of the competition.

Another idea could be just to build this wizard in to your web interface that you guys have already built for Fuppes itself.

---

