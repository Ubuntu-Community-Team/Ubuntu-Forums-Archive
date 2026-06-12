---
title: "Kworld 115 ATSC Setup? Only One Channel?"
date: 2009-01-06
forum: Mythbuntu
---

### Post by MCrittenden on 2009-01-06
I installed MythTV via apt-get to a HDTV box running Ubuntu 8.10, and got it to recognize the card as described in the mythtv wiki, but I can't figure out what settings I should be using.

The most success I've found is by configuring the card as a v4l card and using us-cable (I'm a Charter customer on the east coast, so signal is coming straight from coax port in the wall to the tuner card), and that seems to recognize a lot of channels on the channel scan, but when I go to watch TV, each channel seems to be the same as all the others. That is, every channel listed (something like 2 to 125) outputs the same thing, so it's like it's not really changing channels. 

Any idea what I could be doing wrong here? I've just been pressing up and down on the keyboard to change channels in myth, is that right? Thanks!

---

### Post by ian dobson on 2009-01-06
Hi,

I think you need to configure the card as a DVB card then do a full channel scan.

Not sure about the keyboard shortcuts to change channels but arrow up/down sounds OK.

Regards
Ian Dobson

---

### Post by MCrittenden on 2009-01-06
According to the wiki at [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) you configure the card as two different devices, one DVB and one v4l. I haven't had much success scanning for channels using the DVB configuration, but I must be missing something somewhere. Do you know if it matters which of the two ports is being used?

---

### Post by MCrittenden on 2009-01-06
Looks like ATSC/QAM use the outside port, and NTSC uses the inside port, so I'll give the outside port a shot tonight and see if I can get anything. 

However, that still doesn't explain why I can't get any more than 1 channel on the analog port?

---

### Post by laceration on 2009-01-06
I have same exact card. You are correct about the position of the ports. When I first got it I did have cable.  I could not get this card to work with analogue.  I wasn't that interested in it and it won't exist soon anyways, so I did not try too hard, but I question if this card could do it.  For QAM I found out there was no way to way to get a signal from my [ex]cable co without decrypting with their box.  You should check with your cable co.  Some cable companies will not encrypt lower tier stations.  There is no way you will get HBO or ESPN out of the wall though. There is good chance they have the signal totally locked down.
Cable cos are about 1000x more closed source than MS Windows if you ask me.  I went to dvb over the air (which this card does well),  bit torrent and web video and haven't looked back.

---

### Post by MCrittenden on 2009-01-07
Wow, crap. Well so if you're doing DVB OTA, I guess you are using the outer port and configuring as a DVB device, using us-bcast and Terrestrial(vs8 or whatever it is)? I'm getting nothing so far like that but I'm also uing a cheap antenna which might have something to do with it.

---

### Post by newlinux on 2009-01-07
I am currently using the kworld 110 (basically same card) for both analog and digital capture (cable for both). I have an input set up as V4L and an Input set up as DVB. Which RF input is used for what is depends on which version of the driver you have (I've had them switch with upgrades). But on stock hardy it is as you have described above for me.

Try using the analog portion of the card outside of myth with tvtime. What channel is it outputting? What is in your logs when you try to change channels? 

Also, although HBO you will probably never get via unencrypted QAM, some places allow ESPN through unencrypted QAM. I used to even get the HD version of ESPN via unencrypted QAM, but now I only get the SD version. Where I am at the almost all the basic cable stations (1-99) are available via unencrypted QAM because they are doing away with a lot their analog duplicates to free up space for more HD channels.

Analog cable can be around a couple more years, the current analog deadline in February only applies to OTA broadcast. Cable companies can wait, if they want...

---

### Post by MCrittenden on 2009-01-07
Glad you're here! You seem to be everywhere this card is mentioned. I'll check it out in tvtime ASAP. Where are the logs I should be looking at? Or do I Just look at the output when myth frontend is run from a command line and I change channels?

---

### Post by newlinux on 2009-01-07
> **MCrittenden said:**
> Glad you're here! You seem to be everywhere this card is mentioned. I'll check it out in tvtime ASAP. Where are the logs I should be looking at? Or do I Just look at the output when myth frontend is run from a command line and I change channels?

I've had 3 of these cards (and a card with the same digital chip) for 2.5 years or so now, so I've gone through the "wars" as it were :) and tried to share my experience and help others.

