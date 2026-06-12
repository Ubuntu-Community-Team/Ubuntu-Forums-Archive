---
title: "Amarok and transcode for putting non-mp3s on your iPod/iPhone"
date: 2010-06-03
forum: Multimedia Software
---

### Post by daveola on 2010-06-03
I had been using Amarok and the 'Transcode before transferring to device' option was greyed out for my media devices.


This had been bothering me and I found some old postings on the Ubuntu forums about this but no solution.  I just figured out the solution, so I figure I'd post it here so that others can find it.

First you need to have Amakode installed.

Amarok is able to *use other tools* to convert files to the needed format before transferring them to the iPod or iPhone.

This means you need to have the capability to do the conversion in the first place, so you need to apt get 'lame' (to encode mp3s) and then a decoding tool to handle whatever format your files are in.

As an example, if you have oggs that you want to convert, you'll need an ogg decoder like the one found in the 'vorbis-tools' package.

After installing those, you can get the Amakode script by going to the Tools menu in Amarok and choosing Script Manager.

Then click on Get More Scripts and install Amakode.

Now you can add the iPod or iPhone by choosing 'Configure Amarok' from the 'Settings' menu, the 'Media Devices' tab on the left is what you're looking for.

When you create a new device, it should give you and click on the settings (gears) next to it, you can choose to 'Transcode before transferring to device"

But sometimes after installing Amakode, you'll notice that this option is greyed out for new media devices!  This was the part that didn't make any sense since I had Amakode installed.

Turns out that you can have the script installed and it can still have the option grayed out.  This was what was confusing me.  The problem is that the option will be shown, but it will only be selectable if the script is running.  So go to "Tools -> Script Manager" and select "Amakode" (it's under "Transcoding") and click on "Run".  Then your greyed out problems should be solved.

Note that when transferring it will seem like Amarok hangs, this is because you won't get any status information while it's doing the conversion, give it a few minutes before assuming that it's broken.

---

