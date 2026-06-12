---
title: "Mythbuntu on eeebox: suggestions/comments"
date: 2009-03-05
forum: Multimedia Software
---

### Post by Victormd on 2009-03-05
I'm thinking about setting up mythbuntu on a eeebox that I have and don't use much. I've seen some of the posts from 2008 on this but wanted to know if there are any updates.

1. I'm not really worried about having a "TiVo-like" equipment (i.e., rewind, restart). Basically I want to be able to play my movies from the eeebox and record from the TV/DVD.

2. Now, with respect to the USB I/O tuner. I need one that allows me to connect my cable/antena to the eeebox and provide an output from the eeebox - and hopefully it should be cheap!
I've found [this]("http://www.amazon.com/gp/offer-listing/B0001AU7Q6/sr=/qid=/ref=olp_tab_all?ie=UTF8&coliid=&me=&qid=&sr=&seller=&colid=") but I'm not really sure it's all I need...

Has anyone done this? If so, any suggestions on additional hardware??
Thanks

---

### Post by Victormd on 2009-03-06
Anyone??

---

### Post by Victormd on 2009-03-07
Bump...
this would be really helpfull before I go out and by any additional HW...

---

### Post by ozybard on 2009-03-09
I have just (last evening) got Myth Frontend running on an eeebox utilising wireless G.  Everything is working OK although Live TV and Recording Playback are a little jittery.  I intend to upgrade my router to Draft N in the next few days which I hope will deal with that little problem so when it's done, i'll post back.

I have also set up a Pinnacle Nano usb stick on this little box which worked OOTB and performs extremely well for standard definition.

Feel free to post back if I can help further.

---

### Post by Victormd on 2009-03-09
I guess my main concern is the TV/CABLE I/O because the eeebox does not have TV output so I need something that can (i) receive the signal and send it to the eeebox, (ii) process the signal (not to overload the atom proc. - this is not a must though) and finally (iii) output from the eeebox to the TV. Does the Pinnacle Nano USB do that?

---

### Post by ozybard on 2009-03-10
To clarify a couple of things:-

The pinnacle nano usb device is a DVB-T device that plugs into a spare usb port.  It is capable of processing digital TV and passing this signal to suitable software.  As I'm a gnome desktop user, I use ME-TV as the TV player.

My eeebox is connected to an LCD monitor although depending on the model of eeebox you have, an AVI output socket is provided which can drive VGA or HDMI with a suitable adaptor or straight dvi if the tv can take it.  I dont think that there would be a solution if the tv is analogue however but I could be wrong.

Another strategy could be to set up mythbuntu on another standard size computer capable of taking any of the myriad of PCI tuner cards available as a backend only machine and then set up the eeebox as a frontend only device making use of the inbuilt wireless N capability to access live TV, recordings, music and videos and any of the other functions that Myth can provide.  This is the strategy that I have adopted.

Hope this helps [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by Victormd on 2009-03-10
Well, the problem is that at this point, I'm looking for an alternative use for my eeebox and don't want to spend any more money than I have to so I don't think setting up another computer as a backend is an alternative. Furthermore, this is mainly to have something to tinker with in my spare time... :)

I've found this cable: [http://www.newegg.com/Product/Product.aspx?Item=N82E16882339047](http://www.newegg.com/Product/Product.aspx?Item=N82E16882339047) that takes care of the eeebox-TV output so now the pinnacle nano usb is starting to look like an attractive solution.

---

### Post by ozybard on 2009-03-10
Ok...I understand

If you can source a Pinnacle Nano then you will find that it works OOTB.  There are of course a number of other usb DVB dongles supported under Linux and LinuxTV is a good place to start looking for supported devices.

Just for your info,  DVB-T can be viewed successfully via Kaffeine, Me-TV, Xine-UI or VLC.  The advantage of Me-Tv is that it produces a standard Channels.conf file automatically on the first launch of the programme.  That file can then easily be used for Xine-Ui or VLC if you so wish.  Saves a lot of command line stuff.

HIH....Post back if I can help further

---

### Post by Victormd on 2009-03-11
Hey, thanks a bunch! This is all very helpfull information. This weekend I'm going to try to play around with it a bit and if I run into any problems I'll post back!
Thanks again...

---

