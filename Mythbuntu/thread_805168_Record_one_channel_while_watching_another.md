---
title: "Record one channel while watching another?"
date: 2008-05-23
forum: Mythbuntu
---

### Post by webeducation on 2008-05-23
Hello all, I recently purchased a tivo and really dislike the fact that I cannot record one channel while I watch another. As a result, I am currently looking to setup a mythbuntu system with the wintv pvr500 mce card, but I do have some concerns.

Using MythBuntu:

1) Would I be able to for example record channel 223 while I am watching channel 202?

2) Also, which version do you guys think is the most stable?

---

### Post by mrand on 2008-05-23
> **webeducation said:**
> Hello all, I recently purchased a tivo and really dislike the fact that I cannot record one channel while I watch another. As a result, I am currently looking to setup a mythbuntu system with the wintv pvr500 mce card, but I do have some concerns.

Using MythBuntu:

1) Would I be able to for example record channel 223 while I am watching channel 202?

2) Also, which version do you guys think is the most stable?
1. The quick answer is yes - you can record from even more than two... but that answer assumes a few things.  Where are channels 223 and 202 coming from?  If it is cable or sat, at a minimum you'll need two set-top-boxes; one for each channel you want to watch (or record).

2. While VERY usable by non-technical people, mythtv still has a lot of development going on.  You should go with the latest stable/released version available.  Documentation and discussions will typically revolve around that version.  You don't want to be stuck on an old one.

[INDENT]   Marc[/INDENT]

---

### Post by webeducation on 2008-05-23
Thanks for the fast reply. I really appreciate the help. 

In response to question 1, channels 223 and 202 are coming from a digital cable box (not high definition). Currently I have verizon fios. I also (luckily) have an extra verizon motorola box sitting here collecting dust while taking 5 bucks out of my pocket each month.

I'm guessing the first verizon box would connect to the pvr500 via coax. And then other via composite or svideo. I really like the fact that I could have a lot of capture cards. Mythbuntu sounds more powerful than I though.

Would I need to set this up as a front-end or back-end on mythbuntu? Is there really any difference?

---

### Post by mrand on 2008-05-23
> **webeducation said:**
> Thanks for the fast reply. I really appreciate the help. 

In response to question 1, channels 223 and 202 are coming from a digital cable box (not high definition). Currently I have verizon fios. I also (luckily) have an extra verizon motorola box sitting here collecting dust while taking 5 bucks out of my pocket each month.

I'm guessing the first verizon box would connect to the pvr500 via coax. And then other via composite or svideo. I really like the fact that I could have a lot of capture cards. Mythbuntu sounds more powerful than I though.
With all respect to the Mythbuntu guys, the power is all in the mythtv component itself.  What the Mythbuntu guys did was create a wrapper that makes mythtv easier to install and manage.  Again, we all appreciate all their efforts!

