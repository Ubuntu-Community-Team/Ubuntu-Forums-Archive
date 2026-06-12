---
title: "how to: get fixed Banshee, the easy dangerous way"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by gsiliceo on 2008-01-08
Gutsy and for brave people only:

**Tired of the smart playlists bug where you cant create playlist based on number of stars in banshee?**
[Download my tar here]("http://mihd.net/l6ixgb"), unpack it in your desktop and then go to a terminal and do
> sudo nautilus
Once in nautilus with root capabilities go to /home/[COLOR="Red"]YOURUSERNAME[/COLOR]/Desktop
Copy the banshee folder you unpacked 
Now go to
/usr/lib
Rename the folder called banshee, to backup.banshee
Then edit menu>paste
And now you have a newer version of banshee that works.
I haven't tested all so there may be new bugs.
If you want to go back to the original banshee enter nautilus in sudo mode and delete the new one and rename backup.banshee to banshee.

The version i included can read your current database so you will not lose anything, but just in case backup it /home/YOURUSERNAME/.config/banshee

[In case you missed it, it's here ttp://mihd.net/l6ixgb]("http://mihd.net/l6ixgb")

---

