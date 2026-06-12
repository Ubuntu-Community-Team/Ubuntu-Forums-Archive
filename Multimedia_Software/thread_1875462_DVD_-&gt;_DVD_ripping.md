---
title: "DVD -&gt; DVD ripping"
date: 2011-11-04
forum: Multimedia Software
---

### Post by Mex5150 on 2011-11-04
HI All,

When I was on widoze I did this:
DVDFab -> folder (to remove junk I didn't want)
Folder -> DVDShrink (to compress different parts at different compression rates)
Burn to disk.

When I moved to Fedora, I looked for linux alternatives, but not finding and not being able to get DVDFab working under WINE, I did the above in a windoze virtual box.

Due to Fedora forcing GNOME3, I jumped to Ubuntu, the problem is VirtualBox is very slow and unstable here. So far I have not managed to get to the end of a single DVDFab rip without it bombing out.

I have searched for options, but it seems everybody else wants either DVD -> mpg, or DVD9 -> DVD5 without dropping any junk. Neither option is good for me.

I want to watch DVDs I have bought and paid for without being forced to sit through trailers for other films and FBI warnings. It would probably be easier to just go via the pirate route and download stuff, but I used to be able to get high quality rips of just the stuff I wanted under windoze, why can't I with Linux?

Any ideas on how to achieve this?

-Mex

---

### Post by BicyclerBoy on 2011-11-04
Install libdvdcss(2) /restricted extras packages & then install HandBrake.

HB will allow you to rip/preview/select/crop/shrink & encode to H264 in a mpeg4 or mkv container.
Your 5GB DVD can become 1GB mkv easy.

VLC for windows has libdvdcss built-in.
With libdvdcss you can play the DVD in totem/mplayer/mythtv/VLC.

I see you want to leave the format as mpeg2 for DVD..so slightly different process needed.
HB can still do that.
Some new DVD players will support mpeg4-ASP on DVD media..

---

### Post by Mex5150 on 2011-11-04
> **BicyclerBoy said:**
> Install libdvdcss(2) /restricted extras packages
Already installed>  then install HandBrake.

HB will allow you to rip/preview/select/crop/shrink & encode to H264 in a mpeg4 or mkv container.
Your 5GB DVD can become 1GB mkv easy.Unless things have changed since I last looked at HandBrake, it can only convert to a flat video file, not a fully structured DVD, and as such is totally useless for my requirements.
> VLC for windows has libdvdcss built-in.
With libdvdcss you can play the DVD in totem/mplayer/mythtv/VLC.I have no problems playing DVD's, I want to know how to remove junk, but otherwise keep the same structure (and if I can use different compression ratios on different parts even better).
> I see you want to leave the format as mpeg2 for DVD..so slightly different process needed.
HB can still do that.
Some new DVD players will support mpeg4-ASP on DVD media..Either you missunderstood what I am asking, or I missunderstood your response, but as far as I can see, according to previous experiments, this is no good for me.

Thanks for your input anyway though.

-Mex

---

### Post by nerdy_kid on 2011-11-04
Take a look at dvd95 in the software center.  I think it can do what you want.

---

### Post by Ohmn on 2011-11-04
K9Copy works well too. You go from DVD->mpg. Then use Devedee to go from mpg->.iso. The thing is with devedee, you can choose a splash screen of your choosing. You can also use K9copy to DVD-> .iso of all the parts of the DVD you want and then burn the .iso with K3b.

---

### Post by dniMretsaM on 2011-11-04
Try [DVDStyler]("http://www.dvdstyler.org/").

> **Mex5150 said:**
> Unless things have changed since I last looked at HandBrake, it can only convert to a flat video file, not a fully structured DVD, and as such is totally useless for my requirements.

No, HB does do chapters.

---

### Post by Mex5150 on 2011-11-04
> **Ohmn said:**
> K9Copy works well too. You go from DVD->mpg. Then use Devedee to go from mpg->.iso. The thing is with devedee, you can choose a splash screen of your choosing. You can also use K9copy to DVD-> .iso of all the parts of the DVD you want and then burn the .iso with K3b.It seems I wasn't being clear enough, I want the DVD structure to match the original, just without the annoying adverts, I do NOT want a hacked together DVD from a ripped movie file, I want alternate audio and subtitles available too.

DVD95 seems the best option, but I can't see how to set different compression for different parts (I want extras, making of, etc to have higher compression so the actual feature will be better quality).

-Mex

---

### Post by BicyclerBoy on 2011-11-05
Granted I did not explain much about authoring a new DVD partly because it is piracy & partly because it is unnecessary.

But your first post did not clearly state you wanted a DIY burnt DVD video disk.

You must be watching DVDs on a stand-alone player..
I don't watch FBI warnings or previews or any rental **** on real DVDs.
Most stand-alone players can have firmware setup changes to allow warning skipping.

I don't see a reason to make an edited optical copy for HTPC use.. DVDs are just a PITA & laser burnt discs have shorter lifetime than HDD.

But can you not use DVDShrink in Wine ? Ripping the ISO is not the problem.

---

### Post by mc4man on 2011-11-05
For titles **without** structure protection I'd just use vobcopy to mirror the disc to file (VIDEO_TS), pretty much the same as DVDDecrypter  used to do in windows
A basic command would be 
```
vobcopy -v -m -F 16
```

Then just install wine & run dvdshrink thru it, works just like you know.

(- Actually many of the excellent dvd video tools work just fine in wine including VobBlanker, PcgEdit, Ifoedit,  DvdRebuilder, CCE, ProCoder & HCenc encoders & even, with a few small adjustments, your DVDFab HD Decrypter (at least the free version) which could be useful for ripping structure protected disks

---

### Post by Mex5150 on 2011-11-05
Hi

OK, I'll try again, Things I want:
1) The ability to copy of the orriginal DVD structure, with all menus, extras, language options etc.
2) The ability to remove bits I don't want (trailers for other films, FBI warnings, etc, to leave more room for the bits I **do** want).
3) The ability to compress diferent parts at different rates (more for the extras, etc, so the main feature will have more room, and can therefore be at a higher quality).

