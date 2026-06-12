---
title: "Frontend Randomly Freezes"
date: 2011-01-25
forum: Mythbuntu
---

### Post by Barry_IA on 2011-01-25
[FONT=Palatino Linotype]Hi Folks!

This topic probably been discussed previous but I couldn't it.  Installed Mythbuntu  10.10 a while ago.  The one Frontend I currently have operational will randomly lock up/freeze.  It is a P4, 3.2 GHz, and off-hand can't recall the memory nor video card.  The problem doesn't seem to be due to a drop out problem as other threads have suggested: the Frontend will not lock up in the same place.  Also doesn't seem to be related to resolution -- a 1080 will play fine and a (no resolution listed) will lock up three times.  Or the opposite: this afternoon downloaded and installed the system upgrades, rebooted, and tested.  The half-hour (no resolution) programme played all the way through and about an hour and fifteen minutes into a two-hour recording at 720 the video (and audio) locked up ==> freeze framed.

There is generally no 'premonition': the picture will just freeze.  On rare instance have seen a 'hiccough' in the display and about a half-second later it freezes but that is rare.  By the 'hiccough' it's a fraction of a second glitch in the display -- possibly a gray frame being displayed.

The Hard Drive's LED will usually continue to randomly flash while the picture is frozen.  The only way I have found to fix the problem is to perform a hard boot: hold the front panel power switch for four seconds.  (There is no reset switch.)  The Frontend appears to boot normally -- no error messages.  AFACT there is no problem with the Backend computer.

Both machines (Back- and Frontends) ran 10.04 without any freeze problems.  I reformatted the Backend due to what appeared to have been a file corruption problem

(I did run another thread about a problem with a P4, 1.8 GHz machine with an installation problem.  This is not the same machine.)
            
Any suggestions?  One thread suggested a problem with static electricity -- AFAICT the system is properly grounded -- even ran a ground wire to the service panel.  TIA!
[/FONT]

---

### Post by nickrout on 2011-01-25
Logs?
Overheating?
Bad power supply?
memtest?

---

### Post by newlinux on 2011-01-26
> **nickrout said:**
> Logs?
Overheating?
Bad power supply?
memtest?

HDD failure (fsck)?
/var/log/syslog?
/var/log/messages?

:)

Sorry, I know this isn't a funny situation - but these are legitimate additional things to look into.

---

### Post by novellahub on 2011-01-26
What playback profile are you using?
Video Hardware?

---

