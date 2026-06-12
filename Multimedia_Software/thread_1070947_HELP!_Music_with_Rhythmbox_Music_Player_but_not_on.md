---
title: "HELP! Music with Rhythmbox Music Player but not on Firefox???"
date: 2009-02-15
forum: Multimedia Software
---

### Post by ub0 on 2009-02-15
I finally was able to configure my Sound Blaster live card correctly on Ubuntu 8.10...and I can hear live streaming music off of Rhythmbox Music Player.

but if I try to hear audio from any web site, like youtube videos or other audio online, nothing gets played....

Can anyone give me some ideas or help to configure this correctly?

---

### Post by bcooperb on 2009-02-15
I am having the same problem. I had sound working everywhere, I was watching a few flash videos on differnet sites inculding YouTube. I had audio, and then....After a system update? i don't have audio in flash videos in firefox anymore.

I do still have system sound and RythmBox music.

Ubuntu 8.10
Firefox 3.0.6

---

### Post by bcooperb on 2009-02-15
I fixed it on my end! 

After reading some other issues people had posted I realized my sound settings:

System>Preferences>Sound

on the Device Tab, most of my options were set to Auto Detect. I put them all on ALSA and closed and restarted Firefox. Audio Worked.

Checked my Rythmbox to make sure that was still working, and all other sound and system sound was working as well. Hope that helps!:KS

---

### Post by ub0 on 2009-02-16
> **bcooperb said:**
> I fixed it on my end! 

After reading some other issues people had posted I realized my sound settings:

System>Preferences>Sound

on the Device Tab, most of my options were set to Auto Detect. I put them all on ALSA and closed and restarted Firefox. Audio Worked.

Checked my Rythmbox to make sure that was still working, and all other sound and system sound was working as well. Hope that helps!:KS

That did not work for me. :( I have to set everything to "SBLive! Value"...and even then I only get audio from Rhythmbox and not in Firefox...

does anyone else have any solutions? Why does Flash and Firefox not have audio in Ubuntu 8.10?

---

### Post by lenards on 2009-02-17
try using synaptic (or apt-get) to install the following: 

flashplugin-nonfree

when I updated to Intrepid, I had not flash sound in firefox.  I dig up some posts and it seemed that installing that helped - so I did it and I have sound now (I just can't get sound recorder to work).  

I hope that helps.

---

### Post by ub0 on 2009-02-18
> **lenards said:**
> try using synaptic (or apt-get) to install the following: 

flashplugin-nonfree

when I updated to Intrepid, I had not flash sound in firefox.  I dig up some posts and it seemed that installing that helped - so I did it and I have sound now (I just can't get sound recorder to work).  

I hope that helps.

Still nothing for me. I donloaded the latest package and can sill only hear audio during the Ubuntu login screen and using Rhythmbox. Any flash audio from Firefox is not coming through. 

:(

---

### Post by john.trip on 2009-02-26
Hi.

I had similar problem. When viewing stream video from youtube Firefox crashes.

Check if you have SWF player installed. Uninstall it and if needed, re-install flash plugin.

Cheers!

-JT-

---

### Post by ptqk on 2009-03-31
> **bcooperb said:**
> I fixed it on my end! 

After reading some other issues people had posted I realized my sound settings:

System>Preferences>Sound

on the Device Tab, most of my options were set to Auto Detect. I put them all on ALSA and closed and restarted Firefox. Audio Worked.

Checked my Rythmbox to make sure that was still working, and all other sound and system sound was working as well. Hope that helps!:KS

I had a similar problem. I had the non-free flash plugin installed but couldn't make firefox-audio and rhythmbox work at the same time. I had to reboot the system and choose if I wanted to see youtube or listen to a streaming OR hear my music on rhythmbox.

I chanegd from Autodetect to ALSA in the Sound Preferences and It Works!
Thanks

[Ubuntu 8.04]
[Firefox 3.0.8]

---

### Post by netwarriorwy on 2009-03-31
I found these two solutions on other threads. I had that problem in the past when I was using Hardy Heron.

[COLOR="Navy"]Solution 1:
> sudo apt-get install libflashsupport

Solution 2:
[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")[/COLOR]

Hope that helps.
:popcorn:

---

