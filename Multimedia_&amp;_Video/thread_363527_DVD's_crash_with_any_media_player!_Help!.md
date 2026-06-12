---
title: "DVD's crash with any media player! Help!"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by ZeroXR on 2007-02-17
I used the Ubuntu Guide Wiki's instructions for the repositories and etc. When I try to use Totem-xine or VLC, The DVD's will go through the menu then crash before the video track plays.

Totem spits out an error saying to check and see if the libdvdccs codec is installed (which it is) and VLC just halts video playback completely.

I have searched and tried every solution that was previously suggested with no luck... Anyone want to set me in the right direction? Any help is appreciated!

---

### Post by yabbadabbadont on 2007-02-17
Let's start with the obvious first trouble-shooting step.  Does the disk play correctly in a stand-alone dvd player?

---

### Post by ZeroXR on 2007-02-17
In my household DVD player, there are no issues with playback.

On my spare P4 Win XP laptop, it plays just fine too.

---

### Post by yabbadabbadont on 2007-02-17
How did you install libdvdcss?  Did you install libdvdread3 and then run /usr/share/doc/libdvdread3/examples/install-css.sh?

Here is what I did to playback DVDs just as an example.  First I edited /etc/apt/sources.list and enabled the universe and multiverse repositories.  Then I installed libdvdread3 and ran the install-css.sh script.  Next I installed libxine-extracodecs, libxine-main1, and xine-ui.  Finally, I ran the xine program and adjusted the settings so that my dvd drive was the one listed for dvd playback.  I have both a cdrw and a dvdrw drive so I made sure the right one was selected.  After that it was just a matter of restarting xine and then clicking on the DVD button (after inserting a DVD of course :)).

---

### Post by ZeroXR on 2007-02-17
I installed libdvdccs3 via the terminal command at the Ubuntu Guide Wiki

```
sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install totem-xine
```

In Totem, I'll direct it to read the disc from the quick open prompt using this directory:

dvd:///dev/hdc

It'll play the menu and copyright notice, but 4 seconds into the video track it'll crash saying that the libdvdccs may not have been installed.

VLC does the same, but it's more "cryptic" as it kills playback with no error messages.

---

### Post by ZeroXR on 2007-02-17
Anyone from the daytime folks want to take a stab at helping me out?

I'm still puzzled after fighting this for most of last night.

---

### Post by yabbadabbadont on 2007-02-17
I don't have any new suggestions, sorry, but I was wondering if this is a commercial dvd or one that you burned yourself?  If commercial, which movie is it?  If it is a new release, it might be that they have come up with yet another copy protection scheme that breaks the linux playback tools...  (it has happened before)

---

### Post by ZeroXR on 2007-02-17
Jay and Silent Bob Strike Back is the test movie in question.

---

### Post by yabbadabbadont on 2007-02-17
> **ZeroXR said:**
> Jay and Silent Bob Strike Back is the test movie in question.

That's too old to be a new encryption scheme.  Too bad you can't play it, that's a good movie.  Do you get the same behavior when playing any other DVD?

---

### Post by ZeroXR on 2007-02-17
I haven't tried any others yet... I'll probably try one of my X box-set DVD's and a few other movies to see if they work though.

It's the only thing really paining my with my system and I want to get it to work.

---

### Post by ZeroXR on 2007-02-17
I just tested Office Space and on the [Play Movie] option, it did the same thing! It get's weird though.

Here's an oddity...

When I use the Chapter Selection on Office Space, I can pick any chapter OTHER than the first chapter. I duplicated the test for Jay and Silent Bob Strike Back and I could do the exact same thing.

It seems to have to do with the first chapter when the DVD shows who the production company is... 

In Jay and Silent Bob, the stop happens right after the Dimension Films logo comes on the screen and the "star" shines across the 'm'.

In Office Space, it's right after the Fox Home Video logo screen.

Does this help you out any?

---

### Post by yabbadabbadont on 2007-02-17
Not really.  Like I said, it doesn't happen to me on dapper.  However, I believe that the intro is encoded on the disc as a seperate title.  Maybe you can pass some command line parameter to specify at which title to start playing?  Here's a thought though, try starting the second chapter through the menu, and then see if you can rewind back to the start of the first chapter...  it might help narrow things down for anyone else who is reading this thread.

---

### Post by ZeroXR on 2007-02-17
Tried that actually and it ends up crashing in Totem-xine or stopping to a dead halt in VLC.

---

### Post by ZeroXR on 2007-02-17
Any Edgy users want to chime in? I'm confused if anything now...

---

### Post by yabbadabbadont on 2007-02-17
You might see if mplayer can handle it.  You might also try using one the ripping apps to see if you can rip a disc to your harddrive and then play it from there.  It would be interesting to see if it actually *could* be ripped given that you can't play it.

---

### Post by ZeroXR on 2007-02-18
Well, here's another odd quirk...

