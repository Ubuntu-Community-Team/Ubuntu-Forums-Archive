---
title: "preferred dvd player"
date: 2008-11-07
forum: Multimedia Software
---

### Post by mlwalter on 2008-11-07
Right now, whenever I put in a DVD, it will try to open in MPlayer (as I told it to always do this action).  I would like to change this to VLC.  Any suggestions?

:popcorn:

---

### Post by mc4man on 2008-11-07
Are you using 8.04 (hardy) or 8.10 (intrepid)? (or something earlier

_If using 8.04_ how did you -  "told it to always do this action'

---

### Post by mlwalter on 2008-11-07
I am using Intrepid.  When I put the DVD, the dialog box asked what application to use.  I choose MPlayer and clicked the checkbox saying "Always do this action..." (or something to that effect.

---

### Post by mlwalter on 2008-11-07
I figured it out.  I went into Nautilis and under Edit...Preferences...Media tab, I was able to change it to VLC.  I could have also changed it to "Ask me what to do".

---

### Post by mc4man on 2008-11-07
Yeah it's been made very easy to add/change choices in Intrepid.

Whenever  a choice is added (or added by you) it's available as you noted and also becomes available in the right click on the dvd icon -> open with

If you wanted a way for mplayer (gmplayer) to work right you'd go back to preferences -> media and in the drop down for DVD Video choose 'open with other application'. From there choose 'use a custom command' and insert this

```
 gmplayer dvd://
```

Then you'd see 'gmplayer as a choice and it will work right

Also note to speed up gmplayer when viewing a dvd you can go -> right click in gmplayer window -> preferences -> misc. and uncheck 'Stop Xscreensaver'

---

