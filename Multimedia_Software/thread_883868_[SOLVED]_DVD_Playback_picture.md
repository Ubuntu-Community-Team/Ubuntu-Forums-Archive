---
title: "[SOLVED] DVD Playback picture"
date: 2008-08-08
forum: Multimedia Software
---

### Post by njd4k on 2008-08-08
The problem:

Quality of video is really bad. There are weird horizontal distortions in the picture -- vertical lines have no stability. I don't really know how to explain it other than that. Screen shots below. This is not a problem with other types of video, like online flash movies. It's just DVDs.

Computer specs: in my signature

What I've tried:

-- pretty much every movie playing program in the Add/Remove menu
-- installing, uninstalling, reinstalling the proprietary ATI driver.
-- turning off desktop effects (which fixed other video problems I've been having but not this one).

Since I'm not having trouble with other video now, I'm starting to wonder whether the Linux DVD codec is just flawed. Does anybody else have this problem? Is watching a DVD on Linux just mean coming to terms with bad picture quality?

[IMG]http://i258.photobucket.com/albums/hh269/njd4k/Screenshot-2.png[/IMG]

[IMG]http://i258.photobucket.com/albums/hh269/njd4k/Screenshot-1.png[/IMG]

---

### Post by unoodles on 2008-08-08
Try this:
install xine.
After it is installed, go to setup, and change the video drivers.
Just start at the top of ths list, you will see options like xv, opengl, xshm, etc.. One of them should work.

---

### Post by njd4k on 2008-08-10
Thanks for respondingI installed gxine 0.5.901, but none of the video drivers seem to work. They all did seem to be wrong in different ways though:

dxr -- fuzzy in the way pictured above
aadxr -- fuzzy, and jerks forward and backward between frames unexpectedly
xv -- VERY jerky, video is shifted to the left (and a big chunk of what should be on the left is on the right side)
XDirectFB -- very jerky, fuzzy
DirectFB -- jerky, fuzzy, weird horizontal lines
SyncFB -- jerky, horizontal lines
opengl -- gxine locks up and crashes
caca -- fuzzy and jerky
xshm -- fuzzy, jerky, lines
aa -- fuzzy and jerky
none -- fuzzy, jerky, lines
xxmc -- horizontal lines, jerky, the image seems to get out of line vertically for moments
sdl -- only the upper 1/16th of the picture is even displayed
fb -- jerky, horizontal lines, vertical alignment
xmvc -- horizontal lines, vertical alignment

Is there anything else I can try?

---

### Post by Roasted on 2008-08-10
What video player were you using when the above picture was taken?

Are you using 32bit or 64bit?

---

### Post by njd4k on 2008-08-10
> **Roasted said:**
> What video player were you using when the above picture was taken?

Are you using 32bit or 64bit?

I'm using 64-bit Hardy.

I think I was using the VLC media player, which runs the best on my computer (totem doesn't like menus...), but the video output is basically the same on every player I've tried.

---

### Post by Roasted on 2008-08-10
Have you tried 32 bit Ubuntu, or at least another DVD in VLC/64 bit that yields the same results as the problematic DVD?

---

### Post by njd4k on 2008-08-10
> **Roasted said:**
> Have you tried 32 bit Ubuntu, or at least another DVD in VLC/64 bit that yields the same results as the problematic DVD?

I've tried about 10 DVDs with similar problems for all of them.

I haven't tried 32-bit Ubuntu since I was first testing this under Wubi. I've thought about switching to it for other reasons, but since I basically have to reinstall everything if I switch it's more work than I really want to put in. If nobody has any solution to this problem, though, then I may just give up and switch. :(

---

### Post by Roasted on 2008-08-10
I just went from 64 bit Ubuntu to 32 bit Ubuntu, but it wasn't due to DVD issues. I went back due to sound card issues. My onboard card sucked, yet worked in 64 bit. I got a PCI 7.1 card which is fricken nice, yet it has issues in 64 bit. So I went to 32 bit and suddenly everything worked.

However, I recall having fine DVD playback in 64 bit... 

I'll sit on this idea for a few and get back to you if I come up with anything...

---

### Post by njd4k on 2008-08-10
> **Roasted said:**
> I just went from 64 bit Ubuntu to 32 bit Ubuntu, but it wasn't due to DVD issues. I went back due to sound card issues. My onboard card sucked, yet worked in 64 bit. I got a PCI 7.1 card which is fricken nice, yet it has issues in 64 bit. So I went to 32 bit and suddenly everything worked.

However, I recall having fine DVD playback in 64 bit... 

I'll sit on this idea for a few and get back to you if I come up with anything...

Thanks. I haven't been able to find any other forums started by people having this issue. But it seems the 64-bit just has fewer people using it and the bugs aren't as shallow...

---

### Post by njd4k on 2008-10-26
The problems has become less bad:

-- I switched to 32-bit Hardy for an unrelated reason. The distortion improved a little.
-- I upgraded to 8.10. The picture improved more.

It's still not DVD player quality, but at least the video I've been doing testing with is watchable now. I'm marking the thread "solved" for lack of a "close enough" marker. Still, it makes me consider shelling out for the commercial, proprietary Fluendo software Canonical has started selling...

---

