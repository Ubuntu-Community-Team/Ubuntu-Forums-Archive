---
title: "libdvdcss2 quality flaws"
date: 2009-04-04
forum: Multimedia Software
---

### Post by frankwakeman on 2009-04-04
I've been using Ubuntu 8.10 since November, sometimes dual-booting with Vista, sometimes trying to stick with 8.10 alone.  Because I have got the hang of Audacity now for recording a guitar there is only one use left for Vista for me, which is watching DVDs.  I've found libdvdcss and libdvdcss2 disappointing on three different computers, and unless I've misremembered this I think I found it similarly disappointing with XP using VLC.

The main flaw of it is that during certain types of motion in a film the picture sort of moves in strips, and in some scenes - it's weird how it's inconsistent - the picture seems to be made up of identifiable horizontal lines.  I've not seen this with the proprietary DVD software coming with my Vista laptop and previous XP machine, though I had noticed my newer laptop isn't quite as good for DVD playback, not quite as sharp.

Does everyone find this with watching DVDs on a Linux/Ubuntu system, is it normal, or does it only happen with certain machines that might be a bit lacking driver-wise, or can adjustments be made to get rid of these flaws?  Or don't people notice it?

I choose not to have TV in my home and watch a lot of films and DVDs of TV series so this is something that may see me reinstalling Vista in the next few days.

I find these flaws occur with VLC, Totem Xine and GXine alike.

Thanks in advance.

---

### Post by wolfen69 on 2009-04-04
in my experience, on 5 different computers, dvd playback has always been great. in vlc, go to tools>preferences>video and set the output to X11 video output. this may help. other than that, i can't help, as i've never had a problem with videos.

---

### Post by frankwakeman on 2009-04-05
I'd read about selecting X11 before and wondered if I'd missed some vital step out.  I have it selected now and initially thought the glitches solved, but they're not yet.  I'd wondered anyway whether the 'default' that was selected would have been the X11 output anyway.  I tried some of the others - there's about 8 output settings on the list - but they are either worse, like openGL, or the same.

My laptop is a 1.6 ghz dual core machine, with 2 gb RAM (the video RAM is shared), though my desktop is 1.3 ghz single core with 512 mb RAM with a 256 mb video card and the same glitches.

Mightn't the problem be a subtle one others have overlooked or aren't fussy about?  I could still invite a friend round for a 'video night' without them complaining, it's not terrible, but it's not on a par with the equivalent Windows facilities at all.

I played about with VLC skins for the first time too, and all eight I downloaded are very buggy.

At a guess the LinDVD program that can be bought or that comes with Dell Ubuntu machines still only uses libdvdcss2.

A Vista dual-boot is still likely for me.  If anyone else has any ideas let me know.  Thanks.

---

### Post by mc4man on 2009-04-05
If what your seeing is what I think it is then it's more a combination of your hardware, 8.10, compiz and mainly your video drivers. Libdvdcss2 only provides the decryption keys, nothing affecting the video quality issues I believe your seeing.

Even though my hardware is somewhat dated (p4's with nvivdia 7800 series cards) I never had anything but perfect video playback in regards to dvd video till 8.10

With 8.10 there was/is a very subtle defect in the picture quality in certain scenes, almost unnoticeable. (i believe it's related to vsync

Upgrading the video drivers from the nvidia 177 to 180.xx and now 185.xx eliminated it except in some extreme action, camera motion scenes where it still exists.
An example would be during the chase scene in chapter 3 of " Quantum of Solace', happens maybe half a dozen times or so. (whether played back from the disk or hdd 

On the other hand on the same machine (tri-boot) in either xp or hardy, playback with vlc and  mplayer of the same scene and all dvd video is flawless.

Certainly on your desktop (with only 512 ram ) I'd try using Hardy instead of Intrepid (and try sticking with Xv which is superior to X11

---

### Post by frankwakeman on 2009-04-05
Thanks.  H'mm, well it's good to know that I'm not imagining things - what you describe from the Bond film sounds like the kind of thing.  Sideways motion or top to bottom is when it's most noticeable.

I'll try the Xv if it's there (I take it you mean that's a video output in VLC).

Unfortunately using 8.04 isn't an option for me I think, as it is only since 8.10 that the thing's worked well with mobile broadband.  I wonder if I could install 8.04 and then update Network Manager.  Something I can do at a relative's house with my laptop but not my desktop without inconvenience.  (If only it was uniformly easy to move .deb files around with pen drives.)

At any rate, I wonder if, as it's likely to do with the Ubuntu version, that this is related to why Compiz is proving to be a problem for some people as of 8.10 - brief scratchy scribbly effects when opening a window.

I hope they sort this out, and that 9.04 and 9.10 won't be worse.

---

### Post by frankwakeman on 2009-04-05
I see an XVideo extension video output if that's what you meant.

---