Things I do **NOT** want:
1) an mpg/avi/whatever file.
2) a hacked together DVD from a ripped movie file (I have the original disk and can do this on a different OS, why should I be forced to do that under Linux?)

> **BicyclerBoy said:**
> Granted I did not explain much about authoring a new DVD partly because it is piracyHow exactly is a ripped mpeg any less piracy than a DVD? I said in my OP I own the disks, I even said I want to do this myself to avoid downloading pirate copies of stuff I already own.

>  & partly because it is unnecessary.NO, it may be unnecessary for you, but that is what I want, and that is why I specifically asked for it.

> But your first post did not clearly state you wanted a DIY burnt DVD video disk.I thought it would have been obvious from the title 'DVD -> DVD' rather than 'DVD -> AVI' or something, I also mentioned burning to disk in the text.

> You must be watching DVDs on a stand-alone player..Usually, yes.

> I don't watch FBI warnings or previews or any rental **** on real DVDs.Good for you, but I don't see how that answers my original question.

> Most stand-alone players can have firmware setup changes to allow warning skipping.Many dont, and even the ones that do can't majically prevent disks ever being damaged, another reason I prefer to use ripped copes that can easily be redone rather than trash an expensive original that will need to be re-bought.

> I don't see a reason to make an edited optical copy for HTPC use.. DVDs are just a PITA & laser burnt discs have shorter lifetime than HDD.Then why are you on a thread about just that? I **DO** see a reason for this, hence the question.

> But can you not use DVDShrink in Wine ? Ripping the ISO is not the problem.Although it can be quite unstable, I am using DVDShink, however it does not give me the option to drop out trailers, and warnings while keeping the rest of the structure.


[quote=mc4man]For titles **without** structure protection I'd just use vobcopy to  mirror the disc to file (VIDEO_TS), pretty much the same as DVDDecrypter   used to do in windows[/quote]That doesn't help much as I can get the files to the HDD via DVDShrink, what I want is a way of dropping parts I don't want. I can then use shrink to selectivly compress different parts, but it would be nice to use native Linux stuff all the way through though.

-Mex

---

### Post by dniMretsaM on 2011-11-05
Maybe have a look at [this]("https://wiki.archlinux.org/index.php/Dvdbackup") (I know it's from the Arch Wiki, but all the packages are available in the Ubuntu repos and all the instructions should work), specifically "The Whole DVD."

---

### Post by mc4man on 2011-11-05
> **Mex5150 said:**
> Hi

 I can get the files to the HDD via DVDShrink, what I want is a way of dropping parts I don't want. I can then use shrink to selectivly compress different parts, but it would be nice to use native Linux stuff all the way through though.

-Mex

Well, I always take a slightly different view - use the best tool for the job, as far as DVD_VIDEO linux tools are lacking compared to win tools. (vobBlanker is well suited to removing specific parts, dvdshrink is ok to a point, though I've generally preferred to demux & re-encode with a mpeg2 encoder vs. transcoding

Anyway - your best bet to "natively" selectively rip to file keeping the orig. menu may be k9copy. Whether it also can do differing compressions on individual VTS's I don't know though it works much like dvdshrink in  it's transcoding. 
Otherwise it can be set to rip only by setting the target size larger than the source size, then use dvdshrink or whatever

---

