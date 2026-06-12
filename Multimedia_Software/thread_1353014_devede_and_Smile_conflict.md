---
title: "devede and Smile conflict?"
date: 2009-12-12
forum: Multimedia Software
---

### Post by dave r on 2009-12-12
I have just done a clean install of Karmic after using Jaunty. In jaunty I had both Smile and devede and made some great slide shows. I am now trying to install devede and smile in karmac but I am finding that installing smile removes devede and installing devede removes smile, can someone tell me how to get them both on the same computer and playing nice. I have searched this forum and the only thing I found was to do with manslide and devede which did'nt make much sense.

---

### Post by cotcot on 2009-12-12
I have smile and devede running. I compiled smile as explained on the smile website. Then I have compiled devede 3.14.0 as usual (./configure ; make ; sudo checkinstall).

---

### Post by dave r on 2009-12-12
> **cotcot said:**
> I have smile and devede running. I compiled smile as explained on the smile website. Then I have compiled devede 3.14.0 as usual (./configure ; make ; sudo checkinstall).

Thanks for the reply, you will need to explain compile in simple layman's terms, I have never compiled any thing,

---

### Post by cotcot on 2009-12-12
If you have never compiled a program then you should read about this first.
[[COLOR="Red"]Here[/COLOR]]("https://help.ubuntu.com/community/CompilingEasyHowTo") is howto for compiling

---

### Post by dave r on 2009-12-12
> **cotcot said:**
> If you have never compiled a program then you should read about this first.
[[COLOR="Red"]Here[/COLOR]]("https://help.ubuntu.com/community/CompilingEasyHowTo") is howto for compiling

Cheers I will have a play with that when I have more time, any idea what's changed in karmic and stopped them existing on the same computer?

---

### Post by mc4man on 2009-12-12
Where are you getting the Smile package from? (assuming you didn't build it

---

### Post by dave r on 2009-12-12
mc4man from getdeb [http://old.getdeb.net/release/4750](http://old.getdeb.net/release/4750)

---

### Post by mc4man on 2009-12-12
The problem is that smile-data depends on smilutils which while available in karmic it is misconfigured as to it's libavcodec versions

Devede depends on the extra versions of the ffmpeg libs (libavcodec-extra-52

That why devede is being removed and vica-versa 

smilutils should have been configured for karmic with depend allowing the extra instead of unstripped versions

It would be better to fix smilutils which can be done very easily without compiling, could describe later if needed (have to go out.

This will also work, shouldn't cause any issue, if so post back and we'll fix smilutils

**Install devede first**, then go into synaptic, search ffmpeg, and install all the 'unstripped' libraries

Make sure you install a stripped version for every extra version installed (up to 7 possible

Don't remove the extra versions installed, the unstripped packages are just dummy transitional ones.

The your smile-data will install without removing anything (tested here see screen 3, devede is installed and not removed

---

### Post by dave r on 2009-12-13
Thanks mc4man I will have a look at that this afternoon,sound good.

---

### Post by mc4man on 2009-12-13
Small note - there is a new karmic version of your Smile on getdeb, though they aren't providing a smilutils so the issue would be the same.

If you decide to use that version you'll still need to install the 'unstripped' transitional packages as described.

The downside to the 'new' getdeb, - it appears you need to add getdeb to your software sources to install packages.

While I quess that would be ok, if you do so, I'd disable the getdeb source after installing smile ( or anything else you wanted from there.

If you leave the source enabled and do an update thru the update manager then any package you have installed that's also in the getdeb repo will be updated and that's not always a good thing

[http://www.getdeb.net/updates/Ubuntu/9.10/?q=smile](http://www.getdeb.net/updates/Ubuntu/9.10/?q=smile)

Edit: if the unstripped cause you any issue then I'll show you how to edit the deb ( basically you download it and open the control file with a small script. Then save and a new modified .deb will be made - quite simple

screen shows the edits  (replaced unstripped with extra in 4 places

---

### Post by dave r on 2009-12-13
> **mc4man said:**
> The problem is that smile-data depends on smilutils which while available in karmic it is misconfigured as to it's libavcodec versions

Devede depends on the extra versions of the ffmpeg libs (libavcodec-extra-52

That why devede is being removed and vica-versa 

smilutils should have been configured for karmic with depend allowing the extra instead of unstripped versions

It would be better to fix smilutils which can be done very easily without compiling, could describe later if needed (have to go out.

This will also work, shouldn't cause any issue, if so post back and we'll fix smilutils

**Install devede first**, then go into synaptic, search ffmpeg, and install all the 'unstripped' libraries

Make sure you install a stripped version for every extra version installed (up to 7 possible

Don't remove the extra versions installed, the unstripped packages are just dummy transitional ones.

The your smile-data will install without removing anything (tested here see screen 3, devede is installed and not removed

Seems to have done the trick, I have both on the magic box. I have started a slideshow and all seems to be well, the only thing I have encountered is a warning when opening Smile that smile control dependencies are missing SOX-MP3 support, not available on your system.

---

### Post by mc4man on 2009-12-13
possibly ( if desired
```
sudo apt-get install libsox-fmt-mp3
```

And as mentioned you'd be able to upgrade to a karmic build from getdeb if you wish - it should install cleanly - ( just don't leave the source enabled

---

### Post by dave r on 2009-12-13
All sorted, thanks for all your help mc4man

---