If you start mythfrontend from the menu or with the --service option, your frontend logs will be in /var/log/mythtv (which is where you backend logs are too). You can also view the log in the method you described from the commandline.

In this case, you'll want to look at both frontend and backend logs. 

Also, what kernel are you running? There are known problems with analog capture and this card on the 2.6.25 kernel... But they are fixes you can try.

```
uname -a
```

will tell you your kernel version

---

### Post by newlinux on 2009-01-07
also, I'm curious about what channel your card is stuck on. See if it is a channel changing problem or a tuning problem. If it is always stuck on the start channel, perhaps you can see what happens when you change the start channel in mythtv-setup - see if it starts on a different channel. If so, at least you know it can sucessfully tune different channels, it's just having a problem changing channels.

---

### Post by MCrittenden on 2009-01-07
Kernel version is 2.6.27-9 I believe. I'll check tvtime and changing the start channel in the next hour. I'm pretty sure that it is stuck on the start channel now that you mention it. Thanks so much!

---

### Post by newlinux on 2009-01-07
one more thing... :) You may be able to find out what channels are available in your area from your provider via unencrypted QAM by checking:

[http://www.silicondust.com/hdhomerun/channels](http://www.silicondust.com/hdhomerun/channels)

---

### Post by MCrittenden on 2009-01-07
Wow looks like the lowest digital channel is 20 in my area and I never let the scan get that high before giving up. Hmm...

---

### Post by newlinux on 2009-01-07
> **MCrittenden said:**
> Wow looks like the lowest digital channel is 20 in my area and I never let the scan get that high before giving up. Hmm...

When using digital, Always do a full scan and let it complete (unless you already know where all the channels are located). The channels tend to be clustered in the higher frequencies. I takes a while. If anything, do a high frequency only scan...

---

### Post by MCrittenden on 2009-01-07
Well here's where I'm at. I was able to pick up quite a few QAM 256 and 64 channels using the inner (not outer like I thought it would be) port, which is awesome. Getting audio and everything. So that's good.

However, I'm still not getting any analog (now I can't even pick up that one channel), which is what I'm really after. Tried both ports, no luck. I'll keep plugging away and post some logs tonight if I can't get anywhere.

---

### Post by newlinux on 2009-01-07
did you try tvtime? What happens when you try to tune an analog station? Are you trying both inputs for analog?

---

### Post by MCrittenden on 2009-01-07
Here are the logs. Had to cut some from the beginning to fit in the file size constraint. Thanks again for all your help so far.

---

### Post by newlinux on 2009-01-07
Have you created video sources (different ones) for both the analog and digital inputs and bound them to the two inputs? How do you currently have your video sources and inputs set up?

---

### Post by MCrittenden on 2009-01-07
> **newlinux said:**
> Have you created video sources (different ones) for both the analog and digital inputs and bound them to the two inputs? How do you currently have your video sources and inputs set up?

Oops, sorry didn't realize you posted again before I put up the logs. Nope, I haven't had a chance to try tvtime so far. I will give it a shot tonight.

I followed the mythtv wiki page for the ATSC 110 for directions on setting up the two devices in myth. Basically, for analog, it's just a V4L device, with the only change from the default settings being to change the sampling device to 32000. For DVB, it's a DVB DTV capture card with the only change being to check the Open DVB card on demand box as described in the wiki page.

For video sources, I've just been doing try-all with DataDirect (or whatever it's called) as the grabber. When scanning, I've been trying the basic Cable frequency. How's that sound?

---

