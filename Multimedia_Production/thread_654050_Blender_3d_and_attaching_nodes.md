---
title: "Blender 3d and attaching nodes"
date: 2007-12-30
forum: Multimedia Production
---

### Post by mcavady on 2007-12-30
I am wondering about attaching nodes to my system (ubuntu studio 7.10) I would like to know if anyone has managed to attach nodes and use them for rendering with blender 3d. I am new to the Linux way, not to say that I am finding it a great thing. Please help if you can, even if its a link to start me on my way. 

Thanks James

---

### Post by eye208 on 2008-01-02
What do you mean by "attaching nodes to the system"? I am a Blender user, but I don't get your question. If you talk about Blender's node-based material/compositing system, it has no relation to the underlying operating system, so there is no "Linux way" of using it. Please clarify your question.

---

### Post by mcavady on 2008-01-02
URM well I want to attach nodes to my pc to speed up the rendering process, Does blender or linux accommodate this? Just that ot does take a long time to render some of my work.

I was thinking of attaching nodes, and then using them for speeding up the render time.

I hope this is clear, 

thanks for the reply 

James Mcavady

---

### Post by eye208 on 2008-01-03
> **mcavady said:**
> URM well I want to attach nodes to my pc to speed up the rendering process, Does blender or linux accommodate this?
The program "reppu" ([http://packages.ubuntu.com/gutsy/graphics/reppu](http://packages.ubuntu.com/gutsy/graphics/reppu)) will help you set up a Blender-based render farm. Just run it with the --server option on each host, then start the rendering process from the main machine, providing the list of hosts and the .blend file to render.

Another option is [DrQueue](http://www.drqueue.org/) which was also used in the production of the movie "[Elephants Dream](http://www.elephantsdream.org/)".

---

### Post by mcavady on 2008-01-03
thanks I will be well on my way with that, more reading but should be fun. Thanks again for you time.

James Mcavady: guitar:

---

### Post by mcavady on 2008-01-03
Well been sat here for a few hours and think that i am a bit lost and having a hard time of it!! Have you used this software before? Looking for a few pointers. I have managed to get the DrQueue in to the 

usr/locals 

folder how ever i am having a little trouble getting the rest of it together!!

seen the bash command far to much at the moment. I am looking at the screen and its gone all a blur!!

The other bit that has totally confused me is;

scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 1128, in _main

Bit lost here!

there are some help pages out there but they are not that easy to follow as I am new to this as I said in one of my posts. 

Just a guess but this is something that a newbi does not usually get into! 

I hope you can help. 

James mcavady

---

### Post by mcavady on 2008-01-03
Just to let you know I have now got the node software install some how! dunno how just happened, all I need now is a couple of ps3's and i should be well away. Thanks soooo much for your help. reppu is a bit confusing but after about a hour it makes sense! 

Dunno if that put the extra menu's into blender or whether it was something else i did!! 

Now i have a node manager part to blender and seems to work fine.

Thanks again James Mcavady

---

