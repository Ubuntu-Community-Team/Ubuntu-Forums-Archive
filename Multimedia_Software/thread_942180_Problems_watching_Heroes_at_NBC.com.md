---
title: "Problems watching Heroes at NBC.com"
date: 2008-10-08
forum: Multimedia Software
---

### Post by entikryst on 2008-10-08
I'm having problems watching the new episode of Heroes at NBC.com.  Say's I must have the newest flash player.  I do have the new flash player so I don't now what the problem is.  I've tried the flash nonfree under synaptic package manager also and pointed firefox to use it with no luck. Here's the link [http://www.nbc.com/Heroes/video/episodes/#vid=729541]("http://www.nbc.com/Heroes/video/episodes/#vid=729541")  Does it work for you?

---

### Post by pytheas22 on 2008-10-08
I can never watch NBC.com video using the native Linux Firefox browser--things look like they're working correctly, but nothing loads.  But if I run the Windows version of Firefox in wine, it works fine.  So try installing wine with:
```

sudo apt-get install wine
```

then download the Windows installer for Firefox from [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html) .  Run the installer just as you would in Windows; after it's done, you can launch Firefox from the Applications>Wine>Programs menu.

Please let us know if that solves the problem.

Also, as an alternative to NBC, hulu.com works great with my native Linux browser and should have all the episodes of Heroes, so you could just watch it there if you don't want to deal with the wine stuff.

---

### Post by entikryst on 2008-10-08
Yeah I did have to end up watching it on hulu it just doesn't look as good.  I will have to try it under wine.  I wonder if it will have less fps.  I noticed the video doesn't play under Mac OS X Panther but will on Tiger.  Weird.

---

### Post by jovo_26 on 2008-10-23
I run Hardy, I installed Wine and Firefox. Then I went on NBC and installed they f*&@ing plugin. It seems to work fine at first but:
1-I have the sound but not the video, which is a bit disturbing
2-when I close the Win Firefox windows, Ubuntu crahes and the computer restarts! (i thought those things only happened in Windows!).
I am a comlete newbie (i installed hardy one week ago for the very first time). Does anyone know how to fix that?
Thank you!

---

### Post by pytheas22 on 2008-10-23
> I run Hardy, I installed Wine and Firefox. Then I went on NBC and installed they f*&@ing plugin. It seems to work fine at first but:
1-I have the sound but not the video, which is a bit disturbing
2-when I close the Win Firefox windows, Ubuntu crahes and the computer restarts! (i thought those things only happened in Windows!).
I am a comlete newbie (i installed hardy one week ago for the very first time). Does anyone know how to fix that?
Thank you!

The last time I used wined Firefox on NBC, it worked fine, although I haven't done it in a few months.  I suspect that your problem has to do more with wine than the NBC site, however, if your whole system is crashing when you try to close Firefox.  It might help to reinstall wine:
```

sudo apt-get remove --purge wine
sudo apt-get install wine
```

Otherwise, I would just watch the stuff on hulu.com.  The player there works great in Linux (presumably because hulu.com actually cares about people who aren't Microsoft customers), and I don't think that the video quality is any worse than that of nbc.com.  Plus the commercials are shorter, I believe.

---

### Post by jovo_26 on 2008-10-23
Ok I'll try that.

I tryed to watch Desperate Housewives with Hulu but it launches the ABC player.

---

### Post by pytheas22 on 2008-10-23
> I tryed to watch Desperate Housewives with Hulu but it launches the ABC player.

That's strange.  When I watch The Office it just plays in my web browser, and I thought all the content on the site worked that way.  I'll see if Desperate Housewives works for me when I get home.

---

### Post by BetaMaster on 2008-10-24
I haven't tried Desperate Housewives (I use gnash so I can't use Hulu on Linux) but I remember that Hulu doesn't just have its own content, it indexes other station's websites too, so some shows, like Boston Legal (personal experience) and for all I know, Desperate Housewives, will take you to the other website's page to view it.

UPDATE
I just checked, and yes, Desperate Housewives is only indexed on Hulu. It takes you to ABC's pages to watch it.

---

