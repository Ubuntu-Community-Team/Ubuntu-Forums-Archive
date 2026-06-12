---
title: "Some n00b questions, hopefully easy ones"
date: 2009-03-05
forum: Mythbuntu
---

### Post by SirVilhelm on 2009-03-05
I am sick of paying $18/month for a crappy Cox HD-DVR, my friend suggested I try out MythTV and loaned me some hardware just to do a proof of concept. I loaded up Mythbuntu and went geek crazy. So far the experience has been a good one. I have very little Linux experience but usually figure things out after spending time tinkering with it.

So, I have a couple questions.

1.) I am currently using the Hauppauge HVR1600 1101. When I plug the coax directly into the TV I get a decent SD picture. But when I plug the same coax cable into the turner card the picture seems very degraded. It looks fuzzy and skips frames. Now I know there are a lot of little tweaks I can be doing but like I said, I have very little experience. Can someone point me in the correct direction.

2.) On the top of the screen I get a horizontal line about 2 pixels deep of what looks like noise. Is there a way to crop that off? I went into the screen wizzard and moves the brackets down a bit but all that did was resize the screen, not crop.

3.) The Hauppauge HVR1600 1101 comes with a USB IR receiver and remote. I've tried all the built in Hauppauge drivers and the Media Center drivers (since it is technically for Windows Media Center) and nothing seems to work. There is a red LCD that lights up on the receiver when I push buttons on the remote but that's it. Are there additional drivers I am missing?

4.) Video/Music library - Is there a way to setup multiple directories for the multimedia directories? I see where I can specify one directory for each Video and Music libraries but I have multiple DNS-323 NAS devices that I want to be able to pull music and video from.

5.) Netflix - How do I set it up? I can view movies they offer but I don't see how I can actually view them? I am sure it's something simple.

6.) Is there a plugin that will automatically encode a recorded show to AVI and dump it to a network share?


This is all I can think of for now. I really appreciate any feedback. I will be testing Windows 7 Media Center next but do to DRM I don't think that will be what I am looking for. Hopefully I can figure this out and make everything happy. 

My only disappointment is getting cable HD doesn't seem to be an easy task. IE HBO HD.

---

### Post by cb951303 on 2009-03-05
I'm not really experienced on mythtv but I know the answers to couple of your questions, so here we g:popcorn:

3) IR is handled by an application called "lirc" [http://www.lirc.org/](http://www.lirc.org/) I would check out their wiki/forum/maillist etc
5) I hear netflix doesn't support linux sorry
6) What do you mean by encoded? Mythtv already encodes the recorded videos otherwise 1 movie would take half of a HDD :D
Best way to to share your recorded videos is to install and setup samba server. You can directly share the directory where mythbuntu saves recorded files and voila!

---

### Post by SirVilhelm on 2009-03-05
> **cb951303 said:**
> 
6) What do you mean by encoded? Mythtv already encodes the recorded videos otherwise 1 movie would take half of a HDD :D
Best way to to share your recorded videos is to install and setup samba server. You can directly share the directory where mythbuntu saves recorded files and voila!

Ok, guess I need to jump in that directory and see what format it saves them as. I just assumed that it saved the files as some weird file format.

---

### Post by cb951303 on 2009-03-05
> **SirVilhelm said:**
> Ok, guess I need to jump in that directory and see what format it saves them as. I just assumed that it saved the files as some weird file format.

from mythtv docs:
> 
For cards without hardware encoding capabilities (all cards supported by V4L not listed above), Myth includes two methods for software encoding: RTjpeg and MPEG-4. RTjpeg has significantly fewer CPU demands than MPEG-4, but it generates larger files than MPEG-4 for a given recording.

For DVB and HDTV cards, no further configuration is required after setting up the card using the 'mythtv-setup' program. For all other cards, configuration is done through MythFrontend. Selecting 'Recording Profiles' from the 'TV Settings' screen will list the profiles currently available for the cards in your system. Depending on what types of cards you have installed you may see:

    (Create new profile group)
    Software Encoders
    Hardware MPEG Encoders
    Hardware MJPEG Encoders
    Transcoders


I'm guessing the file format is avi, or maybe ogv :)

---

### Post by boof1988 on 2009-03-05
> **SirVilhelm said:**
> 
3.) The Hauppauge HVR1600 1101 comes with a USB IR receiver and remote. I've tried all the built in Hauppauge drivers and the Media Center drivers (since it is technically for Windows Media Center) and nothing seems to work. There is a red LCD that lights up on the receiver when I push buttons on the remote but that's it. Are there additional drivers I am missing?

I'm using Mythbuntu 8.10 with the Hauppauge HVR-1600.  The remote (labelled "RC 6") works... but I need to select "Windows Media Center Remotes (old version Microsoft USB ID" in the Infrared Devices menu (in MCC) to get it to work. 

> **SirVilhelm said:**
> 5.) Netflix - How do I set it up? I can view movies they offer but I don't see how I can actually view them? I am sure it's something simple.


My understanding is that the Netflix feature in Mythbuntu allows the viewing (and possibly editing?) of the user's Netflix queue.  So I don't think there is a watch-it-now feature for Netflix in Mythbuntu.

