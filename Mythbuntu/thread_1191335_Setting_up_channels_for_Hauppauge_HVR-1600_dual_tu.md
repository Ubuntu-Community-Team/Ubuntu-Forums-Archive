---
title: "Setting up channels for Hauppauge HVR-1600 dual tuner (analog/digital)"
date: 2009-06-18
forum: Mythbuntu
---

### Post by Jeconti on 2009-06-18
Alright, so a lot is riding on this one. If I can figure out how to set up this system, I win a bet with my Dad, and a Microsoft loyalist since the 70s will have to put Jaunty on his non-production desktop.

I'm running Mythbuntu 9.04, and my cable provider is TWC. I am not using a set top box, rather, running the coaxial cable directly to the card.

The card has been installed and configured correctly. I have downloaded and compiled the latest V4l-DVB driver on the system. My issue has been with recognizing channels.

I've tried it a few different ways. First off, the IVTV ID does not recognize the card, even though it's the profile that specifies MPEG2 encoding. I can set up the card using the DVB DTV profile, or the regular old MJPEG one.

When I set up the card with the MJPEG profile, I scan channels, and it grabs a lot of them, but then when I go to play the channels, the screen flickers for a second, then does nothing.

When I set up using the DVB DTV profile, it recognizes the QAM and ATSC capabilities, but will not get any channel info when scanning.

I've been using this [MythTV Wiki page]("http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)"), however ran in to an issue that I don't know how to solve.

When I run ```
scan atsc/us-Cable-Standard-center-frequencies-QAM256
```

The terminal returns ```
scanning atsc/us-Cable-Standard-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

```

Ideas? Help?

---

### Post by ian dobson on 2009-06-19
Hi 

The "main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy" means something else is using the card. If you wish to use the scan program then make sure that mythbackend is not running (/etc/init.d/mythbackend stop).

With the rest I can't help you much, I don't know your card.

Regards
Ian Dobson

---

### Post by klc5555 on 2009-06-19
Re: the analog half of the card.

It has an odd quirk with mythtv-setup. The card is an mpeg2 hardware encoder.  But when adding the card in the mythtv backend setup, if you try to add it directly as a mpeg2 card, mythtv will not recognize it.

The trick is to add the card as an ordinary v4l analog card, which is recognized. Save this. Then, go back into the Capture Card setup for this card, and _change_ it from ordinary v4l card to an mpeg2 card. Now it should be recognized correctly as an mpeg2 card. You can save this and you should be good to go.

Re: the digital half of this card: I hope you have really good DVB signal strength --these cards seem to be a bit deaf. However, I don't know whether the digital issues with these cards are hardware or software based. There has been an awful lot of work being done over the last 8 months or so on the cx18 driver, so your experiences with the 1600 may be perfectly pleasant.

Cheers! :)

---

### Post by Jeconti on 2009-06-19
Thanks guys, both suggestions have worked to an extent. I was able to properly load the analog half and have successfuly scanned channels.

However, when I move over to the frontend and move to watch TV, the screen goes dark for a moment, then flashed back to the TV menu.

On the digital half, the running backend was the issue, but I've tried three scans now with no luck of tuning to QAM or ATSC channels.

---

### Post by klc5555 on 2009-06-19
> **Jeconti said:**
> Thanks guys, both suggestions have worked to an extent. I was able to properly load the analog half and have successfuly scanned channels.

However, when I move over to the frontend and move to watch TV, the screen goes dark for a moment, then flashed back to the TV menu.

On the digital half, the running backend was the issue, but I've tried three scans now with no luck of tuning to QAM or ATSC channels.

1)Make sure the analog half of the card is the first card added in the backend setup --the first card added is the default fired up for "livetv". If the dvb half is first, but not set up completely/correctly, "livetv" will die when you try firing it up.

2) Make sure you have run mythfilldatabase after finishing the backend setup.

3) Sometimes there's a permissions problem if you're using storage directories other than the default /var/lib/mythtv/recordings  If the "mythtv" account can't write to every storage directory, it kicks you to the menu. Make sure every storage directory is owner: mythtv; grp: mythtv and is writeable by the mythtv user (i.e. permissions at 775) Your own main user account should have been added to the mythtv group as a part of the backend setup process. 

4) The cx18 module frequently refuses to load cleanly on boot. Result may be blank screen, pink screen, degraded sound, or even bailing out to the main menu. In these cases, the pair of commands from a terminal "sudo rmmod cx18" and "sudo modprobe cx18" will generally get it loaded correctly. If you have rebooted anywhere hereabouts after setting up your backend, make sure it was a shutdown and cold boot after 30-ish seconds rather than just a warm restart.

