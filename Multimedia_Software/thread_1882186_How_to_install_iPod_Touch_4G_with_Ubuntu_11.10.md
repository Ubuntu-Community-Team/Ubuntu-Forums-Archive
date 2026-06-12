---
title: "How to install iPod Touch 4G with Ubuntu 11.10?"
date: 2011-11-16
forum: Multimedia Software
---

### Post by bliffle on 2011-11-16
I have a new (used, refurbed) iPod Touch 4G and my intention is to use it without a contract, so I want to transfer the Classical CDs I have on my Thinkpad Ubuntu 11.10 system to the iTouch.

The iTouch turns on OK and does the limited things I can do from the HOME screen. I even connected to my WiFi, inputting the router password successfully from the keyboard.

I plugged the USB into my Thinkpad and was able to read the ID with "idevice_id -l" as well as "lsusb -v | grep -i iserial".

I installed "gtkpod" from Synaptic and it looks like that will work if I can just figure out how to use it! Maybe gtkpod will even transfer my tunes to the ipod. Or maybe some other utility is required, I don't know.

So I read several web pages that promised enlightenment, but so far no joy. So I watched several youtube videos and increased my confusion greatly, but still no enlightenment.

I don't know if I need to jailbreak the ipod, or run 'redsnow' or 'limerain' or whatever, or if there is simply some way to do it with gtkpod or some other ubuntu utility.

Can anyone help me?

---

### Post by bliffle on 2011-11-19
After days and days of googleing and reading, I am gradually making progress on this. I actually have transfered (I believe) some music to the iPod! It remains to be seen if I can actually play them from the iPod.

Now the problem is to do something at the iPod screen. I'm stymied at the signon screen. Ordinarily one would download the "iTunes" client to a computer then use it to (presumably) send Apple a bunch of personal data, including, perhaps, credit card info. But that's exactly what I don't want to do. 

So now I'm reading and exploring "INIT" and whatever to see how I can do the equivalent without Apples approval.

---

### Post by Knowsnothing on 2011-11-22
Having a similar problem running with JB'ed iOS 5.0.1.

I just want to transfer music and podcasts!  I haven't found anything that works.  Would love to hear if you've found something.

Bump!

---

### Post by bliffle on 2011-11-24
Tried gtkpod with every writeup I could find and never got one even close to working. Tried banshee, too. Now I'm trying rhythmbox, no joy so far.

---

### Post by bliffle on 2011-11-25
My new thought (having failed to get anything to connect to iPod and send my tunes there) is to *gasp* put the dreaded "iTunes" on an XP computer (with NO internet access to preclude iTunes blabbing my private info to Apple) and then connecting iPod to that XP system. Then, I hope, there might be a way for me to send my tunes from XP to iPod.

Can that be done? Has anyone tried anything like that? Or, does Apple jail us, the user, just like the iPod? Can we ONLY load the iPod with tunes from iTunes?

---