### Post by newlinux on 2009-01-07
You want two different video sources. One for analog stations, one for your digital stations. You want to V4L to be attached to one video source, and the digital to be attached to the other. The easiest thing to do in schedules direct is to create two lineups and then associate one of those lineups with your digital video source and the other with your analog. You can do it all with one schedules direct lineup (you'll still need two video sources in myth) but the steps to do that are a bit more complicated.

The reason you need two video sources is because the digital side and the analog side will tune different sets of channels - this is the only way to tell the analog side what channels it can tune and the digital side what channels it can tune.

Your logs indicate you haven't bound a video source to at least one of your inputs. 

also if you zip up your logs you can post more - I would want to see at least  all the stuff in between "Switching from None to WatchingLiveTV" and "Switching from watchingLiveTV to none" (or something like that)..

---

### Post by MCrittenden on 2009-01-07
Alright, but the video sources for each input will still have the same settings right? They're just identical but separate in order to let one input have one set of channels and the other input to have another set? If so, I'm pretty sure that's what I've been doing, but who knows! I'll check it out definitely. 

The reason it looks like one of my inputs doesn't have a video source is probably because whenever I've been testing an input, I removed the video source to the other input just to make sure that wasn't causing problems. 

Also, would schedules direct have any effect on the problems I'm having? I've just kind of been ignoring that part of it, thinking that it only affected the program listings, and didn't have anything to do with getting the picture.

EDIT: It's not possible that one port is being used for both digital and analog is it? I read a post by someone somewhere that said his system was doing that, so just checking.

---

### Post by newlinux on 2009-01-07
> **MCrittenden said:**
> Alright, but the video sources for each input will still have the same settings right? They're just identical but separate in order to let one input have one set of channels and the other input to have another set? If so, I'm pretty sure that's what I've been doing, but who knows! I'll check it out definitely. 

The reason it looks like one of my inputs doesn't have a video source is probably because whenever I've been testing an input, I removed the video source to the other input just to make sure that wasn't causing problems. 

Also, would schedules direct have any effect on the problems I'm having? I've just kind of been ignoring that part of it, thinking that it only affected the program listings, and didn't have anything to do with getting the picture.


I'm not sure what you mean by your video sources having the same settings. Which settings are you referring to? The easiest thing to do is to have them reference a separate Schedules direct lineup. So you should have 2 lineups in schedules direct. The login settings should be the same. Yes, the point is to allow different channels to be associated with different inputs (which is what will happen). This is exactly how my setup is.

I'm not sure if schedules direct will have something to do with it, but your video sources certainly will if you are having problems tuning certain channels. 

If you want to test them separately I think it would be better to delete the input you are not using, not remove the source. That's the cleanest way to test them separately.

Have you looked at the channels in your video sources to make sure they are right and available? 

Where are you now? Digital channels working fine, but analog not tuning at all or analog only staying on one channel? this information is important to know how to interpret the errors in your logs. So it would help to clarify what problems you are having, and post new logs and then detail what you tried to do at the time of those logs (what the logs are from).

---

### Post by MCrittenden on 2009-01-07
By both video sources having the same settings, I was referring to the login info for schedules direct and the option at the bottom (select try-all, us-cable, etc...can't remember what the option's called). So I should have two identical video sources, one for analog and one for digital, both pointing to the same schedules direct account. Got it.

So far, yes, digital channels tuning pretty well. I'm getting about 20 of them (probably 6 or 7 stations with multiple substations for each of them). I've tried using an old antenna to get an ATSC signal which didn't work but that was more out of curiosity than anything.

And no luck with analog at all. All the possible settings combinations I've tried so far have returned no signals on the station scan when using analog. This is obviously a step backward from yesterday when it locked on dozens of stations but I could only get it to display one of them, so I'm sure I screwed it up somewhere along the way. 

I'm almost positive that when I did get the one analog channel, I was using the inner input, and now I'm getting QAM on the inner port, so I don't know what happened there. Anyway, I'm at work now so I'll give it another go tonight and zip up some logs for you. Thanks again!

EDIT: Should I clear the current logs before I get home and start messing with it again? Or is it better for you to see everything at once?

---

### Post by newlinux on 2009-01-07
just show me the new stuff. And make sure to try both inputs for your analog cable... On mine QAM and analog cable are different inputs. QAM/ATSC on one, and NTSC on the other... But this is driver dependent...

---

### Post by MCrittenden on 2009-01-07
When I get this working then I'm sending you a car! :)

---

### Post by newlinux on 2009-01-07
> **MCrittenden said:**
> When I get this working then I'm sending you a car! :)

I'll take it, but not necessary :). I hope we do get it working. 

just to clarify, make sure you have two  separate lineups in your schedules direct account. Then associate the each lineup with a different video source. If you really only want to have one lineup for two different sources you can, but you need to follow this procedure:

[http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4](http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4)

I think for simplicities sake, YOu should start be deleting all tuners and video sources, and only create an analog tuner and source and try and get that working to start.

---

### Post by MCrittenden on 2009-01-07
When you say associate each lineup with a different video source, is that something that I do inside Myth? Or do I just give it a username and password and Myth automatically knows which lineup goes with which account? I know how to add multiple lineups in schedules direct, but I haven't seen a place to associate a certain lineup with a certain source.

---

### Post by newlinux on 2009-01-07
> **MCrittenden said:**
> When you say associate each lineup with a different video source, is that something that I do inside Myth? Or do I just give it a username and password and Myth automatically knows which lineup goes with which account? I know how to add multiple lineups in schedules direct, but I haven't seen a place to associate a certain lineup with a certain source.

In the place where you create your video source in mythtv-setup, after you enter your username and password, click "retrieve lineups" Wait a little bit, and then the dropdown below it (I think - it's somewhere on that page) will let you select which schedules direct lineup you want.

---

### Post by MCrittenden on 2009-01-07
Awesome. I get off in about an hour, will update then. Thanks again.

---

### Post by MCrittenden on 2009-01-07
Well, I deleted all video sources and devices in Myth, created a new V4L device (and only changed audio sampling rate), created a new video source (using us-cable instead of try-all this time), retrieved the listings from the website, and then ran a channel scan on V4L (Television input) using that video source. Got nothing. So deleted everything again, switched the cable to the other input, then went through the whole process again, and got nothing on the scan again. Here's the log from all of that (frontend log is empty since I didn't open frontend):

[http://dl.getdropbox.com/u/141679/mythbackend.log](http://dl.getdropbox.com/u/141679/mythbackend.log)

And it looks like a channel scan in tvtime isn't getting anything either. Tried both ports there too. I checked to see if there was a myth backend process keeping priority over the tuner or anything like that and didn't see anything. So that's where I'm at now. I'll try a few more things in the meantime.

EDIT: The channels are all static in frontend but at least the listings are showing up. Gotta love cheap thrills :)

---

### Post by newlinux on 2009-01-07
probably gotta turn up the verbosity of the backend log. Not much useful there. Yeah, you will want to stop the backend before using tvtime.

A couple things. 

1. You actually don't need to run a channel scan for analog stations. I never do. I just download the channels from the listings source (assuming you selected the channels you want/get in schedules direct already). When the tuner is working it will tune those channels without scanning first.

2. After doing 1 (retrieving the channels this option should be on the same page as the scan) run the frontend and try to tune the stations. Need to see what the frontend log says when trying to tune, as well as the backend.

3. do you have any other tuners in this machine? A web cam or anything of the sort?

Let's get some basic information.

what does:

```
dmesg | grep -i saa713
```

return?

---

### Post by MCrittenden on 2009-01-08
Is the verbosity turned up in general settings or somewhere else? 

About the channel scan, it just seems like that would be a little faster way to tell if it's getting anything than to exit mythtv-setup, run mythfilldatabase, open up frontend, and then try tuning a channel, but I'll be sure to try tuning from now on if you need to see what happens on the logs when I do that. Thanks for the tip.

Nope, I don't have any other tuners or a webcam or anything unfortunately.

How do I know if mythbackend is running (and stop it to use tvtime)? It seems like it always is but I can't ever spot it on the process list, unless it has a weird name.

I'm at work again right now, so I'll run the dmesg when I get home and give you the output.

Sorry I have so many questions! Thanks again!

---

### Post by MCrittenden on 2009-01-08
Double post, sorry.

---