### Post by Barry_IA on 2011-01-29
[FONT=Palatino Linotype](That's odd: I thought I had posted an update the other day -- forgot to submit?  Clicked on an older e-mail notification to get here.)

Checked the logs (and thanks for telling me where the logs were located!)  Both *syslog* and *messages*  gave the same last two lines:

Jan 25 16:28:02 IBM-M51 kernel: [ 6322.983308] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 2
[/FONT][FONT=Palatino Linotype]Jan 25 16:28:02 IBM-M51 kernel: [ 6322.987775] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 2 [/FONT][FONT=Palatino Linotype]     

I started the *fsck* command suggested by NewLinux but chickened out: "Warning!!!  The filesystem is mounted.  If you continue you ***WILL*** cause ***SEVERE*** filesystem damage.  Continue?"  Nope!!  I have enough problems!! <gg>  

As for playback profile, presuming the one selected in Util/Setup > Setup > Appearance which is Mythbuntu (Widescreen).  In Playback OSD it's BlackCurves-OSD.  The only change from default is the CC Text is set for 120%.

Video hardware per lspci is nVidia GT218 [GeForce 210] (rev 2a).

I then installed the couple of dozen updates available this morning (January 29th) -- looks like some kernel updates included; rebooted.  Noticed again the "restart now" button of the Update manager window flashes on clicking but otherwise no action.  (This normal??)  I have to click on the blue circular arrow icon at the upper right.  Not a big deal, just looking for any clues to the lock up problem.

Currently running MemTest; will post the results later.
  [/FONT]

---

### Post by newlinux on 2011-01-29
yes, hard disk checks should only be done on unmounted filesystems. You can't unmount your root filesystem if you are booted up. After a certain number of boots fsck runs automatically before your boot up. Or you can run the liveCD or a recover cd and run fsck there - If you don't know what you are doing with fsck - you probably shouldn't mess around with manually it until you've got some guidance or read up on it.

What you listed was not your playback profile - that's in the TV Settings - Playback, a couple of screens in.

From the couple of lines you posted from syslog you are running the open source nouveau driver. You definitely want to be using the proprietery nvidia driver. Have you installed the nvidia driver (System->Administration->Hardware drivers in gnome)?

The other logs to look at are:

/var/log/mythtv/mythfrontend.log (if you run mythfrontend from the menu)
/var/log/mythtv/mythbackend.log

you will want to look at them around the times of the freeze.

---

### Post by Barry_IA on 2011-01-29
> **newlinux said:**
> yes, hard disk checks should only be done on unmounted filesystems.   [FONT=Palatino Linotype]<snip>

Thanks, Newlinux!  Will look into those later: off to work shortly.  Next post is the results of MemTest.  (Seemed logical to keep separate.)[/FONT]

---

### Post by Barry_IA on 2011-01-29
[FONT=Palatino Linotype]Results of MemTest 
 
Memory:   1023 M    2689 MB/s
Chipset:    Intel i915P/G    (ECC: disabled) - FSB: 199 MHz - Type DDR1
Settings:   RAM  199 MHZ (DDR339) / CAS: 3-3-3-8 / Dual Channel (Interleaved)

Wall time   2:53: 06  (increments)
Cached       1023M
RsvdMem   24K
MemMap    e820
Cache          On
ECC             Off
Test             Std
Pass             7
Errors         2073  [2089 @ 2:57:47]
ECC errors  0

[FONT=Courier New]Tst  Pass Failing Address        Good     Bad      ErrBits  Count Chan
---  ---- ---------------------- -------- -------- -------- ----- ----
 4      0 0002e608a00 - 742.0 MB 94a989c0 94a889c0 00010000    1
 5      5 0002a608f40 - 678.0 MB 00000000 00010000 00010000 1363
 5      5 0002a608f60 - 678.0 MB 00000000 00010000 00010000 1634
 5      5 0002e608f20 - 742.0 MB 00000000 00010000 00010000 1365
 5      5 0002e608f40 - 742.0 MB 00000000 00010000 00010000 1366
 6      5 0002e608a00 - 742.0 MB fffffffe fffefffe 00010000 1367
[FONT=Palatino Linotype]
Assuming by this there is something wrong with one of the modules.  Will try reseating before purchasing new.  Any reason to go over 2 GB (assuming the motherboard accepts?) - I don't recall the Information screen showing me using Swap drive. but then I'm looking at it when the system is idle (not playing a recorded show).

TIA!
[/FONT][/FONT]  [/FONT]

---

### Post by Barry_IA on 2011-01-31
> **newlinux said:**
> What you listed was not your playback profile - that's in the TV Settings - Playback, a couple of screens in.

From the couple of lines you posted from syslog you are running the open source nouveau driver. You definitely want to be using the proprietery nvidia driver. Have you installed the nvidia driver (System->Administration->Hardware drivers in gnome)?

[FONT=Palatino Linotype]Installed the nVidia driver, but from Applications > System > Additional Drivers as could not find your path.  (Mythbuntu vs. Ubuntu?)  Noted on boot the "Mythbuntu 10.10" graphic during boot looked to be in Courier (vs. an icon).  Big deal, as everything else looked fine, but figured might have some significance.  Big problem was no audio!   Did go into the sound controller window (at desktop):
 -     Intel ICH6 (Alsa mixer)
 - - - -               Master, PCM, Aux all at or near top (full)
 -     HDA Nvidia (Alsa mixer)
 - - - -               IEC958, IEC958 1, IEC958 2, IEC958 3 all checked 

TV Show Playback tests:
    No resolution stated:    Video fine, no audio (tested Mute, Volume level, TV volume -- all OK)
    720:   videio fine, no audio  (There is a continuing problem of pixelation at and above 5x, eventually drop back to the selection menu with the message "Video Frame Buffering failed too many times".  Had this problem previously.
   1080: goes to the "X rebooted screen" ==> displays my name and "other".  Enter password and back at the Select the TV Show screen.

Did a soft reboot twice -- same problems.

Uninstalled the driver; soft reboot.  I have sound!!   Still get the pixellation problem with the 720 resolution (had that before fiddling).
[/FONT]

---

### Post by Barry_IA on 2011-01-31
> **newlinux said:**
> What you listed was not your playback profile - that's in the TV Settings - Playback, a couple of screens in.

[FONT=Palatino Linotype]Playback Profile ( 3/8 ) says "Current Video Playback Profile: CPU+" .  Not fiddling with this setting until instructed as the other options are just as if not more cryptic! <g>[/FONT]

---

### Post by newlinux on 2011-01-31
> **Barry_IA said:**
> [FONT=Palatino Linotype]Installed the nVidia driver, but from Applications > System > Additional Drivers as could not find your path.  (Mythbuntu vs. Ubuntu?)...
Well, I did say that was in Gnome - if you are running stock mythbuntu then you are probably running XFCE desktop - default but changeable in mythbuntu, not the gnome desktop - default but changeable in ubuntu.)

> 
 Noted on boot the "Mythbuntu 10.10" graphic during boot looked to be in Courier (vs. an icon).  Big deal, as everything else looked fine, but figured might have some significance.  Big problem was no audio!   Did go into the sound controller window (at desktop):
 -     Intel ICH6 (Alsa mixer)
 - - - -               Master, PCM, Aux all at or near top (full)
 -     HDA Nvidia (Alsa mixer)
 - - - -               IEC958, IEC958 1, IEC958 2, IEC958 3 all checked 



What do you want to use to output audio - HDMI or spdif or??? I could easily help you with the audio. It will be different to configure when using the nvidia driver. in alsamixer where the spdif outputs unmuted (did they have MM underneath them?)
> 
TV Show Playback tests:
    No resolution stated:    Video fine, no audio (tested Mute, Volume level, TV volume -- all OK)
    720:   videio fine, no audio  (There is a continuing problem of pixelation at and above 5x, eventually drop back to the selection menu with the message "Video Frame Buffering failed too many times".  Had this problem previously.
   1080: goes to the "X rebooted screen" ==> displays my name and "other".  Enter password and back at the Select the TV Show screen.

Did a soft reboot twice -- same problems.

Uninstalled the driver; soft reboot.  I have sound!!   Still get the pixellation problem with the 720 resolution (had that before fiddling).
[/FONT]

the video is where switching playback profiles may help. You don't have to modify them at all, and you can always change back to CPU+. There are a few presets to try (CPU++, Normal, Slim, etc.) that you can select from the dropdown menu. Selecting the right profile is key to good video, and selecting the wrong one can also affect your audio...

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

---

### Post by Barry_IA on 2011-02-02
[FONT=Palatino Linotype]Hi Folks!

I did a little bit of research on what the MemTest results are trying to tell me.  One site is relatively basic (which is good for us amateurs!! <g>) but seems to indicate the bad RAM is the cause of my random lockups.

(quoting and extracting)
[/FONT]
**Common symptoms of bad ram**

There are many indicators of bad memory, some of which can be completely  overlooked but generally they come down to the following:
[LIST]
[*]**Distorted graphics on the screen.** 
One of the stranger indications of bad memory. Ive seen so many users  put this down to graphics cards. The user has then gone and bought  themselves a new £100 graphics card to find out their £20 stick of RAM  was the fault. This is a great point to which to use Memtest, just to  make sure of the fault.
[*]**Crashes or [COLOR=#0000ff]Blue screens[/COLOR] during normal operation of the system (emails, web surfing etc.)**
General use of faulty RAM will produce a [COLOR=#0000ff]Blue screen[/COLOR].  However again don't automatically assume this is RAM associated. There  are hundreds of different items that could cause these symptoms and so  diagnostics are required.
[*] **Crashes during memory intensive tasks such as using Photoshop, playing 3d games etc..**
When intensive programs are used there is a greater risk of hardware  over-stressing itself, thus causing errors. This is actually an area of  testing completed by Memtest to check for RAM stability. 
The general term for this would be **stress testing**. This is were hardware is put under **extra pressure** to perform large task. Faulty RAM [COLOR=#ff0000]would not[/COLOR] be able to cope in most instances under this pressure thus singling it out as faulty.
[/LIST]
[FONT=Palatino Linotype]
(Source: [http://www.geekstogo.com/forum/topic/246994-guide-to-using-memtest86/](http://www.geekstogo.com/forum/topic/246994-guide-to-using-memtest86/) )

Well, according to my limited understanding this is indicating the errors MemTest found could be the cause of my problem.  So I think I'll be ordering some replacement RAM and leave the configurations options as they are for the time being.  (I'm presuming the installation process thought these were best for my hardware.)   Will report back and hopefully add a 'Solved'![/FONT]
[FONT=Palatino Linotype]


...Surviving the snowstorm here in the Midwest -- have a few other projects to keep me busy.  Suppose I should go out and shovel!
[/FONT]

---

### Post by nickrout on 2011-02-02
yes of course if memtest is showing errors you need to fix that first.

---

### Post by Barry_IA on 2011-02-15
[FONT=Palatino Linotype]Hi Folks!

Received the new RAM and installed a few days ago -- old was 1 MB, new is 2 GB.  Ran Memtest for several hours and reported everything is now fine.  Enjoyed watching a few nights of shows and then last night it locked up about 13 minutes into a half-hour show!  (Waaa!!)  Same as previously: no warning, just locks up.  Hard boot (power switch) needs to be done to get out.  (BTW, I did notice the LED for the hard drive was flashing irregularly -- not sure if I mentioned that before.)  It played hour-long shows recorded at 1080 with no problem.  (I have the feeling the length of the show nor the resolution has anything to do with the problem.)

And FWIW I think I noticed after the reboot the down-arrow icon to indicate updates were available was now displayed.  (February 14 at approximately 10:15 p.m. CTZ [Chicago], if that makes any sense. Doubt it. <g>)

Ran MemTest this morning and afternoon -- after 6 hrs 13 minutes no errors reported in 7 passes.

I checked the error logs (*/var/log/syslog* and */var/log/messages*) quite frankly no idea what I'm looking for -- I'm presuming something occurs right before the lockup.  I neglected to get the exact time of the lockup but looks to be Feb 14 22:12 according to logs and as I remembered to finally look at the clock on the wall.  Tons of things going on.  The logs are (hopefully!) posted at  [http://mythbuntu.pastebin.com/efRkNW5g](http://mythbuntu.pastebin.com/efRkNW5g).   

So, thanks!  Was sooo hoping the problem would have been resolved with the new memory.    Thanks again for the assistance.

...Well, that link didn't seem to work.  Try  [/FONT][FONT=Palatino Linotype][http://mythbuntu.pastebin.com/jD5cyH5v]("http://mythbuntu.pastebin.com/efRkNW5g")  -- otherwise I've copied them to a thumbdrive (so the next part of the learning curve would be where and how to upload that!)
[/FONT]

---

### Post by nickrout on 2011-02-15
Intermittent problems are always hard to resolve. Often a bad power supply will give you similar problems, or an overheating problem.

Sometimes diagnosis can only be elimination.

The kernel log is at /var/log/dmesg*

Your second link doesn't work either. I don't know why mythbuntu is at the start of your pastebin url. If I hit "new" and paste something I get a url like [http://pastebin.com/zyspN6tE](http://pastebin.com/zyspN6tE)

---

### Post by Barry_IA on 2011-02-16
> **nickrout said:**
> Intermittent problems are always hard to resolve. Often a bad power supply will give you similar problems, or an overheating problem. 

[FONT=Palatino Linotype]Hi Nickrout!

Yes, 'love' those intermittents!  I'm thinking might not be power supply nor overheating problems as "everything seems to work" ==> the picture is up and normal, just freeze-framed, there is irregular blinking to the HDD LED, no change in the fan sounds.  Of course, I've been proven wrong before. <g>
[/FONT]


> Sometimes diagnosis can only be elimination.

The kernel log is at /var/log/dmesg*

Your second link doesn't work either. I don't know why mythbuntu is at the start of your pastebin url. If I hit "new" and paste something I get a url like [http://pastebin.com/zyspN6tE](http://pastebin.com/zyspN6tE)[FONT=Palatino Linotype]That's why I was hoping to post the logs.  BTW, 'mythbuntu.pastebin.com' and 'pastebin.com'  look like they go to the same site from this end.   I was able to copy */var/log/syslog* and */var/log/messages* to a thumbrive and will see about uploading them to pastebin.com after lunch.  

BTW, thank you for  your assistance.  Hopefully I'm not coming across as as smart-<rump> or anything with responses like the first paragraph.  It could very well be a power supply or overheating problem for all I know (which at times seems to be very little! <g>)

[/FONT]

---

### Post by Barry_IA on 2011-02-16
[FONT=Palatino Linotype]Well, I think I posted  SysLog.1  [/FONT]at [http://pastebin.com/nCMGbjy6](http://pastebin.com/nCMGbjy6) .   [FONT=Palatino Linotype]Otherwise it's[/FONT] "**By SysLog.1  for Barry_IA on the 16th of Feb 2011**"[FONT=Palatino Linotype].   (I need mountain climbing gear for this earning curve! <gg>)


And Messages.1 is at  [http://pastebin.com/7gASFdEL](http://pastebin.com/7gASFdEL) .   Otherwise it's "[/FONT]         **By Message.1  for Barry_IA on the 16th of Feb 2011**[FONT=Palatino Linotype]"
[/FONT]
[FONT=Palatino Linotype]
Will submit the Kernel Log later.

TIA!!
[/FONT]

---

### Post by nickrout on 2011-02-16
> **Barry_IA said:**
> [FONT=Palatino Linotype]Well, I think I posted  SysLog.1  [/FONT]at [http://pastebin.com/nCMGbjy6](http://pastebin.com/nCMGbjy6) .   [FONT=Palatino Linotype]Otherwise it's[/FONT] "**By SysLog.1  for Barry_IA on the 16th of Feb 2011**"[FONT=Palatino Linotype].   (I need mountain climbing gear for this earning curve! <gg>)


And Messages.1 is at  [http://pastebin.com/7gASFdEL](http://pastebin.com/7gASFdEL) .   Otherwise it's "[/FONT]         **By Message.1  for Barry_IA on the 16th of Feb 2011**[FONT=Palatino Linotype]"
[/FONT]
[FONT=Palatino Linotype]
Will submit the Kernel Log later.

TIA!!
[/FONT]

I see you seem to be using the nouveau driver. I thought earlier in the thread you said you were going to update to the nvidia driver.

---

### Post by Barry_IA on 2011-02-17
> **nickrout said:**
> I see you seem to be using the nouveau driver. I thought earlier in the thread you said you were going to update to the nvidia driver.

[FONT=Palatino Linotype]Hi Nickrout!

Before replacing the RAM did switch to the nVidia driver but no audio so switched back.  Posted that  "[/FONT]2 Weeks Ago 08:17 AM[FONT=Palatino Linotype]" (not getting any other information on that messages timestamp in the current mode).  Search for [/FONT][FONT=Palatino Linotype]*"Mythbuntu 10.10" graphic during boot looked to be in Courier (vs. an icon).*   (At least that text$ should be somewhat unique!)   **Is message #9 in this thread.**  .
[/FONT]

---

### Post by Barry_IA on 2011-02-23
[FONT=Palatino Linotype]Nickrout:

Hope you and your family and friends are OK, or as reasonably OK as one can be with the earthquake.
[/FONT]

---

### Post by nickrout on 2011-02-24
Gee thanks, nice to know you are thinking of us. All safe but house screwed - mythtv not on without power. 

was going to get married at home this weekend, we'll have to put that off for a while.But we r alive, a relief.

just about to check out the first official death list.

---

### Post by Barry_IA on 2011-02-26
> **nickrout said:**
> Gee thanks, nice to know you are thinking of us. All safe but house screwed - mythtv not on without power. 

[FONT=Palatino Linotype]Hi Nickrout!

Glad and frankly surprised (and relieved!) to hear from you -- things look rather bad from what we see on the newscasts here in Iowa (United States).   Too bad about having to delay the marriage and the damage to your home but at least you and yours are alive.

To get back on-topic (I'm not sure how strict they are here) I have switched the Playback Profile from CPU+ to CPU++;  was the next option in rotation and the options displayed on my configuration screen are nothing like what the ones displayed at [www.mythtv.org/wiki/Playback_profiles]("http://www.mythtv.org/wiki/Playback_profiles").  (They did indicate they were guidelines....)  The good news is changing to CPU++ my shows  recorded at 720 resolution don't pixelate and do a buffer overflow error any longer!  FF (the '>' keyboard command) works nicely, and I got the Closed Captioning back on a local station where it wasn't displaying at all with the original Playback Profile.  Unfortunately still had a lockup problem, but you indicated that was because the system for some reason is set to use nouveau rather than nVidia.  I'll see what I can do about figuring out why no audio when I use the nVidia driver.

FWIW the last lock up I captured did have an additional error message:

[FONT=Courier New]Feb 22 20:28:58 IBM-M51 kernel: [ 2065.994189] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 2

Feb 22 20:28:58 IBM-M51 kernel: [ 2065.999078] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 2

**Feb 22 20:28:58 IBM-M51 kernel: [ 2066.012957] [drm] nouveau 0000:01:00.0: PFIFO_CACHE_ERROR - Ch 2/0 Mthd 0x0000 Data 0xff373632**

Feb 22 20:28:58 IBM-M51 kernel: [ 2066.012975] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 2

Feb 22 20:29:10 IBM-M51 kernel: Kernel logging (proc) stopped.

Feb 22 20:30:08 IBM-M51 kernel: imklog 4.2.0, log source = /proc/kmsg started.[/FONT]

The one in boldface is new -- or at least I haven't seen it previously.  Did a Google search for '0xff373632' but it didn't find anything.

So, take care; good luck, TTYL....
[/FONT]

---

### Post by Barry_IA on 2011-02-26
[FONT=Palatino Linotype]Something else I was doing reminded me of this.  For whatever reason it seems like the lockup/freeze problem occurs when I get notified of an update.  All but two of the freeze problems occurred either with a download notification being displayed prior to the viewing session or (more often) after a freeze on reboot a download notification icon is now present.  Usually it is the 'down arrow' but last night it was an icon that looked like a gear.  

I know: doesn't make any sense but.... <g>[/FONT]

---

### Post by nickrout on 2011-02-27
> **Barry_IA said:**
> [FONT=Palatino Linotype]Hi Nickrout!

Glad and frankly surprised (and relieved!) to hear from you -- things look rather bad from what we see on the newscasts here in Iowa (United States).   Too bad about having to delay the marriage and the damage to your home but at least you and yours are alive.




In-laws have power, phone, internet and relatively undamaged house. We are staying there (8 in a 2 bedroom house plus small camper van). The other brother-in-law works for [www.spaceships.tv](www.spaceships.tv) and all staff were allowed to take a van with cooker, water, portable toilet etc. However the big boss in Auckland is now pissed and wants the vans on the road with non existent tourists in them. Unbelievable. 

There is a lot of spirit here, I have been amazed by random acts of kindness.

---

### Post by Barry_IA on 2011-03-03
> **nickrout said:**
> In-laws have power, phone, internet and relatively undamaged house. We are staying there (8 in a 2 bedroom house plus small camper van). The other brother-in-law works for [www.spaceships.tv]("http://www.spaceships.tv") and all staff were allowed to take a van with cooker, water, portable toilet etc. However the big boss in Auckland is now pissed and wants the vans on the road with non existent tourists in them. Unbelievable. 

There is a lot of spirit here, I have been amazed by random acts of kindness.
[FONT=Palatino Linotype]
Hi Nickrout!

Glad to hear you're staying with family; was thinking perhaps camping out in a shelter of some sort, perhaps Internet on a laptop -- charging the battery not quite figured out. <g>  As for the big boss in Auckland -- so much for charity and caring for his people!  :(

Any suggestions on how to get the audio going when using the nVidia driver?  When I tried before had no sound.  Also found changing the Playback Profile seems to help, though there is something about the 45 minute mark: about that time into the show the system seems to like to freeze -- give or take a few minutes.

And it may seem obvious but I'll state it anyway: I can wait.  I feel a bit guilty asking you for help when you have the damage to your home to attend to, your wedding plans to reschedule, and local friends to help get back on their feet.

[/FONT]

---

### Post by chrisblue on 2011-03-03
Hi Barry,

Just so you know you are not on your own I also am having freezing issues when in playback. Some things to add to your issues that I have found that may be similar to your situation.

When the video freezes the back end is still working OK because I can use another PC to access via MythWeb.

The key combo Alt SysRq R E I S U B does not do anything (REISUB is a way of doing a clean shut down and reboot when your screen is locked. It terminates any processes, kills any processes, syncs the drives, unmounts the drives and reboots). However REISUB works fine when the system has not hung.

I have worked though the different CPU options but will also follow some of the ideas here and check the logs a bit more throughly.

I have a combined FE/BE and a recent clean install of 10.10 with new database and new recordings.

Cheers

Chris

---

### Post by cknight725 on 2011-03-03
I'm having similar issues (mythbuntu 10.10, xfce) -- tho not identical -- after upgrading to Kernel 2.6.35-**27**-generic

I see it most from VirtualBox 4.04 -- the system just goes walkabout when I try to run one of my XP VMs
[QUOTE=uname]
Linux office-myth.domain.com 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

[/QUOTE]

[QUOTE=lspci]
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
04:00.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
04:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
[/QUOTE]

---

### Post by Barry_IA on 2011-03-03
> **chrisblue said:**
> Hi Barry,

Just so you know you are not on your own I also am having freezing issues when in playback. Some things to add to your issues that I have found that may be similar to your situation.

When the video freezes the back end is still working OK because I can use another PC to access via MythWeb.

The key combo Alt SysRq R E I S U B does not do anything (REISUB is a way of doing a clean shut down and reboot when your screen is locked. It terminates any processes, kills any processes, syncs the drives, unmounts the drives and reboots). However REISUB works fine when the system has not hung.

I have worked though the different CPU options but will also follow some of the ideas here and check the logs a bit more throughly.

I have a combined FE/BE and a recent clean install of 10.10 with new database and new recordings.

Cheers

Chris

[FONT=Palatino Linotype]Hi Chris!

Wow: I feel like I'm back in college with the Aussies and New Zealanders!  (U.S. college with a large international student body).

One of Nickrout's earlier suggestions was to check the memory -- MemTest did find a problem and I replaced (and increased).  He also suggested overheating or a failing PSU which I'm thinking isn't a problem as the machine continues to work: I can see the HDD LED flashing. 

I've not heard of the Alt_SysReq_R_E_I_S_U_B reset option but will try it -- or try to  <trying on keyboard without hitting keys>  I hope that's keying the letters in sequence as I'm not sure it's physically possible to depress them all at once!

I did see Alt_SysReq_k  -- also supposed to do some sort of a reset/escape from the locked video state.  All that does here is goes from the frozen screen, I think to a black screen and back to the locked-up video.  Hit the key combination again does nothing.  (It has been a while since I've tried it -- never worked.)

The Playback Profile change here (IIRC CPU++ to CPU+ -- my notes are downstairs) fixed a problem with Fast Forwarding shows recorded at 720.  Originally would pixellate and halt but I could resume -- hmm: forgot the details of that as when I did it accidentally I knew to immediately hit "P" to stop the pixellation.  "No Resolution" and 1080 were fine.  Changing the Playback Profile changed things so there is only one command displayed and it seems to work for all resolutions, plus gave me back Closed Captioning on a certain TV station.  (As the U.S. uses ATSC and terms and definitions might be different, feel free to ask)

Umm, got myself distracted!  It was suggested the lockup problems were due to using the nouveau drivers instead of nVidia -- when I tried installing them the video worked but had no audio so uninstalled.  Currently awaiting instructions on how to correct the audio problem.  (In the Mixer window I have sliders with the "Intel ICH6 (Alsa Mixer)" option but not with the "HDA Nvidia (Alsa Mixer)" option -- those are probably system-specific.)

So, hopefully we can help each other out with the help of the people who know what they're doing! <g>
[/FONT]

---

### Post by Barry_IA on 2011-03-03
> **cknight725 said:**
> I'm having similar issues (mythbuntu 10.10, xfce) -- tho not identical -- after upgrading to Kernel 2.6.35-generic

I see it most from VirtualBox 4.04 -- the system just goes walkabout when I try to run one of my XP VMs

[FONT=Palatino Linotype]Hi CKnight!

I'm not sure what kernel I'm running -- whichever one was installed with Mythbuntu 10.10 and the updates as of one or two nights ago.  Oddly enough it seems about two out of three times the Backend locks up when there is an update: a few too many times it would be running fine, lock up, and on reboot the Desktop would show the Download Arrow or Gear icon.  I'm not finding anything in the logs to support this theory, though I'll admit to not knowing what to look for either!
[/FONT]

---

### Post by chrisblue on 2011-03-03
Barry,

Is the back end actually locked up. I am assuming that you have a combined FE/BE. Do you have another PC on the network that you can use to access the BE via Mythweb?

The REISUB command is done by holding ALT and SysRq at the same time and then typing in seq R E I S U B holding each key for a second or so and leaving a couple of seconds inbetween each. You do need big hands or a small keyborad :)

I can't see that your issue is related to the update process I know that mine certainly isn't but why don't you turn off checking for updates or make it manually driven that way you can eliminate it from your process.

Chris.

---

### Post by Barry_IA on 2011-03-07
[FONT=Palatino Linotype]Hi Chris!

The computer locking up is a FrontEnd, with just Mythbuntu on it.  Currently no other Frontend available; working on that.

I did "get" to try ALT_SysReq_REISUB the other night and it did release and reboot!  At least not quite as aggravating as getting up and pushing the power button!  I'm not a couch potato, but....
[/FONT]

---

### Post by Barry_IA on 2011-03-07
[FONT=Palatino Linotype]In the "FWIW Dept'", tried installing the nVidia driver again this morning, because I've been told the nouveau one is causing the lock-up problem.  Summary: with the nVidia driver installed installed the video looks OK but no audio ==> the volume control bar at the bottom is at zero and stays there.  Rebooted a couple of times, still no audio.  Uninstalled the driver, they talk again!  (I was going to make a joke about the old movies with no sound and then the 'talkies' but.... <g>) 

A few things noted, and since I don't know what I'm doing don't know how relevant these comments are.

The command *lspci | grep -i video* doesn't find anything

*lspci | grep -i nvidia* finds:
-- video controller GT218 [GeForce 210]
-- Audio device high definition audio controller.  (There are no model numbers.


*lshw | grep - i nouv* finds:
-- configuration: driver=nouveau latency=0   (BTW, that was before I installed the nVidia driver.)

Looked in the output file (w/o grep) and it said the width is 64 bits for the nouveau driver and 32 bits for the HDA driver.  Any significance or just don't need as much for audio?

Also noted with and without the nVidia driver installed the Mixer window does not show any volume sliders for the HDA option while it does for the Intel ICH6 one.  I have all four options check for HDA -- neglected to write them down.  

The HDA option came up first in the Mixer options when the nVidia driver was installed; the Intel one with the nouveau driver.  For poops and giggles tried switching the audio option to the Intel -- no sound.  Looked around in Myth's Setup, didn't see anything, plus a little afraid of loosing the audio completely when fiddling around with settings I don't know about.

After the nVidia driver was installed I did see the gear icon at the upper right of the Desktop.  Clicked to see if anything further should be downloaded -- it indicated no.  Did the (soft) reboot and no gear nor down arrow.

Did three soft reboots, never did get audio (tried the F10, F11, [, ] keys) -- slider stayed at 0.  Uninstalled the nVidia driver, rebooted, they can talk! <g>

BTW, and I mentioned this the previous time I tried installing the nVidia driver, on boot the "Mythbuntu" logo appears as if it is in a Courier font rather than the normal log.  Also noted four dots underneath rather than the normal five, and I don't think they changed colour in sequence.  During the reboot shutdown the text lines displaying at that function were also in Courier.  When at the Desktop and in Myth itself the fonts looked normal.  No idea if significant, but....
[/FONT]

---

### Post by newlinux on 2011-03-07
when you have the nvidia driver installed what is the result of:
```

aplay -l

```

What version of ALSA are you running and what are you using for your audio output (spdif or HDMI or...)?

I have a g210 in one of my machines and for me there are a couple of steps that need to be taken to have audio working, depending on what version of ALSA you are running.

---

### Post by chrisblue on 2011-03-07
> **Barry_IA said:**
> [FONT=Palatino Linotype]Hi Chris!

The computer locking up is a FrontEnd, with just Mythbuntu on it.  Currently no other Frontend available; working on that.

I did "get" to try ALT_SysReq_REISUB the other night and it did release and reboot!  At least not quite as aggravating as getting up and pushing the power button!  I'm not a couch potato, but....
[/FONT]

Rather than just making life easier for the odd couch potato :) the REISUB process makes sure that every thing is shut down "nicely", ie all the drive are synched and then unmounted. Just doing a hard reset may corrupt data if it hasn't been written to the drive.

I also need to have a look at the video driver as I am using the Nouveau driver as I had issues with 10.4 getting the nVidia to accept any configuration changes (ie screen resolution etc). Now I have installed 10.10 I will have another go and see if my issues are similar to yours.

Chris

---

### Post by Barry_IA on 2011-03-08
> **newlinux said:**
> when you have the nvidia driver installed what is the result of:
```

aplay -l

```What version of ALSA are you running and what are you using for your audio output (spdif or HDMI or...)?

I have a g210 in one of my machines and for me there are a couple of steps that need to be taken to have audio working, depending on what version of ALSA you are running.

[FONT=Palatino Linotype]Hi New Linux!
 
Ran the *aplay -l* command several times to see what changes might appear.  Figured might tell something. ...So far I'm just giving it a blank stare. %)

*Aplay -l* with the nouveau driver (no changes to system made yet):
card 0: NVidia [HDA Nvidia], device 3, NVIDIA HDMI [NVIDIA HDMI]
.     Subdevices: 1/1     [there is no '.' at the beginning -- using it to force the indentation]
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: NVidia [HDA Nvidia], device 7, NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: NVidia [HDA Nvidia], device 8, NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: NVidia [HDA Nvidia], device 9, NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0


----------
Installed the nVidia driver, reboot.  Noticed there were some downloads to do so installed these.

*aplay -l* (with the nVidia driver installed):
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 1: NVidia [HDA Nvidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: NVidia [HDA Nvidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: NVidia [HDA Nvidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: NVidia [HDA Nvidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0


Looked at the Mixer GUI: HDA Nvidia switches are IEC958,  [/FONT][FONT=Palatino Linotype]IEC958 1, [/FONT][FONT=Palatino Linotype]IEC958 2, [/FONT][FONT=Palatino Linotype]IEC958 3 (all four checked.  Only tab for this option is 'Switches".

Checked playback of a TV show; the volume control is working ==> slider moves left/right with F10, F11, but no sound output.  Previously (the other day, the time before I tried installing the Nvidia driver) it was stuck at 0.

<reboot>  Now the volume slider is stuck at 0.  Results of aplay -l (will we see something different?)
card 0: Nvidia [HDA Nvidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: Nvidia [HDA Nvidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: Nvidia [HDA Nvidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: Nvidia [HDA Nvidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Inetl ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: ICH6 [Intel ICH6], device 4:: Intel ICH - IEC958 [Intel ICH6 - IEC958]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0


Figure reboot one more time; can change the volume again but no sound.    *aplay -l*:
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 1: Nvidia [HDA Nvidia], device 3: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: Nvidia [HDA Nvidia], device 7: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: Nvidia [HDA Nvidia], device 8: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: Nvidia [HDA Nvidia], device 9: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0

(Hope I typed all that correctly!  Couldn't figure out how to copy the highlighted section in Terminal to a file in the thumbdrive.  Using (or trying to!) *nano*.

Uninstalled the nVidia driver -- sound's back!

Need to get back to you on the version of Alsa I'm running.
[/FONT]

---

### Post by Barry_IA on 2011-03-08
> **newlinux said:**
> What version of ALSA are you running and what are you using for your audio output (spdif or HDMI or...)?
 
[FONT=Palatino Linotype]Hi again, NewLinux!

Made it back -- tried to find the Alsa info by wandering around the GUIs, drop down menus, half-remembered commands, etc., etc.  Gave up and found how to do it via Google in about 10 seconds!  (For the other newbies, go to the Terminal and type *cat /proc/asound/version*).

Advanced Linux Sound Architecture Driver Version 1.0.23.  (So now we know what "alsa" means! <g>)


As for 'audio output', can I assume HDMI?  The video card has an HDMI output and I use an HDMI input on the TV.  Nothing gets changed when the audio works other than using the nouveau driver   (So when did you figure out I was a newbie to Linux? <laff>)
[/FONT]

---

### Post by Barry_IA on 2011-03-08
> **chrisblue said:**
> Rather than just making life easier for the odd couch potato :smile:  the REISUB process makes sure that every thing is shut down "nicely",  ie all the drive are synched and then unmounted. Just doing a hard reset  may corrupt data if it hasn't been written to the drive.

I also need to have a look at the video driver as I am using the Nouveau  driver as I had issues with 10.4 getting the nVidia to accept any  configuration changes (ie screen resolution etc). Now I have installed  10.10 I will have another go and see if my issues are similar to yours.

Chris
[FONT=Palatino Linotype]
Hi Chris!

Yes, I wasn't all  all thrilled with having to cut the power with the front panel switch  but any other way didn't work so essentially had no choice.  Much rather  do an orderly shutdown.  There have been a few times when the machine  has had to put itself back together ==> recovery mode.  

NewLinux  has inquired about and I have posted information back on ALSA and the  driver version I have.  ...Did find something out ==> I had attempted  to cut and paste the Terminal's output text to the Thumbdrive -- the  file as saved but to hard drive under a filename of what I thought was  the path and filename on the thumbdrive.  The tricks I've been using  since MS-DOS 2.11 don't always work under Linux! <g>[/FONT]

---

### Post by newlinux on 2011-03-08
> **Barry_IA said:**
> [FONT=Palatino Linotype]Hi New Linux!
 
Ran the *aplay -l* command several times to see what changes might appear.  Figured might tell something. ...So far I'm just giving it a blank stare. %)

*Aplay -l* with the nouveau driver (no changes to system made yet):
card 0: NVidia [HDA Nvidia], device 3, NVIDIA HDMI [NVIDIA HDMI]
.     Subdevices: 1/1     [there is no '.' at the beginning -- using it to force the indentation]
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: NVidia [HDA Nvidia], device 7, NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: NVidia [HDA Nvidia], device 8, NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: NVidia [HDA Nvidia], device 9, NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
   [/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0


----------
Installed the nVidia driver, reboot.  Noticed there were some downloads to do so installed these.

*aplay -l* (with the nVidia driver installed):
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 1: NVidia [HDA Nvidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: NVidia [HDA Nvidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: NVidia [HDA Nvidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: NVidia [HDA Nvidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0


Looked at the Mixer GUI: HDA Nvidia switches are IEC958,  [/FONT][FONT=Palatino Linotype]IEC958 1, [/FONT][FONT=Palatino Linotype]IEC958 2, [/FONT][FONT=Palatino Linotype]IEC958 3 (all four checked.  Only tab for this option is 'Switches".

Checked playback of a TV show; the volume control is working ==> slider moves left/right with F10, F11, but no sound output.  Previously (the other day, the time before I tried installing the Nvidia driver) it was stuck at 0.

<reboot>  Now the volume slider is stuck at 0.  Results of aplay -l (will we see something different?)
card 0: Nvidia [HDA Nvidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: Nvidia [HDA Nvidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: Nvidia [HDA Nvidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 0: Nvidia [HDA Nvidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Inetl ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]   Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: ICH6 [Intel ICH6], device 4:: Intel ICH - IEC958 [Intel ICH6 - IEC958]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0


Figure reboot one more time; can change the volume again but no sound.    *aplay -l*:
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
card 1: Nvidia [HDA Nvidia], device 3: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: Nvidia [HDA Nvidia], device 7: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: Nvidia [HDA Nvidia], device 8: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0
[/FONT][FONT=Palatino Linotype]card 1: Nvidia [HDA Nvidia], device 9: [/FONT][FONT=Palatino Linotype]NVIDIA HDMI [[/FONT][FONT=Palatino Linotype]NVIDIA HDMI[/FONT][FONT=Palatino Linotype]][/FONT]
[FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]Subdevices: 1/1
[/FONT][FONT=Palatino Linotype].     [/FONT][FONT=Palatino Linotype]    Subdevice #0: subdevice #0

(Hope I typed all that correctly!  Couldn't figure out how to copy the highlighted section in Terminal to a file in the thumbdrive.  Using (or trying to!) *nano*.

Uninstalled the nVidia driver -- sound's back!

Need to get back to you on the version of Alsa I'm running.
[/FONT]

Well, one problem you'll have is that your cards switch orders (or rather are randomly assigned card #s after reboots). We'll get to that later.

I need you to do a couple of things.

1. type
```

alsamixer
```
at a terminal (incidentally, it would tell you the version of ALSA at the top of this app).

Press F6 and select the HDA NVidia sound device. Based on your aplay output you should see 4 SPDIF devices. Make sure none of them are muted (MM). If they are, press the "m" key to unmute them (it's a toggle).

2. Determine which card # is your HDMI device. (it appears to change after reboots for you but you can tell which is which by the aplay -l output).

If it is card 1 run the following commands

```

speaker-test -c2 -twav -Dplughw:1,3

```

```

speaker-test -c2 -twav -Dplughw:1,7

```

```

speaker-test -c2 -twav -Dplughw:1,8

```

```

speaker-test -c2 -twav -Dplughw:1,9

```

Let me know if you hear any sound from these commands(ctrl-C to cancel out of those commands). If your HDMI devices are on Card 0 replace the 1s with 0s (e.g. -Dplughw:0,8) in the previous command.

---

### Post by newlinux on 2011-03-08
The above, of course, is with the nvidia driver installed.

---

### Post by Barry_IA on 2011-03-09
[FONT=Palatino Linotype]Hi NewLinux![/FONT]

> **newlinux said:**
> Well, one problem you'll have is that your cards switch orders (or rather are randomly assigned card #s after reboots). We'll get to that later.

[FONT=Palatino Linotype]Nothing like adding a few complications to the beginner! <g>
[/FONT]

> **newlinux said:**
> ```

alsamixer
```at a terminal (incidentally, it would tell you the version of ALSA at the top of this app).

Press F6 and select the HDA NVidia sound device. Based on your aplay output you should see 4 SPDIF devices. Make sure none of them are muted (MM). If they are, press the "m" key to unmute them (it's a toggle).
 
[FONT=Palatino Linotype]None are muted; tested using the toggle to be sure ==> got the "MM" and "off" at 'Item'.[/FONT]


> **newlinux said:**
>  2. Determine which card # is your HDMI device. (it appears to change after reboots for you but you can tell which is which by the aplay -l output).

[FONT=Palatino Linotype]Nvidia is Card 1, Devices 3, 7, 8, 9.      

Speaker-test....1,3:  Displays to screen but no audio

Speaker-test...1,7:  Female voice: "Front Left....Front Right...."   Wo-hoo!!

Speaker-test....1,8:  [/FONT][FONT=Palatino Linotype] Female voice: "Front Left....Front Right...."  Really??!!  Was only expecting one device to work.

Speaker-test...1,9:[/FONT][FONT=Palatino Linotype] Female voice: "Front Left....Front Right...."  Wow!  Three out of four!!  Bet if the first one worked I'd have sound!  Now for the next step! :)[/FONT]

---

### Post by newlinux on 2011-03-09
Okay, so it is working, there just needs to be some configuration (it's common for one of them not to play audio - you really only should have just one, but that's another story we may address later). Before we get things too final, lets see if you can get sound from myth. What version of myth are you running (how sound is setup is different in .23 than it is in .24)? Also who is the manufacturer (or rather what brand) is your g210?

This may seem like a strange question, but after you get audio out of the other devices (1,8 1,9 etc.) have you tried running the speaker test on 1,3 again? It's okay if it doesn't work still, I'm more curious than anything else because of something I ran into on my g210 when I set it up...

Also, do you get sound from any other applications other than myth after running those speaker tests? How about if you put the following in your ~/.asoundrc file

pcm.!default hdmi:NVidia

---

### Post by Barry_IA on 2011-03-09
> **newlinux said:**
> Okay, so it is working, there just needs to be some configuration (it's common for one of them not to play audio - you really only should have just one, but that's another story we may address later). Before we get things too final, lets see if you can get sound from myth. What version of myth are you running (how sound is setup is different in .23 than it is in .24)? Also who is the manufacturer (or rather what brand) is your g210?

This may seem like a strange question, but after you get audio out of the other devices (1,8 1,9 etc.) have you tried running the speaker test on 1,3 again? It's okay if it doesn't work still, I'm more curious than anything else because of something I ran into on my g210 when I set it up...

Also, do you get sound from any other applications other than myth after running those speaker tests? How about if you put the following in your ~/.asoundrc file

pcm.!default hdmi:NVidia


[FONT=Palatino Linotype]Hi NewLinux!

Did a few of the tests -- dr's appointment shortly.

Mythbuntu 10.10 -- Frontend (the problematic one) has the current updates as of this morning.

Tested the Device 1,3 again -- it now has sound!  Tested the other three and they do too.  (Devices 3, 7, 8, and 9 all now work.)

"Test other applications" -- Firefox to YouTube music video -- no sound.

Will check on manufacturer/brand of the g210  (lspci | <what? - brainphart!> -i g210  ??) and edit the .assoundrd file when I get back.
[/FONT]

---

### Post by newlinux on 2011-03-09
> **Barry_IA said:**
> [FONT=Palatino Linotype]Hi NewLinux!

Did a few of the tests -- dr's appointment shortly.

Mythbuntu 10.10 -- Frontend (the problematic one) has the current updates as of this morning.



I'm not sure which mythtv versions you can have installed on 10.10, is the default .24? I need the version of mythtv, not mythbuntu. You can type ```
 mythfrontend --version 
``` and then tell my what is reads for Mythtv Branch or Library API.

> 
Tested the Device 1,3 again -- it now has sound!  Tested the other three and they do too.  (Devices 3, 7, 8, and 9 all now work.)



That's consistent with the behavior I get from my g210, which is why I asked. It's weird to me, but some of the devices won't work until after I do a speaker test on the other devices. So it is really sounding like yours works just like mine.
> 
"Test other applications" -- Firefox to YouTube music video -- no sound.

Will check on manufacturer/brand of the g210  (lspci | <what? - brainphart!> -i g210  ??) and edit the .assoundrd file when I get back.
[/FONT]
Those other apps are probably using the other sound card by default.

make sure it is the ~/.asoundrc that you edit. I suspect if speaker-test is working when you edit your .asoundrc other things will work (except myth - which will need to be directly configured, most likely, especially if you are running .24).

For the manufacturer - ```
lspci -v
``` might give it to you. You can search through the output for the g210 Subsystem.

---

### Post by Barry_IA on 2011-03-09
> **newlinux said:**
> I'm not sure which mythtv versions you can have installed on 10.10, is the default .24? I need the version of mythtv, not mythbuntu. You can type ```
 mythfrontend --version 
``` and then tell my what is reads for Mythtv Branch or Library API.

[FONT=Palatino Linotype]Hi NewLinux!

Mythtv Branch:   Branches/release-0-23-Fixes
Library API: 0.23.1.201000710-1
QT Version:  4.7.0
MythTV Version:  26437

Figured the last two might be of some significance.[/FONT]



> **newlinux said:**
> That's consistent with the behavior I get from my g210, which is why I asked. It's weird to me, but some of the devices won't work until after I do a speaker test on the other devices. So it is really sounding like yours works just like mine.

Those other apps are probably using the other sound card by default.
 
[FONT=Palatino Linotype]I'll worry about those later!


[/FONT]

> **newlinux said:**
> make sure it is the ~/.asoundrc that you edit. I suspect if speaker-test is working when you edit your .asoundrc other things will work (except myth - which will need to be directly configured, most likely, especially if you are running .24).

[FONT=Palatino Linotype]Couldn't find; tried *find | grep - i asound* and a few less letters.[/FONT]



> **newlinux said:**
> For the manufacturer - ```
lspci -v
``` might give it to you. You can search through the output for the g210 Subsystem.

[FONT=Palatino Linotype]Ah!  Subsystem: eVga.com Corp. Device 1211

Also saw these lines - don't know if significant or not:
[virtual] Expansion ROM at d308000 [disabled] [size=512K]
. . .   (Probably not -- I'm probably more concerned with RAM)
Kernel driver in use: nvidia
Kernel modules: nvidia-current, nouveau, nvidia-fb

And thanks for the assistance!
[/FONT]

---

### Post by newlinux on 2011-03-09
Okay - that's the info I need. You're running .23 (I'd upgrade to .24 if I were you, but that's a subject for another thread). The audio setup in .23 is a little different than .24. Let's start with this:

1. Unless you previously created it, an ~/.asoundrc file won't exist. You should create it and put the line I had previously in there. I should have mentioned that earlier.

2. Then check and see if other apps work for sound (mplayer, firefox, system sounds). Depending on how you have mythfrontend configured it may even work after you do this.

3. I need to know what audio output device you have myth set to. It should be in the Utilities/Setup->Setup->General a few screens in if memory serves me correct.

---

### Post by Barry_IA on 2011-03-09
> **newlinux said:**
> Okay - that's the info I need. You're running .23 (I'd upgrade to .24 if I were you, but that's a subject for another thread). The audio setup in .23 is a little different than .24. Let's start with this:

[FONT=Palatino Linotype]Hi NewLinux!

I'm not sure I'd dare!!  I'm not even sure I want to reboot! <g>  Things are improving and that calls for a Happy Dance Smilie   \\:D/    [/FONT]


> **newlinux said:**
> 1. Unless you previously created it, an ~/.asoundrc file won't exist. You should create it and put the line I had previously in there. I should have mentioned that earlier.

[FONT=Palatino Linotype]Does tend to explain why it couldn't be found! <g>  Created using the command *sudo nano ~/.asoundrc* then typing *pcm!.default hdmi:NVidia* (saying that partially so others reading this thread will know what to do).

Tested the speaker-test thing on all four devices (3, 7, 8, 9) -- so far, still so good!

Firefox to YouTube video -- I get sound!!! Woo-hoo!!   It's using "S/PDIF 1" (the second one listed in the AlsoMixer GUI. ....Well, I muted the first one and no change, muted the second and it went silent, unmuted; didn't test the other two.   The sound is at a decent volume (with the nouveau driver had to crank up the TV's volume) but sounds a bit distorted - sounds like a faint sleigh bell at the end of words.  ... I know: quit whining! <ggg>   

You said to check other apps - at this point really haven't used anything on that system but Firefox and MythTV.  I think I have the DVD player going -- the <Eject> option opens and closes the tray -- played with that this morning for some reason.   [/FONT]




 > **newlinux said:**
> 3. I need to know what audio output device you have myth set to. It should be in the Utilities/Setup->Setup->General a few screens in if memory serves me correct.

[FONT=Palatino Linotype]You are correct!  And MythTV does play with sound!!  The  volume slider does doe up/down but doesn't have any effect on the audio level; <mute> doesn't work either ("Stop whiiiiinning!" <gg>  I'm guessing I need to set the Audio Output Device to "Alsa: HDMI"?  (Haven't done anything yet.)

Anyway, the "Audio System" page:
. . . Audio Output Device:  ALSA: default
. . . Speaker configuration: Stereo  (TV's 'just' stereo)

I think we're getting there!! :)  [/FONT]

---

### Post by newlinux on 2011-03-09
Alright - good. Well, I can't help troubleshoot the mythtv internal volume thing, I've never used it (I always use the receiver and/or TV and/or system volume to control that). Also, it's hard to troubleshoot sound quality problems remotely for obvious reasons...

Alsa:default is fine as an audio output device in .23. The reason you weren't getting sound before with the nvidia driver was probably in part because HDMI wasn't the default audio output. What you put in the .asoundrc made it the default. But Changing it to alsa:HDMI *should* work too

Now we probably need to get this working so that you don't have to change anything after reboots.  I've got some ideas on that, but don't have time to write them up now.

You can get the information I'm going to use from:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

Essentially, we're going to set some module options to ensure your nvidia HDMI comes up as the same card each time... Gotta run. Hope to be back on tomorrow.

Glad we've progressed. At least now you can seee if you have lockups using the nvidia driver.

---

### Post by Barry_IA on 2011-03-09
> **newlinux said:**
> Alright - good. Well, I can't help troubleshoot the mythtv internal volume thing, I've never used it (I always use the receiver and/or TV and/or system volume to control that). Also, it's hard to troubleshoot sound quality problems remotely for obvious reasons....

[FONT=Palatino Linotype]Hi NewLinux!

Controlling the sound using the TV's remote control isn't a big deal -- usually do it that way anyway.  Thought I should mention it  and the 'sleigh bell distortion' thing; was watching a bit of live TV and didn't notice any sound distortion; in fact the picture looked sharper than usual.  Will be watching a recorded show or two tonight -- hope all goes well!!
[/FONT]

> **newlinux said:**
> Alsa:default is fine as an audio output device in .23. The reason you weren't getting sound before with the nvidia driver was probably in part because HDMI wasn't the default audio output. What you put in the .asoundrc made it the default. But Changing it to alsa:HDMI *should* work too
 
[FONT=Palatino Linotype]I think I might try editing .asoundrc to the HDMI option to see if that fixes the Firefox audio.  Won't do until tomorrow at the earliest as also running short on time on this end.  Day off today, which worked out great!!  (Thank you again!)[/FONT]


 > **newlinux said:**
> Now we probably need to get this working so that you don't have to change anything after reboots.  I've got some ideas on that, but don't have time to write them up now.

You can get the information I'm going to use from:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

Essentially, we're going to set some module options to ensure your nvidia HDMI comes up as the same card each time... Gotta run. Hope to be back on tomorrow.

Glad we've progressed. At least now you can seee if you have lockups using the nvidia driver.

[FONT=Palatino Linotype]It's amazing how all this information is out there -- just hard to find if one doesn't know what the heck they're doing! <g>    ...I'll be looking forward to continuing this, and hopefully also late tomorrow afternoon.  I'm in the Chicago time zone.  Have a good evening ... or whatever time it is where you are! <g>[/FONT]

---

### Post by Barry_IA on 2011-03-10
> **newlinux said:**
> Glad we've progressed. At least now you can seee if you have lockups using the nvidia driver.
[FONT=Palatino Linotype]
Good Morning, NewLinux!

No lock ups last night -- watched about 1½ hours of recorded shows.  Audio was fine -- the distortion problem might just be with Firefox using the old driver as you mentioned.  As noted the picture was sharper.  With the nouveau driver the picture was detailed but with the nVidia driver it is more so.

Didn't want to shut down the Frontend computer as it was working but had to.  Will see what happens this afternoon after work!  
[/FONT]

---

### Post by chrisblue on 2011-03-10
Barry,

How did you remove the nvidia drivers when after you had installed them.

I thought I would try to install them to solve my freezing problem and apart from the changed mythbuntu splash screen font which you reported I get a command prompt asking me to log in. 

I can log in using the mythbox user and p/w but the am still at a terminal prompt.

Just like to remove the nvidia drivers and go back to what I had before. WAF is going to go downhill fast tomorrow AM with no TV.

Chris

---

### Post by chrisblue on 2011-03-10
Barry,

OK panic over for now :)

ssh'd in from another box and edited the xorg file and replaced nvidia with vesa and I am back with a working mythbox...phew

Solution found here [http://ubuntuforums.org/showthread.php?t=488145](http://ubuntuforums.org/showthread.php?t=488145)

Since the nvidia driver is installed I will see if it solves my freezing problem. One thing I did note though is that blank screens between channel changes are now a bright green. Kind of jarring to see.

Cheers
Chris

---

### Post by newlinux on 2011-03-10
> **chrisblue said:**
> Barry,

OK panic over for now :)

ssh'd in from another box and edited the xorg file and replaced nvidia with vesa and I am back with a working mythbox...phew

Solution found here [http://ubuntuforums.org/showthread.php?t=488145](http://ubuntuforums.org/showthread.php?t=488145)

Since the nvidia driver is installed I will see if it solves my freezing problem. One thing I did note though is that blank screens between channel changes are now a bright green. Kind of jarring to see.

Cheers
Chris

Are you using the nvidia driver or do you just have it installed? Just having it installed probably won't change much if you aren't using it. Remember, when using the nvidia driver, it is a very good idea to play with your playback profiles.

---

### Post by newlinux on 2011-03-10
> **Barry_IA said:**
> [FONT=Palatino Linotype]
Good Morning, NewLinux!

No lock ups last night -- watched about 1½ hours of recorded shows.  Audio was fine -- the distortion problem might just be with Firefox using the old driver as you mentioned.  As noted the picture was sharper.  With the nouveau driver the picture was detailed but with the nVidia driver it is more so.

Didn't want to shut down the Frontend computer as it was working but had to.  Will see what happens this afternoon after work!  
[/FONT]

Good, hopefully it stays more stable. told you that you would definitely want to use the Nvidia driver :). It has so much more quality and features. Not sure why the firefox sound is so bad. did you say like a sleigh bell at the end of words? Not sure what that means. You might need to adjust mixer settings. IF you have sound at all it's using the same sound card as mythtv is because you don't have any other sound hooked up hooked up to the TV where you are getting your sound from. 


Okay, now for the experimentation part to make sure things work the same after reboots. Don't worry, we can back out of these changes easily.

in your /etc/modprobe.d/alsa-base.conf file (create if you don't have it)

put:
```


options snd-hda-intel enable_msi=0 index=1 probe_mask=2

```

and reboot.

Let me know the output of aplay -l, use alsamixer to confirm no spdif output is muted and try the speaker tests on the card,device you have available. This point of these options is to make sure you have only one Card,device for HDMI (you currently have four, but really you are only supposed to have one, and having four may complicate things/cause problems). The other issue is should solve is making sure your HDMI card always comes up as card 1 instead of switching each reboot.

Hopefully this will work. I've had some mixed results with the module options but I have an off brand g210. Your brand is listed in that wiki with instructions to use that probe mask.

---

### Post by chrisblue on 2011-03-10
> **newlinux said:**
> Are you using the nvidia driver or do you just have it installed? Just having it installed probably won't change much if you aren't using it. Remember, when using the nvidia driver, it is a very good idea to play with your playback profiles.

I plan to uninstall the nVidia driver and reinstall the version .19 driver and see how I go with that. At least I know that I can fall back on the vesa driver to get a display if I need to.

Maybe over the weekend. Holiday for me on Monday so plenty of time to work out issues.

---

### Post by Barry_IA on 2011-03-10
> **chrisblue said:**
> How did you remove the nvidia drivers when after you had installed them.

[FONT=Palatino Linotype]Hi Chris!

You don't!  You follow NewLinux's instructions! <ggg>

The way I installed and removed was via the Desktop (if you automatically go to MythTV hit escape, it should give you three options like "No - go back to MythTV", "Yes - exit to the desktop", and "Yes - exit and shutdown".  Verbage is approximate.    Click through: Applications > System > Additional Drivers..  When you select this it will take a while as it searches.  Eventually (about a minute) it displays a window about the nVidia driver -- either installed or not installed, depending on which it is.  With the driver installed at the lower right is the <Remove> button. Click, verify, and wait about a minute until it tells you the removal is complete and reboot.  Clicking that reboot button never seems to do anything; I've had to reboot using with the circular icon at the upper right or the shutdown options in Applications.   ...The reboot will take a little longer than normal with finishing up of the installation.
[/FONT]



> **chrisblue said:**
> I thought I would try to install them to solve my freezing problem and apart from the changed mythbuntu splash screen font which you reported I get a command prompt asking me to log in. 

[FONT=Palatino Linotype]Does the window look really plain?    Mine had my first and last name and underneath I think it said "Other".  Selecting me it then asked for my password.  You might end up in an endless loop as you installed the driver differently.  I was getting mine while I was in Myth and asked it to play a TV recording with a resolution higher than the monitor would handle.  I was using an old CRT; it would handle 720p but a 1080p show and the X server (X something!) would crash.  [/FONT]
 


> **chrisblue said:**
> Just like to remove the nvidia drivers and go back to what I had before. WAF is going to go downhill fast tomorrow AM with no TV.
 
[FONT=Palatino Linotype]I'm kind of laughing here because it was that sort of thing I wanted to avoid -- while the lock up was annoying not being able to watch any shows downstairs would have been a PITA.  One reason I didn't do anything unless instructed.   (Need an icon for 'chicken'! <g>)    [/FONT]

---

### Post by Barry_IA on 2011-03-10
> **newlinux said:**
> Good, hopefully it stays more stable. told you that you would definitely want to use the Nvidia driver :). It has so much more quality and features. Not sure why the firefox sound is so bad. did you say like a sleigh bell at the end of words? Not sure what that means. You might need to adjust mixer settings. IF you have sound at all it's using the same sound card as mythtv is because you don't have any other sound hooked up hooked up to the TV where you are getting your sound from.

[FONT=Palatino Linotype]Hi NewLinux!

Think we'll worry about the Firefox sound a little later -- the TV shows playback is much more important.  As for the "sleigh bell" reference, overall the sound (while in Firefox, at YouTube) sounded like a barely audible ringing (think tinnitus -- ringing in the ears) with the end of words a louder brief ring.  Didn't sound echo-y but maybe a little like a bit of feedback.            [/FONT]



> **newlinux said:**
> in your /etc/modprobe.d/alsa-base.conf file (create if you don't have it)

put:
```


options snd-hda-intel enable_msi=0 index=1 probe_mask=2

```and reboot.

[FONT=Palatino Linotype]Before starting I did test Myth - no audio.  Didn't panic. <g>  

The file does exist so I appended the text to the bottom.  Rebooted and yes, did check Myth -- we have audio!!  :p 

The AlsaMixer GUI now only has one control: "S/PDIF".

*aplay -l* results:
card 0: ICH6 [Intel ICH6], device 0: Intel ICH {Intel ICH6]
. . . Subdevices: 1/1
. . . Subdevice #0: subdevice #0
Card 0: ICH6 [Intel ICH6]m device 4: Intel ICH - IEC958
[/FONT][FONT=Palatino Linotype]. . . Subdevices: 1/1
. . . Subdevice #0: subdevice #0
Card 1: Nvidia [HDA Nvidia], device 3: Nvidia HDMI [Nvidia HDMI]
[/FONT][FONT=Palatino Linotype]. . . Subdevices: 1/1
. . . Subdevice #0: subdevice #0
[/FONT]

[FONT=Palatino Linotype]Speaker-test results:
1,3: OK: get audio
1,7, 1,8, and 1,9 now give "Playback error: -2 No such file or directory"  I'm presuming this is correct as originally I had "4" cards and now only the one.

And thanks again for your assistance!!  Will check what's going on with Firefox's audio and get back.[/FONT]

---

### Post by Barry_IA on 2011-03-10
> **chrisblue said:**
> Since the nvidia driver is installed I will see if it solves my freezing problem. One thing I did note though is that blank screens between channel changes are now a bright green. Kind of jarring to see.
 
[FONT=Palatino Linotype]Chris:

Rereading through the messages to see if any replies while I was on and noticed this.  I don't recall seeing a bright green screen -- hopefully that gets corrected.  I wonder if that's a function of installing the nVidia driver the way you did vs. the way I suggested or something your TV/monitor is doing ==> you know how when the signal is gone one can get a blue screen.
[/FONT]

---

### Post by chrisblue on 2011-03-10
I think that the issue is that even though I installed the nVidia driver I have had to disable it and use the vesa driver to get any display at all.

As I said up thread I plan to remove that driver and install version xxx.19 which is I think available in one of the repos as I read somewhere that xxx.18 is broken.

However the good thing is I do have the vesa driver to fall back on.

With the nVidia driver that I installed I couldn't get ANY graphical interface as I think the x server (?) wouldn't start so all I could get was a full screen terminal log in. Always a bit scary when that happens. Hence my question as to how you removed it. You used the GUI which I couln't access but if you had used the terminal to remove it I could have done something similar.

Anyway I looks like your issues have been solved which is great. Kudos to Newlinux for the successful outcome:)

---

### Post by Barry_IA on 2011-03-10
> **chrisblue said:**
> I think that the issue is that even though I installed the nVidia driver I have had to disable it and use the vesa driver to get any display at all.

As I said up thread I plan to remove that driver and install version xxx.19 which is I think available in one of the repos as I read somewhere that xxx.18 is broken.

However the good thing is I do have the vesa driver to fall back on.

With the nVidia driver that I installed I couldn't get ANY graphical interface as I think the x server (?) wouldn't start so all I could get was a full screen terminal log in. Always a bit scary when that happens. Hence my question as to how you removed it. You used the GUI which I couln't access but if you had used the terminal to remove it I could have done something similar.

Anyway I looks like your issues have been solved which is great. Kudos to Newlinux for the successful outcome:)

[FONT=Palatino Linotype]Hi Chris!

If version 18 has a problem then probably best to go on to v.19.  Hope that solves your problem, or at least enough of it so you can install the nVidia driver.  ...I have essentially no idea of what version anything is other than "Mythbuntu 10.10".  Nothing like jumping in and learning Linux after! <g>  

And yes, soooo glad to have the correct driver -- hopefully will resolve the lockups.  LIS, last night was the first time -- bookmarked frequently but didn't need it.  As the problem is infrequent ind intermittent will continue to do so until feel more assured it has been resolved.  I'm reasonably certain it has.

And the new computer arrived today.  Working the weekend so no time until Monday to install Mythbuntu on that one.  At least if I see that nouveau thing I have a pile of printouts to guide me![/FONT]

---

### Post by newlinux on 2011-03-10
> **Barry_IA said:**
> [FONT=Palatino Linotype]Hi NewLinux!

Think we'll worry about the Firefox sound a little later -- the TV shows playback is much more important.  As for the "sleigh bell" reference, overall the sound (while in Firefox, at YouTube) sounded like a barely audible ringing (think tinnitus -- ringing in the ears) with the end of words a louder brief ring.  Didn't sound echo-y but maybe a little like a bit of feedback.            [/FONT]





[FONT=Palatino Linotype]Before starting I did test Myth - no audio.  Didn't panic. <g>  

The file does exist so I appended the text to the bottom.  Rebooted and yes, did check Myth -- we have audio!!  :p 

The AlsaMixer GUI now only has one control: "S/PDIF".

*aplay -l* results:
card 0: ICH6 [Intel ICH6], device 0: Intel ICH {Intel ICH6]
. . . Subdevices: 1/1
. . . Subdevice #0: subdevice #0
Card 0: ICH6 [Intel ICH6]m device 4: Intel ICH - IEC958
[/FONT][FONT=Palatino Linotype]. . . Subdevices: 1/1
. . . Subdevice #0: subdevice #0
Card 1: Nvidia [HDA Nvidia], device 3: Nvidia HDMI [Nvidia HDMI]
[/FONT][FONT=Palatino Linotype]. . . Subdevices: 1/1
. . . Subdevice #0: subdevice #0
[/FONT]

[FONT=Palatino Linotype]Speaker-test results:
1,3: OK: get audio
1,7, 1,8, and 1,9 now give "Playback error: -2 No such file or directory"  I'm presuming this is correct as originally I had "4" cards and now only the one.

And thanks again for your assistance!!  Will check what's going on with Firefox's audio and get back.[/FONT]

You should only have one plug now with those module options, and it should work between reboots (although if it doesn't double check the alsamixer and make sure it's not muted - that happens to me sometimes for no apparent reason after reboots - I didn't investigate because I rarely ever reboot any my machines. I've had uptimes over a year (: ). The other speaker-tests are no longer relevant as having four was really more of a bug than anything. You are supposed to have one, should make more things work consistently. So you are good on that front. Except for the firefox audio - which I don't have many ideas about, but maybe something will come to mind.

---

### Post by Barry_IA on 2011-03-11
> **newlinux said:**
> You should only have one plug now with those module options, and it should work between reboots (although if it doesn't double check the alsamixer and make sure it's not muted - that happens to me sometimes for no apparent reason after reboots - I didn't investigate because I rarely ever reboot any my machines. I've had uptimes over a year (: ). The other speaker-tests are no longer relevant as having four was really more of a bug than anything. You are supposed to have one, should make more things work consistently. So you are good on that front. Except for the firefox audio - which I don't have many ideas about, but maybe something will come to mind.
[FONT=Palatino Linotype]
Hi NewLinux!

Didn't reboot last night except on the instruction to do so (after adding the line to alsa-base.conf) -- this time not a 'fear' of loosing what is working but awaiting instructions.  The good news is another night of no lockups!  \\:D/  Yes, that deserves a happy-dance smilie!  Planning on checking the unit later this morning, plus see what Firefox's audio is up to.

Should be able to apply a "Solved" very soon!  :)
[/FONT]

---

### Post by newlinux on 2011-03-11
> **Barry_IA said:**
> [FONT=Palatino Linotype]
Hi NewLinux!

Didn't reboot last night except on the instruction to do so (after adding the line to alsa-base.conf) -- this time not a 'fear' of loosing what is working but awaiting instructions.  The good news is another night of no lockups!  \\:D/  Yes, that deserves a happy-dance smilie!  Planning on checking the unit later this morning, plus see what Firefox's audio is up to.

Should be able to apply a "Solved" very soon!  :)
[/FONT]

Cool. Let me know if you have any problems with no sound. I'm pretty sure I know enough things to fix them, but I'm hoping we've already made things pretty solid so for the most part, even after reboots things should just work. And here's to hoping lockups are gone. Might be worth it setup an new thread for firefox audio - others may have had the problem who aren't looking at this thread.

---

### Post by Barry_IA on 2011-03-11
> **newlinux said:**
> Cool. Let me know if you have any problems with no sound. I'm pretty sure I know enough things to fix them, but I'm hoping we've already made things pretty solid so for the most part, even after reboots things should just work. And here's to hoping lockups are gone. Might be worth it setup an new thread for firefox audio - others may have had the problem who aren't looking at this thread.
[FONT=Palatino Linotype]
Hi NewLinux!

Just came from downstairs -- tested the system.  Did a regular boot -- Frontend system was off overnight.  Booted normally, got sound with Myth.  Tested Firefox's audio ==> went back to the same YouTube video with the 'sleigh bell' audio -- none this time!!    Yesterday had also turned down some of the audio controls in the analog/Intel portion as they were showing red.  Today tested to see which one ==> individually applied muting to the analog controls -- no change. Switched to the HDA Nvidia card -- mute - silence!  So now Firefox is using the same audio support as Myth is, which is good.

So now I'm going to apply "SOLVED!" to this thread-- think I remember where!.  ...Take care of ChrisBlue!  And again, thanks for all your assistance!
[/FONT]

---

### Post by Barry_IA on 2011-03-15
[FONT=Palatino Linotype]As a follow-up, there have been no lock-ups since switching to the nVidia driver and correcting the problem with the audio.  Definitely 'solved' and a big thanks to NewLinux and all the others who got me on the right track![/FONT]
           :popcorn:

---

