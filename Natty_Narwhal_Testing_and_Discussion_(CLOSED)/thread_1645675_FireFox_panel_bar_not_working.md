---
title: "FireFox panel bar not working"
date: 2010-12-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nm_geo on 2010-12-14
Has anyone had an issue with the FireFox tabs File-Edit-View-History-Bookmarks-Tools-Help not working in unity? I had trouble with it earlier and did the Classic desktop reboot and it is okay now.

---

### Post by efflandt on 2010-12-14
Things have been I little flaky for me since I did updates late last night.  When I log in to Ubuntu Desktop, Unity comes up, but the top panel is unresponsive (except Ubuntu logo), as are Firefox menus.  At that time doing **unity --reset** seemed to restore everything back to normal while that terminal was open.  But after updates when I got home early this evening, that restores the panels at the top, but Firefox menus were still unresponsive unless I did **compiz --replace** instead (and left that term open).

But it also seems like if I log in and top panels are unresponsive, if I open and close a terminal and some programs, everything starts working (like currently without resetting or replacing anything).  So it is a mystery what triggers it to work or not. But once it starts working, it works fine that session (except snowy Unity icons after suspend).

If I try logging into Classic, all the applets crash and only some of them run when I click each dialog to restart them.  Failsafe works fine.

---

### Post by nm_geo on 2010-12-15
when you run **compiz --replace **do get unresolved children errors?  Is that why you leave the terminal open or just to have it handy?

---

### Post by kyleabaker on 2010-12-15
> **nm_geo said:**
> when you run **compiz --replace **do get unresolved children errors?  Is that why you leave the terminal open or just to have it handy?

Closing the terminal after running **compiz --replace &** ends the process so you will lose window decorations. You can however, put that in a bash file on your desktop, make it executable and double click it when needed.

---

### Post by ratcheer on 2010-12-15
> **kyleabaker said:**
> Closing the terminal after running **compiz --replace &** ends the process so you will lose window decorations. You can however, put that in a bash file on your desktop, make it executable and double click it when needed.

You should be able to run the command under the nohup command and be able to close the terminal without ending the process. I.e.,

**nohup compiz --replace &**

Tim

---

### Post by chrismine on 2010-12-15
nohup compiz --replace & does not work for me.

Another thing I founf is that you loose right click funcionality with unity running in Nautilus, Firefox and Chrome.

---

### Post by ratcheer on 2010-12-15
> **chrismine said:**
> nohup compiz --replace & does not work for me.

Another thing I founf is that you loose right click funcionality with unity running in Nautilus, Firefox and Chrome.

Odd. I am using it now. Also, right-click in Firefox is working, too.

Tim

---

### Post by kyleabaker on 2010-12-15
> **chrismine said:**
> nohup compiz --replace & does not work for me.

Another thing I founf is that you loose right click funcionality with unity running in Nautilus, Firefox and Chrome.

I think the right click bug is unrelated. I saw this happen yesterday for a little while. I closed an app and it all started working again. I'm not sure which app was the culprit, but it seemed to be linked to something I was running.

---

### Post by cariboo on 2010-12-15
I've had strange right-click problems on a couple of installs, on one system the problem seems to be solved with todays compiz-updates, the other system, which may be ready for a fresh install one of these days, was a problem last night, but seemed to be OK this morning.

---

### Post by chrismine on 2010-12-15
It may have been a glitch or update fixed it, it is working now.

---

