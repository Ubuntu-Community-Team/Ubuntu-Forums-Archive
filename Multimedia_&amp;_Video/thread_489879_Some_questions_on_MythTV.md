---
title: "Some questions on MythTV"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by CSMatt on 2007-07-01
I'm thinking of building a MythTV box to replace my TiVo, mostly because I'm not comfortable with TiVo's anonymous reporting on my usage. It's also a pain to archive recordings to DVD by having to import them into my computer with TiVoToGo first, and I would prefer an integrated solution like the MythArchive plugin promises (yes, I know about the HUMAX recorders, but I can't transfer my lifetime subscription from my Series2 DT to another device).  However, before I invest time and money into MythTV, I have a few basic questions that I am hoping that someone with MythTV experience could answer.  I know that this isn't a MythTV forum, but I couldn't find an official forum to ask questions on.

[LIST=1]
[*]The two features I use on the TiVo the most are the Season Pass and the WishList for movies on cable.  I have a feeling that a Season Pass equivalent exists with MythTV, but I don't know if the scheduler is smart enough to skip duplicates, or what it considers to be a duplicate.  I remember that the TiVo OS is able to detect if a Season Pass recording is deleted without being watched at least once and will thus not count a future airing of that episode as a duplicate.  Does MythTV behave in a similar fashion?
[*]Is there any way that MythTV can search the program listings to find movies?  I'm just talking about finding anything listed by Tribune as a movie and displaying it in a list for be to look up.  I used a WishList on TiVo for this, and I'm not expecting the more detailed WishList-like features in MythTV (like actor or director search), but I was wondering if something as vague as a search for any upcoming movies was possible?
[*]I cannot connect my box to an Ethernet connection because the router is in another room and my house does not have Ethernet jacks in the walls.  Can I use a USB wireless device with my MythTV box?  I will be using Ubuntu for the underlying OS, so this is more of an Ubuntu question.  I'd prefer not to have to use a wireless PCI card because I want a slim case and this will limit the number of PCI cards I can have.
[*]How much processing power is used for archiving recordings to DVD?  I will be using hardware-encoding tuners to reduce CPU usage, but the transcoding done by MythArchive will no doubt require a good amount of power.  My box will be a combined frontend/backend setup, so I want it to be as quiet and as power saving as possible and do not want a machine that is too powerful.
[*]How much electrical power is a MythTV box generally going to use?  Given my inability to coax Ubuntu into standby or hibernate mode successfully, I don't anticipate being able to use the ACPI startup/shutdown feature.
[/LIST]

---

### Post by tgm4883 on 2007-07-01
> **CSMatt said:**
> I'm thinking of building a MythTV box to replace my TiVo, mostly because I'm not comfortable with TiVo's anonymous reporting on my usage. It's also a pain to archive recordings to DVD by having to import them into my computer with TiVoToGo first, and I would prefer an integrated solution like the MythArchive plugin promises (yes, I know about the HUMAX recorders, but I can't transfer my lifetime subscription from my Series2 DT to another device).  However, before I invest time and money into MythTV, I have a few basic questions that I am hoping that someone with MythTV experience could answer.  I know that this isn't a MythTV forum, but I couldn't find an official forum to ask questions on.

[LIST=1]
[*]The two features I use on the TiVo the most are the Season Pass and the WishList for movies on cable.  I have a feeling that a Season Pass equivalent exists with MythTV, but I don't know if the scheduler is smart enough to skip duplicates, or what it considers to be a duplicate.  I remember that the TiVo OS is able to detect if a Season Pass recording is deleted without being watched at least once and will thus not count a future airing of that episode as a duplicate.  Does MythTV behave in a similar fashion?
[*]Is there any way that MythTV can search the program listings to find movies?  I'm just talking about finding anything listed by Tribune as a movie and displaying it in a list for be to look up.  I used a WishList on TiVo for this, and I'm not expecting the more detailed WishList-like features in MythTV (like actor or director search), but I was wondering if something as vague as a search for any upcoming movies was possible?
[*]I cannot connect my box to an Ethernet connection because the router is in another room and my house does not have Ethernet jacks in the walls.  Can I use a USB wireless device with my MythTV box?  I will be using Ubuntu for the underlying OS, so this is more of an Ubuntu question.  I'd prefer not to have to use a wireless PCI card because I want a slim case and this will limit the number of PCI cards I can have.
[*]How much processing power is used for archiving recordings to DVD?  I will be using hardware-encoding tuners to reduce CPU usage, but the transcoding done by MythArchive will no doubt require a good amount of power.  My box will be a combined frontend/backend setup, so I want it to be as quiet and as power saving as possible and do not want a machine that is too powerful.
[*]How much electrical power is a MythTV box generally going to use?  Given my inability to coax Ubuntu into standby or hibernate mode successfully, I don't anticipate being able to use the ACPI startup/shutdown feature.
[/LIST]

1.  I know there is a wishlist and a season pass.  It doesn't as of this version know that you have watched a show or not, but this has been implemented in .21

2.  I believe that number 2 is possible.  Im pretty sure you can have it record things based on a search of the description (ie actors name)

3.  Check working in Ubuntu first.  If it works in ubuntu, it should work in mythtv.

4.  This depends on how you are archiving it.  Hardware encoders generally record straight to mpeg2 which is dvd format.  You can also archive to mythtv format.  Both of these shouldn't require that much extra processing power.  If your transcoding also, then i'm not sure.  Although a 64-bit system would help in this department.

5.  ???

---

### Post by PilotJLR on 2007-07-01
Transcoding to DVD takes about 2 hours for a 1 hour HDTV program for me... on the cheapest Core 2 Duo I could buy. During this time, everything works, but the CPU will stay at 100% til it's done.

Power wise... entirely a function of your hardware. One or two hard disks and a reasonable processor don't take much energy.

---

### Post by newlinux on 2007-07-02
1. There are already a couple of third party mythtv plugins that do this. TVwish is a commandline one.

2. You can definitely do this I search just for movies, premiers, and various other things all the time using mythweb. You can do searches of descriptions, subtitles, titles, categories, much like tivo...

3. as previously stated, if it works with ubuntu...

4. as previously stated. what processor and how much RAM?

5. It doesn't take an extermely powerful system...

---

### Post by CSMatt on 2007-07-02
This is what I've been thinking of getting for the box, to answer your question regarding the hardware.  I haven't yet choosen a hard drive or an optical drive though.

---

### Post by tgm4883 on 2007-07-03
Couple recommendations.

1st, you have enough power.  I would have gone with a Core 2 Duo, but this will work.  If you plan on transcoding your shows or movies I recommend the 64-bit version.  Works great on my X2

2nd, this setup only has 2 pci slots.  I see you have 2 PVR 150's.  I would recommend that you get a PVR 500.  Basically it is 2 PVR 150's on one card.  It's roughly the same price as the two cards and will allow you to upgrade in the future.  (When you get to HD, streaming HD over a firewire connection via a STB works pretty well.  And you will need that extra space for a firewire card.)

3rd,  I recommend the MCE remote over the PVR 150 remote.  I have both and the MCE remote not only has more buttons, but is also better build quality.

---

### Post by roncrump on 2007-07-03
> **CSMatt said:**
> 
3. I cannot connect my box to an Ethernet connection because the router is in another room and my house does not have Ethernet jacks in the walls. 


Have you considered ethernet over power (HomePlug)? All that requires are free power points.

I have an XP computer sitting in a wireless blackspot connected to my router via HomePlug; rock solid, quicker than 802.11g wireless.

Ron.

---

### Post by CSMatt on 2007-07-03
> **tgm4883 said:**
> I see you have 2 PVR 150's.  I would recommend that you get a PVR 500.  Basically it is 2 PVR 150's on one card.  It's roughly the same price as the two cards and will allow you to upgrade in the future.  (When you get to HD, streaming HD over a firewire connection via a STB works pretty well.  And you will need that extra space for a firewire card.)

3rd,  I recommend the MCE remote over the PVR 150 remote.  I have both and the MCE remote not only has more buttons, but is also better build quality.
I've heard that there were some [quality problems with the PVR 500](http://mythtv.org/wiki/index.php/Hauppauge_PVR-500#User_Experiences) over on the MythTV Wiki, so that's why I went with two PVR-150s.  There's already a FireWire plug in the front of the case for streaming, so I don't need to worry about FireWire although the cord plugging into the front of the case from the back will admittedly look rather ugly.  I would have used [this motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131014&Tpk=Asus%2bM2NPV-VM) and an HTPC case, but all of the HTPC cases look like there as big as most mid-end surround sound receivers.  I want mine to be the size of a standard appliance.  Unless you can recommend a small case that would be adequate, I'm probably going to go with the barebone.
> **roncrump said:**
> Have you considered ethernet over power (HomePlug)? All that requires are free power points.

I have an XP computer sitting in a wireless blackspot connected to my router via HomePlug; rock solid, quicker than 802.11g wireless.

Ron.
I haven't heard of those.  Where can I find one?

---

### Post by newlinux on 2007-07-03
You can find them at best buy type stores. Dlink and Netgear make a few models. There is also a competing powerline technology, called DS2. Both netgear and Dlink make adapters too. I've used hte Netgear DS2 based product, and it worked pretty well in some places in my home (how well they work depend onyour wiring and other "environmental" factors so they will work better in some outlets than others).

---

### Post by roncrump on 2007-07-05
> **CSMatt said:**
> 
I haven't heard of those.  Where can I find one?

[Netcomm]("http://www.netcomm.com.au") do it in Australia, but I presume there is other equivalent gear elsewhere. Shoving Homeplug into google throws up a heap of stuff.

Ron.

---

### Post by teet on 2007-07-06
4.  I have a PVR-150 that I set to record at 720x480 resoution with the DVD-2 Special setting.  I first edit my recording by marking all the commercials.  Then I "transcode" my recording.  I have "transcode" set up to splice out the commercials WITHOUT re-encoding anything.  This only takes 1-2 minutes to do as compared to several hours if I were to reencode.  Next I use mytharchive to burn to disc.  Again, I choose not to re-encode the video since it is already in DVD standard format.  I do, however, have to reencode the audio (myth records it in MP3 but it needs to be in AC3 or something).  It probably takes 30-45 minutes to go through the whole mytharchive process.  

-teet

---

### Post by gheywood on 2007-07-06
> **teet said:**
> 4.  I have a PVR-150 that I set to record at 720x480 resoution with the DVD-2 Special setting.  I first edit my recording by marking all the commercials.  Then I "transcode" my recording.  I have "transcode" set up to splice out the commercials WITHOUT re-encoding anything.  This only takes 1-2 minutes to do as compared to several hours if I were to reencode.  Next I use mytharchive to burn to disc.  t


If this facility to remove adverts part of MythTV??

---

### Post by tgm4883 on 2007-07-06
> **gheywood said:**
> If this facility to remove adverts part of MythTV??

MythTV can be set to auto flag for commercials.  Depending on the type of show it may miss some (Saturday Night Live) but it usually gets most if not all of them.  Then when your watching shows, it can auto skip commercials if you want.

Then Mytharchive can load this commercial flagging list (or you can set the splices yourself) and when you burn to  DVD, voila, no commercials.

---

### Post by teet on 2007-07-06
> **tgm4883 said:**
> MythTV can be set to auto flag for commercials.  Depending on the type of show it may miss some (Saturday Night Live) but it usually gets most if not all of them.  Then when your watching shows, it can auto skip commercials if you want.

Then Mytharchive can load this commercial flagging list (or you can set the splices yourself) and when you burn to  DVD, voila, no commercials.

Exactly.  The commercial detect is pretty good, but it seems to miss at least 1 commercial break on most shows.  Often, it will miss the break before the last 30 seconds of the show.

You could always watch the show the first time with autoskip turned on.  If you find that myth detected all the commercials, you can just open the show, hit "E" to enter edit mode and then "Z" to import the commercial cut list (I think "Z" is the right key...it's not right in front of me).  The just choose to transcode and BOOM! you have a video file with no commercials.  It can really help save on space.

-teet

---

### Post by gheywood on 2007-07-06
Probably a dumb question, but how does it actually know what is a commerical break?

---

### Post by tgm4883 on 2007-07-06
> **gheywood said:**
> Probably a dumb question, but how does it actually know what is a commerical break?

From MythTV Wiki
> Commercial Flagging
From MythTV
Jump to: navigation, search

This detection method uses information from blank-frame, scene change, and logo detection and can easily be modified to take advantage of other detection information. It works in a fundamentally different way than the normal blank-frame and scene change methods. The code groups the frames into blocks separated by blank frames and rates each block based upon several factors such as the rate of scene change, what percentage of frames in the block have a logo present, how long/short the block is, etc.. Indications that a block is part of a commercial (such as very high rates of scene changes) lower the block's score, while indications that a block is part of the show (such as having a logo present on most frames) raise the block's score. In the end the blocks are looked at as a group and various bits of logic applied to make the final determination where commercials start and end. On most of the shows tested, this method seems to be doing a much better job than just blank-frame or blank-frame plus scene-change.

See: Commflagging 

Commflagging
> Commflagging
From MythTV
Jump to: navigation, search

This is the process by which MythTV detects commercial breaks in recorded shows and marks jump points in the database so that such breaks can be skipped (or later cut out of the recording during transcoding).
[edit]
Configuration

Commflagging can be configured within the 'General' page of 'Utilities/Setup > Setup > TV' in mythfrontend.

Setting the 'Commercial flag new recordings' tickbox enables commflagging for all subsequent recordings that take place on channels which are not set to 'commercial free'.

Commercial skip method: A variety of different methods can be used to detect commercial breaks.

    * Blank Frame Detection - is used to determine when a programme fades to black (this invariably happens between show segments)
    * Blank Frame & scene change detection - as above but tries to determine that a large amount of the picture has changed
    * Scene change detection - tries to determine that a large amount of the picture has changed
    * Logo detection - looks for a part of the picture that does not change during a recorded show - i.e. an onscreen logo. Logos are usually removed for the duration of commercial breaks, making them 'easier' to spot.
    * All - use all commercial detection methods at the same time 

An additional option - 'Strict Commercial Detection' - tightens up the rules used to detect commercials. This should be disabled if commercials are not being detected & marked.

Note: 'Automatically flag commercials' in a show's recording options must be enabled for any method other than 'blank frame detection' to work. That is to say, only blank frame detection flagging will work if commflagging is run as a job at a later date.
[edit]
Usage

Once recordings in MythTV have been flagged for commercials (commflagged), ad-breaks can be skipped.

During playback

The End or Z key (by default) jump to the next commercial break marker. The Home or Q (by default) key will jump back to the previous commercial break marker.

Commercial skipping can be enabled on a show-by-show basis by bringing up the OSD menu during playback and selecting a commercial skipping option. Choices given are:

    * Off - i.e. do nothing when markers are reached
    * Notify but do not skip - indicate that a commercial marker has been reached
    * Skip automatically - skip between markers automatically 

As a default option

Within the 'TV playback' section in mythfrontend's setup menus, there is a 'Commercial Skip' settings page.

Here the options for default actions on commercial flagged recordings can be set:

    * Automatically Skip Commercials: Off, Notify but do not skip, Skip Automatically 

    * Commercial skip auto-rewind amount: automatically rewind 'x' seconds after performing a commercial skip 

    * Commercial skip notify amount: announce a commerial marker has been detected 'x' seconds before the marker 

    * Skip blank frames after commercials: Automatically skip past the blank frames at the end of a commercial break 

---

### Post by gheywood on 2007-07-06
Superb. Thanks for that.

---

### Post by djchandler on 2007-07-06
> **roncrump said:**
> Have you considered ethernet over power (HomePlug)? All that requires are free power points.

I have an XP computer sitting in a wireless blackspot connected to my router via HomePlug; rock solid, quicker than 802.11g wireless.

Ron.

Another solution may be a little more messy, but it works in my home. If you have central air/heating, have you considered stringing cable through the ductwork? That way you do not have to drill holes in walls and/or floors. I just get the cable down into my basement, then string it just like all the electrical and telephone wiring is done. I keep my router, ethernet switch, and dsl modem in the basement, which does make this easier, and less cluttered upstairs. Exit of cabling is through the air vents in each room. A little prying with a big screwdriver on the sheet metal in the basement below that vent allows the the entrance. You can hammer the sheet metal tight around the cable easily. Mind you this is a one story house with full basement about 60+ years old. I've been doing this since I first cabled the house for 10base-2 about 16 years ago. (That's coax for you youngsters. Everything wired in series, and terminated on both ends. Detecting loose connections was a pain, and dropping a  computer in or out was as well.) It sort of looks okay upstairs if you can color coordinate and/or hide the cat5 cable. I don't trust wireless, and probably never will. I am looking forward to hard-wired gigabit ethernet too. :twisted:

DJ

PS You should probably be a homeowner to do this. If you aren't, it could void your lease or rental agreement, but this causes less modification than other cabling schemes.

---

