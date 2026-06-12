---
title: "EPG on Frontend, I don't want all the channels!"
date: 2015-08-23
forum: Mythbuntu
---

### Post by Antonio_Carballo on 2015-08-23
This is driving me bananas....

Using the backend's Channel Editor I click the [visible] field to remove the check mark. Thus, the channel is removed from the EPG. I repeat the process for 50+ channels. I go to the front end (different computer from the backend's) and load the program guide but those channels are still shown in the guide.

What is it that I need to do in order to remove those channels from the frontend's EPG? Thanks again for your help.

/AC

---

### Post by hollywoodpete on 2015-08-23
Are you using scheduledirect.org for your EPG? If you are, you need to log onto your scheduledirect account and edit out the channels you don't want. Otherwise they keep populating on your backend.

---

### Post by Antonio_Carballo on 2015-08-24
That's the first thing I did before I started messing with the Channel Editor: edited the EPG at the Schedules Direct's website and removed the channels I did not want.

I have refreshed the backend's EPG to make sure that it gets only the enabled channels. I went to the Channel Editor and those channels were still shown in the list. That's why I decided to make them invisible to the frontend's EPG...

SOLUTION: Finally, I decided to delete a channel from the Channel Editor to see if it removed it from the frontend's EPG. It worked but making it invisible should be enough to remove a channel from the frontend's EPG. This could be a bug.

Thanks for the feedback.

/AC

---

### Post by hollywoodpete on 2015-08-24
"Should" and "Does" isn't the same thing with Mythbuntu. It took me 6 months to tweek it into something usable. I actually gave up on the frontend and use Kodi. I log in with MythWeb to schedule stuff. If that is how you were trying to uncheck the visible box, there is a fix. I will find it and post back.

---

### Post by Antonio_Carballo on 2015-08-24
OK. Thanks for the info.. Look forward your post.

I was using the backend's Channel Editor to deal with the channels. I do use the web interface to manage the recordings. It's much more powerful.

Funny that you prefer Kodi rather than the mythfrontend. The family hated that interface: one too many times the kids went back to the Kodi's main menu while watching TV. Wife veto Kodi sooner than the kids. So, I'm working on new menus using the mythfrontend...maybe in another 6 months I'll present the new interface to the rest of the family.:p

/AC

---

### Post by afremont on 2015-08-24
I tried using mythweb to make changes to the channel stuff, as in Settings/Channel Info, but several of the fields I tried updating wouldn't "stick" such as "Channel Name" and "useonairguide".  I had to go run the back end setup program on myth to change those things.  Is there a list somewhere of the things that won't actually change through mythweb.  Outside of that, I like mythweb, especially for setting up recording schedules.  Kodi isn't real great at that.  Outside of that, I like Kodi.  I have two Raspberry Pi2s and an Amazon Fire TV Stick running it.  The Pis run OpenELEC.  I have kodi on a couple of windows boxes, but just for experimenting and bug testing, I don't really use them for anything else.

---

