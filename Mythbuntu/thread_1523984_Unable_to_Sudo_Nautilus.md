---
title: "Unable to Sudo Nautilus?"
date: 2010-07-04
forum: Mythbuntu
---

### Post by zacharyrs on 2010-07-04
Not sure why but I am unable to create the root document view in Mythbuntu. Here is my CL:

```
]zachary@zachary-desktop:~$ gksudo nautilus
zachary@zachary-desktop:~$ gksudo nautilus
zachary@zachary-desktop:~$ gksudo nautilus
zachary@zachary-desktop:~$ sudo nautilus
sudo: nautilus: command not found
zachary@zachary-desktop:~$ sudo nautilus
sudo: nautilus: command not found
zachary@zachary-desktop:~$ 
```


Why is it doing this? I simply need to change perms on a folder and thought this was quickly way.

---

### Post by tgm4883 on 2010-07-04
well, if you are using Mythbuntu, you probably want to use "Thunar", as Nautilus isn't installed by default. Even then, that now the quickest way to change permissions.

You probably want to check out chmod and chown

---

