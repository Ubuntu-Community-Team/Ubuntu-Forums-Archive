---
title: "Attn: Mythtv buffs, need suggestions"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by vv88 on 2007-05-30
Currently I have a 200 GB Frontend + Backend, ubuntu studio frontend, and wireless frontend.  I don't use the wireless and studio frontend very much, but the option to access the backend is nice.  The backend is running off a PVR-150, which is fine, because I only need one tuner.  However, I would like to utilize the server side a little better by adding frontends for my tv sets.  Obviously, I need to concoct some sort of receiver setups w/ remotes.

What I have:

1)Modded xbox (evox, DVD package and remote, 40 GB HDD)
2)An older pc (PIII, 512 MB RAM, 40 GB HDD)

Something like mediamvp would be great, but I'm trying to get around that.  I tend to think that the first thing I need to do is upgrade the video card in the old PC in order to get a video out.  This could be connected by LAN cable, but I would like to make the xbox wireless.

Also, I would like to mention that mythtv (frontend) is not necessarily a necessity.  I would just like to have access to the media files on the backend.  Again, through my television sets (two, one through xbox, one through the old pc).  Setting up simple shares may do the trick.

I welcome any comments/suggestions that anyone could provide.  Thanks in advance!

---

### Post by newlinux on 2007-05-31
Installing mythfrontend is pretty easy for the older Pc. What kind of video card and how what speed is the processor? You could also just setup some shares and use vlc.

You may also want to look into Elisa.

You could use XBMC for the xbox...

---

### Post by vv88 on 2007-05-31
Thanks for the suggestions newlinux.

Setting up the frontends is really not the issue.  Actually, I was working on the xbox last night and was able to make a connection using xbmcmythtv.  Needless to say, I still have to work on the shares because things aren't syncing right now.  Data connection is good and I can pull up jpegs and info, but the shares settings still need work. 

The old PC is at least 833mhz, but right now it's kind of pulled apart.  It's been running ubuntu off and on for about a year now (actually kubuntu, xubuntu, ubuntu at different times).  The video card would have to have an AGP interface.  Also I'm wondering if there would be a problem going with ATI instead of nvidia.  Moreover, I'm wondering if old reliable will have power to run a frontend without any problems. 

Lots of questions here I know.  If everything thing above seems sufficient enough, I've got one more.  The two external frontends I'm running right now have no problem changing channels/navigating through keyboard.  It was a bit of a task getting things running with an IR blaster/MCE remote (backend/frontend combo).  Could you or anyone else recommend a remote that would work well on a the standalone frontend pc (USB or otherwise)?

Thanks for the help.  I'm going to take a look at elisa.

---

### Post by rhpot1991 on 2007-05-31
I have seen Streamzap recommended quote a bit.
[http://www.amazon.com/Sherwood-USBIR2-Streamzap-Remote-Control/dp/B00008XETO/ref=pd_bbs_1/002-4603176-5851242?ie=UTF8&s=electronics&qid=1180639303&sr=8-1](http://www.amazon.com/Sherwood-USBIR2-Streamzap-Remote-Control/dp/B00008XETO/ref=pd_bbs_1/002-4603176-5851242?ie=UTF8&s=electronics&qid=1180639303&sr=8-1)

I went a different route for my frontend, picked up a pvr-150 from Circuit City for $70 (price match from their website) just to use the remote and IR dongle.  I ended up installing a backend on that box, and making my pre-existing backend the master backend so now I have 2 tuners able to record.  It just made more sense to invest that money in something (the tuner) that I could reuse later and get the remote functionality out of it.

A P3 getting near 1ghz should be able to run a backend with a pvr-xxx card as they have hardware encoding built in.

Other options: Why not move one of the existing frontends next to a tv?  Also I seem to recall words about the xbox dvd remote working with a mythfrontend running there.

Video Card:
I just replaced my ATI 9600 pro because of horrible driver support.  ATI drivers in myth currently have a bug where the screen is way too large and you only see the top of the video.  There are workaround for this but it requires having your CPU do much of the work that your video card used to do, thus a lot of freezing occurs.  It also requires you to patch mythtv to use an ATI hack otherwise everything is blue.

I just ordered an asus N6200/TD/128 GeForce 6200 card for my frontend box:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121542](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121542)
Not really thrilled with it thus far, the video out of the composite connector is very washed out, and my fonts are fuzzy around the outside.  I need to hack the xorg config some more and see if I can do anything or if I have a bad card or if its just a junk card (Anyone else out there have one of these, or have any bright ideas for me???)

---

### Post by newlinux on 2007-05-31
> **rhpot1991 said:**
> I have seen Streamzap recommended quote a bit.
[http://www.amazon.com/Sherwood-USBIR2-Streamzap-Remote-Control/dp/B00008XETO/ref=pd_bbs_1/002-4603176-5851242?ie=UTF8&s=electronics&qid=1180639303&sr=8-1](http://www.amazon.com/Sherwood-USBIR2-Streamzap-Remote-Control/dp/B00008XETO/ref=pd_bbs_1/002-4603176-5851242?ie=UTF8&s=electronics&qid=1180639303&sr=8-1)

I went a different route for my frontend, picked up a pvr-150 from Circuit City for $70 (price match from their website) just to use the remote and IR dongle.  I ended up installing a backend on that box, and making my pre-existing backend the master backend so now I have 2 tuners able to record.  It just made more sense to invest that money in something (the tuner) that I could reuse later and get the remote functionality out of it.

A P3 getting near 1ghz should be able to run a backend with a pvr-xxx card as they have hardware encoding built in.

Other options: Why not move one of the existing frontends next to a tv?  Also I seem to recall words about the xbox dvd remote working with a mythfrontend running there.

Video Card:
I just replaced my ATI 9600 pro because of horrible driver support.  ATI drivers in myth currently have a bug where the screen is way too large and you only see the top of the video.  There are workaround for this but it requires having your CPU do much of the work that your video card used to do, thus a lot of freezing occurs.  It also requires you to patch mythtv to use an ATI hack otherwise everything is blue.

I just ordered an asus N6200/TD/128 GeForce 6200 card for my frontend box:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121542](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121542)
Not really thrilled with it thus far, the video out of the composite connector is very washed out, and my fonts are fuzzy around the outside.  I need to hack the xorg config some more and see if I can do anything or if I have a bad card or if its just a junk card (Anyone else out there have one of these, or have any bright ideas for me???)
I have the Geforce 6200 LE (PCIe) however, it doesn't have a composite connector, but the VGA out works great. I also have an Geforce mx 440 and a Geforce 6150 that all do myth just fine (HDTV via DVI and VGA).

So for me the cards are good, but I can't speak to the composite connection.

I would stick with nvidia and stay away from ATI. ATI cards in myth and linux are hit and miss.

I use a harmony remote emulating an MCE remote with MCE USB IR receivers and they work great for me. Don't use IR blasters.

---

### Post by vv88 on 2007-05-31
Wow.  I know it took me awhile to get to what I was really looking for, but you two took care of the task very well.

That streamzap remote is EXACTLY what I was looking for. Thank you!

Also, I am currently running all nvidia (old and newer cards) and they work flawlessly with linux/myth.  So I wanted to be sure.  Your comments were definitely welcomed here also. 

Sidenote: I am using the xbox dvd remote with the xbox setup and it works quite well.  Now if I could my recordings/live tv to work, I'd be all set!!!

Another sidenote: I actually looked at that exact nvidia card on newegg.

When all these these settings are successfully implemented, I'll be looking for a wireless card for the pc in the  next phase.

Again, thank you newlinux and rhpot1991 for your suggestions!

---

