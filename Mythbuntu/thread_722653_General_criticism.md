---
title: "General criticism"
date: 2008-03-12
forum: Mythbuntu
---

### Post by peterthewolf on 2008-03-12
Mythbuntu may be a worthy attempt and may get better.

My criticism is that mythtv is easier to install on ordinary ubuntu.

This may be because mythbuntu asks questions that the audience does not know  the answer to. In my case I am not offered a choice I recognise when it asks which remote I am using. I am using a very common Hauppauge Nova. If installing under normal ubuntu I am not asked this and have to do some research to find what I need to do. But in the midst of install this is not an option.

Then again during mythtv setup when choosing a TV card I do not get a clear indication of what option to use for my DBT card. If I install under ubuntu only one option works for the card. And worse that option does not see the card on mythbuntu.

So I think you should look at the audience you are after. If it is someone who is prepared to try linux then forget it. If it is for someone who just wants a media centre then a redesign to be more understandable to Mr Jo in the street is urgently needed.

Oh nearly forgot. The point of mythtv nowadays is to watch TV on a large LCD or plasma screen. Now if that TV is the PC monitor as well it should not be a problem, but it is. Mythbuntu like ubuntu cannot install using my 32in Samsung LCD. For ubuntu thats excusable but for mythtv NO after all thats what it is aimed at. Not that any distro should fail when talking to probably the most "intelligent" monitors to date.

---

### Post by kreegor on 2008-03-12
I disagree. I am new to linux (though learning heaps more about it) and MythBuntu was the first Linux distro I tried. I wanted to fiddle around with Mythtv but had no idea how to actually install it in ubuntu in the first place.

1) The great thing about MythBuntu was that there is no need to look up how to install mythttv on it in the first place making it excellent for linux noobs to get a myth box going. I could navigate my way through an installation disc but then having to download, unpack and install the actual mythtv application was unknown to me. I won't go into installing and configuring lirc etc on a new machine. That's all done with MythBuntu as well which is great because that would be a real pain for a newbie IMO.

2) if you are building a HTPC box that it is assumed that you at least have some basic hardware knowledge. If you don't have a basic hardware knowledge then you shouldn't expect to put together a PC easily. e.g. you should at least know what type of tuner card you have. There is no way the system can configure that card before it has installed the drivers etc. Once MythBuntu is set up and you reboot the machine, the card is detected (funnily enough) and can be selected in the list.

3) Installing on a large TV is no problem. I did it.. mind you I have a vid card that is supported by Linux and MythBuntu has the drivers for it. Once again, install the drivers and reboot. It is amazing what happens when a machine actually knows how to run the installed hardware. I currently run my MythBox on 32inch LCD TV with no problem (installed connected to the same TV), no skipping, artifacts, blurring, colour or resolution problems.

So coming from a Linux noob I have to say that MythBuntu was freaking easy to get working even for someone who knew very little about Linux. I have since recommended it to a few people who have found it really simple to use as well. Maybe installing MythTv on an already installed Ubuntu machine is easier for a Linux guru but definitly not for a someone like me.

---

### Post by nasha on 2008-03-12
As with the last poster, i disagree with everything you said...

You say its easier to install on ubuntu? Its already instaled on mythbuntu.... No dependencies to sort out, no compiling binaries, no nothing. Just a working install, straight out of the box.

The only things that need to be done, is install and configure tuner and remote. Both of which there is plenty documentation on the internet for, provided you made the right hardware choice.

Mythbuntu is perfect for the new linux user, as it enables them a quick an easy way to get started... I should know, i was a new user once too

As for big TV's... I have one frontend running on a 42in plasma at 720p, and i have another frontend running off a 37in LCD.... Both with no issues...

Im not sure what you were basing our opinions on, but they don't seem very well though out...

---

### Post by laga on 2008-03-13
> **peterthewolf said:**
>  I am using a very common Hauppauge Nova.


