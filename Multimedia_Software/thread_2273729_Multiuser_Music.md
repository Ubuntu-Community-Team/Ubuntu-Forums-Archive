---
title: "Multiuser Music"
date: 2015-04-15
forum: Multimedia Software
---

### Post by Skaperen on 2015-04-15
my usage practice of Ubuntu involves switching to other user logins often.  each user login has its own desktop layout for things i do. currently i am logged in to "forums" and have the Firefox tab for "Ubuntu Forums" selected.

**what i am wanting to do is start my music to play and have it keep on playing when i switch console**.   in the "admin" user login i tried switching to a root shell and start playing music in a screen shell that inherited the root permissions. then i disconnected the screen session and it kept on playing so far.  but as soon as i switched to the "forums" user the music stopped.  **i am wanting to find a way to keep it going.**

---

### Post by TheFu on 2015-04-15
Use a client/server player. Run the "server" as a userid with permissions for audio output on the system (otherwise it won't work). Ubuntu sets up those permissions only for a console login, not for network logins, so we have to do it manually.

Can't recall the name of any programs now. Sorry.  xmms .... something.

---

