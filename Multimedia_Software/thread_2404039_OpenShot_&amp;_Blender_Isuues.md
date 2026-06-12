---
title: "OpenShot &amp; Blender Isuues"
date: 2018-10-19
forum: Multimedia Software
---

### Post by Bhakti108 on 2018-10-19
Hi, I have researched this issue without luck, the OpenShot forums seems to be inaccesabe at the moment, so hoping someone can help me here. 

I cannot get animated titles to work because OpenShot will not find the executable for Blender. I have Blender 2.79 installed in my home directory. I have changed the executable path in the user preferences of OpenShot but still get the error message. Both programs work on their own.

Anyone got any ideas please?

[ATTACH=CONFIG]281384[/ATTACH]         [ATTACH=CONFIG]281385[/ATTACH]

---

### Post by Claus7 on 2018-10-19
Hello,

I might have misunderstood sth, yet when I try:
which blender 

then the output I get is:
/usr/bin/blender

The blender version is 2.79.b under the lubuntu 18.04 repositories. Is this the executable you are seeking?

Regards!

---

### Post by Bhakti108 on 2018-10-20
Thanks Claus7, the repository version I get is 2.68. 

So I downloaded the latest build from Blender.org. Its installed under my home directory and works perfectly when the executable file is clicked. 

However using the path as revealed in both file manager and in terminal will not activate Blender from OpenShot therefore I cannot use the 3d animated titles from within OpenShot. 

very frustrating.

---

### Post by Claus7 on 2018-10-20
Hello,

> **Bhakti108 said:**
> ...I have Blender 2.79 installed in my home directory. ...

> **Bhakti108 said:**
> ...the repository version I get is 2.68. 



so your ubuntu box is not 18.04. Your manual installation created the folder shown in your picture where lies the blender executable. It should have worked, yet how about adding this folder location to your path as well, just for checking?

You could open a terminal and do something like:
PATH="$HOME/*"add here your blender path without the quotes"*/:$PATH"

then at the same terminal open openshot and invoke blender. Is it working that way?

Regards!

---

### Post by Bhakti108 on 2018-10-21
I got frustrated, I definately had v2.79 installed, so I got rid of the copy in my home dir, and reinstalled from the software manager, but nope it still wouldnt work. So I decided to do a whole new install of 18.04. Completed that a couple of hours ago, installed OpenShot and Blender from software manager, and bobs your uncle, its all working. Bit annoying, but at least with Linux we can do this reinstalling stuff so easily and quickly. I love it. 

Anyway thanks for suggestions, don't know why it wouldnt work but it is now.

---

