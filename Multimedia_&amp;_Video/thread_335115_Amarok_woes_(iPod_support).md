---
title: "Amarok woes (iPod support)"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by intrepidus on 2007-01-09
I just built amarok from source, hoping to get iPod support...no luck. It doesn't have iPod listed in the Media Devices section. I have libgpod and gtkpod installed also.

Is this something typical and easy to fix? gtkpod runs fine. Amarok just can't do it.

---

### Post by pay on 2007-01-09
Try ```
sudo aptitude libgpod-dev build-essential faac
./configure --prefix=/usr --with-mp4v2 --with-libgpod
```

---

### Post by thecapuchin on 2007-01-10
I've actually had a fair amount of luck when working with iPods and Amarok.  All that I've had to do when attempting to connect is this:

Open Amarok.
Click the Settings menu.
Click Configure Amarok.
Click on the Media Devices icon.
Click Add Device.
In the dialog that appears, click the drop down and choose "Apple iPod Media Device"
Enter a name for the device (in my case 'Stealthpod')
Enter the mount point for the device (Ubuntu's default is /media/ipod)
Click OK.

After that, the only thing that I've noticed as being a 'problem' is that if I open Amarok after attaching my iPod, Amarok will display a message when I click the Connect button stating that there is a previously existing lock in place and would I like to remove it.  Clicking on Remove does just that and the playlists and artist names are displayed.

---

