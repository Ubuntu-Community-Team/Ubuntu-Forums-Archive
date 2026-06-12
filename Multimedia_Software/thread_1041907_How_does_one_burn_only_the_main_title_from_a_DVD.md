---
title: "How does one burn only the main title from a DVD?"
date: 2009-01-17
forum: Multimedia Software
---

### Post by grantchambers on 2009-01-17
I am trying to burn the main feature of a DVD only, so a dual layer DVD will fit on a standard one (minus the menus and special features).  I am used to using a program called DVD2One for Mac and it works great for this.  Are there any similar programs for Ubuntu?

---

### Post by binbash on 2009-01-17
you can do it with k9copy

---

### Post by arachnegl on 2009-01-17
Hi,

I use acidrip. Its a really easy GUI frontend to mencoder/mplayer. (Do be careful which audio track you encode though.)

G

---

### Post by grantchambers on 2009-01-17
Thanks, K9copy and acidrip both worked great, but... K9copy is a little confusing, and acidrip is not quite what I need.  Unless I am using it improperly, acidrip appears to only be useful when encoding a DVD to .avi or .mpeg.  Do you loose any quality when encoding video_TS to .avi and then to back to Video_TS?  If not, then I would definitely recommend acidrip, and I wouldn't mind the extra time.  But, as far as I can tell that can't be the best way to complete my project.  I think K9Copy would be my best bet, but all of my trials have had some (albiet minor) problems.  For Example: when trying to back up one of my DVDs, K9 was successful in isolating the main feature, but the end result still included the original DVD's surround sound set-up menus.

Is there a way to isolate the TS file and transcode it to .iso with the terminal (I prefer this to GUI)?  I have been using mkisofs, but it also copies the menus and extras, and I don't know how I can configure (if possible) to isolate the main feature???  Is there a way to examine the TS file and then manually extract the film; then I could use a program like DeVeDe or K3B to burn the TS file to a DVD.

I'm sorry if this is confusing, but I really don't understand how the TS files are created and/or grouped.

---