In Hardy, I can easily see four choices related to hauppauge remotes. One of them is labeled "Nova-T 500" although I'm not sure if that's the correct remote for you. In any case, it's very easy to try all four of them and if they don't work, you can just create a bug report and we'll try to add support for you remote.

> 
 If installing under normal ubuntu I am not asked this and have to do some research to find what I need to do.


Lirc will ask these questions if you run ```
sudo dpkg-reconfigure lirc
```
It's part of the package.

> 
But in the midst of install this is not an option.


It is. Open firefox and do all the research you want or need. Even if you don't want to configure your remote immediately, eg because you need to research a bit more, you can just continue installing and go to mythbuntu-control-centre later. Or just do it manually as you seem to prefer that.

> 
Then again during mythtv setup when choosing a TV card I do not get a clear indication of what option to use for my DBT card. If I install under ubuntu only one option works for the card. And 


I don't think you're supposed to get a "clear indication", you have to choose the correct card type yourself.

> 
worse that option does not see the card on mythbuntu.


There was probably a problem with the drivers then, which also explains your confusion when trying to select the correct card type. I guess the card works fine after rebooting, so you could have gone to mythbuntu-control-centre, started mythtv-setup and tried again.. But as I said before, It's your job to find out what kind of capture card you have and set up MythTV accordingly.


> 
The point of mythtv nowadays is to watch TV on a large LCD or plasma screen.


That's what you want to do with MythTV. It's not "the point of mythtv".


> 
 Now if that TV is the PC monitor as well it should not be a problem, but it is. Mythbuntu like ubuntu cannot install using my 32in Samsung LCD. For ubuntu thats excusable but for mythtv NO after all thats what it is aimed at. Not that any distro should fail when talking to probably the most "intelligent" monitors to date.

The most "intelligent" monitors? Sorry, you don't know what you're talking about. HDTV sets often have problems giving out correct EDID information.

