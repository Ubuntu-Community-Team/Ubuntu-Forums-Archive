---
title: "Best way to install patch?"
date: 2009-08-24
forum: Mythbuntu
---

### Post by cabbage on 2009-08-24
Greetings,

I am running mythbuntu on Jaunty with the weekly fixes build. I've just built myself a vga to scart cable for use with my PAL 4:3 interlaced CRT and found that I still need to run a de-interlacer. Unfortunately I can no longer run Bob because myth doesn't think I have the double frame rate, so I need to apply this patch:

    [http://svn.mythtv.org/trac/ticket/2903](http://svn.mythtv.org/trac/ticket/2903)

My question is this. What is the best way of applying this patch to my existing system without loosing everything?

Should I download the package sources - but that doesn't include the sources from the weekly rebuilds so I'd end up going back in terms of versions?

Should I download the SVN version?

Will I need to manually remove all my myth packages first? What else will that remove?

What are the implication for future upgrades?

What is the 'ubuntu' way of doing this? I'd really like to keep things as simple as possible and not deviate much from the standard packages.


Thanks,

Cabbage.

---

### Post by superm1 on 2009-08-24
So the best thing to do is follow up with the upstream developers to get that patch included.  We try not to include one off patches directly in the Ubuntu packages as they should be upstream and benefit everyone.

If you can't get upstream to take it, try again.

If you still can't get upstream to take it, you can try to talk to us, but we're unlikely to integrate it as a delta.  So your next fallback is apt-get source mythtv and grab the weekly's set of things and apply your patch, do the build yourself.  You lost the nice weekly updates by doing this though.  You could also go as far as to create your own weekly build service similar to what we do with the patch applied, but I'd recommend against that.

---

### Post by cabbage on 2009-08-24
Thanks for the advice.

I think the chances of getting this patch included are zero given that it was created three years ago and closed as invalid!

Do the weekly mythbuntu repos offer the source as I don't have a deb-src line in my mythbuntu-repos.list?

---

### Post by superm1 on 2009-08-24
Ah we should be including the src line.  If not, that's a bug!

In the interim,
Copy and paste the line and just change the deb at the beginning to deb-src.

I understand that this patch is in trunk just reading through that bug briefly.  Why can't it be backported to 0.21-fixes? It looked like an updated one was attached 3 months ago for this exact purpose.

---

### Post by cabbage on 2009-08-24
Interesting...

I've added in the deb-src line and updated apt. Doing a "apt-get sources mythtv" still gives me mythtv_0.21.0+fixes19961. Whereas I'm currently running 0.21.0+fixes20508. (I'd like to keep to fixes.)

I tried to find out when #2903 when into trunk and I stumbled upon:

    [http://svn.mythtv.org/trac/ticket/6391](http://svn.mythtv.org/trac/ticket/6391)

This is exactly what I need!

Apparently it was backported to vanilla 2.1 fixes branch four months ago. So what version should I be running to get this? Is it in the repositories as a binary?

My sources list includes:

deb [http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu](http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu) jaunty main
deb-src [http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu](http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu) jaunty main

Thanks for your help...

---

### Post by superm1 on 2009-08-24
> **cabbage said:**
> Interesting...

I've added in the deb-src line and updated apt. Doing a "apt-get sources mythtv" still gives me mythtv_0.21.0+fixes19961. Whereas I'm currently running 0.21.0+fixes20508. (I'd like to keep to fixes.)

I tried to find out when #2903 when into trunk and I stumbled upon:

    [http://svn.mythtv.org/trac/ticket/6391](http://svn.mythtv.org/trac/ticket/6391)

This is exactly what I need!

Apparently it was backported to vanilla 2.1 fixes branch four months ago. So what version should I be running to get this? Is it in the repositories as a binary?

My sources list includes:

deb [http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu](http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu) jaunty main
deb-src [http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu](http://uk.weeklybuilds.mythbuntu.org/mythbuntu/fixes-0.21/ubuntu) jaunty main

Thanks for your help...
So his patch was backported to be applicable to 0.21 fixes but never made it in.  Make a new bug on svn.mythtv.org requesting it to go in and explaining the etymology of the patch.

Make sure you do an apt-get get update after adding the deb-src line.  If it's not working, it's possible the UK mirror isn't mirroring source packages (which I'd say is a bug).

You can get the src in that case by doing this:

```
sudo dpkg-reconfigure mythbuntu-repos
```

and pick the PPA.  There is definitely available source on the PPA.

---

### Post by cabbage on 2009-08-25
Thanks. I've changed to the PPA repo and I've now got mythtv-0.21.0+fixes21383 with source. So I guess the UK mirror is broken.

Now I'm confused again. The patch for #6391 updates files that are not in the fixes source. Does this mean the only way to get this functionality is to move to trunk?

...

You have to admire anyone who uses the term etymology in their posts!

---

### Post by jyavenard on 2009-08-25
> **superm1 said:**
> Ah we should be including the src line.  If not, that's a bug!

In the interim,
Copy and paste the line and just change the deb at the beginning to deb-src.

I understand that this patch is in trunk just reading through that bug briefly.  Why can't it be backported to 0.21-fixes? It looked like an updated one was attached 3 months ago for this exact purpose.

0.21-fixes won't receive any modifications any further I don't think as 0.22 is only about 2 months away...

I did backport that fix to 0.21, it's present in my mythtv ubuntu packages.
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by jyavenard on 2009-08-25
> **cabbage said:**
> 

Now I'm confused again. The patch for #6391 updates files that are not in the fixes source. Does this mean the only way to get this functionality is to move to trunk?



You probably didn't use the right patch for 0.21

Note that there are dependencies for that patch...

Note also that there are many downsides to using the new deinterlacer.

The resolution set on your TV, must exactly match the resolution of the video you're playing. Not scaling can occur as this would change the original interlaced signal, and the TV wouldn't see it as such.

Also you need to output a deinterlaced signal with your video card, which isn't always an easy task.

---

### Post by cabbage on 2009-08-26
I was being silly. I looked at the patch and saw it reference a file that didn't exist and assumed it wouldn't work - without even trying to apply it!

Now its on and compiled and working :-).

Good news about 0.22 - I look forward to it...

---

