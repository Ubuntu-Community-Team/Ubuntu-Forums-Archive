---
title: "Mplayer and &quot;Places&quot;"
date: 2009-09-06
forum: Multimedia Software
---

### Post by terwilligerjones on 2009-09-06
I just upgraded via clean install to 9.04. I began to edit some audio, I realized I had not installed mplayer. I did so, finished my edit and clicked Places. 

Mplayer tried to play my home directory. I purged mplayer and clicked Places. Brought up my home directory just fine. I reinstalled mplayer and tried again -- no good. Mplayer pops up, then says "Seek failed". Remove mplayer, and we're back to normal. 

I removed .mplayer and tried again. Same result. Anyone have any idea how to trouble shoot this? 

terwilliger

---

### Post by mc4man on 2009-09-06
Right click on any folder -> properties -> open with and choose 'open folder' (or similarly named

If for some reason that doesn't work then run and post this

```
cat ~/.local/share/applications/mimeapps.list
```

---