### Post by inobe on 2011-11-25
cross platform, give it a try [http://www.clementine-player.org/](http://www.clementine-player.org/)

my kids use it to transfer music on kubuntu, i don't know what version ios they have, i over heard them saying, they won't update ios because it will break.

everyone i know that use linux has a sansa fuze, my kids get that ipod stuff from relatives.

sell your pods, get android base players, players that have opensource software.

google, do your research, then buy stuff that works on all platforms and avoid restrictive devices.

---

### Post by bliffle on 2011-11-25
The trouble is I paid for this iPod so I gotta put it to use. I can see it has possibilities and I'm sure others have gotten it working.

I think the key is somehow with "iFuse" and/or "libimobiledevice" to prepare the way in to the iPod.

---

### Post by bliffle on 2011-11-26
I have several windows XP computers that I would be happy to run with "iTunes" if that meant I could copy over the MP3s I already have. Of course, I would run it off the network and submit NO personal information. Some of those MP3s are from CDs I've had for 25 years and some are even from LPs I've had 50 years that are irreplaceable. I see NO reason to pay Apple a bounty for them holding my iPod hostage in a jail. I also have NO interest in buying the music that the iStore sells.

I paid $180, fair and square, for this used iPod, which has an intact serial number and which the seller assures me is not stolen.

If the iTunes program has a facility to import my personal MP3s I would be happy to use it.

If I can use a linux program on my 11.10 ubuntu system (or the 10.04 or 9.04 systems that I also have) I would be happy to install and use it. But if Apple has a dream that they can extort money from me to transport music that I have long owned and paid for, simply by making my player inoperable, then I'll forget Apple Computer Corp (again!) and get something like an Android.

There's a limit to my patience. 15 years ago I dumped a fully rigged Apple IIci (that I bought when it was first announced) in the trash because Apple never gave me a single development tool, and which I could never land a consulting job with, while I was easily pulling in high-ticket Windows contracts. I decided then that the Mac guys were a bunch of dinks, and that includes Steve Jobs (who I knew socially, a dork compared to Woz who was a Real Guy) so I walked away. 

So this iPod adventure was a test to see if the attractive iPad was In My Future, especially since my wife loves her Mac and despises the Windows systems I've prepared for her. I thought I could migrate away from my ancient Palm T5 (after using palms for 13 years and not seeing a logical successor at Palm).

But it looks like I'll walk away from Apple again and go someplace where I feel more welcome and less a slave.

---

### Post by Jay Car on 2011-11-26
If, after all the time and effort you've put into it, you still can't find a way to make it work for you, maybe it's time to resell it and try to recoup what you paid for it.  Then buy something that works. 

Continuing to attempt to make that iPod into something it isn't will only lead to more frustration. It's a bit like banging your head on a brick wall in an attempt to make your headache go away.

:)

---

### Post by bliffle on 2011-11-26
Reputedly there's a way to use the iPod with ubuntu, they say in various forums. So that's all I want to do. And it seems several people have gotten this thing working, so that's what I want to do: transfer some of my MP3s to the iPod so I can listen from the iPod.

---

### Post by drillerccg on 2011-12-11
I don't understand the problem. What contract do the ipods come wit?. All I can tell you is my experience. My son has an iPod Touch version 4.2.1. Had all kinds of problems with Ubuntu prior to 11.10. Would not recognize, sync, or anything else. But 11.10, as bad as it looks with Unity, has been handling all kinds of ipods. I have now tested a shuffle, classic, nano, and the touch mentioned above. All work great with 11.10 using Banshee. I never installed anything extra other than out of the box 11.10 and ubuntu restricted extras i usually install after a fresh install. (from software center). I hate anything Apple but this lifts a huge hurdle when I switch people from Windows to Ubuntu (47 people and counting).

---

### Post by bliffle on 2011-12-11
My ubuntu  11.10 is the old 11.04 I installed from CD, then I upgraded online to 11.10 several weeks later. Maybe that's my problem. Maybe I should re-install 11.10 from a fresh CD. 

I started trying to use 'gtkpod' rather than 'Banshee'. Maybe that screwed something.

---

### Post by kerry_s on 2011-12-11
install oplayer(free) on the ipod, plug in the ipod, go into oplayer->documents folder using nautilus, paste your music/vids there. you should now be able to play using oplayer.

suggest you find a windows machine & update to ios5.0.1, cut the iTunes chord.
you can share a folder in Ubuntu & access in player from wifi.
i ditched iPod & went back to Android, so much easier. i now use a galaxy player 5.0

---

### Post by drillerccg on 2011-12-12
I love Android too but if you already have an iPod touch and don't want to fork over another $300 for the Samsung player, you should know that 11.10 works great with the iPod touch. No problems.

---

### Post by onecuwldood on 2011-12-23
> **bliffle said:**
> I have several windows XP computers that I would be happy to run with "iTunes" if that meant I could copy over the MP3s I already have. Of course, I would run it off the network and submit NO personal information. Some of those MP3s are from CDs I've had for 25 years and some are even from LPs I've had 50 years that are irreplaceable. I see NO reason to pay Apple a bounty for them holding my iPod hostage in a jail. I also have NO interest in buying the music that the iStore sells.


