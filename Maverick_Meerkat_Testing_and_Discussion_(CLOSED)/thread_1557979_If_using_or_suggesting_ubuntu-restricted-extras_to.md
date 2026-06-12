---
title: "If using or suggesting ubuntu-restricted-extras to.."
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-08-21
..add decoding, encoding support, ect., then note that it has been split into 2 packages.
( have always felt it was better to add plugins, ect, individually for various reasons rather than to use or suggest using u-r-e.

The more useful package for decoding is now called ubuntu-restricted-addons
The addons package will install on a 32 bit system the gstreamer0.10-pitfdll package which for the most part is un-needed and can produce poorer or no decoding of certain streams.

I'd remove the pitfdll package if it's  installed.

---

### Post by coffeecat on 2010-08-21
Can you expand on this a bit, please. According to Synaptic, ubuntu-restricted-addons is a dependency of ubuntu-restricted-extras, and the package description for ubuntu-restricted-addons says:

> You should not install this package directly, but instead install the
ubuntu-restricted-extras package.(That's on a 64-bit system.)

Are we at some sort of transitional stage towards getting a tidied-up bundle of restricted stuff? Because that package description seems to contradict part of what you are saying.

---

### Post by seeker5528 on 2010-08-21
> **mc4man said:**
> The more useful package for decoding is now called ubuntu-restricted-addons
The addons package will install on a 32 bit system the gstreamer0.10-pitfdll package which for the most part is un-needed and can produce poorer or no decoding of certain streams.

I have not really followed what is happening with binary only codec support since, for some time now, for the stuff I do personally having the w32/w64 codec pack installed doesn't really seem to make a significant difference in what I can or can't play back.

Don't really see how pitfdll is all that useful unless there are some Fluendo provided codec packs that use it? If you have the w32codecs or w64codecs package installed you should get the "benefit" they provide anyway because ffmpeg will use them.

Don't see why it would be only on the 32 bit version of Ubuntu unless it just doesn't get much attention and was never updated to handle w64codecs?

Don't know why it would produce poorer or no decoding of streams unless you have taken the additional steps to install w32 or w64 codecs? And even when one of these is installed, don't know why those codecs would be given priority over more native solutions in cases where the more native solution works good?

I do know that in times past when the native codec solutions were a lot more flaky and limited it often worked out better for me if I got the binary codecs .gz/.bz2 file [from MplayerHQ](http://www.mplayerhq.hu/design7/dload.html), extracted the codecs, and copied them to '/usr/lib/codecs/' instead of getting the .deb packaged solution. But that was then, this is now. ;)

Later, Seeker

---

### Post by mc4man on 2010-08-21
All I was suggesting was that if using or sugg. u-r-e that the addons is more useful for decoding support ( and can be installed sans the extras package) and that on a 32 bit install to remove the pitfdll package which is of little value and can have a negative effect.
(can be demonstated

As far as the comment "You should not install this package directly"  -  well that makes very little sense..

---

### Post by coffeecat on 2010-08-21
> **mc4man said:**
> As far as the comment "You should not install this package directly"  -  well that makes very little sense..

To be honest, I did think it was a bit odd. I wonder what the package maintainer had in mind when saying that. But thanks for drawing attention to this.

---

### Post by mc4man on 2010-08-21
> Don't see why it would be only on the 32 bit version of Ubuntu unless it just doesn't get much attention and was never updated to handle w64codecs?

the pitfdll package is only for 32 bit (w32codecs), w64 codecs is not supported and of even less value - take a look inside, it only has 3 files which are all real media related and handled otherwise.

> Don't know why it would produce poorer or no decoding of streams unless you have taken the additional steps to install w32 or w64 codecs?
Obviously pitfdll is of no use or effect with out w32codecs installed, most who do install pitfdll will have or will get w32codecs.

> don't know why those codecs would be given priority over more native solutions 

Don't know why either but they  do, ( haven't bothered to ck. all possibilities, so can't say for sure in all codecs covered by pitfdll

---