But back to your STB's.  So your extra verizon box can also tune to the cable channels that are received off Fios?  I don't have Fios and haven't read that much about it, so I don't know.  Another thing to investigate is how you change the channels on the set top boxes.  Worse case (if they don't have a serial port or functional firewire) you use an IR blaster.  Speaking of firewire, if the STB's have firewire and it works (that's a coin toss), that is by far the best quality video you're going to be able to get - use that and forget the PVR-500.
> Would I need to set this up as a front-end or back-end on mythbuntu? Is there really any difference?Hmm.  There is a huge difference between front ends and back ends.  The main requirement of a mythtv setup is that you have a backend, which controls the scheduling, tuners, and video capture - without that, it's really not mythtv.  To set up the schedules, you need an interface to the backend - that's either mythweb, or mythfrontend.  You can have multiple front ends.  To watch recorded items, you can use mythweb, mythfrontend, or if you want to just browse the file system, nearly any video player in existence.

Hope that helps,

[INDENT]Marc[/INDENT]

---

### Post by volkswagner on 2008-05-24
What is the model of the set top boxes?

Just to add a little.  If you have only one pc, the backend and frontend will be installed on that machine (connected to your TV and set top boxes).  As mentioned earlier, the backend can be tucked away with out a frontend installed.  You would then need a second pc or frontend machine connected to the tv.  Mythtv support's XBMC if you have an old xbox lying around.  It makes a great Standard def. frontend with mods to the xbox.  There are other UPnP frontend devices supported also.

You can try version 8.04 live CD and see if your video, sound, and network cards play nice before installing.  The live CD needs to see a backend on your network for the TV function, but you can check your hardware support.

---

### Post by webeducation on 2008-05-24
Thanks again for all your responses.

Both verizon boxes I have are the motorola qip2500-3. Both can tune to the cable channels that are received off Fios and they have serial ports and usb. Not too sure what I would use the usb for though? (see pic below)

[IMG]http://hackszine.com/pvr_fios_2.jpg[/IMG]

Since I only have one computer, I would need to have both the backend and frontend on it. It also sounds like I will need to get 2 PVR-150's instead, due to the IR situation. I do not see how the pvr500 would control both stb's? Right now I have the tivo using an ir blaster, and I have to tell you the channel change is super slow. 

I like the live-cd idea, I will try to use that to make sure it all works beforehand. I am hoping not to screw it all up as it seems a bit complicated. But considering a lot of people are saying its one of the best solutions out there, I will push on.

---

### Post by mrand on 2008-05-24
> **webeducation said:**
> Thanks again for all your responses.

Both verizon boxes I have are the motorola qip2500-3. Both can tune to the cable channels that are received off Fios and they have serial ports and usb. Not too sure what I would use the usb for though? (see pic below)

[IMG]http://hackszine.com/pvr_fios_2.jpg[/IMG]

Since I only have one computer, I would need to have both the backend and frontend on it. It also sounds like I will need to get 2 PVR-150's instead, due to the IR situation. I do not see how the pvr500 would control both stb's? Right now I have the tivo using an ir blaster, and I have to tell you the channel change is super slow. <...>
I've never heard of anyone being able to do anything useful with the USB port.  The 9-pin "data port", however, is almost certainly a RS-232 (serial) control port, which, if enabled, may be able to change channels - it does on my Motorola STB (from Time Warner).  I've not done IR blasting, but I'm sure there are ways to do it without having another tuner card.  Live-CD works on a good number of machines, but some may require you to use the alt-cd.

Have fun,

   Marc

---

### Post by tgm4883 on 2008-05-24
certain ir receivers/transmitters have dual transmitters.  Meaning you can use one for one box, and the other for the other box.  My MCEUSB2 has both and I have successfully gotten them to blast seperate directv boxes.  With that being said, I no longer do it that way and use a strictly cable connection to the directv boxes.

Volkswagner:  right on, one tiny correction though.  XBMC supports MythTV, not the other way around.  XBMC does this by way of implementing the MythTV protocol or via UPNP.

Webeducation:  I don't know much about TV over FIOS.   Do you have to have a box at every TV?

---

### Post by webeducation on 2008-05-24
Currently I have only one tv in the household and it is hooked up to one box. The other box was hooked up to another tv, but since we got rid of that tv, we just have an extra box. What type of capture card are you using? Did it come with the mceusb2?

---

### Post by tgm4883 on 2008-05-24
You can get the PVR-500 with a MCEUSB2 remote, or you can buy them seperately.  I bought mine seperately off of ebay for about $30 each shipped.  I like the remote so much I've bought 4 of them.  You can probably get them for less that $30 shipped on ebay, i usually just grab a buy it now though.

Here is the different types of mce remote on the mythtv wiki
[http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)
I have the third one from the left, the version 2 that says microsoft at the bottom.

This is the remote i'm talking about
[http://cgi.ebay.com/Microsoft-OEM-Media-Center-Remote-Control-MCE-New_W0QQitemZ120264269939QQihZ002QQcategoryZ51086QQssPageNameZWDVWQQrdZ1QQcmdZViewItem#ebayphotohosting](http://cgi.ebay.com/Microsoft-OEM-Media-Center-Remote-Control-MCE-New_W0QQitemZ120264269939QQihZ002QQcategoryZ51086QQssPageNameZWDVWQQrdZ1QQcmdZViewItem#ebayphotohosting)

Here is a newegg.com link that (I believe) contains the same thing.  (This kit contains the remote that is third from the right.  It is also a version 2 and should work just fine.)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116632&Tpk=pvr-500](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116632&Tpk=pvr-500)

:EDIT: 

Almost forgot.  I have both a PVR-500 and a PVR-150.  (I also have a pcHDTV 5500, but when I moved I no longer get cable :(  )  Keep in mind that I don't use the ir transmitters anymore and instead use a serial/usb connection to change the channels.  I did have the blasters working seperate boxes at one point.  Off to dinner, i'll post my channel changing script later to show you how they both work.

---

### Post by webeducation on 2008-05-25
Those remotes look pretty sweet and once I get things up and running I'll probably grab one from ebay. So far I just ordered the wintv pvr500 mce bundle from newegg. The remote is not the same as the one you showed me but it will have to do for now. I noticed that there are 2 midi jacks on the mceusb2. Since each of the midi ports will go out to each cable box, I'll need to pick up 2 serial cords, one for each. 

Running scripts in linux sounds complicated. Is this something I would need to copy/paste, or is there more involved?

---

### Post by tgm4883 on 2008-05-25
It appears that I have deleted those scripts :(  Running scripts isn't difficult.  Just copy them to /usr/local/bin and make sure that you point the tuner to use it in mythtv setup (under channel change script)

The scripts are usually just downloadable so you can just copy them into that directory.  The scripts I had before just set which transmitter to use and then used the existing channel change script.

---

### Post by webeducation on 2008-05-27
Okay, the scripts don't seem that bad, and so far I've managed to find a few good articles regarding the installation as well as running the scripts. 

One last question which could really be a deal breaker on whether or not I install this is ...

Does MythBuntu have the ability to burn a tv recording to dvd?

---

### Post by volkswagner on 2008-05-27
Mythtv has a plugin, mytharchive.  You can enable it to archive and burn to dvd.

---

### Post by bkr1_2k on 2008-05-27
webeducation, 

Frankly I'm surprised you couldn't use the tivo to watch a channel and record another one.  I tried out the tivo a few months back and had no problems doing that with my fios service.  I bought the $79 tivo (on sale for $59) and didn't have any issues.  I don't subscribe to any of the HD channels, though, which may be the issue if you were trying to watch and record two separate HD channels.  I don't know if tivo has put out a dual HD tuner model yet.

That said, I haven't messed with any significant amount of linux stuff since buying a mac 5 years ago and the mythbuntu install was quite easy for me.  I had issues with the 7.1 installer not giving me a way to address my backend and get it running (on a combined frontend/backend machine) but the 8.04 install went very well.  I'm using dual PVR150 tuner cards and so far most things are working the way I had hoped.  It took about an hour to do the install on my P3 933.  I'm going to go back and tweak a few things over the next week or so, but that's just for performance and partitioning preferences.

---

### Post by tgm4883 on 2008-05-27
Yes you can use mytharchive.  Works pretty well and allows you to transcode to different formats, remove commercials, etc.  It's much much more advanced than the TiVo burner.

---

### Post by webeducation on 2008-05-27
After hearing all the good things I can do with mythbuntu, I really don't see any reason to go with any other sort of pvr/dvr system. I'm really exited to get this project started.

With the Tivo (standard), I was able to watch one station while recording another, but (and I know this might seem lazy :)) I would have to change the tv channel to 3 while the tivo was recording on video1. Even though I didn't have both boxes hooked up at the time, I think that if I did I would just have another remote to deal with. Besides with all the features of mythbuntu, it doesn't seem like there is much of a comparison at all between the two.

Also, the support I've gotten so far through this forum is just another reason for me to install mythbuntu. Thanks to all.

---

