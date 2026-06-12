---
title: "I give up.  Mythbuntu is to difficult"
date: 2008-08-10
forum: Mythbuntu
---

### Post by The Pinny Parlour on 2008-08-10
2 days of stuffing around trying to get 2 different Tv cards going.  

First, Asus My Cinema U3000 USB
Second, Dvico DVB-T Pro

After trying all sorts of guides etc, NONE OF THEM WORK for me.

Mythbuntu PDF guide
[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)
[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)
[http://linuxtv.org/hg/~pascoe/xc-test/](http://linuxtv.org/hg/~pascoe/xc-test/)

and numerous others.

I can understand that Mythbuntu is a slimmed down Ubuntu.  So i had to install text editor, achiver just to install drivers, firmware and read manuals.

Thanks for trying Mythbuntu makers but it's darn way to hard to get it working.  (shakes head)  2 days I wasted.

---

### Post by nasha on 2008-08-10
[HTML]http://www.linuxtv.org/wiki/index.php/Asus_My-Cinema-U3000_Mini[/HTML]
The ASUS is supported by the v4l-dvb linux driver, so you should have no issues getting that running:
```
$ hg clone http://linuxtv.org/hg/v4l-dvb
$ cd v4l-dvb
$ make
$ sudo make install
$ sudo modprobe -v dvb-usb-dib0700
```
Thats all thats required.
Dvico DVB-T pro doesnt seem to be listed as a supported device.

You wasted 2 days because you didnt do your research, but in hindsight, its nothing. Ask any member of this forum how many days in total theyve spent with mythtv for different things at times, and you'll find its much more than 2days. I know personally this is certainly the case for me, and every minute was worth it.

---

### Post by The Pinny Parlour on 2008-08-10
> **nasha said:**
> [HTML]http://www.linuxtv.org/wiki/index.php/Asus_My-Cinema-U3000_Mini[/HTML]
The ASUS is supported by the v4l-dvb linux driver, so you should have no issues getting that running:
```
$ hg clone http://linuxtv.org/hg/v4l-dvb
$ cd v4l-dvb
$ make
$ sudo make install
$ sudo modprobe -v dvb-usb-dib0700
```
Thats all thats required.
Dvico DVB-T pro doesnt seem to be listed as a supported device.

Tried that...didn't work.  Doesn't matter as I have little interest in it after wasting so much time on it.    Will use something else.

---

### Post by JugeHuge on 2008-08-11
I have now played three months to get Mythtv working perfectly. I Still have some problems but it's starting to look good..

---

### Post by SiHa on 2008-08-11
I'd advise you to try Ubuntu + Mythtv first. When you've figure out how to get it all configured, then you can try Mythbuntu.
Much easier, in my opinion.

---

### Post by Nate B. on 2008-08-11
I'm not trying to be crass nor unsympathetic, but it sounds like you may be using hardware that is a bit more obscure than most on this list.  I installed Mythbuntu two weeks ago tonight and because I was waiting on my capture card to arrive, it was a few days later before I could test video capture which worked the first time I tried it.  I'm using the very common Hauppage PVR-150.  By last weekend I was manually scheduling recordings.  Because of the unavailability of a DB-15 connector locally, I had to put off scheduled DVR operation until this past weekend and it worked flawlessly.

While I have almost nine years of Debian experience, I had to call on little of that as far as Mythbuntu was concerned.  I'll admit that I did install Midnight Commander and FTE immediately after installation.  And while I spent several hours over the course of a few days getting familiar with Myth and Mythbuntu, I'll have to disagree that Mythbuntu is too difficult compared to other methods of installing and configuring Myth (from what I've read).  Perhaps it is more difficult than off the shelf solutions for other platforms, but with flexibility comes a certain complexity and a steeper learning curve.  Nowhere have I read that Myth is intended to be ready for general use by non-technical users or that it is ready for use without the expectation that a person will get their hands dirty getting some aspect working.  That said, it is a credit to the Mythbuntu developers that they are offering a system with sane defaults and as easy of a setup as could be expected at this time for nothing more than the cost of the download time and a CDROM to burn it to.  That has to be worth a few hours of one's time to get it working.

Then there is the freedom aspect of GPL licensed software which is worth a lot.  So, take a break and give your mind some time to relax.  Often one's subconscious will wrangle with a problem while a person is doing other things and then an idea will suddenly pop up when you least expect it.  In the mean time, browse the forum archives and the Myth Users mailing list and you'll get some ideas.  If you do that, I predict that you'll have things working in a manner of days.  Good luck!

---

### Post by andylquk on 2008-08-11
Mythbuntu is IMHO a fantastic package.  I agree with the previous posts, you do need a certain amount of technical know-how, and it pays to do your research.

I've been using Mythbuntu for over a year now, and am still making minor tweaks here and there everynow and then.  Just this weekend just gone I tweaked the myth gallery ui.  I view this kind of effort as a learning curve.

You sound frustrated so perhaps it is time to take a break from mythbuntu, but I would suggest returning to it fresh in a few days time - it really is worth it.

---

### Post by Archmage on 2008-08-11
I send one year to try to make Vista run on a 386. It still wont work, therefore Vista is to difficult.

---

### Post by newlinux on 2008-08-11
mythbuntu (or ubuntu + myth) is pretty good, but doesn't work great for everyone. I installed ubuntu+ myth on my old .20.2 system and it really only took me a night to get it all working (it is a 3 backend 5 frontend system). I was amazed. My previous myth install took weeks. I'm a week into using the system and it is already pretty much fully configured, and I've added another backend. Compared to my previous installs, this was the easiest by far. Granted, my previous experience helped me. But installing myth and ubuntu on the same machines as I had previously done took much less effort than it did before.

For most with good  hardware choices, I bet you can get 80%-90% to where you want to be very quickly with mythbuntu, with extra effort for personalization and tweaks remaining.

You can always try one of the otehr myth distros.

---

### Post by Scott Atkinson on 2008-08-11
I think Mythbuntu is great, and run it myself - along side BeyondTV, Microsoft's MCE 2005, EyeTV on a couple of Macs and three Tivos. 

However, in fairness to the OP, not everyone - including not every Mythbuntu user - is prepared to negotiate the learning curve.

Mythbuntu/Myth TV is starting to move out of the 'wild west, you better know what you're doing' phase, and I suspect the number of people who just want to watch/record tv and be done with it is growing.

As much progress as Mythbuntu's maintainers have made toward reducing the complexity of the install, (and their work is amazing, I think) more needs to be done to make it a no-brainer.

And it either needs to be a no-brainer, or Mythbuntu needs to have a big sign hung on it that says 'mere mortals should keep moving.' 

Scott A.
Watertown NY

---

### Post by se99paj on 2008-08-11
Mythbuntu is not easy, in fact I find even using Ubuntu a chore.

I know the first time I installed mythtv I was playing around with it for a good weekend trying to get it to work, but even after I got it working I have been messing around with it to tweak bits here and there to get good performance. I even spent the last weekend trying to get a mythtv frontend on my windows PC.

But I also think that its an amazing bit of free software, it does everything that I want it to do and its completely free.

---

### Post by laga on 2008-08-11
> **Scott Atkinson said:**
> 
As much progress as Mythbuntu's maintainers have made toward reducing the complexity of the install, (and their work is amazing, I think) more needs to be done to make it a no-brainer.

And it either needs to be a no-brainer, or Mythbuntu needs to have a big sign hung on it that says 'mere mortals should keep moving.' 



Suggestions are always welcome!

---

### Post by Scott Atkinson on 2008-08-11
Again: the Mythbuntu team is excellent, as far as I'm concerned. Their work let me get MythTV operating, after some failed attempts.

For a computer user with a modest amount of knowledge and interest, (say, me, for instance...) the install is just good enough - at least on the analog side - to get through.

But if you know less than that, you can end up in trouble quickly. For instance, when going through the mythtv part of the set-up, it may not be obvious to mere mortals that when you're done with one part of the install you need to escape back to get to the next part.

For people used to wizards - or for just anyone who thinks in terms  of going from 'A' to 'B' to 'C' - stuff like that can be daunting.

Also, it can be unobvious how to resolve even simple things, like you video card not being detected at first blush.

And...even with a certain necessary amount of obscurity on the subject of dvd + codec playback, there must be a way to tell the user that they don't have the right stuff installed.

I'm like everybody else; it's easier to carp and pick at what's wrong than come up with workable answers to the problems - and the thrust of my post wasn't intended to be 'Mythbuntu has to get better.' That'll happen.

What I was fumbling around trying to say was - don't assume, at this point, that people picking up Mythbuntu have anything remotely like the kind of knowledge users have traditionally brought to the project.

s.

---

### Post by gwm123 on 2008-08-11
Been meaning to setup a MythTv system for a while now and I am finally getting around to it. I am an engineering student and generally don't have a lot of time on my hands so I really don't want to have to worry about hardware issues. Are there any computers from major computer manufactures (HP, Dell, etc etc) that support (maybe not officially) MythTv really well? I would like something that is a good media PC...Large Hard drive with HDMI and DVI video outputs, and coaxial video input. Any Suggestions?

A large amount of memory and powerful processor would be good as well for encoding and decoding.

---

### Post by newlinux on 2008-08-11
The dell ubuntu machines probably do. I have a dell 530n running as a secondary High def backend and frontend that works fine. You might want to upgrade the video though if you want an HDMI connection.

---

### Post by Hayesio on 2008-08-11
> Re: I give up. Mythbuntu is to difficult 

--------------------------------------------------------------------------------

Quote:
Originally Posted by nasha  
HTML Code:
[http://www.linuxtv.org/wiki/index.php/Asus_My-Cinema-U3000_MiniThe](http://www.linuxtv.org/wiki/index.php/Asus_My-Cinema-U3000_MiniThe) ASUS is supported by the v4l-dvb linux driver, so you should have no issues getting that running:

Code:
$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ cd v4l-dvb
$ make
$ sudo make install
$ sudo modprobe -v dvb-usb-dib0700Thats all thats required.
Dvico DVB-T pro doesnt seem to be listed as a supported device. 

Tried that...didn't work. Doesn't matter as I have little interest in it after wasting so much time on it. Will use something else.


If your still interested in getting the ASUS mini u3000 to work in Mythbuntu, I have some experience with this.

A couple of things I found:

1. Dont know why, but the above procedure did not work for me until i installed the latest kernal in mythbuntu. Try getting all your updates prior to starting that procedure.

2. I installed kaffeine (the KDE media player) and the device worked out of the box without the procedure quoted above (but with kernal updates). If you try this, dont auto scan for channels - sellect the channel table instead. You may have to boot the system without the device plugged in, then plug it in after you close the frontend because mythtv will occupy the device when it loads.

3. If the green light on the device is on, the module is installed and the device should work.

It works perfectly for me now. Your problem maybe related to something else.  I had a problem i thought was the ASUS mini that actually turned out to be a problem with playback of mpeg files! What exactly is it doing?

Hope this helps, 'cause Mythbuntu is a damn fine investment!

---

### Post by CornMaster on 2008-08-12
I had a weird issue where installing Mythbuntu didn't install grub.  So when it rebooted, everything died.  A few CDs and reinstalls later, I was in the same boat.  I ended up installing grub from the CD manually, and writing my own boot file (a first for me).

After using it for a while, I realized I don't like xfce (or whatever the default display is) and I installed ubuntu desktop, and turned off all the special mythbuntu stuff.

On my other ubuntu desktop, I just installed the mythbuntu package, and it was much smoother.

I'd recommend ubuntu+mythtv install, or ubuntu+mythbuntu install, but I understand that my problems were pretty unique, so that might not be right for everyone.

I'm pretty happy overall with mythbuntu performance.  The MOTD status script on login stopped working 10 days ago, probably when I switched back to ubuntu-desktop.  Other than that (and the install), it has been pretty flawless.  Of course, I could always use a bigger hard drive. ;)

---

### Post by sml on 2009-04-27
> **The Pinny Parlour said:**
> Tried that...didn't work.  Doesn't matter as I have little interest in it after wasting so much time on it.    Will use something else.

Also tried that. No luck either.

:(

---

### Post by uncle hammy on 2009-04-27
For what it's worth, I spent a week researching hardware before I set up my systems.  As a result, with almost no Linux experience, I had my system up an running (by running I mean recordings scheduled and using it to watch TV) in a night.

Now, I had a few bumps and a few "how do I's?" to do some tweaking, but the system was fully operational.  I would suggest that researching your hardware is key.

People seem to want to use any old hardware that they have laying around because they've heard Linux is fast and stable and you can get away with that.  However, if you're building a HTPC system, you're not really building any old thing, and some forethought is warranted.

---

### Post by AboveTheLogic on 2009-04-28
> **uncle hammy said:**
> For what it's worth, I spent a week researching hardware before I set up my systems.

Same here. I spent a great deal of time combing the myth wiki, newegg, amazon, and ebay to find hardware that, according to the wiki, works. There were cheaper hardware alternatives, but I went with hardware that had the best results for others, and it seems to work well.

There are many other bugs and issues I'm still ironing out, but the hardware seems to all be recognized and controlled just fine.

---

### Post by Zeedok on 2009-04-28
I've had my Mythbuntu box for about 4-6 weeks and I have definitely had some teething problems (like I realised my TV reception wasn't great, so that needed to be tuned, had problems with the DVD drive mounting and recently I had trouble getting a remote control to work) but I agree the key is to select the right hardware at the outset.  I actually had my system put together by a guy who does linux pre-installed systems.  He was a great help in choosing the hardware components.

Don't give up.

---

### Post by wyliecoyoteuk on 2009-04-28
I have been a fan of Mythbuntu since 8.04, just moved to 9.04, and had some issues with my TV card (a Hauppauge Nova-T 500), but it turned out to be the new firmware was dodgy, rolled it back and it works fine.
I just love the flexibility that MythTV gives you, nothing else matches it for scope.

Having said that, if you just want to watch TV on your PC and record the odd program - it is overkill.

I can't agree more as to hardware- I have several TV cards, the Nova-T 500 is a little more awkward than the others, being 2 USB tuners on a PCI card is a little odd, after all, but it works too.

---

### Post by bhampton on 2009-04-28
I respect your frustration.

I am really on the other end of the spectrum though.

I had the notion that I wanted to build a Linux based HD compatable PVR on Saturday and Mythbuntu looked good and now about 3 days later everything I working perfectly.

For me... The installation does most everything for me. I had to learn a little thing about setting up the capture card and also went a few rounds with lirc but even though I know nothing about linux I've never experienced something as easy to setup and work with as I now have with MythBuntu.

-Brian

---

### Post by tobiz on 2009-04-28
I've spent ~6mnths getting Mythbuntu working and it's all been worth it.  Is it production quality? Not yet but it's getting there and provided you do your research before selecting components they can usually be made to work. My latest upgrade was to an SSD for the  root partition, this took a day to get working, ie save old HDD partition and restore to new SSD. My system has a WAF of 6-7! Not bad for a full HD TV, 7.1 sound, stored DVDs, CDs etc. Total S/W cost: ~£3.50 for Mythbuntu 8.10 on DVD. Cost of H/W: let's not talk about that!

---

### Post by avacado on 2009-09-16
$ sudo modprobe -v dvb-usb-dib0700[/code]
 
I have a similar problem, with a developer message coming up in dmesg output asking me to use the old insmod command to insert a module which makes my card detectable.
 
modprobe is the new insmod
 
The syntax for the modprobe command is not self evident.
I follow the first half of the command line you have written above, but how do you know that dvb-usb-dib0700... is the right module ?
 
Hamish

---

### Post by TopEnder on 2009-09-16
I agree totally with the original post and I question some of the other posts,  WHY should you need to muck around for up to 6 months trying to get Mythbuntu - TV working.  It only took me a couple of hours to get all the following working, me TV Gxine, Xine & VLC Media Player.   For viewing all products work well, for recording me TV works well for me.  The USB stick I am using is a Gadget Geek (af9015 chip).

---

### Post by lumpy on 2009-09-18
If you give up after a few days then NO media center out there will be to your liking.   Buy a HD tivo and call it done.

---

### Post by rickyble on 2009-09-18
I agree that is not for the masses but Im not sure anything at this level is.  If you want something that is just very very easy and works you will have to wait for the big companies to create it and put it on the shelf for thousands of dollars.  I am not aware of anything that will do everything it will do in one box and is that flexible.  I have been using it for a couple of years now and just did a reinstall.  It took me a while after I first installed it to tweak it like I wanted it and to discover the full flexibility of it all.  The modularity of the frontend/backend is just fantastic and also the diskless boot clients.  I have seen a couple of companies that sell the front ends like appliances.  But if you are looking for a couple of days install config and it all works perfectly its not likely to happen.  I do say good luck though maybe you will find the backend/frontend nirvana.  Integrated with my hacked dtv boxes I love it.

---

### Post by TopEnder on 2009-10-14
> **TopEnder said:**
> I agree totally with the original post and I question some of the other posts,  WHY should you need to muck around for up to 6 months trying to get Mythbuntu - TV working.  It only took me a couple of hours to get all the following working, me TV Gxine, Xine & VLC Media Player.   For viewing all products work well, for recording me TV works well for me.  The USB stick I am using is a Gadget Geek (af9015 chip).
Well, I did persist and now I have Mythtv working, it was not a simple task but after reading most of the posts on Ubuntu & Mythtv forums and thanks to those that posed them, I have acheived what I set out to do, next step will be to get the recording side working and install some of the other plugins.

---

### Post by ConXtionS on 2009-10-14
I am on week three bro... I feel your pain

---

### Post by sawbuck on 2009-10-14
Let me chime in with my paltry two cents.....

Yeah, Fedora+MythTV, Mythdora, Ubuntu+MythTV and Mythbuntu, all require work and can (still is) frustrating.  Through several years, time permitting, I've tried XP & MCE, and Haupauge stuff with windows, Snapstream as well.  While all of these have had some success and variousl forums to "help" I think it takes experience to make them work even with the help.  Muddling through the jargon and written/posted material leaves me, at the end of the day, realizing how little I know.  Many users make it look so easy with a suggestion that works for them but often I spend a lot of time trying to understand what it is they did.

That said, Mythbuntu (and other MythTV versions) seems to work for most on avariety of equipment and the price is right :P  I'm still pulling hair trying to get a system down that is comparable to the monthly $80US or so I used to spend on cable or sattelite PVR boxes.  Is ti there yet?  No, but I'm able to capture and watch most of what I want with good quality once it is trannscoded to std DVD level for my aging equipment.

I have one card,  a Hauppauage 1600, (though it has two tuners, in the US analog no longer works so I only use the ATSC tuner)  that has its own set of problems but many kind strangers have helped me get up to the level I'm at now.  I still have the other stuff mentioned above around but my frustration level hasn't reached the point of wanting to go back to any of it yet especially $80 a month.

I consider myself too green to offer any advice except to search these forums for similar problems you are having and post specific problems.  Most of the time one of the gurus will work you through a solution.  Also, if you can find the time, experiment with similar problem/solutions even if it isn't a match for your situation.  If it works, post it - it might solve one of my problems......

---

### Post by sydneysuder on 2009-10-15
Yes there is a lot of help. But the bottom line is that you shouldn't need it if it was to be used as drop in replacement for something like set top box.

I like Mythbuntu. But I have no illusions about my non-techie friends having a chance or ever setting one up. That is why you see $4000 MCE systems outthere that people actually buy.

---

