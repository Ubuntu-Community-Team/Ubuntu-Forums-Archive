---
title: "Studdering Flash Performance"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by jorwex on 2008-01-28
Hey all,

I've got an Athlon XP 2500+ with 1GB of ram and an AGP PNY GeForce 6600. I'm running Gutsy that I installed from those CD's you can order (from canonical i think?). Is it out of the ordinary for my flash peformance to be not totally up to par? 

Every 5 minutes or so, the sound and video will repeat in a split-second loop for about 2 seconds and then resume. It's tolerable, and won't make me switch back to windows, but I'd love to know if there's a way to fix it.

I used Envy to install the video drivers, and i have Compiz installed, but I have turned everything off and have desktop effects set to 'None.'

Thanks!

---

### Post by wolfen69 on 2008-01-28
completely remove flash from synaptic and try this one. [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by Castaa on 2008-01-28
> **wolfen69 said:**
> completely remove flash from synaptic and try this one. [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

Cool.  What is different about this flash plug-in?


I have a similar issue when watching some YouTube videos (which are of course flash based).  I get a CPU spike for about a second about every 50 seconds when playing a YouTube video.  And no CPU spikes otherwise when doing other non-flash based things.

Thanks!

---

### Post by jorwex on 2008-01-28
I'm a bit confused as to how to uninstall Flash. I tried searching for "flash" in Synaptic, and none of the results have checkmarks next to them, so I can't find it in Synaptic. I Installed it from the tar.gz from adobe's site if that helps. 

If you extract that, theres an executable text file "flashplayer-installer" and a "libflashplayer.so" file.

If i just remove the libflashplayer.so file from my ~/.mozilla/plugins directory, is that enough?

Thanks!

PS In my about:plugins page in firefox, the flash plugin that's installed says r115 like the file posted earlier. are they different? is this optimized for ubuntu or something?

---

### Post by Castaa on 2008-01-29
> **wolfen69 said:**
> completely remove flash from synaptic and try this one. [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

After installing this package (and uninstalling the old), performances is MUCH better.  No CPU spikes and the CPU load is much lower when viewing YouTube videos.

THANK YOU :KS

---

### Post by jorwex on 2008-01-29
Does anyone know how to remove the flash installation that I got from [HERE?]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")

Specifically I mean from option 1 on that site. Nothing comes up when I search for "flash" in Synaptic. Thanks,

Jordan

---

### Post by jorwex on 2008-01-29
Should I just install this one over the old one?

---

### Post by Castaa on 2008-01-31
> **jorwex said:**
> Should I just install this one over the old one?

He said uninstall the old version.  Then install this one.

---

### Post by jorwex on 2008-01-31
Ya but I don't know how! it's not in synaptic! I'm getting a little antsy about this waiting a few days for someone to reply, and then i still dont know how to uninstall it. 

sorry for being a prick, but i just want this done so i can watch tv shows online again. 

so, to make it clear, 

**Does anyone know how to remove Adobe's Flash Player if it's NOT in Synaptic?**

Thanks,

Jordan

---

### Post by Castaa on 2008-01-31
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15380&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15380&sliceId=1)

See removal instructions.

---

### Post by Castaa on 2008-01-31
Actually I just determined that it probably wasn't the flash plug-in at all that was causing the CPU spikes to occur. It was gnome-system-monitor!  I close that and the spikes went away and the YouTube flash video played without a hitch.  Very strange. 
**[SIZE=2]Excessive CPU usage by Gnome System Monitor[/SIZE]**

[https://bugs.launchpad.net/gnome-system-monitor/+bug/93847](https://bugs.launchpad.net/gnome-system-monitor/+bug/93847)

---

### Post by jorwex on 2008-02-01
wow! i looked for a bit trying to find something like that. thanks man!

---

