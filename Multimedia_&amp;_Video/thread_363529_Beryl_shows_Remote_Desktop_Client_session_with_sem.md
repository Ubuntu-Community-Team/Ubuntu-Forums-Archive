---
title: "Beryl shows Remote Desktop Client session with semi-transparency"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by renee.gonzales on 2007-02-17
I have installed Beryl with AIGLX on Ubuntu 6.10. When I use rdesktop to connect to another win xp machine, the remote desktop client window shows semi-transparent and it cannot be adjusted correctly using the Beryl feature to increase/descrease opacity of the window.

This small problem seems to be fixed when I change the window manager from Beryl to metacity. This gives me 0% transparency on my remote desktop client window. But I would like my rdesktop windows to have 0% transparency when using Beryl as my window manager.

Is there a Beryl configuration that will help me with this problem?


Thanks in advance.

---

### Post by mcduck on 2007-02-17
Add the client to the 'Window Specific Settings'-plugin's 'Disable ARGB visuals'-list.

---

### Post by renee.gonzales on 2007-02-18
Thanks mcduck. That worked perfectly.

---

### Post by Slim Odds on 2007-03-17
> **mcduck said:**
> Add the client to the 'Window Specific Settings'-plugin's 'Disable ARGB visuals'-list.

I tried this, but it didn't work for me.

Can you give some more details?

Thanks

---

### Post by caldridge on 2007-04-18
> Add the client to the 'Window Specific Settings'-plugin's 'Disable ARGB visuals'-list.
This is very cryptic IMO

go to beryl-settings manager > window management > set window atrribs by varius criteria > disable ARGB visual > and add > c:rdesktop:1

Probably have to restart the window manager after that, I did and now the terminal server is working correctly.

Also, don't forget to check the box on the left of the settings mgr for the option 'set window atrribs'

:-)

---

