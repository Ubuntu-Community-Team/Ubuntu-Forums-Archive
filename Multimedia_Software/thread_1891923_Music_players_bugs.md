---
title: "Music players bugs"
date: 2011-12-06
forum: Multimedia Software
---

### Post by yoramdavid on 2011-12-06
Hello all,

I am using Ubuntu 11.10 gnome-classic.

I am having trouble with media players. I am still looking for one which is "suitable" for me for listening music only (I use VLC for video and like it):

I had **Rhythmbox** for a long time, then gave up on it as it was giving me problems, I do not remember which.
I then switched to **Banshee** but Banshee all of the sudden stops playing. It also lacks some features I like such as fade out.
I then tried **Guayadeque** and quite like it, one can customize its look but it does not keep my settings after closing. I have to load my profile every time.
I then tried **Listen** and liked it too, it would start up playing music automatically but crashes often.
So, now I am back to Banshee but it still stops...

Any idea why and how to solve the problem?
How shall I troubleshoot it?
Is there any better music player than those which is more stable?

Thank you in advance for your help.

Yoram

---

### Post by hansdown on 2011-12-06
Hi, yoramdavid.

Try 

 ```
clementine
```

It has fade in/out.

---

### Post by yoramdavid on 2011-12-06
> **hansdown said:**
> Hi, yoramdavid.

Try 

 ```
clementine
```

It has fade in/out.

Thank you hansdown,

Yes, I know clementine, I tried it but did not liked it, I do not remember why. I think it did not have other features I like.

Regards,

Yoram

---

### Post by 311005901 on 2011-12-06
I know it's not open source, but Spotify is a great music player that organizes music in the cloud and on your harddrive. Although the Wine version of Spotify crashes a lot for me, the official Ubuntu preview [found here]("http://www.spotify.com/us/download/previews/") works seamlessly with both Gnome classic and Unity. I'd recommend taking a look.

---

### Post by yoramdavid on 2011-12-06
> **hansdown said:**
> Hi, yoramdavid.

Try 

 ```
clementine
```

It has fade in/out.

I have installed clementine and giving it another try. :)

---

### Post by yoramdavid on 2011-12-06
> **311005901 said:**
> I know it's not open source, but Spotify is a great music player that organizes music in the cloud and on your harddrive. Although the Wine version of Spotify crashes a lot for me, the official Ubuntu preview [found here]("http://www.spotify.com/us/download/previews/") works seamlessly with both Gnome classic and Unity. I'd recommend taking a look.

Thank you 311005901,

There is a free version but it will display advertisements. I prefer to stay in the open source software.

Regards,

Yoram

---

### Post by yoramdavid on 2011-12-07
Well, Clementine: I do not like the program. Cannot make it the way I like, cannot even have it to show all the tracks on a 
Listen is my preferred, but it opens with a blank page and does not play.
Banshee stops from time to time and stops or jumps from track to track abruptly in opposite to listen and Guayadeque who have a nice fade out.

Is there any way to make Guayadeque to open my profile on starting?

Regards

---

### Post by camaron1 on 2011-12-08
That shoudn't happen with guayadeque. You can report your problem at [http://guayadeque.org/forums/index.php](http://guayadeque.org/forums/index.php) and you are sure to get help.

---

### Post by yoramdavid on 2011-12-08
> **camaron1 said:**
> That shoudn't happen with guayadeque. You can report your problem at [http://guayadeque.org/forums/index.php](http://guayadeque.org/forums/index.php) and you are sure to get help.

Thank you camaron1,

You are right.
After digging on the Internet about Guayadeque, I found that there are two versions of it: one from the ppa (the one I had installed) and a svn version (that one is more often updated).
Why two versions??
I read about it and ended up removing the one I had installed and installed the svn version and now indeed it works fine.
Still one thing I want to be able to do: have it start playing automatically when opening the program.

Regards,

Yoram

---

### Post by camaron1 on 2011-12-08
The closest thing is in Preferences to tick Play Random Track When Playlist is Empty. You still have to click Play but it will start playing from whatever Allow filter you have set up.

---

### Post by yoramdavid on 2011-12-08
> **camaron1 said:**
> The closest thing is in Preferences to tick Play Random Track When Playlist is Empty. You still have to click Play but it will start playing from whatever Allow filter you have set up.

Thank you once more,
Yes, I have that option enabled and in fact it starts playing as soon as I hit the play button on my keyboard.

