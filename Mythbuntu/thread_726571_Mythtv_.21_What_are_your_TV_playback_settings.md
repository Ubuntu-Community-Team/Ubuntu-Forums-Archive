---
title: "Mythtv .21 What are your TV playback settings"
date: 2008-03-16
forum: Mythbuntu
---

### Post by volkswagner on 2008-03-16
I understand there is a vast, variety of hardware out there.  I was using libmpg2 and linear blend for deinterlace prior to upgrade.  Also I had tried "xvmc" worked well with linear blend.

I have tried numerous combinations all with there own negative side effects.  I have read "the new deinterlace requires more cpu".  Which is new?  When I make changes do I need to restart the frontend, or X?  Should the changes be immediate?  Prior to upgrade the settings were more simplistic.  I am not sure, but I am assuming the 1,2,3,4, individual settings are for priority settings.  Am I correct these are to be variable against the original video size?  To make sure I am viewing with the settings I changed, what is the best method to eliminate variables?  Shall I leave choices 1-4 and make them all the same?  Shall I delete all but one and edit it?  The top field is "current", how do I know the system is using "standard", "CPU", "CPU+", "High Quality", etc?

I realize this is a lot of questions.  I am looking for an explanation of this setup screen(s).

After messing with the settings to reduce, shutter, artifacts, and frozen video, I now can't view the guide, or browse channels.

This setup will probably rock once setup correctly.  Looking for a little guidance.

---

### Post by volkswagner on 2008-03-16
I guess I should ask SD vs HD.

---

### Post by superm1 on 2008-03-16
Lots of "daunting" stuff on that page.  Rather than trying to explain it all, hopefully a nice wiki page gets written somewhere to explain it.  I don't see one right now though...

Here's an overview explanation.  Those top grouping are different "pre-fabbed" playback profiles.  Hopefully most people can get away with them choosing one that fits them well.

The reasoning for them is to be able to have a few profiles to switch back and forth among easily.  As you probably saw, they are broken down into resolutions in each profile.  If you are doing HD stuff, it's the > 1280x720 suboption.  If you are doing SD, its the > 0x0 suboption.  Hitting edit on each suboption lets you modify the deinterlacer used, and all sorts of fun stuff.

---

### Post by Calash on 2008-03-17
I had to change the "Standard" profile to use libmpg2 for best playback performance.  The way it came by default worked ok, but if there was any load on the system it would skip and studder a bit.

I think I have "bob" for the deinterlace setting.

That screen is a pain to navigate with the remote :)

---

### Post by volkswagner on 2008-03-17
I don't know why I can't get browse channels to work.  When I hit Up/down on the remote or keyboard nothing happens.

It seems I will need separate settings for HD and SD.  The previous version worked well with one setting, (libmg2 and LinearBlend) for both HD and SD???

I am still pecking away to find my best overall setting.  I just wish I knew why I lost changing channels with up/down (it was working prior to changing playback settings).

---

### Post by rhpot1991 on 2008-03-17
There is a wiki entry, not all that much info on it, but its a start:
[http://www.mythtv.org/wiki/index.php/Playback_profiles](http://www.mythtv.org/wiki/index.php/Playback_profiles)

---

### Post by volkswagner on 2008-03-17
Thanks for the link.  I have success.  I am not able to set separate profiles for SD and HD.  I may not be using the correct resolution separator.  I do have a setting that works well for both SD and HD.  I chose standard decoder, video renderer DirectX, and most any including none for deinterlace work well.  Seems strange ffMpg works vs. xVmc and libmpeg2 as I had prior.

To fix the browse mode not working, I deselected it then after viewing tv I selected again.

---

