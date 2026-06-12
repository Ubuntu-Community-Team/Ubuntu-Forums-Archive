---
title: "Lingering video in Firefox"
date: 2011-02-17
forum: Multimedia Software
---

### Post by ScttN485 on 2011-02-17
I'm not really sure what to call it or what to search for so I'll just describe my issue. I recently watched a flash video in firefox, and when I went to a new page, that page loaded normally except for one issue. The video I watched was still sitting in the background. Any page with a dark background (unless it's a image) has the video obstructing the page. I can't click on it, and it's hard to read text when I have a bright flash video just sitting right behind the text. I can't take a screenshot because it doesn't show up there, but in the photo editor I can see it in the dark spots of the picture when I move it around. What's my issue and how can I fix it?

---

### Post by mcavady on 2011-02-17
> **ScttN485 said:**
> I'm not really sure what to call it or what to search for so I'll just describe my issue. I recently watched a flash video in firefox, and when I went to a new page, that page loaded normally except for one issue. The video I watched was still sitting in the background. Any page with a dark background (unless it's a image) has the video obstructing the page. I can't click on it, and it's hard to read text when I have a bright flash video just sitting right behind the text. I can't take a screenshot because it doesn't show up there, but in the photo editor I can see it in the dark spots of the picture when I move it around. What's my issue and how can I fix it?

I am guessing but I think when  you went to the next page the browser chache may not have cleared. I have had similar thing happen but the updtaes seem to have fixed all of this flash wiredness.

---

### Post by protozorq on 2011-02-20
Had the same problem. The video appeared even as background in terminal emulation windows. 

downgrading to nvidia driver version 173 did it for me. 

Don't know if this is the actual origin of the problem but its a workaround.

---

### Post by qyot27 on 2011-02-20
Are you using compositing ("Desktop Effects")?  Occasionally something like this would happen to me with dialog boxes or menus, and the fix is to refresh the window manager with either *compiz --replace* or *metacity --replace*, whichever one is relevant to you.

---

### Post by mcavady on 2011-02-20
> **protozorq said:**
> Had the same problem. The video appeared even as background in terminal emulation windows. 

downgrading to nvidia driver version 173 did it for me. 

Don't know if this is the actual origin of the problem but its a workaround.

Nice one I will have a try with that and see if that solves it for me too, here's hoping!

Have you found that the full screen over lay does not work either, well most of the time it is just a scaled up still of what ever flash video was on the screen at the time.

Been most frustrating.

---