### Post by hollywoodpete on 2015-08-24
Here is the thread I started when I had a similar issue. [http://ubuntuforums.org/showthread.php?t=2254699](http://ubuntuforums.org/showthread.php?t=2254699)
The fix is here. [http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html](http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html)
Once I fixed MythWeb it became awesome.

I honestly love Kodi. I have it on my phone and multiple devices on every TV in the house. Even my wife tolerates it. I change skins occasionally which makes it interesting.

---

### Post by Antonio_Carballo on 2015-08-24
Thank you for your feedback. I mean that.

I have 2 RPI2s and a Liva box (pretty cool box!). I have been testing and configuring many, many HTPC software products this year. Most are junk but Mythbuntu's backend **works pretty flawlessly;** the frontend needs **a lot of work**---Kodi's plugin is not good enough for me or my family and the frontend's GUI is convoluted. Once again I must bring up the interface issue. For Mythbuntu to become the DE-FACTO HTPC interface it must be simplified. It has way too many options. I look at the Charter (my cable provider) DVR and it's f*g simple. Click on a program and one can record it once or set up a series recording (that's it!); another click and I get the EPG. That's what the GP (general population) wants: simple and easy to use. Can I set up that up with mythbuntu's frontend out of the box? Nope. I have to reconfigure the menus....manually. And that's the beauty of this product. I can re-configure it. But not everybody has programming skills.

I'm a software developer and I get the bells-n-whistles of the product but for this product to be embraced by everyone it must be simplified. I'm going to simplify it so that my family can appreciate its power. Wonderful product. What I'm saying is that **more does not mean better**....

That's my opinion. What's yours?

/AC

---

### Post by hollywoodpete on 2015-08-25
Since you are the OP and changed your own topic, I will chime in with my opinion. I agree that Myth BackEnd is the best PVR solution I have found. Using a headless server, it handles live TV and recordings fine as long as I log in with MythWeb. I am limited to 3 tuners with my HDHomeRun so I'm not sure I would like everyone to be able to schedule recordings at anytime. I also don't want Myth to be in charge of my music or movies. My storage on my server is 2 TB which fills up quickly with TV, My NAS is over 30 TB so it will hold plenty of movies for now. We can watch movies from any TV and not have to look for DVDs.

I agree that the Myth FrontEnd is a mess. Kodi meets my family's needs perfectly. Even my youngest (11) can navigate the menus and her friends love her system. I don't need her to schedule recordings. She will ask if she can watch a series. If it gets my wife's approval, I can record it and my daughter and her friends can watch it. We never have to rush home from dinner or a party to catch a show in progress. We start the show at the beginning on our time.

Overall, Myth is quirky but has a lot of potential.

---

### Post by afremont on 2015-08-25
> **hollywoodpete said:**
> Here is the thread I started when I had a similar issue. [http://ubuntuforums.org/showthread.php?t=2254699](http://ubuntuforums.org/showthread.php?t=2254699)
The fix is here. [http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html](http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html)
Once I fixed MythWeb it became awesome.

I honestly love Kodi. I have it on my phone and multiple devices on every TV in the house. Even my wife tolerates it. I change skins occasionally which makes it interesting.

That must have been the problem.  I can now update via mythweb.  I have over 100 channels in the list so.....  Thanks

---

### Post by afremont on 2015-08-25
I like kodi too, but I'm not sure how many other choices I really have since I like running the RPi for the front end.  I don't use mythfrontend either, but it's not really because I don't like it, I just choose to run a headless back end so I don't have a PC sitting in the living room.  I have three front ends, so it makes sense to keep them as cheap as possible.  One is a smart TV and it can access the back end by itself, but the interface is really ugly IMO and doesn't provide the capability that kodi does with addons, though it does do a decent job of Netflix and Amazon video playing which kodi really can't do.

I'm still looking for a good solution to streaming recorded TV to my phone.  Kodi runs it, which is okay when I'm at home, but doesn't work well across the net with limited bandwidth.  When I ran WMC as the back end, I really like Remote Media Center (client on phone) and Remote Potato (side server on WMC machine).  It did a great job of transcoding on the fly with no major delay before streaming.  The Myth things I've used so far aren't quite as slick. I want one program that does it all nicely and clearly like Remote Media Center did.  I've tried Mythling, Mythtv Player and MythTV Android and none of them works all that great for me.  I want to access my stuff over the net and, from what I've read, it looks like I need to install and configue OpenVPN to have any semblance of security.

Don't get me wrong, I love MythTV and I've used it off and on for way over 10 years.  I think it's been more like 15 years.  I just want a seamless way to access my content remotely.

---

### Post by Antonio_Carballo on 2015-08-25
> **hollywoodpete said:**
> Here is the thread I started when I had a similar issue. [http://ubuntuforums.org/showthread.php?t=2254699](http://ubuntuforums.org/showthread.php?t=2254699)
The fix is here. [http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html](http://lists.mythtv.org/pipermail/mythtv-users/2014-July/365893.html)
Once I fixed MythWeb it became awesome.

I honestly love Kodi. I have it on my phone and multiple devices on every TV in the house. Even my wife tolerates it. I change skins occasionally which makes it interesting.

I followed the instructions and modified the **php.ini** file; I then went to the mythweb interface (gave up using the backend's Channel Editor). I just unclicked the "visible" field and clicked [save] at the bottom of the channel page. I went to the frontend's program listing and like magic the channel was gone.=d> Thanks * 1M!

---

