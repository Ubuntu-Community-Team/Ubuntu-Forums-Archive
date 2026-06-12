---
title: "I've got some root problems!"
date: 2009-06-10
forum: Mythbuntu
---

### Post by Billsputters on 2009-06-10
No not hair!

When I shut down Mythbuntu closes quite happily, and then gets to the desktop and continues to shutdown. In this process I see a quick flash of two windows, one a terminal, the other the NVidia setup dialogue box. I've noticed that the terminal window has the prompt root@mythtv-befe, which implies that the root owns it, and probably the NVidia dbox as well.

How do I exit these windows. I need to log on as root somehow, but I am at a loss.

Also, and this maybe related, when booting up, I have two terminals opening and one editor, for as far as I can see, no apparent reason. It's annoying, and I'd like to get rid of them as well.

---

### Post by laffinet on 2009-06-10
I'm assuming that you have to close the two terminals and the editor at startup manually, righ ?

If so you might want to try this:
Let Mythbuntu boot normally, close everything that you don't want to open at startup.
You then need to save this session as the new startup session. To do this you need to go into the main menu. I forgot where exactly it is, I thing Settings->Session. In there is an option "save current session" or so. Do that, reboot, see if it helped.

---

