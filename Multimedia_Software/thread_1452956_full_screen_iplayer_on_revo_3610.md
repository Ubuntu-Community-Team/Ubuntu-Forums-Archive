---
title: "full screen iplayer on revo 3610"
date: 2010-04-12
forum: Multimedia Software
---

### Post by steadyeddy on 2010-04-12
Hi Folks - I have been researching and trying to set up the above (with both karmic and now lucid). The last task is to get iplayer running fullscreen without stuttering (windowed is fine.
I just do not seem able to achieve this thro Chrome or firefox (xbmc did it ok before the beeb messed it up!)
I have latest nvidia drivers and am displaying on sony 37KDL5500.
Everything else seems to be working fine. Mplayer will play HD vids ok.

Any ideas?

---

### Post by steadyeddy on 2010-04-13
bump
anyone?

---

### Post by steadyeddy on 2010-04-26
Anyone any thoughts?

---

### Post by rasheedl on 2010-05-10
I have had exactly the same problem as you for 2 months. The thing is it works perfectly in Windows 7 and even fullscreen 1080p using smplayer on Ubuntu works fine. It's just anything in flash like iplayer or 4OD.

Let me know if you get it working.

---

### Post by doctor_regtools on 2010-05-14
I just got my revo, and am experiencing this exact same problem too, so would really like to find a solution.

---

### Post by sinkyboy2000 on 2010-05-23
> **doctor_regtools said:**
> I just got my revo, and am experiencing this exact same problem too, so would really like to find a solution.

me too!

---

### Post by JwB Zoofware on 2010-05-24
Install get-iplayer. I've been using it for a few weeks now.

However, install the development version from maverick meerkat (2.76), as the one from lucid doesn't work for me anymore. According to the changelog, the BBC changed some file paths around breaking compatibility. It can be downloaded from:

[https://launchpad.net/ubuntu/maverick/amd64/get-iplayer/2.76-2](https://launchpad.net/ubuntu/maverick/amd64/get-iplayer/2.76-2) (amd64)

or

[https://launchpad.net/ubuntu/maverick/i386/get-iplayer/2.76-2](https://launchpad.net/ubuntu/maverick/i386/get-iplayer/2.76-2) (x86)

It's used through the command line, but its pretty easy to get to grips with, for example, to download the latest Doctor Who:

```
james@jameslaptop:~$ get-iplayer | grep "The Hungry Earth"
259:    Doctor Who: Series 5 - 8. The Hungry Earth, BBC HD, Audio Described,Drama,Highlights,Popular,SciFi & Fantasy,TV, default,audiodescribed,

james@jameslaptop:~$ get-iplayer --get 259
```

and then watch it in mplayer or whatever. You can also stream programmes straight to a media player.

Personally, I think it's alot quicker than using flash and a browser :) The flash implementation on linux is very very poor.

---

### Post by sinkyboy2000 on 2010-05-24
> **JwB Zoofware said:**
> Install get-iplayer. I've been using it for a few weeks now.

However, install the development version from maverick meerkat (2.76), as the one from lucid doesn't work for me anymore. According to the changelog, the BBC changed some file paths around breaking compatibility. It can be downloaded from:

[https://launchpad.net/ubuntu/maverick/amd64/get-iplayer/2.76-2](https://launchpad.net/ubuntu/maverick/amd64/get-iplayer/2.76-2) (amd64)

or

[https://launchpad.net/ubuntu/maverick/i386/get-iplayer/2.76-2](https://launchpad.net/ubuntu/maverick/i386/get-iplayer/2.76-2) (x86)

It's used through the command line, but its pretty easy to get to grips with, for example, to download the latest Doctor Who:

```
james@jameslaptop:~$ get-iplayer | grep "The Hungry Earth"
259:    Doctor Who: Series 5 - 8. The Hungry Earth, BBC HD, Audio Described,Drama,Highlights,Popular,SciFi & Fantasy,TV, default,audiodescribed,

james@jameslaptop:~$ get-iplayer --get 259
```and then watch it in mplayer or whatever. You can also stream programmes straight to a media player.

Personally, I think it's alot quicker than using flash and a browser :) The flash implementation on linux is very very poor.

Wow. Great shout - thanks for that.

However, youtube and other flash videos are the same, so does anyone know how to fix the problem with the browser?

---

### Post by crossfire on 2010-07-11
afaik there is no solution to run flash video smoothly until adobe adds (GPU) hardware acceleration to flash on Linux. The atom processor in the acer is just not fast enough.
Adobe are apparently committed to doing this for all platforms but have published no time scales. Flash 10.1 added hardware acceleration for Windows and there is a pre-release version for mac with acceleration, fingers crossed Linux will follow shortly after. 

I suspect, although haven't heard anything to confirm, that Adobe will add support around the time that Chrome OS gets released as I expect they won't want to miss that bandwagon. 

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Your options are:

1) Download the video and watch in mplayer etc as suggested above.
2) Run Windows
3) Wait for Adobe to pull their finger out.

---

