---
title: "XM Radio via Firefox on Ubuntu"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by Blind Buzzard on 2007-06-08
Has anyone had luck listening to XM Radio on Ubuntu?  

With Windows, Firefox uses the WMP plugin to play the content streaming from the net with no problem.  In Ubuntu, Firefox attempts to play the content with Rhythmbox, I'm assuming.  But it doesn't play automatically or by hitting the play button.

---

### Post by Chappy7777 on 2007-06-08
I just got my sound card working, and now have streaming audio, etc. I know you can get Firefox to play XMMS, which seems like it would play XM for you. I know it will play stream MP3s and oggs.
To get this to work, click  on edit/preferences (in FFox),in Smart Browsing click "New Type" box.  
Type: mime : audio/x-scpls   Description:MP3 & )GG stream with .pls extension. Extension: pls
Open with usr/bin/xmms    Give Virgin Radio UK or Nullsoft's Shoutcast site.
Good luck as I have not actually done this yet. You likely know more about Linux than I do, as I am still a NooB. However, the learning curve is no longer vertical :)
Chappy

---

### Post by moore.bryan on 2007-06-20
*from another post:*
> 
Re: Radio?             
                                                         if the stream/content uses windows media player (wmp) to play it, you'll need some tinkering. i use iceweasel (firefox), so i just installed the [mediaplayerconnectivity plugin]("https://addons.mozilla.org/en-US/firefox/addon/446"). for other streams, you may want to install streamtuner (it's in the repos, maybe medibuntu repo)... it has tons of choices and uses xmms, which--i would guess--would allow it to be used with audacious as well.
*i find it works best with xine...*

---

