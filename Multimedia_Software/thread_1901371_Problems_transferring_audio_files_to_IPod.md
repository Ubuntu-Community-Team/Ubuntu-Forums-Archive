---
title: "Problems transferring audio files to IPod"
date: 2011-12-28
forum: Multimedia Software
---

### Post by FelixT379 on 2011-12-28
I wasn't sure where to post this, but I guess it goes in the multimedia section. I use the latest version of Ubuntu. I got a new IPod Nano Touch so I tried to use it in Banshee. It sees the IPod, it even allows me to transfer mp3 tracks to it, but when I unplug the IPod and go see the track list, it says that there are no music on it. When I plug it back, I can't see the tracks I transfered, but the tracks are on the Ipod because it shows that memory has been used (the orange color). In the file manager, I can see all the track files in the root folder of the Ipod. I went on a Windows machine to try it and it works fine. I could transfer music. And when I go back to Banshee, it sees the tracks I transfered using Windows. But if I try transfering music from Banshee again, the Ipod won't see it once I disconnect it.

I also tried using the Ipod program that can be downloaded from Ubuntu software manager... gtkpod I think. It's pretty much the same problem I have.

---

### Post by neu5eeCh on 2011-12-28
I actually had this problem on the Windows side, using Media Monkey. I never solved it, but was forced to use ITunes when uploading to or managing my IPod. I still use Media Monkey to manage my library _ cause it's huge. This was with my 160g IPOD classic, by the way. I'm convinced that it's because APPLE deliberately threw a wrench in the system. Jobs **hated** anyone circumventing his "vision" for how his hardware and software should be used. Sorry I can't be any more helpful.

---

### Post by X_Splinter on 2011-12-28
Use gtkpod

---

### Post by tptmrk on 2011-12-28
I'm having a similar problem with a **new iPod touch**. 
I've already tried **gtkpod**, which says:
> Could not find iPod directory structure at '/home/uname/.gvfs/iPod touch'.

If you are sure that the iPod is properly mounted at '/home/uname/.gvfs/iPod touch', it may not be initialized for use. In this case, gtkpod can initialize it for you.

Do you want to create the directory structure now?
then
> Error initialising iPod:
Newly mounted iPod at '/home/uname/.gvfs/iPod touch' could not be loaded into gtkpod.
that popup can't be closed and then the first message is shown again. Trying again gives the message:
> Error initialising iPod:
Unsupported checksum type
Newly mounted iPod at '/home/uname/.gvfs/iPod touch' could not be loaded into gtkpod.

I also tried **Banshee**, which converted my mp3s and put them in what appears to be the top level directory of the iPod, but the iPod doesn't recognize them.

**Rhythmbox** also says that the iPod is not initialized and fails to be able to do so.

I tried downloading a free song from iTunes within the iPod UI hoping that would create the file structure to add songs, but no luck. I've tried googling this hoping to just create the folders needed in **Nautilus**, but no luck there either.

:confused:

---

### Post by X_Splinter on 2011-12-28
> **tptmrk said:**
> I'm having a similar problem with a **new iPod touch**. 
I've already tried **gtkpod**, which says:

then

that popup can't be closed and then the first message is shown again. Trying again gives the message:


I also tried **Banshee**, which converted my mp3s and put them in what appears to be the top level directory of the iPod, but the iPod doesn't recognize them.

**Rhythmbox** also says that the iPod is not initialized and fails to be able to do so.

I tried downloading a free song from iTunes within the iPod UI hoping that would create the file structure to add songs, but no luck. I've tried googling this hoping to just create the folders needed in **Nautilus**, but no luck there either.

:confused:
I get those errors and I am still able to transfer songs to the ipod.

Of course the best solution is using Windows, you could try VirtualBox

---

### Post by tptmrk on 2011-12-28
OK. I plugged the iPod into my wife's Vista laptop and it recognized it, installed drivers or whatever, and asked if I wanted to manage the device with RealPlayer. Realplayer didn't see it and neither did Windows Media Player. 

It mounts just fine and I can see it in Nautilus as well as some folders. It sure seems like if I could just figure out what to name the music folder I might be able to just create a folder and drop the files there in Nautilus.

Warning: rant below
I refuse to use iTunes. I tried it years ago and it created a new (DRM) copy of every file AND it was the most useless of any media player I've tried. Besides, I'd like to be able to add music with my computer! I thought Apple's main schtick was that their stuff is easy to use! I guess it's only easy to use if you use only their (expensive) hardware and software.  I should be able to browse the folders and dump files in just like every other device I've used!

---

### Post by X_Splinter on 2011-12-28
> **tptmrk said:**
> OK. I plugged the iPod into my wife's Vista laptop and it recognized it, installed drivers or whatever, and asked if I wanted to manage the device with RealPlayer. Realplayer didn't see it and neither did Windows Media Player. 


LOL dude, you need iTunes

---

