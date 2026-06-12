---
title: "Video Graphic Problem"
date: 2011-02-15
forum: Multimedia Software
---

### Post by Shadenius on 2011-02-15
I have the oddest problem which I met just today, I believe.
I searched some topics but couldn't spot this exact same problem so I decided make a topic. I probably cannot phrase the problem well enough but as they say a image tells more than a thousand words.

The problem:
[http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus.png](http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus.png)

It happens with any type of video be it avi, mp4, mkv or any other I try to play with exception of flash with my browser. Otherwise everything is perfectly normal.

Do take a note that when I take a screen shot with the program (Totem, VLC or any other video player I play the video) the picture is perfectly normal like so:
[http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus-HowToTrainYourDragonavi-2.png](http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus-HowToTrainYourDragonavi-2.png)

I have on my PC:
Ubuntu 10.04
ATI Radeon 9800 XT
AMD Sempron +3000
1 GB DDR2

---

### Post by Yellow Pasque on 2011-02-15
I suggest trying the latest video drivers from xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
If it doesn't go well, you can always restore your old config with the ppa-purge tool found in that repo.

---

### Post by Shadenius on 2011-02-16
Tried it but no luck. The problem still preserves but thanks for trying to help.

---

### Post by hsoulen on 2011-02-16
> **Shadenius said:**
> I have the oddest problem which I met just today, I believe.
I searched some topics but couldn't spot this exact same problem so I decided make a topic. I probably cannot phrase the problem well enough but as they say a image tells more than a thousand words.

The problem:
[http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus.png](http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus.png)

It happens with any type of video be it avi, mp4, mkv or any other I try to play with exception of flash with my browser. Otherwise everything is perfectly normal.

Do take a note that when I take a screen shot with the program (Totem, VLC or any other video player I play the video) the picture is perfectly normal like so:
[http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus-HowToTrainYourDragonavi-2.png](http://i202.photobucket.com/albums/aa79/Eurogon/Random_Stuff/Kuvakaappaus-HowToTrainYourDragonavi-2.png)

I have on my PC:
Ubuntu 10.04
ATI Radeon 9800 XT
AMD Sempron +3000
1 GB DDR2

This does look like an overlay problem but just does not make a lot of sense as you are seeing it with several different players, I guess they are all using the same renderer.

Have you tried with mplayer? I am asking as mplayer will allow you to try several different renderers to see if you can identify the problem. I suggest trying it with the smplayer front end.

Once you have it installed and have loaded a video file you can go to "Options-> Preferences" then under "General" you will see the "Video" tab where you can try several Video output "drivers".

I suggest you try "x11" as the simplest form of output driver (very slow rendering) just to see if it clears up the problem.

If not than per the other suggestion in this thread, video drivers are probably the issue.

Cheers,

Hank

---

### Post by Shadenius on 2011-02-16
Thanks hsoulen. Your method worked wonders with my videos. Now I can again enjoy my films. It seems like output driver xv (default for radeon cards) was the problem.

Three hip hip hurrays for you.

---

### Post by meluxx on 2011-02-16
photobucket is too slow for me, but i guess i have same problem (green, blue, red stripes/textures flickering above movie), i believe yesterdays update did something to my system.

EDIT: Iam using ATI too and everything is ok when i disable "accelerated video output (overlay)"

---

### Post by hsoulen on 2011-02-16
> **Shadenius said:**
> Thanks hsoulen. Your method worked wonders with my videos. Now I can again enjoy my films. It seems like output driver xv (default for radeon cards) was the problem.

Three hip hip hurrays for you.

Glad I could help.

I almost never use Totem anymore as it just does not give me enough options, mplayer is my player of choice.

Cheers,

Hank

---