I was hoping there would be a way to make it play automatically like "Listen" does.
I tried the code "--play-enqued %u" but no luck.

Regards,

Yoram

---

### Post by camaron1 on 2011-12-08
> **yoramdavid said:**
> Thank you once more,
Yes, I have that option enabled and in fact it starts playing as soon as I hit the play button on my keyboard.

I was hoping there would be a way to make it play automatically like "Listen" does.
I tried the code "--play-enqued %u" but no luck.

Regards,

Yoram

What I would suggest it to go to guayadeque.org forums and make that request. There is where the developer will know about it. I personally think that'd be very cool

---

### Post by yoramdavid on 2011-12-08
> **camaron1 said:**
> What I would suggest it to go to guayadeque.org forums and make that request. There is where the developer will know about it. I personally think that'd be very cool

I am having trouble accessing the site, but there is already such feature request:
[http://www.guayadeque.org/forums/index.php?p=/discussion/338/autoplay-on-start](http://www.guayadeque.org/forums/index.php?p=/discussion/338/autoplay-on-start)

And apparently it is also possible to have guayadeque integrated into the sound menu:
[http://www.guayadeque.org/forums/index.php?p=/discussion/333/integrate-guayadeque-in-ubuntu-soundmenu](http://www.guayadeque.org/forums/index.php?p=/discussion/333/integrate-guayadeque-in-ubuntu-soundmenu)

I edited dconf accordingly but it does not work.

I could not access either pages, so I do not know what is there.
I get a 500 Internal sever error, will try later to see what they say about it.

---

### Post by camaron1 on 2011-12-08
Yes, sometimes the site is not accessible for a short period or time.

As for the Sound menu: you don't need to tweak dconf, just check guayadeque Preferences. There is where you can activate soundmenu integration. In fact I would recommend you to go trough all the options in Preferences as there are tones of options. Do check the online manual as well (a bit outdated now but it will be getting some love soon)

If you have playlists you can access 20 of these directly from the soundmenu which is great. 

Guayadeque is a very powerful piece of software and much better than the usual suspects (yes, Banshee, Rhythmbox, Amarok, I'm talking about you...), and the more you use it the more features you will discover. Some are not very obvious at all. Here is one for you: when you double-click on the Artist/Album/Track name in the player (where the controls are) theses elements will automatically be selected in your Library view...

Enjoy it

---

### Post by yoramdavid on 2011-12-08
> **camaron1 said:**
> Yes, sometimes the site is not accessible for a short period or time.

As for the Sound menu: you don't need to tweak dconf, just check guayadeque Preferences. There is where you can activate soundmenu integration. In fact I would recommend you to go trough all the options in Preferences as there are tones of options. Do check the online manual as well (a bit outdated now but it will be getting some love soon)

If you have playlists you can access 20 of these directly from the soundmenu which is great. 

Guayadeque is a very powerful piece of software and much better than the usual suspects (yes, Banshee, Rhythmbox, Amarok, I'm talking about you...), and the more you use it the more features you will discover. Some are not very obvious at all. Here is one for you: when you double-click on the Artist/Album/Track name in the player (where the controls are) theses elements will automatically be selected in your Library view...

Enjoy it

Thank you again.
I downloaded the manual and compared the settings tabs: I do not have the option to integrate with the sound menu.
I have version 0.3.4.

Thanks for the tip. :)

---

### Post by yoramdavid on 2011-12-08
> **camaron1 said:**
> What I would suggest it to go to guayadeque.org forums and make that request. There is where the developer will know about it. I personally think that'd be very cool

"Hi, regarding the automatic playing on opening Guayadeque, I found this and I just tested it without rebooting the computer and it works:

You can get that if you check the option to resume playback when track is longer than and set length to 0

That way everytime the player get closed saves the current track position and resume it when you restart it. 

Its not exactly what you want but its better than having to restore the window and click play I guess.

Thanks for your help"

From here:
[http://www.guayadeque.org/forums/index.php?p=/discussion/338&post#Form_Body](http://www.guayadeque.org/forums/index.php?p=/discussion/338&post#Form_Body)

---

### Post by MoreOrLess on 2011-12-08
What's wrong with rhythmbox? If it's crashing, try starting it without plugins enabled.
```
rhytmbox --disable-plugins
```
The Magnatune plugin is known to cause crashing. See this for description/workaround: [https://bugzilla.gnome.org/show_bug.cgi?id=661957](https://bugzilla.gnome.org/show_bug.cgi?id=661957)

---