5) If the card still doesn't get going for you, you'll need to check the mythfrontend and mythbackend logs for the time you try to initialize livetv, to see what's blowing up for you at that point.

---

### Post by Jeconti on 2009-06-19
Alright, we're getting somewhere here people. Digital tuning still hasn't happened, but the analog tuner is up and running, scanned channels, and even opens and displays when I launch livetv.

However, the picture and audio are extremely choppy. Almost like it loads a few frames, displays, then pauses and loads more frames.

Which is wierd, cause the first thing I tried right after was watching TV on my Mini9 using mythtv frontend, which worked with no issues.

So, the mystery continues. I'll do some searching myself, but I just wanted to update the thread.

---

### Post by MythAaron on 2009-06-22
Check out [this wiki page.]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600")  It's specific to the 1600 and the one I used when I set up my card and it was fairly painless.  It looks like you are most of the way there, so you can probably skip down to the configuration part.  There is a script near the bottom of the page that should fix your choppy A/V problem.

The cx18 driver is kind of green, so it needs some TLC.

---

### Post by sliverbaer on 2009-06-22
Howdy,

I recently just set up Mythbuntu 9.04 with the HVR-1600, also.  Analog signals scanned fine, but as of yet, I don't have the digital atsc detecting any signals over cable.  (I also have TWC and no set top box.)