### Post by neu5eeCh on 2011-12-28
> **tptmrk said:**
> OK. I plugged the iPod into my wife's Vista laptop and it recognized it, installed drivers or whatever, and asked if I wanted to manage the device with RealPlayer. Realplayer didn't see it and neither did Windows Media Player.

Yeah, sorry Dude. 
 
Jobs **_despised_ **tweakers. He was the ultimate control freak. Nothing pissed him off more than users messing with his "works of art". It's said that he didn't even want employees to be able to open windows in his new mutil-billion dollar Apple compound - "people just screw things up". I suspect that Apple has done its best to _**force**_ users to use ITunes; and I suspect he hated the fact that Linux users could access **_his_** Ipods without ITunes. I also detest ITunes, but use it on Windows to move music on and off my Ipod while using MediaMonkey (which **also** couldn't write tunes to my IPOD in windows!) to actually manage my music library. I basically use Itunes as a glorified middle man and nothing more.

So, if you refuse to use ITunes, let me know how it goes. I'd be willing to buy your paperweight off you for the right price.[B]:biggrin:

Edit: [/B]It's also in Apple's interest to prevent you from bypassing ITunes, since they want you to be forced into their ITunes store. They make a lot of money through that store and they will do everything they can to force you into it.

---

### Post by kalfusisagod on 2011-12-28
You have to use iTunes with iPods. I've attached a screen shot of my 160G iPod connected to iTunes and the SPECIFIC and RANDOM folder structure it uses.

When the iPod and iTunes sync, the iPod gets some sort of database file on it to tell it where each song is. If you plug in a ipod into a computer that's been recently synced with itunes and you turn on hidden folder view, you will see a folder called ipod_control. Within that folder are folders named F01, F02, F03 and so on. Within those folders are the actual mp3s with random names like DYUX.mp3. The mp3 files still retain their ID3 tags (name, artist, album etc) but I think the iPod database file actual controls the iPod on what it displays and also stores the play and skip counts for iTunes. 

So as you see in the screenshot, it's VERY specific and you can't just drag and drop mp3s onto a iPod. Anyway, iTunes was great about a year ago. Now Apple has added way too much and it's become bloated. I have a very fast computer (i7 2720QM quad core @2.2GHz with 16 gigs of ram) and a 22,000 mp3 library. iTunes is very slow now because of the bloat (iTunes Match, iTunes cloud, Ping, iTunes store etc) But you have no choice. Hope this helps everyone understand the iPod folder structure.

---

### Post by tptmrk on 2011-12-28
I dug the packaging out the trash. I'm going to sleep on this, but after a super quick google search I think I can get an android tablet that would run all the apps I planned on using on this iPod (ireal b, ted talks, pandora, netflix, hulu, words with friends? etc...) and sync with a bluetooth headset to probably just stream music on my local network and save any trouble syncing. At that point I'm just out the $20 I already spent in the iTunes store. 

If I eventually get a smart phone I'll probably get an Android phone, too, and I'm guessing getting an Android tablet now would mean my computer, tablet, and phone would all play nice together (and integrate better with google voice and such).

So disappointing. I really liked this thing until I tried to put music on it.

---

### Post by tptmrk on 2011-12-28
> **kalfusisagod said:**
> But you have no choice. Hope this helps everyone understand the iPod folder structure.

Thanks! You posted this while I was typing the last post, but I actually set up iTunes on my wife's computer and transferred a song. I looked at the file structure and found a long randomly named file and those f01 folders. What a mess. I guess if you have the money to buy all Apple stuff you don't mind because it all does work together and you never see anything behind the scenes. I'd rather spend my money on technology that is more "open", even if I don't understand the ins and outs of all that, either.

I had also found this in the Ubuntu documentations
> Neither the iPod Touch nor the iPhone are officially supported by any Linux music management applications at this time.

---

### Post by neu5eeCh on 2011-12-28
> **kalfusisagod said:**
> iTunes is very slow now because of the bloat (iTunes Match, iTunes cloud, Ping, iTunes store etc) 

I noticed that with the last update. It now takes between 40 to 60 seconds for ITunes to start up on my 64bit Windows 7 install! Part of this, probably, is because the music library isn't stored "in Itunes", but externally.

---

### Post by FelixT379 on 2011-12-29
And I don't even have Windows at home. Oh well... I thought Apple was better than Microsoft, but I guess not... I'm sure the Linux geeks will find a way to bypass this somehow, at some point. But for now, screw Apple.

---

### Post by kalfusisagod on 2011-12-29
Yeah I remember when the Palm Pre used Apple's iPod's USB ID to sync with iTunes, Apple was furious over this. [http://nanocr.eu/2009/06/04/palm-pre-usb-hack-confirmed/](http://nanocr.eu/2009/06/04/palm-pre-usb-hack-confirmed/) Apple just wants to you to buy their products. I'm surprised that Apple even provides iTunes on Windows. I'm starting to wonder why they don't provide for Linux. Probably small market share and too many distros equals too much work for not enough money.

@VTPoet Apple's product code is becoming more bloated. My iPhone 3GS is very laggy now with the new iOS5 on it. iTunes is just as laggy as you've said and I have a fairly new computer (ASUS G73SW, non-stock) They need to clean up their code, and drop features that they don't need like iTunes Ping. But I guess that's a ploy to force people to upgrade to new hardware every 2 years (hint hint iPhone 4S). That's why you can't install OSX onto any non-Apple machine without doing some serious hacking and solving riddles.

---

### Post by JoeEndUser on 2011-12-30
Sorry, just a discussion point: I have the same problem, but I have to say that I believe this is a linux Kernel problem and not something that Apple did. My wife refuses to update her 9.04 Jaunty machine and my ipod works fine on it, but hasn't worked on any version since 10.04. There are loads of bug reports, but I don't think it is a priority.

---

### Post by kalfusisagod on 2011-12-30
> **JoeEndUser said:**
> My wife refuses to update her 9.04 Jaunty machine and my ipod works fine on it, but hasn't worked on any version since 10.04. 

Really? So you could of synced your iPod with some Linux music program with 9.04 with no problems. Interesting.

---

### Post by bliffle on 2011-12-31
I've got a good working 9.04 on a machine here, so I guess I can try that with the iPod. The question is, which ubuntu program do I use? gtkpod, banshee, rhythmnbox, etc.? And do I need iFuse and/or libimobile on that 9.04 system?

---

### Post by bliffle on 2012-01-01
The iPod Touch is a sort-of 'attractive nuisance'. It looks like such a great machine, slim, bright, lots of apps, etc., that it's hard for a guy to go another route. It seems as though it has a lot of market support, so there are, for example, many bird id apps available (tho they don't really seem any better than the old Nat Geographic app I have on my old Palm T5), and there aren't any good butterfly or wildflower id apps (which is surprising).

It may be that the iPod is just a 'killer' product designed by Apple to dominate a market without fulfilling user needs. Those 'killer' machines and software have been the bane of the computer business for 50 years. They're often used to 'unhook' customers of a competitor, which may even be in violation of anti-trust laws (if anyone cares anymore, since monopolies seem to be permitted in the new economy).

Another thing that I find surprisingly lacking on the iTouch is that there seems to be no security options for me, the user. No signon requirement, no security for contacts, notes, calendars, etc. This is especially dangerous on a machine that is so open to internet hacking.

Especially since Apple seems so intent on poking it's nose into my business, what with their intrusive signup requirements for iTunes (which I successfully dodged, I believe).

So what's the best android replacement for iPod? Slim, apps for wildlife ID, note-taker, audio/video player, calendar, etc. I don't care about twitter and facebook, or even email very much. At the most, a Skype client would be nice, but not necessary.

---

### Post by JoeEndUser on 2012-01-03
Bliffle: just saw your post. I use gtkpod on 9.04, I think my notes on it from the time are further below.

I'd love to hear if you get it going retro-actively.



Go to Synaptic Package manager. Search for libmp4

Mark the following for installation and apply (install) (all four choices):

libmp4-info-perl
libmp4-0
libmp4-dev
gtkpod-aac

Plug the ipod in

Add repository for Ipod:

Open Gtkpod - select edit from the main menu and

Select Repository/ipod options

Select add new repository

Select ipod mountpoint - Click Browse button

Browse to Media folder and select your ipod (probably /media/your user name/ipod)

Carefully choose your correct Model AND Color

All else can remain as default

Click the Add button when done

---

### Post by Sooz Not OpenSuse on 2012-01-04
I've spent several hours now trying to find a solution to my problem with mounting my ipod. It's a first generation 2GB Nano and previously to now has always synced fine with whichever media player I've been using (the ipod was previously used on Windows not Apple). I'm not sure if I have tried syncing since I upgraded to Ubuntu 11.10 from 11.04 - I would guess the upgrade has resulted in the problem. These are the problems:

Unless I plug in the ipod from booting the laptop, it won't appear as a device in Banshee or Ryhthmbox. Even then it won't sync (even though it says it will). All error messages say permission denied. I've tried through terminal to change permissions by chmod, but this isn't working (not under sudo nautilus/root user or anything).

Gtkpod DOES recognise my ipod (all of the time) but it won't sync either (again a permission problem according to the error message). 

I have tried everything I can think of (libimobiledevice files, trawling through forums) but I can't catch a break with this! 

For reference, in the terminal under /media/usb0 it does show the sub-folders and seems to have some recognition that it's an ipod through the /var/log/messages.

I am a relative newbie to Ubuntu - I've been playing with it for a year, but only recently delved into the shell command language and my knowledge is quite patchy. Any help would be gratefully received! 
Thanks

---

### Post by Sooz Not OpenSuse on 2012-01-04
I found how to fix my system - uninstall USBmount from synaptic package manager. My ipod now (ironically) mounts straight away and works fine!

---

