---
title: "Howto fix Audacious playback from SMB shares on Ubuntu 12.04"
date: 2012-04-28
forum: Multimedia Software
---

### Post by KarlFrisk on 2012-04-28
Hi there,

I do not know if it was just me having the problem but after updating to 12.04 the new Audacious was unable to play music from my SMB share. All of my music is stored there so this was a real showstopper. I tried compiling the plugin (smb.so) on my own but it did not work. So, let me briefly share what helped me out:

Instead of browsing the samba share directly via gvfs in nautilus I created a link in my home dir

   ln -s /home/<user>/.gvfs/<share> /home/<user>/nas

and then browsed the music and added it to Audacious from ~/nas.
For me it works flawlessly. Instead of using its own SMB client Audacious is now forced to use the gvfs-mount which seems to be a cleaner solution anyway.

HTH,
K

---

### Post by Danimoth on 2012-05-31
I also had the exact same problem and arrived at your post after searching. 

Thank you, your solution works perfectly :).

---

