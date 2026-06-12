---
title: "Rhythmbox Configuration"
date: 2010-05-02
forum: Multimedia Software
---

### Post by mjc4043 on 2010-05-02
Hello All, 

     I was just wondering if it were possible to alter the behavior of Rhythmbox in the following way via the source code or more conveniently its config files.  I am annoyed by Rb's habit of minimizing when I hit the close button.  This seems like a potentially easy alteration, I just don't know where these files are located.  I am running Lucid and it's default version of Rb 0.12.8

Thank You, 

Michael

---

### Post by whollycow on 2010-05-11
You can change the close/minimize behavior through gconf-editor.

Open a terminal and type in
```
gconf-editor
```

Then browse to 
apps -> rhythmbox -> plugins -> status-icon

Set status-icon-mode to 2

This should cause Rhythmbox to close completely when you press the close button.

Hope that helps.

---

### Post by DAB4970 on 2011-07-08
Is this where I might be able to allow RB to edit and change track # and disc # from the properties window when selecting single and multiple tracks?

---

