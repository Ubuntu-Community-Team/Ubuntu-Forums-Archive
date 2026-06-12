---
title: "How to turn ON the system bell/beep/pc speaker"
date: 2010-03-02
forum: Multimedia Software
---

### Post by rifter on 2010-03-02
This is for all of you who are having problems getting sound out of the PC Speaker, as far as getting the system beep or system bell.  In Karmic (9.10), a change was made to get rid of the system beeps and disable the pc speaker.  Unfortunately for people who liked (or more likely **need**) the beeps, the changes occurred in multiple places and are not that easy to find.

     I had a lot of trouble finding the answers, so I am starting this thread to point people in the right direction.  Props to those brave souls who found the information first, and provided it in these forums.  I link to the major places in _[color=blue][post=8903054]this post[/post][/color]_, giving the three places you want to look to get answers to help with this.  You might have good enough luck with one of them; I pretty much ended up following them all in bits and pieces.

The pc speaker and beeps were disabled in response to _[color=blue][this bug](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/77010)[/color]_.  I believe there were other bugs dealt with here because not everything that was done seems to be covered, if that makes sense.

_[color=blue][This bug](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154)[/color]_ was created in response, in hope of getting the beeps turned back on.  _[color=blue][This post by one of the developers](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154/comments/50)[/color]_ has some pretty comprehensive instructions for getting the beep back on.  I want to note right now, that I did not have to apply his patch to get the beeps back on where I wanted them.  It may already have been included in an update, or was obviated by something else I did.

This is because I ran into the following two threads first.  For starters, I did everything _[color=blue][thread=1331186]this guy[/thread][/color]_ did.  I also followed all of  _[color=blue][thread=1377990]this guy's[/thread][/color]_ instructions, except for the part where he replaced the beep with a different sound.  I want to do that,too, later, but not until I am sure I have all the beeps working again.

I realize this is pretty fragmented, and you may or may not want or need to go as far as I did with this.  When I get a chance to do a new clean install of Karmic (maybe in a vm or something) I intend to go back over these instructions and try to create a synthesis of them that should work for certain.  If I can, I'll figure out a way to script it.

If anything this information should now be easier for people to find.  Thanks again everyone who provided information.

One other thing I should point out.  I didn't get the bug where I had to reload the pcspkr module on every boot, so that must be fixed. (I did have to remove it from the blacklist so it would be loaded on boot, but I didn't have to kill and reload it or add it to rc.local like some people did in those descriptions).

I also did not get the bug of an endless loop of beep sound or multiple beep sounds, but that only happened to people who followed the directions to change the system beep to another sound.  Your Mileage May Vary.

---

### Post by ameanberg on 2011-07-17
Thanks for calling it solved but not explaining how. You know most of the visitors and helpers are people with problems too.

---

### Post by cleary on 2012-01-10
I found this launchpad bug for 11.04 which got me going. 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769314](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769314)

There are 3 steps to follow:
* unblacklist pcspkr kernel module (see (1) in report)
* set bell volume (2)
* load sample bell.ogg (4)

That was enough to re-enable it for me

---

