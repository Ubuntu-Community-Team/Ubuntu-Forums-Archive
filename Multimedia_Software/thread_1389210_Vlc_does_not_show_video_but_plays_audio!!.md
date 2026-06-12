---
title: "Vlc does not show video but plays audio!!"
date: 2010-01-24
forum: Multimedia Software
---

### Post by chinmaya_n on 2010-01-24
Yes,

My vlc player does not show video of a movie but plays audio of that file crystal clear !!
See the attached screenshot!!

I uninstalled completely and reinstalled but in vain!
Plz help me!

---

### Post by chinmaya_n on 2010-01-24
Relax......... I restarted the system after instlling the restricted codecs of ubutnu
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 and then it worked like a charm!
It was my mistake.... Sorry!

---

### Post by Paddy Landau on 2010-05-23
I have this problem now.

I had Hardy 8.04, and VLC worked perfectly.

Now I've done a clean install of Lucid 10.04, and installed Ubuntu restricted extras, but still VLC doesn't show any video (nor does Totem).

However, videos on websites such as YouTube work fine.

I can give you an example:
[This video]("http://www.ted.com/talks/julian_treasure_the_4_ways_sound_affects_us.html") on the TED website works absolutely fine.
But if I use the Download link to download the video, the downloaded video plays only the sound, but the video shows only as a black screen.

Any ideas how I can progress?

---

### Post by Paddy Landau on 2010-05-23
Ah, I found the answer.

Following the [VLC instructions for a black screen]("http://wiki.videolan.org/WindowsFAQ-1.0.x#Why_does_VLC_only_give_black.2C_white_or_garbled_video_output.3F")...

In VLC: Tools > Preferences > Show settings "All" > Video > Output modules > Video output module > OpenGL video output.

Hope that helps someone else.

---

### Post by jeetendrakshetry on 2010-05-23
Hi,
chinmaya_n
I am trying Ubuntu 10.04 first time and operating with LIVE CD(to try) But i am not able to play videos and music with this. please help as the site asks me to add plugins but when i do the same it is not done.
Please Help
Regards

---

### Post by Paddy Landau on 2010-05-23
> **jeetendrakshetry said:**
> I am trying Ubuntu 10.04 first time and operating with LIVE CD(to try) But i am not able to play videos and music with this. please help as the site asks me to add plugins but when i do the same it is not done.
Please tell us the exact symptoms, because we cannot see your computer  screen.

[LIST]
[*]How do you try to play a video?
[*]What happens when you do  it?
[/LIST]

---

### Post by chinmaya_n on 2010-05-24
> **jeetendrakshetry said:**
> 
I am trying Ubuntu 10.04 first time and operating with LIVE CD(to try) But i am not able to play videos and music with this. please help as the site asks me to add plugins but when i do the same it is not done.

Hi 

Running from live CD you can't play multimedia , unless you download the codecs for them.... and doing that will just do for that session and you 've to store them on some other memory.....
Rather you install Ubuntu and download the codecs... and Njoy ! 

If you desperately want liveCD to do your job..... you can go for Linux Mint,another linux disto or
**Advanced:** You can backup a system (along with applications on that system) by using **remastersys** in to a DVD which can be distributed to others. Ask you friend to do that for you, I mean on his system. This copy provides a live CD option & also installable with all the applications! But I dont recommend this :)

You better tell what exactly you want...  in a clear way as Mr.Paddy Landau said !

---

