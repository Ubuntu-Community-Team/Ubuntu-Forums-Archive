---
title: "Show stopper: No DVD RIP in 0.24?"
date: 2010-11-27
forum: Mythbuntu
---

### Post by dibuntux on 2010-11-27
I understand that 0.24 is not compatible with MTD, so is not capable of RIP DVDs. And this is not good, as all step backward are. This is a showstopper.

Does that mean that 0.24 is not able to produce DVDs from recorded LiveTV programs or other video files?

What is pourpose of having the best DVR in town if you cannot make DVDs with menu like the previous version?

Can someone explain?

Thanks in advance

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by thatguruguy on 2010-11-27
ripping and burning dvds are two different things.

EDIT: Try handbrake for ripping DVDs.

---

### Post by dibuntux on 2010-11-28
Hi thatguru,
thanks for the reply! 

You mean I could use handbrake for rip and still use Myth 0.24 for burning a DVD, using the ripped image or livetv recordings?

TIA

---

### Post by nickrout on 2010-11-28
you should be able to. Personally I haven't tried mytharchive for ages.

---

### Post by elgordo123 on 2010-11-28
I normally use dvdfab to rip.  This makes the video_TS and audio_TS folders.  Most of the time ill use handbrake to encode the main movie, or ill use a command to create an ISO then move either the ISO or mp4 to my library.

---

### Post by dibuntux on 2010-11-29
Thanks all for the reply...
I can pass on dvd rip, but the ability to get a DVD out from my Livetv recs or videos is very important.

So is it still possible on 0.24?

---

### Post by thatguruguy on 2010-11-29
Yep.

---

### Post by nickrout on 2010-11-29
Of course looking at the release notes would tell you that mytharchive is stil in active development:

[http://www.mythtv.org/wiki/Release_Notes_-_0.24#MythArchive](http://www.mythtv.org/wiki/Release_Notes_-_0.24#MythArchive)

> MythArchive
Bug Fixes

    * Fix adding MythVideo files when the file is stored in a storage group [24878]
    * Fix thumbnail image finder to display the correct frame [25067]
    * Fix creation of DVDs which contain video titles containing special characters that need escaped [26667] 

Changes/Improvements/Other

    * Replace tcrequant with M2VRequantiser for shrinking MPEG2 video [24416]
    * Improve stream ordering when using ProjectX [25063]

---

### Post by dibuntux on 2010-11-30
Ok, now I get it. Thanks. As for ripping, I took a look at handbrake, release 0.9.4 is not supported on ubuntu becouse of new gnome...

I added boxee to my main menu, is there a rip program automatic enough to be added to DVD menu, so I can use it as a substitute for DVD rip in myth?

---

### Post by thatguruguy on 2010-11-30
> **dibuntux said:**
> Ok, now I get it. Thanks. As for ripping, I took a look at handbrake, release 0.9.4 is not supported on ubuntu becouse of new gnome...

I added boxee to my main menu, is there a rip program automatic enough to be added to DVD menu, so I can use it as a substitute for DVD rip in myth?


Handbrake works fine on my mythbuntu 10.10 system.  I suggest getting the latest version by installing the [ppa for hunterk]("https://launchpad.net/%7Ehunter-kaller/+archive/ppa").

---

### Post by nickrout on 2010-11-30
> **dibuntux said:**
> Ok, now I get it. Thanks. As for ripping, I took a look at handbrake, release 0.9.4 is not supported on ubuntu becouse of new gnome...

I added boxee to my main menu, is there a rip program automatic enough to be added to DVD menu, so I can use it as a substitute for DVD rip in myth?

what format do you want to rip to?

---

### Post by dibuntux on 2010-12-01
Format is not the problem, X264 or Xvid would do. The problem is I would like to use it with a remote control from the sofa, since my machine has no mouse. Possibly in the background...so I can watch tv mean while ripping...
Then if Mytharchive still works, eventually writing to DVD the ripped file.

Any idea?

---

### Post by thatguruguy on 2010-12-01
Assuming you have a working lirc setup, you can always assign mouse movements and button presses to your remote.

---

### Post by nickrout on 2010-12-01
> **dibuntux said:**
> Format is not the problem, X264 or Xvid would do. The problem is I would like to use it with a remote control from the sofa, since my machine has no mouse. Possibly in the background...so I can watch tv mean while ripping...
Then if Mytharchive still works, eventually writing to DVD the ripped file.

Any idea?

I am not sure what the point is of ripping a DVD to mpeg4 and then transcoding it back to mpeg2 so it can be written back to DVD.

However...

Obviously if you are happy ripping to mpeg4 you aren't interested in the dvd menus and stuff like that. there are many many scripts out there to rip dvd's. You can probably adapt any of them to run with no user input, and then assign that to a menu item in mythtv.

---

### Post by dibuntux on 2010-12-02
No, maybe too many subjects in one question... I will puntualize:

1) Of course I do not want to code DVD from mpeg2 to mpeg4 and back to mpeg2... I just want a simple menu entry (run a script in background, ok!) to get a dvd to rip to a file, maybe with the choice of transcoding to mpeg4 if it has to remain in the system, or to mpeg2 if it has to go on a dvd.

2) I want to use mytharchive to create DVDs from my LiveTV recordings, with menus and so on, like it is possible now in 0.23.

3) can you point to a script to rip dvds?

4) handbrake latest ver. have you to install an unstable PPA - I do not like that. On this machine I only run ubuntu approved sw.

Thanks all for your time to reply!

---

### Post by nickrout on 2010-12-02
> **dibuntux said:**
> No, maybe too many subjects in one question... I will puntualize:

1) Of course I do not want to code DVD from mpeg2 to mpeg4 and back to mpeg2... I just want a simple menu entry (run a script in background, ok!) to get a dvd to rip to a file, maybe with the choice of transcoding to mpeg4 if it has to remain in the system, or to mpeg2 if it has to go on a dvd.

OK that clarifies it.> 

2) I want to use mytharchive to create DVDs from my LiveTV recordings, with menus and so on, like it is possible now in 0.23.


as previously answered mytharchive is still in 0.24 and according to the release notes, has had active development.
> 
3) can you point to a script to rip dvds?


I can't off the top of my head, but there will probably be a few people on the mailing list who can help you. first problem is usually identifying which title on the dvd is the main title, there are usually many titles with trailers, copyright warnings etc. It is often title 1 but your mileage may vary.

Once you have found the correct title a simple rip to mpeg2 is as easy as

```
mplayer dvd://1 -dumpstream -dumpfile dvdname.vob
```

Then use handbrake or avidemux to convert to your target of choice.> 
4) handbrake latest ver. have you to install an unstable PPA - I do not like that. On this machine I only run ubuntu approved sw.



then you may prefer avidemux, having said that using handbrake from ppa has never harmed my system.

---

### Post by dibuntux on 2010-12-03
Thanks for your suggestions. I understand mytharchive should be functional. 
I also understand people are having problems with 0.24, with sound, with channel shifting and others...
As for dvd... I understand no easy & elegant solution at hand. MythDVD would let you select the title from a list with remote control, set parameters and go to rip automatically.
I have avidemux installed, but is not a program you can use with out a mouse.

So, I would like to have 0.24, but as for now the draw backs seem more than the advantages...

---

### Post by nickrout on 2010-12-03
avidemux has a commandline version. there is a recent thread on the mailing list on converting recordings to h264. 

[http://www.gossamer-threads.com/lists/mythtv/users/462758#462758](http://www.gossamer-threads.com/lists/mythtv/users/462758#462758)

There is a perl script to run avidemux, I offer it as an example only.

---

