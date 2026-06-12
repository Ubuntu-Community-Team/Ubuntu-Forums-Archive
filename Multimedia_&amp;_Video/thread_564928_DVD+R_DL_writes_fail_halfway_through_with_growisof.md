---
title: "DVD+R DL writes fail halfway through with growisofs?"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by willfe on 2007-10-01
I'm having trouble burning DVD+R dual layer discs on pretty new hardware, but since each attempt is producing coasters I figured I'd ask before this costs me over ten bucks in bad discs :)

The drive in question is a Pioneer DVD+RW (DVR-212D, firmware 1.21). I have some shiny new TDK-branded DVD+R dual layer discs on a spindle.

Regardless of the options I've handed to growisofs, the same thing happens every time: it burns almost exactly half the data then barfs with an "input/output error." The disc is naturally not usable afterwards; 'tis a coaster :( 

I suspect it's bonking into the end of layer 0 and giving up instead of switching to layer 1 to continue the burn (I suspect this because the failure happens at *exactly* the same spot on each burn -- 51.44% through).

At first, I just tried a normal burn:

$ cd pile_of_files/
$ growisofs -Z /dev/sr0 -J -R -V "Blah blah blah" .

Then after doing some reading I found the "--use-the-force-luke=break:[value]" option to explicitly specify where to put the layer break, so I tried:

$ growisofs -Z /dev/sr0 -use-the-force-luke=break:2036096 -J -R -V "Blah blah blah" .

I arrived at that value by using dvd+rw-mediainfo against a blank disc, and noting the "end of layer" block count. That value made zero difference whatsoever in behavior -- it still wrote half the data and barfed.

Then I tried firing up a front-end, thinking I was just missing the "magic incantation." I tried gnomebaker, which didn't recognize that the disc was 8.5GB instead of 4.7GB (it didn't appear to actually *check*, though), and then brasero, which did. Same result, though -- halfway through the burn (at exactly the same point), I became the proud owner of another $1.50 coaster :)

Going back to growisofs (which the two front-ends were using anyway), I tried adding -overburn, to no avail. Dropping to -speed=4 (down from its default detected 8x speed) didn't help either.

growisofs has successfully (without any incident or complication) burned many regular single-layer discs on this machine and drive, and I can burn regular CDs on it as well (with cdrdao and cdrecord). The platform is Ubuntu 7.04, on AMD64. The box has 3GB of RAM if that matters at all.

growisofs reports its version is 7.0.1, with genisoimage 1.1.2.

Any suggestions how to fix this? Thanks in advance for any advice!

---

### Post by willfe on 2007-10-10
In case anyone else is having a similar issue, I've also just tried using k3b to burn a DL disc. It also properly detects the media as DL-capable, but fails because it too uses growisofs. However, it did hand me a useful log, showing all the precise commands it used and the output that resulted, including the errors. I've attached it to this thread.

Any ideas, anyone?

---

### Post by kvonb on 2007-10-10
> before this costs me over ten bucks in bad discs

Ten bucks?  Those cost $12 each over here!!!

You lucky, lucky b@#$%^&d!

And given that the Aussie $ is worth about 90US cents we get ripped of so bloody much over here, especially considering that China is a mere stone throw away.

---

### Post by willfe on 2007-10-10
> **kvonb said:**
> Ten bucks?  Those cost $12 each over here!!!

You lucky, lucky b@#$%^&d!

And given that the Aussie $ is worth about 90US cents we get ripped of so bloody much over here, especially considering that China is a mere stone throw away.

Good grief! Twelve DOLLARS a piece? Okay, I now downgrade my mental picture of my own "suffering" to mere face slaps; they're bending you over :(

Despite the price, have you done any dabbling with DL discs in Linux? Did it work? :P

---

### Post by kvonb on 2007-10-12
> **willfe said:**
> Good grief! Twelve DOLLARS a piece? Okay, I now downgrade my mental picture of my own "suffering" to mere face slaps; they're bending you over :(

Despite the price, have you done any dabbling with DL discs in Linux? Did it work? :P

No, I've never even owned one yet as the price is outrageous!  Apparently my burner is capable of using them though, so once the price comes down then I will certainly try.

Hopefully you will have worked out the problems for me though, save me a bleeding fortune ;)

---