I have referenced the wiki page on the 1600, good info. [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

In searching I found this from the Hauppauge site:

> ATSC digital TV is the over-the-air HD digital TV for North America. ATSC digital TV typically requires an antenna for reception, and is currently broadcast in 200 cities, with over 1500 TV stations. ATSC broadcasts range in resolution from standard definition up to the high definition 1080i format. The WinTV-HVR can be used to watch and record all ATSC formats.
              Note: ATSC digital TV is NOT digital cable TV or digital satellite TV. The WinTV-HVR-1600 cannot receive  digital satellite TV.
[http://www.hauppauge.com/site/products/data_hvr1600.html](http://www.hauppauge.com/site/products/data_hvr1600.html)

The ATSC will only work over the air?  I think I might try an antenna and see what happens.

I'm still working on getting MythArchive to work properly, weird soundless recordings after transcoding, and fiddling with the recording quality settings.   There was also some goofy stuff going on where the frontend would start multiple times, until I turned off the autologin within the Mythbuntu Control Center and turned autologin in the Ubuntu settings along with turning off the startup of the frontend and switching it with starting the MythWelcome screen instead.

I'm really liking MythWeb and ScedulesDirect, makes choosing recordings very easy from anywhere in the house.

---

### Post by Jeconti on 2009-06-22
Yeah, Schedules Direct is rocking my world too right now. Def. worth the 20 bucks a year if you're not getting data over the air. I checked the box of the card more in depth. It seems pretty clear that if you don't have a set top box, you're definitely not getting QAM. The card has no hardware to decode digital cable.

As far as ATSC goes, I still have to try it out. I don't have a digital antenna lying around to play with it. Sadly, it won't make a difference. See, I set up the media server because I'm trying to save money by not buying a TV or paying for DVR. Originally I was just going to use an antenna all by itself, but the apartment where I'm living next semester is a basement. No clear place I could set up an antenna. I can play with it while I'm home for the summer though.

Analog side works great though. When I start livetv the first time, the picture is really choppy. I exit out and start it again and then it works fine.

I am having problems with the program guide during live tv viewing. Whenever I try to bring it up, if flickers and eventually causes the screen to go blank. I'm gonna start searching around for answers to that one.

Also, remote is only moderately functional. Right now I have it set up under one of the WMC profiles. But it lacks basic functionality such as actually controling the volume and not recording.

It's progressing. I'll probably spend some time on a success story post when this is all over.

---

### Post by MythAaron on 2009-06-23
> **Jeconti said:**
> I checked the box of the card more in depth. It seems pretty clear that if you don't have a set top box, you're definitely not getting QAM.
Don't be so quick to write off QAM.  This is from the wiki I mentioned:
> Some of the HVR-1600's (product code 74021 and 74041 found on the tuner label) also support Clear QAM, which is most likely the stuff your cable company uses for your local HD channels.

> As far as ATSC goes, I still have to try it out. I don't have a digital antenna lying around to play with it.
When you are ready, don't worry about buying an expensive "HDTV" antenna.  I use a 10-year old amplified loop antenna and it works pretty well.  Digital is great--you either get it or you don't.  Line of sight is another matter.
> Analog side works great though. When I start livetv the first time, the picture is really choppy. I exit out and start it again and then it works fine.
That is where that script on the wiki page comes into play.  It pulls a little video off the card when Mythfrontend starts that way it is ready when you want to watch TV.
> I am having problems with the program guide during live tv viewing.
You'll get it.  All you need to do is spend some time tweaking the settings.  Take a good look at Utilities/Setup --> Setup --> TV Settings.  That is a good place to get lost for a while--especially in Playback.  That is where you set up you playback profiles and you can squeeze out quite a bit of performance.

What video card do you have?
> Also, remote is only moderately functional.
I can send you my .lircrc if you want.
> I'll probably spend some time on a success story post when this is all over.
I'm sure you will.  Then you will also be able know many of the things that the next newbie needs to know.

---

### Post by Jeconti on 2009-06-23
I'm using a GeForce 8500GT with the open source driver as I've been unable to find a restricted nvidia driver that doesn't conflict with the cx18 driver for the card.

your lircrc would be great, but I'm not sure I'd know what to do with it. I set up my remote using this [thread]("http://www.gossamer-threads.com/lists/mythtv/users/373584")

I've been messing around in the TV and Program Guide settings. No luck yet. What is everyones feeling on OpenGl? I've read place that everyone removes reference to it wherever possible in their config.

---

### Post by MythAaron on 2009-06-23
You really need the restriced driver.  Once you install it, open /boot/grub/menu.lst and add vmalloc=265M to the kernel line.  Then cx18 and nvidia will play together.

---

### Post by klc5555 on 2009-06-23
> **Jeconti said:**
> I'm using a GeForce 8500GT with the open source driver as I've been unable to find a restricted nvidia driver that doesn't conflict with the cx18 driver for the card.



This is a very well-known problem with NVidia + cx18. Insufficient virtual memory allocation. But the solution is simple.

Grub has to be run so that the menu.lst file may be configured to pass a vmalloc parameter to the kernel at boot. vmalloc=256m or vmalloc=512m on the kernel line should do it.

---

### Post by Jeconti on 2009-06-23
I have tried this fix to no avail actually. I don't remember if it was this thread or another that I asked about how to know how much vm you need to allocate.

Edit: Must have done something wrong the first time. Works fine now, and it fixed the flickering problems with the guide. Now all that's left is the remote.

---

### Post by MythAaron on 2009-06-23
Here is my lircrc.  Just rename it .lircrc and put it in you home directory.

---

### Post by sliverbaer on 2009-06-23
Howdy,

This is all I did for my remote.  I disabled the IR Transmitter, cause I don't need it.

[IMG]http://home.roadrunner.com/%7Epodunk/lj/remote.png[/IMG]

As for the model, I have the 74041 LF variety.  It might be the signal, I've got it splitting before it gets to the dvr.  Maybe I'll try it on my LCD TV and see if I get a signal or not.

---

### Post by Jeconti on 2009-06-24
just add he .lircrc file to my home folder?

---

### Post by MythAaron on 2009-06-24
Yes, but do it after sliverbaer's suggestion.

My .lircrc isn't very different than the stock one.  The power button reloads mythfrontend, the red button is a delete button, and the blue button brings up the signal strength OSD while watching OTA TV.

---

### Post by Jeconti on 2009-06-24
Afraid silverbaer's suggestion busted the semi-working configuration I had in place already.

I reverted back to my previous configuration and replaced my .lircrc with the one that you sent me and restarted the lirc daemon. The remote had no noticeable difference in operation after I had done this.

---

### Post by MythAaron on 2009-06-24
Did you restart lirc?  If you did, then try this:
```
sudo ln -sf /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge /etc/lirc/lircd.conf
```

---

### Post by sliverbaer on 2009-06-24
Doh, sorry it didn't work.  I have trouble with it when I'm not pointing at the indented part of the sensor, had to stick it to the front of the tv stand.

I did get the digital HD signals to work.  I reseeded the card, used the line running to my hdtv, ran the scan.  I did connect the split line to the tv, somewhat lower signal, but enough to get a good picture.  I then reconnected the split line to the hvr1600 and still works fine.

I recorded Conan last night in HD.  Picture is great.  I need to work on the splotchy skipping it's doing now.  Got an ATI Radeon 9550 in there, but I notice that my 1GB of RAM I have in the system is being fully utilized, when just the frontend is running, not just playback or recording.  Think more RAM would be better to try first before swapping out the video card?
             
```
             total       used       free     shared    buffers     cached
Mem:       1012468    1002608       9860          0       1072     291852
-/+ buffers/cache:     709684     302784
Swap:       995988     146672     849316
```

---

