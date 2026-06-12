---
title: "[SOLVED] uShare Help"
date: 2008-10-17
forum: Multimedia Software
---

### Post by metalnate on 2008-10-17
I am installing uShare to stream music (no video) to my Xbox360.  I have installed uShare properly, I know this because my 360 sees my computer, but I've made a mistake when editing the ushare.conf file for my music dir. There is no music found.  My music folder is on my desktop I put in the line like this:

USHARE_DIR=/home/nathan/desktop/music

After I edit the .conf file, is there something I have to do in terminal to make it update?  I've just been saving it, if that matters.

I can still not get my music to be visible.  I'm sure I've made a simple mistake, can someone please help me?  Thanks.

---

### Post by cariboo on 2008-10-17
If uSHare is running as a service, you probably should restart it after configuration changes

Jim

---

### Post by rsambuca on 2008-10-17
Yes.  I can't seem to get it to update on the fly either, so you probably just need to stop ushare and start it again.

---

### Post by metalnate on 2008-10-18
Thanks! I restarted the service and my 360 and it is working now.  Thanks for the help.

---

