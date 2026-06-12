---
title: "No Sound In Flash"
date: 2008-07-04
forum: Multimedia Software
---

### Post by TedPacyga on 2008-07-04
So I got the sound to work on my system, like I can hear the log in and log off sound, but when I try to go watch a YouTube  video I get no sound.  First of all, I have a Creative Sound Blaster X-Fi Series card.  Second, I did the Flash sound fix as is stated in this guide: [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2) however the sound still does not work for me on YouTube.  I am new to Linux, so if you guys need me to give you any other information please let me know.  Any help is appreciated, thanks.

---

### Post by ubuntu-freak on 2008-07-04
Try creating a symbolic link of libflashsupport.so to /usr/lib/firefox-addons/plugins as well.

---

### Post by jmlaniel on 2008-07-04
I ended up with a sound problem after changing my Flash player from version 9 to 10 beta (in order to solve the Firefox flash related crash problem).

From what I've seen, you need to stay as far as possible from libflashsupport. I followed the instruction found at this address and I finally got flash support without constant crashing.

[http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox")

Good luck!

---

### Post by ubuntu-freak on 2008-07-04
> **jmlaniel said:**
> I ended up with a sound problem after changing my Flash player from version 9 to 10 beta (in order to solve the Firefox flash related crash problem).

From what I've seen, you need to stay as far as possible from libflashsupport. I followed the instruction found at this address and I finally got flash support without constant crashing.

[http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox")

Good luck!

 
I think he needs it cos' he's using the OSS4 sound server instead of PulseAudio. That's what I'm guessing anyway.

---

