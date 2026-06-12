---
title: "Get desktop or terminal window to come up?"
date: 2010-07-30
forum: Mythbuntu
---

### Post by delta_charlie on 2010-07-30
Hi all, I just tired to install Mythbuntu 10.04 and I can not figure out how to get back to a desktop or get a terminal window up. When I boot the computer I get a box requesting user and login info and when I supply it the computer goes straight into the Media Library, Manage Recordings, Info Center, Ect 

Not sure the ESC key is working and the mouse does not work but I can select the different menus.

How do I get back to the desktop or get a terminal window?

Short of pulling the power plug how do I shut down?

Thanks, DC

---

### Post by newlinux on 2010-07-30
a couple options if you can't esc out of myth.

Try 

Pressing ALT-F2 and then typing in "xterm"

That should give you a terminal.

```

sudo poweroff

```
will shutdown.

---

### Post by delta_charlie on 2010-07-30
> **newlinux said:**
> a couple options if you can't esc out of myth.

Try 

Pressing ALT-F2 and then typing in "xterm"

That should give you a terminal.

```

sudo poweroff

```
will shutdown.

Thanks for the info, the ALT-F2 gets me back to the desktop and I was able to shutdown from there. Looks like the mouse is working ok. Just have to figure out what is wrong with the ESC. I think I will try another key board.

One of the first things I want to do is try and get my SkyStar II DVB-S card to work. Going to read up on that now.

I'm sure I will be back with questions on the SkyStar card.

Later, DC

---

### Post by nickrout on 2010-08-01
At the top mythtv menu the esc button usually gives you a choice to "cancel" "exit frontend" or "exit frontend and shutdown"

However there is an option in frontend setup to set this to another key combo, maybe you have set that.

Also in the X gui, ctrl-escape should show the xfce menu, you can get a terminal from there :)

the skystar 2 works like a dream for me. I have 2 of them.

---

### Post by delta_charlie on 2010-08-01
> **nickrout said:**
> At the top mythtv menu the esc button usually gives you a choice to "cancel" "exit frontend" or "exit frontend and shutdown"

However there is an option in frontend setup to set this to another key combo, maybe you have set that.

Also in the X gui, ctrl-escape should show the xfce menu, you can get a terminal from there :)

the skystar 2 works like a dream for me. I have 2 of them.

Hi, thanks for the info, glad to read the SkyStar2 works well. The problem with the ESC key seems to be confined to the keyboard as I changed the keyboard and now the ESC works.

Later, DC

---

