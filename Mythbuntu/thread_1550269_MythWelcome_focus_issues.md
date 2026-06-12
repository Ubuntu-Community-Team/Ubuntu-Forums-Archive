---
title: "MythWelcome focus issues?"
date: 2010-08-10
forum: Mythbuntu
---

### Post by bcgrown on 2010-08-10
I'm running a combined frontend/backend on Mythbuntu 10.04 with the 0.23-fixes autobuilds,  and everything is up to date as of this post.

I have MythWelcome set up to turn the PC on and off as required.

The frontend uses a Windows MCE remote and every once in a while when I push the big green button, a couple of arrows, and then "OK," my machine shuts down even though the frontend is running.

Those of you who use MythWelcome may recognize that as the sequence (m down down enter) required to select "Shutdown" from the MythWelcome menu.

It seems that MythWelcome is reading the LIRC commands that are meant for the frontend.

Has anyone else had this problem,  or know of a solution?

---

### Post by jonnybignote on 2010-09-22
I believe I've had this problem, both in frontend and when running XBMC, so mythwelcome really shouldn't be responding when completely different programs are focused - wouldn't be so bad if they allowed a seperate keybinding for the welcome menu, so you could assign it to something else...

Havn't figured it out yet.

If you only use mythtv then you could probably fudge it by using a script launcher for mythfrontend that closes mythwelcome and waits for the frontend to close, then reopens it...unsure about this, but it should be fairly simple and should work

let me know if you come up with anything better

---

### Post by bcgrown on 2010-09-27
In the Window Manager settings for XFCE there's an option to prevent focus stealing.

Enabling that seems to make MythWelcome behave better, but doesn't solve the problem completely as I still get surprise-shutdowns occasionally.

---

