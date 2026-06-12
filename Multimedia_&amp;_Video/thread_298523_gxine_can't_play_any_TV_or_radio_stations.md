---
title: "gxine can't play any TV or radio stations"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by dominique_emond on 2006-11-12
Hi,

I have xubuntu installed.

I haven't been able to listen to any internet radio or tv stations
listed in gxine 0.5.7's Media menu.

I keep getting "xine engine failed to start" - "No input plugin found.  Maybe the file does not exist or cannot be accessed, or there is an error in the URL."

Why allow the user to select something from the menu, and then
disappoint them with error messages?  Just don't enable the
Media menu and its sub-items unless gxine is properly configured. Easy !


Does anyone have complete instructions on how to get this working?
(The instructions on the ubuntu "Restricted formats" page doesn't solve
my particular problem.)



P.S.

There should be scripts made available to users to set up their
multimedia apps properly. Until then, Ubuntu should not boast
about being a "Linux for Human Beings".  You still have to be
a linux hacker to get these multimedia issues solved.

(Don't get me started about setting up my Lexmark  X1150 printer !!!)

Just venting.... I do like Ubuntu and Xubuntu more than other linux
versions.

:)

---

### Post by hikaricore on 2006-11-12
It was your choice to install gxine as opposed to running totem (or another default media player).  

I was able to get many radio stations to play just fine.  Others gave me the same error you got, which mostly says you don't have the correct codecs installed to play the streaming media you've selected.  If you wanted to you could lookup the real sites for these stations and see what format they broadcast in.  Some of them may have changed formats since your current build of gxine and xine were packaged.  If these changes were to encrypted wma format or anything like that you have a difficult road ahead of you getting them to play.  I have no need for playing such streams so I've never looked into any hacked or ported codecs to play them.

There are several advanced scripts for such installations, automatix2 and easy ubuntu (dead now i believe).  You may just have to do a little searching on and off site to find your answers.

Good luck,

--Aaron

---