If you have an XP machine already, use it with the iPod. iTunes will import your MP3 library, but be prepared, if you have a lot, it will take it a long time to import. I have around around 500Gig of MP3's and it took iTunes well over 24 hours to import my music. 

You can install iTunes without giving any personal or credit card info. You do not have to pay anything to download and use iTunes. 

As long as I have a Windows box, I won't bother trying to sync my iPods with ubuntu, it's just more trouble than it's worth.

---

### Post by bliffle on 2011-12-31
I finally downloaded iTunes to an XP machine and registered with a $15 gift card using phony personal data. But I still resent the fact that I had to use an email address for my userid (and for Apple to send out a confirmation exchange), even if it is an old deadend email address that goes nowhere.

So I finally got the "sync" to copy MP3s to the iPod, and even managed to get an 'app' installed. But I'd really rather not use the old XP system and I'd like to move mp3's and videos overfrom ubuntu where i have stuff stored and where I reformat media as necessary.

---

### Post by littlepeon on 2011-12-31
here's the deal....you KNEW that you were buying something that is only supported by Windows/Mac yet bought it anyway, and now your UPSET that it is working AS IT WAS INTENDED.
Many have made the ipod work in ubuntu..NOT ALL!
there are many different methods you can use, but few work---it all depends on your ipods hardware/firmware and there have been SEVERAL hardware types in the same line of devices--some will work with ubuntu, some don't like it at all and will NEVER work.
There are several programs in windows that can be used instead of itunes (winamp,windows media player, songbird, copytrans, mediamonkey, fubar2000--just to name a few), but it comes down to the hardware being recognized in order for the reverse-engineering program to work---ubuntu just doesn't work with all ipods/iphones...only a few hardware/firmware combos---and that's the way that apple likes it.
You dont have to give up any personal data to use itunes--moreless have a credit card/pay card to use it---goto google/yahoo, create an email address and use that newly created anonymous account to register with apple and forget about it/them.
Early versions of the ipods needed windows/macs to actually format the hard-drive and wouldn't work unless first connected to such a machine.
Sorry bub, but that's the way that it works---either work with it, or get an android, and help make google the next apple.

have fun, life's short
--Peon

---

### Post by bliffle on 2012-01-01
So, what's the best android replacement for the iPod? Does it work with ubuntu?

I'd rather switch than fight.

---

### Post by tokyobadger on 2012-01-02
I found the following steps elsewhere on these forums a while back, can't remember where so apologies to the person who originally posted.

If you get the following error message when trying to mount an iPod(Touch) or iPhone with iOS4 or above on linux

```
Unhandled Lockdown error (-5)
```then install ifuse and libimobiledevice-utils, on debian derivatives (e.g. *buntu, Mint, etc)

```
sudo apt-get install libimobiledevice-utils
```then run (as user not root)*

```
idevicepair unpair && idevicepair pair
```*if  you have a password on your iPod/iPhone, unlock it first (swipe the on  screen slider to unlock and enter the 4 digit code), then run the  command above - you may need to physically disconnect and reconnect the  device (still unlocked) to make the command work in some circumstances
when successful you should see in the terminal

```
idevicepair unpair && idevicepair pair
SUCCESS: Unpaired with device (your device's serial number)
SUCCESS: Paired with device (your device's serial number)
```
So  far I have tested with an iPod Touch4 and with an iPad2 both running iOS5.0.1 not jailbroken. I access music with Banshee, photos with Shotwell, but I'm not 'managing the media on them from Ubuntu (11.10 64bit). If you are successful with other devices please add to the list to help  others.

I should add that my 11.10 is an evolving upgrade from 10.04, not a fresh install. The two packages mentioned above were not on my system when I succeeded in the steps above. Note that I'm just reading the files, have not tried writing to either device. Hope the above helps.

---

