---
title: "Elisa not loading files"
date: 2008-05-23
forum: Multimedia Software
---

### Post by newb1788 on 2008-05-23
Hi,

I am trying to get Elisa MCE working on Ubuntu Feisty 8.10. I cannot get into the settings; and also I cannot load any files into it. It didn't search for any and I am not sure how to do so through terminal. I tried Elisa.conf- but permission was denied

Any help massively appreciated

---

### Post by aeiah on 2008-05-23
i think the configuration file is in .elisa/elisa.conf

open your home folder, hit ctrl+h to show hidden files, and see where it is. you should just be able to open it and edit the text file since you dont need special permissions for things in your home folder. if i remember correctly, its just a matter of adding the paths to your film and music folders.

you can also add symlinks. elisa has default places that it looks in (you'll have to check what these are, i cant remember) and you can create symlinks at those locations to point towards the locations you want.

---

