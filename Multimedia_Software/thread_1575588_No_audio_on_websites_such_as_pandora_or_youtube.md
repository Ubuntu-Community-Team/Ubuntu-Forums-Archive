---
title: "No audio on websites such as pandora or youtube"
date: 2010-09-16
forum: Multimedia Software
---

### Post by Snowball63 on 2010-09-16
Hi,

I just upgraded from 7.04 to 7.10 to 8.xx (sorry,wasn't on it long enough to remember, 8.10 I think) to 10.04.  I thought everything was good to go, but now I've noticed that audio doesn't work through most of the places I try to get it on the web browser.  For example, youtube, pandora, streaming radio are all silent.  However, I went to an audio test website and that worked.  Also, I can play music saved locally through rhythmbox.  I have tried uninstalling and reinstalling flash and javascript several times through different methods (command line, package manager, and adobe website).  I have also tried installing a variety of codecs and a bunch of packages with gstreamer in the name.  As you can tell, I have not been very methodical about this and I don't really know what what I am doing.  I just want my computer to work.  Oh, I also have experienced several crashes while trying to recreate the problem, though not for the last hour, so maybe I resolved that one somehow.  Anyone have any ideas or questions for me?
-Thanks

---

### Post by lidex on 2010-09-17
Updates tend to leave cruft behind. Remove your old config files and reboot.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

---

### Post by Snowball63 on 2010-09-19
Hi,

Thanks for the tip.  Actually, it doesn't look like 'asound' was left behind.  Tells me no such file or directory.
However, I saw a recommendation in several other posts to try Flashaid from Mozilla.   Although I never got the popup window that I thought I would be getting based on the code it said it would execute, my audio is working on pandora and youtube now.  It said that it was going to install a 32 bit version of flash to match my system.  I assume that means I was running a 64 bit version.  I guess I thought synaptic package manager would have helped me with the basics like that.  Anyway - I'm happy.  Thanks.  This is solved.

---

