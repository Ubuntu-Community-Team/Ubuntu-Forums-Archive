---
title: "ATI Radeon not installable with How To"
date: 2005-11-29
forum: Multimedia &amp; Video
---

### Post by Timokl on 2005-11-29
Dear Community,
 
the last two days I try to install my graphics card with Ubuntu Breezy 64 Bit. I tried this How To [http://ubuntuforums.org/showthread.php?t=76116]("http://ubuntuforums.org/showthread.php?t=76116") -- but it did not work. As I am a Ubuntu and Linux newbie, I am a little bit lost. :???: 
 
**My hardware**
 
I installed Ubuntu on an Acer notebook with AMD Turion 64 cpu. My graphics card is an ATI Mobility Radeon X600. And I have a widescreen lcd with 1200x800 resolution.
 
**My problem**
 
At first, Ubuntu started in 1024x768 mode, which looks quite horrible on my display. :smile: After browsing the forum, I decided to install the latest ATI driver (8.19.10) and downloaded it onto my hard drive. Then I wanted to remove the old driver as suggested in the above mentioned how to. But this did not work, as the old driver obviously had not been installed during Ubuntu setup. When I enter 
 
code:
fglrxinfo
 
I get the response, that this command could not be found. So, I thought, I could start with installing the new drivers rightaway. 
 
**What I did**
 
As mentioned in the how to, I replaced the libdri.a with the older version due to compatibility problems on an AMD64 system.
 
Then I installed module-assistant and tried to build the .deb package. But after running 
 
code:
sudo sh ./ati-driver-installer-8.19.10-x86_64.run --buildpkg Ubuntu/breezy

I did not end up with a .deb file but with a file named something like *fglrx ... update* (sorry for being not concise, but I write from the office computer)
 
And I don't know, what to do with this file. :confused: 
 
Then, I found out how to change the X server's config files to add a new resolution by manipulating the xorg.conf. At first, it worked well. 1200x800 looked very beautiful. :razz: 
 
Well, then I wanted to really install this ATI driver (let's see who is more smart: Me or the computer :smile: ) and run the .run file with the command sh. Worked well at first. Then, I reconfigured xorg.conf with the automatic tool. But then everything went to the worse.
 
I still can use 1024x768, but when i switch to 1200x800, the right and the left part of the screen get "mirrored" -- I see what's happening on the right part as a direct copy on the left side and vice versa. :( 
 
What do you recommend? Trying to repair (in whatever way), or simply kick this installation and install everything anew? As I did not install anything what was not already installed by default, this would be a possible alternative.
 
Hope somebody could help me!
 
Timo

---

### Post by Timokl on 2005-11-30
Anyone with an idea what I should do best at this point?

---

