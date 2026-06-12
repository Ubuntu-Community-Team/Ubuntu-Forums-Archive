---
title: "totem"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Feelin_froggy8877 on 2009-05-02
How do I go about getting totem to open up with the totem-xine engine by default? If I open totem useing my icon it uses the gstreamer...I have to run from term "totem-xine" to get it to use  xine-lib version 1.1.16.3. I am hoping to fix a problem with stage6 movies on joox. right now its telling me I need a "text/html" codec. wich I never heard of b4. I read somewhere the totem-xine is the way to for for this.

---

### Post by Melcar on 2009-05-02
Either remove the totem-gstreamer package, or modify the Totem menu entry to launch totem-xine.

---

### Post by Feelin_froggy8877 on 2009-05-02
How do I modify the menu entry? Would that be In the file menu in totem its self?

---

### Post by Melcar on 2009-05-02
System > Preferences > Main Menu

Look for the Totem entry and hit the Properties button.  Change the command line to totem-xine.  Now totem-xine will launch every time you select Totem from your menu.

---