When I use this MPlayer syntax (mplayer dvd://1 -dvd-device /dev/hdc) in Terminal, the movie plays fine, but somehow the audio track defaulted to French! No problems with playback though... Just lack of an interface to control language tracks or subtitles was a bit odd, as I don't speak French.

When I use this MPlayer syntax (mplayer dvdnav://1 -dvd-device /dev/hdc), the main menu pops up, but the playback is messed up and I get this message:

> Encrypted VOB file! Read DOCS/HTML/en/cd-dvd.html.

---

### Post by yabbadabbadont on 2007-02-18
Sounds like somehow you got a bad version of libdvdcss2 installed... you might try completely removing it and then install it again using the script in the /usr/share/doc/libdvdread3/examples directory.

sudo apt-get --purge remove libdvdcss2

I would also remove the ~/.dvdcss directory and it's contents while you are at it.

---

### Post by ZeroXR on 2007-02-18
Would that cause the crashing with the other media players?

---

### Post by yabbadabbadont on 2007-02-18
Who knows?  :)  At least you got an error message out of mplayer that gives an idea of where the problem may lie.

---

### Post by ZeroXR on 2007-02-18
Reinstalled libdvdcss2 and still got the error with running dvdnav.

The language thing, I fixed with adding **-alang en** just I can't get subtitles to work... I guess MPlayer is the player of choice... :(

yabbadabbadont, you wouldn't happen to know any good pages for a Terminal shy user to learn all about the MPlayer syntaxes, would you? :D

**Edit:** Apparently all of the GUI players have this quirk for me that Chapter 1 crashes but yet anything beyond that plays (albeit choppy). Tested players were Totem-xine and VLC. If anyone has and idea of what is going on, post up!

---

### Post by yabbadabbadont on 2007-02-18
"man mplayer" will give you more information than you will want to wade through... :lol:

There is an "-sid NUM" option for subtitle id, and also a "-vobsub" option (for subtitles encoded directly in the vob file, I think).  You should look for them when you read the man page.  It also lists various keyboard shortcuts you can use while the movie is playing.  However, you can start the graphical version of mplayer from the command line with "gmplayer".  Then you should be able to use your mouse to right-click and select the language and subtitles and such.

---

### Post by chiefbearclaw on 2007-02-19
Not sure if this is related but to those of you who have this odd dvd playback problem, are you all using ATI video (i.e. cards or on-board)?  If so what driver (community or proprietary)?  Just curious.

I experience the exact same problem as initially posted.  If lucky, I do at times find a DVD that will play seemingly okay for a while, however, playback will not make it through all the chapters without crashing.  I have tested it with over 20 - 30 DVD´s (not copies) old and new.  Ruling out any encryption  In fact it has gotten to the point where any media player installed will not only crash but will fail to start upon re-execution (with no error msgs whatsoever sometimes) if I get an error its the same as what was originally stated in the first post.  A reboot & a reinstall of codecs can be a temp fix but will certainly not ´take´.  I´ve reinstalled the OS several times to trouble shoot other factors since doing that was actually easier.  Perhaps there are logs full of helpful info on this DVD playback issue but I have yet to had to time to dig for them and am not even sure exactly what I should be looking for.  I am no expert or dev.  I am using: Edgy < 2.8Ghz P4 < 512MBRam < AGP 4x/8xATI X1600 < IntelD850EMV2 Mobo  with dual monitors and driver from ATI´s site.  Nearly every codec imaginable is installed.  I am currently in one heck of a fight to get my ATI card working correctly which is my initial problem (and yes I have read nearly everything on the web about that issue... and still reading) which has my time more consumed than this particular issue.

I am just interested in knowing if it could be an ATI issue since.. erm.. there are so many problems with ATI it seems.  Another thing I have noticed is that if / when the DVD might play, the audio is usually out of sync (not severe but not slight either).  I am not really asking for help with this particular issue just yet but figured I´d give some feedback and plant my first green coffee bean here.  Hopefully it will spark something and help in some way and not confuse anyone further.  May give all this a try in Feisty just for giggles but I´ll be sure to check back and post anymore information I find in regards to this DVD playback problem.  *Note - playback of any other format either audio or video (mp3´s, avi´s, etc) play fine.  Its only DVD´s for me this problem occurs.

---

### Post by ZeroXR on 2007-02-21
**chiefbearclaw**: In regards to the possibility of a hardware issue, I'm an nVidia user. Here is my system set-up if you're curious.

OS: Ubuntu 6.10 Edgy Eft
Motherboard/Chassis: Shuttle SK41G
Processor: Athlon XP 2100+ (Clocked at 1.74 Ghz)
RAM: 1 x 512mb DDR 266
Graphic Card: GeForce MX 4000 128mb DDR2 AGP 4X
DVD Drive: OEM Samsung DVD ROM Drive, Model SD-612 (16X read speed)

---

### Post by yabbadabbadont on 2007-02-21
> **ZeroXR said:**
> **chiefbearclaw**: In regards to the possibility of a hardware issue, I'm an nVidia user. Here is my system set-up if you're curious.

OS: Ubuntu 6.10 Edgy Eft
Motherboard/Chassis: Shuttle SK41G
Processor: Athlon XP 2100+ (Clocked at 1.74 Ghz)
RAM: 1 x 512mb DDR 266
Graphic Card: GeForce MX 4000 128mb DDR2 AGP 4X
DVD Drive: OEM Samsung DVD ROM Drive, Model SD-612 (16X read speed)

Just out of curiosity, do you know if the region code has ever been set for that DVD drive?  I know that some people have strange playback problems if it hasn't been set.

---

### Post by ZeroXR on 2007-02-21
I had used a firmware tool to check which region my drive was set on back when I had Win XP Pro and it was confirmed as Region 1. I never reset the region, so I still have the original 5 times to change.

All the DVD's I own are Region 1 or Region 0, for the curious.

---

### Post by ZeroXR on 2007-02-21
**chiefbearclaw:** In regards to reinstalling codecs, I have done that almost 3-4 times with no success either.

---

### Post by ZeroXR on 2007-02-21
Is there a possibility that it could be a problem with how my DVD-ROM drive reads?

I don't have a DVD-ROM drive to test, so I can't quite replicate my test on another machine

---

### Post by ZeroXR on 2007-02-21
Here's a wierd anomoly...

I couldn't find any of my other DVDs until today, so I decided to expand my test a bit to my anime collection.

I just tested one of my Pioneer (now Geneon) published anime DVD's and the playback was flawless in Totem-xine. Subtitles worked with out a problem and so did language changes. I could change the language and run subtitles without Totem-xine running into the goofy repeats-every-second "bug" that plagued Jay and Silent Bob Strike Back.

When I decided to retest Jay and Silent Bob Strike Back, it got the message saying libdvdcss doesn't look like it's installed and the DVD seems encrypted with it.

Now I am confused...

Here's the details on the test DVD that worked:

Publisher: Pioneer (Now known as Geneon Anime)
Product ID: 11824
Publishing Date: Circa Late 2002 - Early 2003
Title: X [ONE]
Region Code: Region 1

---

### Post by ZeroXR on 2007-02-23
Region 0 DVD's work alright provided that the menu's are encoded correctly.

_Working_
Hasangeo (Volcano High) - Produced by Tai Seng Video

_Not Working_
Bodyguard from Beijing - Produced by World Video
**Menu doesn't function with Totem-xine**

---

### Post by ZeroXR on 2007-03-04
I did a DVD playback test on my new project laptop and it had no problems with the libdvdcss codecs and played every DVD like a household DVD player.

The drive on the laptop is a Matsushita (Panasonic) DVD-RAM drive.

Tested DVD's on the laptop were: Jay and Silent Bob Strike Back and Office Space

It seems the playback problem is indeed hardware based.

For others, who have problems with their DVD's crashing... It may be due to the drive not being completely supported under Linux.

---

### Post by RealityMaster on 2007-04-15
Yeah, think I've got an un-supported DVD player as well.  Exact same issue

# dmesg | grep scsi
[   10.291188] scsi0 : ata_piix
[   10.462163] scsi1 : ata_piix
[   10.945142] scsi 0:0:0:0: Direct-Access     ATA      ST910021AS       8.04 PQ: 0 ANSI: 5
[   10.948790] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A103 PQ: 0 ANSI: 5
[   11.002740] sd 0:0:0:0: Attached scsi disk sda
[   11.005424] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.005438] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   11.445894] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   11.445962] sr 1:0:0:0: Attached scsi CD-ROM sr0

