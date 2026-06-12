---
title: "Mplayer on KDE - Relogin problem"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by hulet on 2007-05-03
Hello,
I have the strangest problem with mplayer. It plays videos fine when I first login into KDE after booting up computer. However, if I log-out from KDE and log right back in and attempt to play video files with mplayer I get the "Error opening/initializing the selected video_out (-vo) device" error. For the last couple of days I have been trying to solve this problem without any success so any kind of help will be greatly appreciated.

Edit: Also, if I logout from KDE with ctrl+alt+backspace and login back again, mplayer seems to work without any problem. This becomes only a problem if I use the log out button.

---

### Post by taurus on 2007-05-03
Start MPlayer.  Go into Preferences and in the video section, change the driver from whatever it is right now to **xv**.  Save it and close down MPlayer.  Start it again and see if it works this time.

---

### Post by hulet on 2007-05-03
Thanks taurus for the reply. Yes, it works with other vo drivers than xv but the quality is not that good or I can't enlarge the video. I really like XV outputs and mplayer too. They have been very reliable for me through out  the years. I don't really know why they are acting up now.

Btw, I have no problem with playing videos in Gnome with mplayer with xv output. The problem seem to be limited to KDE and even then only when I log back in after loging out.

---

### Post by taurus on 2007-05-03
You mean you can't go fullscreen with MPlayer!  If that's the case, edit ~/.mplayer/config 

```
kate ~/.mplayer/config
```
and add this line to it.

```
zoom = yes
```
Restart MPlayer and see if you can play a movie in fullscreen.

---

### Post by hulet on 2007-05-03
Yay, thanks a lot taurus, it worked. :)

---