Someone else please correct me if I'm wrong on these.  I can't remember where I read about the Netflix stuff.

---

### Post by SirVilhelm on 2009-03-05
> **boof1988 said:**
> I'm using Mythbuntu 8.10 with the Hauppauge HVR-1600.  The remote (labelled "RC 6") works... but I need to select "Windows Media Center Remotes (old version Microsoft USB ID" in the Infrared Devices menu (in MCC) to get it to work. 

I tried that option but no go, do I have to bounce the box or restart the frontend? I went through and tried both Windows Media Center options and all Hauppauge options without any luck.

---

### Post by boof1988 on 2009-03-05
> **SirVilhelm said:**
> I tried that option but no go, do I have to bounce the box or restart the frontend? I went through and tried both Windows Media Center options and all Hauppauge options without any luck.

I am really sorry that I don't have an answer for this question... my remote (RC 6 , black plastic body with a green "Windows" media button in the center) worked OOB with the settings indicated in my earlier post.  Maybe a restart will do the trick??  *dunno*

If you can't get it configured automatically... maybe try the [mythbuntu-lirc-generator](http://packages.ubuntu.com/source/gutsy/mythbuntu-lirc-generator).  I played around with mythbuntu-lirc-generator before I figured out that my remote worked OOB with the weird menu choice {Windows Media Center Remotes (old version Microsoft USB ID)}.

Does your remote have a gray or black plastic body?

---

### Post by newlinux on 2009-03-05
1. You will want to play with your playback profile settings:

[http://www.mythtv.org/wiki/Playback_profiles#Default_profiles](http://www.mythtv.org/wiki/Playback_profiles#Default_profiles)
What kind of GPU/CPU are you using? To specifically trouble shoot it, we'd probably need to see your playback logs. There are many other things you can look into as well... but try some of those out first.

2. In the playback settings you can move and/or stretch the screen - I think it is on the second page of TV playback settings.

4. Separate your directories with a : (no spaces e.g. /videos:/nas/videos). you will need to make sure the directory you are specifying is local to the machine or mounted.

6. Digital captures are usually mpeg-2. Software encoded analog captures are either RTJPEG or MPEG-4 (depends on your recording profile settings) wrapped up in a .nuv container. Hardware encoded analog captures can be various encoding formats in an mpeg-2 container (depends on your recording profile).

What device are you trying to share the recordings with? Mythtv has a UPnP server that automatically shares your recordings. A samba share would work. 

If you need a different file format you can set up transcoding profiles within myth and have them automatically kick off on a per recording basis. You can also use nuvexport or mytharchive, depending on your needs.

If you use the samba share method, you may want to look into "mythrename.pl" for some human readable names instead the format they are in by default.
[http://www.mythtv.org/wiki/Mythrename.pl](http://www.mythtv.org/wiki/Mythrename.pl)

---

### Post by SirVilhelm on 2009-03-05
> **boof1988 said:**
> 
Does your remote have a gray or black plastic body?

Black, sounds exactly like the one you are using. I will continue my efforts on getting it to work since I now know that someone else has it working.

---

### Post by SirVilhelm on 2009-03-05
> **newlinux said:**
> 
What device are you trying to share the recordings with? Mythtv has a UPnP server that automatically shares your recordings. A samba share would work. 


Wow, so much great information. Can't wait to get out of work so I can go home and try all this!

I am specifically wanting to share the media with three Xbox360's that I have in the house. I run TwonkyMedia on the Dlink NAS which does a good job streaming my media.

The main reason I want to throw all this on the NAS devices is for storage. I don't want to throw a bunch of huge drives in the Myth box if I don't have to.

---

### Post by newlinux on 2009-03-05
> **SirVilhelm said:**
> Wow, so much great information. Can't wait to get out of work so I can go home and try all this!

I am specifically wanting to share the media with three Xbox360's that I have in the house. I run TwonkyMedia on the Dlink NAS which does a good job streaming my media.

The main reason I want to throw all this on the NAS devices is for storage. I don't want to throw a bunch of huge drives in the Myth box if I don't have to.

In that case, if your network will support it, you could just record directly over the network to the NAS...

---

### Post by SirVilhelm on 2009-03-05
> **newlinux said:**
> In that case, if your network will support it, you could just record directly over the network to the NAS...

I run everything at Gb, think that is enough? Should be for SD but not sure about HD

---

### Post by newlinux on 2009-03-05
> **SirVilhelm said:**
> I run everything at Gb, think that is enough? Should be for SD but not sure about HD

It should be enough. Unless you have a really really bad GB network :). The HDHomeruns do   recording over the network (and are HD capable) and only have 100Mbps network ports. Your only concerns would be how much other network traffic you have going on...

---

### Post by newlinux on 2009-03-05
also for HBOHD - you can look into firewire (although that channel is most likely 5c encrypted which would block firewire) but for a while I was able to capture premium channels in full digital HD quality via firewire. Just something to look into if you feel like tinkering. Then you could just have a regular set top box and record from it directly.

Also, the Hauppage HD-PVR (a little pricey) can capture HD-quality directly from the component output. but the Linux and myth drivers are still early on. But you don't have to worry about encryption there...

---

