---
title: "my tv displays everything hardley readible and cropped"
date: 2009-12-25
forum: Mythbuntu
---

### Post by Kheos on 2009-12-25
see attachments so you understand what I mean.
I've tried every setting on the tv and this is the best I can get it. If I just watch tv(not via Mythbuntu) it all looks good, so I assume this is something I should change or set in Mythbuntu?

---

### Post by SiHa on 2009-12-26
This is called overscan. Most, if not all TV's have it, the idea is that the picture is displayed oversize so that the ragged edges on analogue broadcasts are cropped. Broadcast TV and DVD allow for this, so nothing important is near the edges. Unfortunately TV's weren't designed with PC's in mind.

There are a couple of options depending on your hardware:

Your TV may have a 'Just Scan' option to display the picture as it's sent. Not sure if this feature is available on (m)any CRT's though.

If you are using proprietary nVidia drivers and TV-Out (S-Vid or composite) you should be able to use the overscan slider in the 'nvidia-settings', utility to reduce this.

Otherwise, the only real option (that I know of) is to Adjust the GUI size in the Frontend Setup, either manually, or by using the 'Screen Setup Wizard'. This will allow you to resize all MythTV output to within the visible portion of the screen. This will not affect the desktop though, you'll have to live with that.

As for the un-readability, that's because the TV is trying to display a picture with a different resolution that the screen. You may be able to improve things by choosing a differet desktop resolution, but small screen-fonts will always look pants.

---

### Post by Kheos on 2009-12-28
> **SiHa said:**
> This is called overscan. Most, if not all TV's have it, the idea is that the picture is displayed oversize so that the ragged edges on analogue broadcasts are cropped. Broadcast TV and DVD allow for this, so nothing important is near the edges. Unfortunately TV's weren't designed with PC's in mind.

There are a couple of options depending on your hardware:

Your TV may have a 'Just Scan' option to display the picture as it's sent. Not sure if this feature is available on (m)any CRT's though.

If you are using proprietary nVidia drivers and TV-Out (S-Vid or composite) you should be able to use the overscan slider in the 'nvidia-settings', utility to reduce this.

Otherwise, the only real option (that I know of) is to Adjust the GUI size in the Frontend Setup, either manually, or by using the 'Screen Setup Wizard'. This will allow you to resize all MythTV output to within the visible portion of the screen. This will not affect the desktop though, you'll have to live with that.

As for the un-readability, that's because the TV is trying to display a picture with a different resolution that the screen. You may be able to improve things by choosing a differet desktop resolution, but small screen-fonts will always look pants.
thanks!
I've got a 'juist' (dutch for just) option on my TV, but that doesn't quite solve it.
I've connected my TV via HDMI, but it seems I don't use the nvidia drivers? any idea how to set it up so I use them?

---

### Post by ubnewbie2 on 2009-12-28
> **Kheos said:**
> thanks!
I've got a 'juist' (dutch for just) option on my TV, but that doesn't quite solve it.
I've connected my TV via HDMI, but it seems I don't use the nvidia drivers? any idea how to set it up so I use them?

There's a section in the Mythbuntu Control Centre that deals with it. I chose the nvidia drivers at install time, however my HDMI display overscanned like yours.  I used the the mythfrontend setup for the GUI size to fix it.  My 'native' res is 1280x720, and I had to set the GUI 1218x692 with x offset of 31 and y offset of 17.  You will probably spend time fine tuning it - I did :)

I also unticked the "use gui size for playback' and set playback (elsewhere) for -2 scaling in both x and y.

Still finetuning...

---

### Post by ubnewbie2 on 2009-12-28
> **ubnewbie2 said:**
> There's a section in the Mythbuntu Control Centre that deals with it. I chose the nvidia drivers at install time, however my HDMI display overscanned like yours.  I used the the mythfrontend setup for the GUI size to fix it.  My 'native' res is 1280x720, and I had to set the GUI 1218x692 with x offset of 31 and y offset of 17.  You will probably spend time fine tuning it - I did :)

I also unticked the "use gui size for playback' and set playback (elsewhere) for -2 scaling in both x and y.

Still finetuning...

Wow, after posting those figures that I tuned in yesterday, this morning I find there is a gap at the top of the screen.  It's a bug and I think it is triggered by deselecting the "use gui size for playback" option and restarting the frontend.  It looks like the "gap" is actually the desktop top-of-screen menu overlaying the GUI.

So I reselected that option, then removed the playback scaling.  So far, it seems to be working.

---

### Post by SiHa on 2009-12-29
[QUOTE=ubnewbie2]
There's a section in the Mythbuntu Control Centre that deals with it. I chose the nvidia drivers at install time, however my HDMI display overscanned like yours. I used the the mythfrontend setup for the GUI size to fix it. My 'native' res is 1280x720, and I had to set the GUI 1218x692 with x offset of 31 and y offset of 17. You will probably spend time fine tuning it - I did 

I also unticked the "use gui size for playback' and set playback (elsewhere) for -2 scaling in both x and y.

Still finetuning... 

Wow, after posting those figures that I tuned in yesterday, this morning I find there is a gap at the top of the screen. It's a bug and I think it is triggered by deselecting the "use gui size for playback" option and restarting the frontend. It looks like the "gap" is actually the desktop top-of-screen menu overlaying the GUI.

So I reselected that option, then removed the playback scaling. So far, it seems to be working. 
      
[/QUOTE]
I have almost exactly the same settings for my GUI, but "use GUI for size playback" is still selected. The only problem is that the XFCE menu panel can show over the top of the GUI - as you described - a bug that Mythbuntu has had since at least 8.04. I solve this by setting the panel size to something big (32, IIRC) then setting it to autohide. 

That way the bar is invisible in normal use, but if you want to use it, taking the mouse to the top will bring it down far enough to show within the visible portion of the screen.

---

### Post by ubnewbie2 on 2009-12-29
> **SiHa said:**
> I have almost exactly the same settings for my GUI, but "use GUI for size playback" is still selected. The only problem is that the XFCE menu panel can show over the top of the GUI - as you described - a bug that Mythbuntu has had since at least 8.04. I solve this by setting the panel size to something big (32, IIRC) then setting it to autohide. 

That way the bar is invisible in normal use, but if you want to use it, taking the mouse to the top will bring it down far enough to show within the visible portion of the screen.

Good idea.  I haven't played with XFCE much.  I found the setting and changed it to your suggestion.

Thanks!

---

