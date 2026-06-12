---
title: "TV-out on Gforce ti500"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by stijngysemans on 2007-06-09
What I want: to display the content of my computer on my Tv.
In windows I used the tv-out and the windows control panel.

In ubuntu I do the following steps:
1. I run the following command
```

sudo nvidia-settings

```
2.I go to X server display configuration.
3. I select Tv-0 disabled.
4. I select "configure"
5. I choose TwinView and press OK.
6. I get the following error:
```

Failed to associate display device 'TV-0' with X screen 0.  TwinView cannot be enabled with this combination of display devices.

```

What should I do?

---

### Post by stijngysemans on 2007-06-11
Anybody?

---

### Post by stijngysemans on 2007-06-17
bump

---

### Post by Titus A Duxass on 2007-06-17
Do a search for TV-out!

---

### Post by jingba on 2007-06-17
I am also trying to figure out how to access the tv-out (s-video).  My system uses SIS 65x video, though.  I thought that reconfiguring the xorg.conf might work, but no-one seems to be addressing my questions.  

Doing a search for tv-out and s-video seems to be useless.  Hope someone can help you with your (and indirectly my) problem.

---

### Post by jingba on 2007-06-17
Not that I know anything about anything where ubuntu is concerned, but I have seen a couple of posts dealing with the s-video and the nVidia chipset.  I tried one of them, but it basically "fubared" my system.  I had to boot from the CD and revert my xorg.conf back to a previous version.

I don't know if this makes any difference, but is there a TV indicated in the display section in your xorg.conf?

If not, here are some links that I am looking at regarding adding these sections to the xorg.conf.  I've not tried them and don't know if they will work, but if you don't have a tv in the display section (not sure if you actually need it), it might help you out.

[http://gentoo-wiki.com/HOWTO_Setup_TV_Output_for_MythTV]("http://gentoo-wiki.com/HOWTO_Setup_TV_Output_for_MythTV")
[http://www.ee.oulu.fi/~iiska/articles/ubuntu_in_a7620.html]("http://www.ee.oulu.fi/~iiska/articles/ubuntu_in_a7620.html")

Obviously they are for different chip sets, but you never know.

---