### Post by |{urse on 2012-03-05
ipod touch on 11.10, my 32gb 4g ios5.0.1 jb'd does nothing but chirp and make me sad every time I plug it in..

Nothing listed on this thread has done it for me so far.

```
idevicepair unpair && idevicepair pair
```

mentioned above,
gives me,

> QueryType failed, error code -256 

pasting the error in google takes me straight to idevicepair.c..

```
lerr = lockdownd_query_type(client, &type);
      if (lerr != LOCKDOWN_E_SUCCESS) {
            printf("QueryType failed, error code %d\n", lerr);
            result = EXIT_FAILURE;
            goto leave;
      }

```

Tells me nothing much. I've even used the idevicepair command above with it's -u switch specifying my specific devices uuid, no love. 

ehci-hcd sees it when I plug it in as per dmesg | tail's output

> [60133.768051] usb 1-2: new high speed USB device using ehci_hcd and address 5
[60133.903032] usb 1-2: configuration #1 chosen from 4 choices


Rhythmbox gives me no love, ifuse is installed and all that jazz, 

So like, anyone else have any suggestions before I skip this thing across a pond?

---

### Post by blur xc on 2012-04-04
> **inobe said:**
> 
google, do your research, then buy stuff that works on all platforms and avoid restrictive devices.

The problem is that going to Android causes a whole new set of restrictions...  It's sad that the market has gone this way but all my kids' friends have ipods and they all use them to primarily play games, imessage, and face time each other.  They play games against each other, and a lot of the games they play together aren't available for Android yet, or ever will.  I have a Nexus S, and will never get an iPhone (very adamantly opposed to Apple, but don't force my feelings on my family) so I have to sit out and not participate with them.  Everyone I know has an iPhone- my siblings, siblings-in-laws, my wife, my nieces, kids, etc., all have iphones or ipods.  So-getting my kids Android media players, while making my life infinitely easier, would negate the purpose of getting them a hand held media player in the first place.  It'd be barely better than no player at all.  I'm all happy that I can finally instagram with my kids...

My perception is that all the Android is the red-headed step child of smart phone app developers.  All the quality outfits develop for iPhone and maybe eventually make an Android port, with exceptions of course.  But- the developers that write for Android primarily, are 2nd rate (don't mean to offend) developers that couldn't get an app approved for Apple's walled garden in the first place.

So, I'll be looking forward to trying those commands when I get home.  My 11yr old just called me at work today asking how to put a song on his ipod that his grandpa emailed him.  I think it's absolutely stupid that he cant access the email from his ipod and just SAVE THE %$#! ATTACHMENT onto the ipod...  Well, to be fair, I didn't try it, but he said he couldn't do it.

I couldn't even begin to express my vehement hatred for iTunes- cursed be the ground that iTunes developers walk on (maybe going a bit far there, but I really hate that program)...  

so ANYWAY- I'm currently on 10.04, but will be upgrading (clean install) to 12.04 here shortly after it's released.  Are things between ios5 and 12.04 better than they are with 10.04?  I've done lots of googling and have a hard time getting a straight answer.

Thanks,
BM

---

### Post by dog-soldier on 2012-04-05
> **kerry_s said:**
> install oplayer(free) on the ipod, plug in the ipod, go into oplayer->documents folder using nautilus, paste your music/vids there. you should now be able to play using oplayer.



i can also say that this also works with Ubuntu 11.04 and a 2nd gen ipod touch with ver. 4.2.1

i also tried it on 10.04 and the documents folder didnt pop up.

---

### Post by seventyeights on 2012-04-08
> Are things between ios5 and 12.04 better than they are with 10.04?

Just so you know, I ran the 12.04 beta 2 live cd and was able to install mp3 support for rhythmbox plus the latest libimobiledevice-utils.1.1.4. Music transfers still do not work, well, the music moves over, but the v5 database does not get synced.  This is perfectly consistant with the chart at [http://www.libimobiledevice.org/]("http://www.libimobiledevice.org/")

---

