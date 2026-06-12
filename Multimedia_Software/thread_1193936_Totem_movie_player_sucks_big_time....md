---
title: "Totem movie player sucks big time..."
date: 2009-06-22
forum: Multimedia Software
---

### Post by finite9 on 2009-06-22
Well, sort of... in some cases... but I got your attention :)

*/Rant on/*

What the heck is it with Totem and Gstreamer!!??

I thought they were making headway but there are serious regressions in Jaunty and it seems development has stood still on the Gstreamer front (from my end-user perspective).

I could play ISO's by dragging the ISO to the Totem window in Edgy Eft, then I got the ability to play them by right-clicking in Nautilus, then I could even stream an ISO over SSH with Intrepid, but now with Jaunty I cannot play ISOs at all!

Then there is the glacial development pace of Gstreamer and the fact that several things are still broken or half-completed after 3-4 years, namely *full* Matroska support, the ability to play *menus* on DVDs [Whooaaaa! slow down there cowboy!] etc.

I have made home movies and packaged them as MPEG-2 ISO files with dvdauthor and they have refused to even play in Totem, whereas they play fine in Mplayer and VLC.

I have been using Totem exclusively for years because of it's ease of use and intuitive interface for just setting a movie going, but now I feel so exasperated im thinking of moving to Mplayer, as it has everything that Gstreamer has not had for like the past decade.

The nail in the coffin came last night when I ripped a DVD to x264/mkv and added a vobsb stream.  Totem refused to even acknowledge the vobsub.  Both VLC and Mplayer handled it without a glitch.

You know, I don't know if these issues are with Totem or Gstreamer, but I don't really care:  Gnome has decided that the way forward is Gstreamer and Totem has gone along with this, so even if the failings are purely Gstreamer, Totem devs should be taking notice and pushing things to get fixed!  Saying "hey try totem-xine" is not an answer.  It's a compatibility-friendly-hanger-on used for emergencies when Gstreamer fails.  There are several things that dont actually wotk with Totem-xine, so what happens is I get a bunch of stuff not working in Gstreamer, and some 3,000 post Forum guru, wanting to accumulate another 50 posts that day, hits quick reply and says "hey have you tried totem-xine" and then I swap over and get another bunch of stuff that stops working that worked in Gstreamer.

I mean, really, when you think about it, Mplayer has had the framework to lpay anything for years.  It might not be a general library framwork that can be accessed by all programs as is the apparent goal of Gstreamer, but everything works.  If Gstreamer cannot develop fast enough, it's going to stagnate.  From end-user perspective, I think it already has.

*/Rant off/*

---

### Post by alphacrucis2 on 2009-06-22
> **finite9 said:**
> Well, sort of... in some cases... but I got your attention :)

*/Rant on/*

What the heck is it with Totem and Gstreamer!!??

I thought they were making headway but there are serious regressions in Jaunty and it seems development has stood still on the Gstreamer front (from my end-user perspective).

I could play ISO's by dragging the ISO to the Totem window in Edgy Eft, then I got the ability to play them by right-clicking in Nautilus, then I could even stream an ISO over SSH with Intrepid, but now with Jaunty I cannot play ISOs at all!

Then there is the glacial development pace of Gstreamer and the fact that several things are still broken or half-completed after 3-4 years, namely *full* Matroska support, the ability to play *menus* on DVDs [Whooaaaa! slow down there cowboy!] etc.

I have made home movies and packaged them as MPEG-2 ISO files with dvdauthor and they have refused to even play in Totem, whereas they play fine in Mplayer and VLC.

I have been using Totem exclusively for years because of it's ease of use and intuitive interface for just setting a movie going, but now I feel so exasperated im thinking of moving to Mplayer, as it has everything that Gstreamer has not had for like the past decade.

The nail in the coffin came last night when I ripped a DVD to x264/mkv and added a vobsb stream.  Totem refused to even acknowledge the vobsub.  Both VLC and Mplayer handled it without a glitch.

You know, I don't know if these issues are with Totem or Gstreamer, but I don't really care:  Gnome has decided that the way forward is Gstreamer and Totem has gone along with this, so even if the failings are purely Gstreamer, Totem devs should be taking notice and pushing things to get fixed!  Saying "hey try totem-xine" is not an answer.  It's a compatibility-friendly-hanger-on used for emergencies when Gstreamer fails.  There are several things that dont actually wotk with Totem-xine, so what happens is I get a bunch of stuff not working in Gstreamer, and some 3,000 post Forum guru, wanting to accumulate another 50 posts that day, hits quick reply and says "hey have you tried totem-xine" and then I swap over and get another bunch of stuff that stops working that worked in Gstreamer.

I mean, really, when you think about it, Mplayer has had the framework to lpay anything for years.  It might not be a general library framwork that can be accessed by all programs as is the apparent goal of Gstreamer, but everything works.  If Gstreamer cannot develop fast enough, it's going to stagnate.  From end-user perspective, I think it already has.

*/Rant off/*

Did you log a fault on launchpad?

---

### Post by finite9 on 2009-06-23
:) It takes an early bird to catch me out that easily.

Yes, I logged a bug for home made ISOs not playing and there was already a bug for ISOs stopping in Jaunty and I am following the thread on Launchpad.  For my home-made ISO issue, it never went anywhere, I gave all info needed but they said not a priority and closed my bug.  The ISO not playing in Jaunty problem has also hit resistance because it's not everyone who experiences it, only a handful of people, but it's apparent even in Fedora.

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/280664]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/280664")
[https://bugs.launchpad.net/bugs/343067]("https://bugs.launchpad.net/bugs/343067")

I had another bug about subs and menus in Totem and got the same response as for my home made ISO bug, namely:

"Actually, DVD playback is undergoing major improvements at the moment,
and we hope it will be working much better in Jaunty and later. This is
why we can't really hope bugs will be fixed in Intrepid, or maybe via an
update at some point. Thanks for reporting bugs, anyway!"

Seems like the 'fob-off' is the standard response lately.  I would say that it starts to sound like Microsft, but maybe thats a bit too harsh.

Incidentlly, I created a bug for ISOs not streaming over SSH in 2007 and the feature actually got implemented, so that is 1 point for Totem, but I suspect that gvfs had nothing to do with my bug report and that ISO over SSH was purely incidental.

Check out the second response to this bug:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/41335]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/41335")

"Do you use totem-xine?"  With the implication that we *should* use xine.

Makes you want to cry.

Or this one:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/117240]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/117240")

"
AndrewArchibald wrote on 2007-05-28: (permalink)

Josh/Kathy,

Installing 'totem-xine' should resolve your issue. You can do this through the Synaptic Package Manager (System -> Administration menu), or by typing 'aptitude install totem-xine' in a console.

Hope this helps.

Andrew.
"

---