[http://www.mythtv.org/wiki/index.php/Modeline_Database#ModeValidation](http://www.mythtv.org/wiki/index.php/Modeline_Database#ModeValidation)
[http://www.gossamer-threads.com/lists/mythtv/users/203517?search_string=edid%20broken;#203517](http://www.gossamer-threads.com/lists/mythtv/users/203517?search_string=edid%20broken;#203517)
[http://www.mythtv.org/wiki/index.php/Special:Search?search=edid&go=Go](http://www.mythtv.org/wiki/index.php/Special:Search?search=edid&go=Go)
[http://www.gossamer-threads.com/lists/engine?list=mythtv&do=search_results&search_forum=forum_1&search_string=edid+broken&search_type=AND](http://www.gossamer-threads.com/lists/engine?list=mythtv&do=search_results&search_forum=forum_1&search_string=edid+broken&search_type=AND)

---

### Post by volkswagner on 2008-03-13
Mythbuntu was probably the quickest and easiest install by this newbie.  I do feel post install could have more documentation included with the install documents.  At least should point the installer what to do with things such as mysql password etc.  I guess the installer would need to refer to a standard myth install document to get this sorted.  I just feel it would be easier if the info was in one spot.

The install of Mythbuntu worked great for me on i386, and AMD64 version.  It worked well with Nvidia and ATI graphics.  It worked while connected to 26" LCD TV, 15"LCD monitor, and 27" CRT TV via s-vid (ati and nvidia).

One persons hardware setup and experience certainly can't create a general rule for the masses!

Mythbuntu Rocks!
The forum makes sure all can ENJOY the music!

Cheers

:guitar:

---

### Post by laga on 2008-03-13
> **volkswagner said:**
>  I do feel post install could have more documentation included with the install documents.  At least should point the installer what to do with things such as mysql password etc.  I guess the installer would need to refer to a standard myth install document to get this sorted.  I just feel it would be easier if the info was in one spot.


Maybe you/we can make a list with what's missing from the documentation so it can be extended?

---

### Post by majoridiot on 2008-03-13
> **laga said:**
> Maybe you/we can make a list with what's missing from the documentation so it can be extended?

this is a **CRUCIAL** issue central to making mythbuntu the best it can be- and sadly, often
the most overlooked as well.   i understand that it is human nature to complain when something
does not go as expected- or desired.  however, unless the mythbuntu devs and the people
writing the install docs and various guides are made aware of deficiencies or errors... or
corrections are not made by the people who find them, then the problems remain for others.

thread-starters like this one always get me riled, as all of the complaints of not being ready for
"jo in the streets" is beyond laughable.  the mythbuntu devs have done an **EXCEPTIONAL** job
of making mythtv more accessible to non-tech-geeks and have vastly improved not only the install
procedures, but also the environment itself.  maybe some changes and improvements have not 
come as quickly or perfectly as some people desire, but i absolutely guarantee you the difference 
between the first time i compiled and installed mythtv years ago and the last mythbuntu install i did 
are so beyond compare as to make complaints of install difficulties almost moot.  very few things 
go as smoothly as one would like.  i'm amazed how smoothly mythbuntu installs, given the 
dizzying array of hardware options out there.

ultimately, i guess the challenge would be for someone to name a better personal media server
that is as robust,  costs NOTHING, runs on an os that costs NOTHING, and is developed, 
maintained, documented and supported by people for FREE.

is mythbuntu perfect?  no.  will it ever be?  no.  can we all make it better? YES.  

how?

1.  choose the correct installation for your skill-set and  do a little research on your hardware, etc. before
the install, so you will better know what you might be facing, issue-wise.

2.  report problems in as much detail as possible in a positive manner

3.  if documentation, a wiki guide, etc. is incorrect, either let a dev/wiki maintainer know- or even better for wikis- 
make the correction yourself, if you have figured it out.

4.  support the community in every *positive* way possible

*<end of rant v1.0>*

---

### Post by uopjohnson on 2008-03-13
I'm not even sure mythbuntu's focus is on the 'joe off the street' sure it works great for them, but I, and many others I'm sure, migrated over after several years of using myth on man platforms from slackware to fedora.  I find the install and interface to be EXACTLY what I want, just the other day I got a frontend up and connected with all my usual plugins and preferences in a half hour.  That is inconceivably better than the weeks it used to take to build transcode dependencies by hand and track down obscure ivtv/kernal incompatibilities that made every install a custom job.  
I guess all that for a big thanks, both to the mythtv devs for their constant improvement and to the mythbuntu devs who had a great idea and have put it into practice perfectly.

---

### Post by thatkidandy on 2008-03-13
> **uopjohnson said:**
> That is inconceivably better than the weeks it used to take to build transcode dependencies by hand and track down obscure ivtv/kernal incompatibilities that made every install a custom job.  

SERIOUSLY. I tried fiddling with myth around 0.18 on top of Ubuntu 6.01 (?) and had lots of trouble with ivtv issues, etc. Not to mention all the trouble getting the (L)AMP part up and running secure as a first timer. 

Are you going to need to do your homework before building a mythbox? YES. With all the hardware choices you have to do some digging before you start...oh and since myth is at a **0.X** release state.

Regardless, mythbuntu is by far the easiest way to set up and maintain a mythbox out of all the options I've tried. The MCC is friggin brilliant.


To the OP:
1. There isnt a LIRCD auto-setup in ubuntu to my knowledge. Mythbuntu sets up your remote automatically. I am fairly positive your remote is supported. If not, this forum is where you could have asked...

2. MythTv setup is...mythtv. This is slightly more out of mythbuntu's control. Did you check out docs at mythtv.org? If there is a difference between the mythtv setup on a properly prepped ubuntu and mythbuntu...you've got me...

3. Again...MythTV is **0.X**. There is no way this is aimed at a Joe in the street. With a little reading, Mythbuntu can work practically 'out of the box'. Otherwise, shell out the $cash$ for Windows Media Center.

4. LCD Issues? dpkg-reconfigure xserver-xorg? If this doesn't work then it is a fault down to the kernel/ubuntu core...but I'd be super-surprized if it wasn't already supported with a little tweaking.

---