:(

---

### Post by diilbert on 2007-08-02
I have to be having the same problem.  When I do 
#dmesg

I get this at the bottom:

```

[14678.750528] cdrom: This disc doesn't have any tracks I recognize!
[15404.657358] cdrom: This disc doesn't have any tracks I recognize!

```

Any idea how to check to see how well my DVDROM/CDRW is supported?

[EDIT]

Alright after doing this: [http://lj4newbies.blogspot.com/2007/07/clean-up-your-ubuntu-box.html](http://lj4newbies.blogspot.com/2007/07/clean-up-your-ubuntu-box.html) I cleaned out some orphaned DVD libs and everything started working. BUT:

I tried 3 DVDs -> Hitch, Kate & Leopold and The Bourne Identity Explosion Edition.  The last one just caused the DVDROM to spin like crazy and crashed gxine.

ANY ideas on that one ?

---

### Post by ZeroXR on 2007-08-03
I'm surprised this topic came back from the grave!

**diilbert**: The "death spin" is typically a sign of an unsupported disc. Were the other running fine without a problem?

---

### Post by msatkinson on 2007-08-19
hi,

If you've not already done so, try installing gstreamer0.8-misc package (or above). I was having the above problem until installing this package.

I also found the Codeine player to be a simple place to start. It's error reporting was useful to me.

Cheers, Mark.

---

