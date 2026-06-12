---
title: "Bad video quality"
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by stiankarlsen on 2006-01-11
When I play a movie file in ubuntu, the pixels on the video sort of expand as you veiw the movie in fullscreen, and it looks horrible, but if i play the same video file in windows, in fullscreen, it looks pretty good, and there are no ugly shaped pixels to spot, they sort of smooth themselves out.

how do i solve this?

i have installed the latest ATI graphics drivers for my x800GT card, perhaps that has something to do with it, or is it something else?

id really like to everything else i can before uninstalling the drivers to see if that helps, seeing as it took quite some time to get them working.

---

### Post by noigeaR on 2006-01-11
which videoplayer do you use? totem?
you could try using a different player like vlc, mplayer or kaffeine or you could select a different engine like xine and see if that helps.

---

### Post by stiankarlsen on 2006-01-12
unfortunately its bad in vlc, totem, mplayer, xine, notoun and so on..

other suggestions? (thanks for your response btw)

---

### Post by kaamos on 2006-01-12
You should set the video output to "xv". For example in mplayer it is in Preferences->Video

Also, are you using the fglrx driver? This sometimes requires extra fixes.. Like adding this to the devices section of your /etc/X11/xorg.conf
```

     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"

```

---

### Post by newuser111 on 2006-01-12
yes use "xv" as your video output in options, that is the best and is supported by ati cards

if it gives an error about xv not being supported, please run "sudo fglrxconfig" in a terminal, this will generate an xorg.conf with the correct xv options turned on

---

