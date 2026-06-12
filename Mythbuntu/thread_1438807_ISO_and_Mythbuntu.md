---
title: "ISO and Mythbuntu"
date: 2010-03-25
forum: Mythbuntu
---

### Post by kdx7214 on 2010-03-25
Okay, absolute beginner here with MythBuntu although I had a successful MythTV setup with 0.21 several years ago.

I have installed 9.04, 9.10, and now the 10.4 beta 1 mythbuntu distro and cannot rip DVDs or play ISO files - which is the main reason for this machine.

I have followed the instructions provided in the faq (i.e. filled in myth's video folder as separate from the storage group, have deleted the storage group, etc.) and still no dice.

Right now I have 10.4 installed and can copy a .iso file into the folder (default install - in storage group) but nothing shows up.  Yet I can copy .mp3 and .jpg files into their respective stores and works just fine.

Can someone give me a hint on where to look next?  If I had hair I'd be ripping it out by now.

Thanks!
Mike

Oh, one other thing.  When I go to rip a DVD it never starts.  It always says "Waiting on DVD" and just sits there.

---

### Post by klc5555 on 2010-03-25
> **kdx7214 said:**
> Oh, one other thing.  When I go to rip a DVD it never starts.  It always says "Waiting on DVD" and just sits there.

OK, depending on the mythbuntu version of the moment, you need to install all the various proprietary medibuntu codecs for handling dvds, done from the mythbuntu control center (or separately by downloading the .deb packages from [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and installing them using the gdebi installer)

If the codecs are installed, you may need to add particular file extensions (e.g.. ".iso", ".ogg", ".ogv", etc.) to the list of recognized file extensions in the player settings in the frontend setup.

If the dvd drive is simply not being recognized at all by myth (even though you installed successfully from the drive), then myth may be looking for /dev/dvd while your machine thinks it actually has /dev/sr0. Depending on myth version du jour (9.04) you will need to change the location of the dvd drive in the frontend "general settings" from "/dev/dvd" to "/dev/sr0" or (for 9.10 -> ?) checkmark the default unchecked "use new media" setting in about p. 7 of the frontend "general" settings, which is reported to also do the job.


Even under the best of circumstances mythtv's dvd ripping capabilities are far from perfect and very frequently have to be supplemented with other 3rd-party tools. But hopefully after this you'll be able to rip more media and less hair.

---

### Post by kdx7214 on 2010-03-25
> **klc5555 said:**
> OK, depending on the mythbuntu version of the moment, you need to install all the various proprietary medibuntu codecs for handling dvds, done from the mythbuntu control center (or separately by downloading the .deb packages from [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and installing them using the gdebi installer)

If the codecs are installed, you may need to add particular file extensions (e.g.. ".iso", ".ogg", ".ogv", etc.) to the list of recognized file extensions in the player settings in the frontend setup.

If the dvd drive is simply not being recognized at all by myth (even though you installed successfully from the drive), then myth may be looking for /dev/dvd while your machine thinks it actually has /dev/sr0. Depending on myth version du jour (9.04) you will need to change the location of the dvd drive in the frontend "general settings" from "/dev/dvd" to "/dev/sr0" or (for 9.10 -> ?) checkmark the default unchecked "use new media" setting in about p. 7 of the frontend "general" settings, which is reported to also do the job.


Even under the best of circumstances mythtv's dvd ripping capabilities are far from perfect and very frequently have to be supplemented with other 3rd-party tools. But hopefully after this you'll be able to rip more media and less hair.


Okay, I have done this with the exact same results.  The .iso files don't show up.    Didn't think about the codecs but have enabled them now.  In reality all I really want to be able to do is to copy the darn ISO files into the folder and play them through the Hauppage PVR350 card I have to a tv.  I'll continue to play with this but if you have other suggestions please let me know.

Thanks!
Mike

---

### Post by tgm4883 on 2010-03-25
ISO's do not work with Storage groups. [http://www.mythbuntu.org/wiki/faq](http://www.mythbuntu.org/wiki/faq)

---

### Post by kdx7214 on 2010-03-25
I am aware that ISO does not work with storage groups.  However I'm not sure that's all of the issues here.

For instance, I can now rip a DVD provided I remove all protection first (i.e. dvdshrink and burn it).  It puts the file in the same place I am putting others.  None of them show up as options in the player - so I can't even tell if it is working or not.

Also, I am using 10.04 beta which supposedly does support ISO unless I misread the readme.

---

### Post by williammanda on 2010-03-25
> **kdx7214 said:**
> Also, I am using 10.04 beta which supposedly does support ISO unless I misread the readme.

I just read today iso is not supported till ver .24. From [http://www.mythtv.org/wiki/MythVideo](http://www.mythtv.org/wiki/MythVideo)

>  Storage Groups

Videos in Myth can now be stored on the backend and streamed to the frontend without a NFS or Samba mount. It is critical to note that the Storage Group implementation is not complete, and to take that into consideration when weighing whether to move to MythVideo Storage Groups. **Hopefully the transition to Storage Groups will be complete for MythTV .24, so this should be taken as a technology preview release only.** 

>  Disadvantages

    * External Video Players (mplayer, xine, VLC) will not work with videos hosted on an SG.
    * **ISO/VIDEO_TS Playback does not presently work in Storage Groups.** 

---

### Post by kdx7214 on 2010-03-25
Okay, even though I've disabled the storage groups and all that, I'll bite.

What version of this thing do I have to download and install to get rid of the storage group nonsense and get a working system?

For a system supposedly designed to help beginners get started with MythTV I would expect it to include only stable and working code.  If a person knows enough to download and install the beta (i.e. not yet working) stuff, then let them do that and not mess up the distro.

---

