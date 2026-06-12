---
title: "Sound Problem/WoW Problem as Well"
date: 2009-02-03
forum: Multimedia Software
---

### Post by sdlong92 on 2009-02-03
Hi all, I just switched to Ubuntu yesterday and I am having some problems that aren't super important, just a bit frustrating and aggravating at times. There are two problems, firstly:

The sound is so much softer in Ubuntu, what I mean to say is that nothing is as loud as it was before. I would venture to guess that music and movies I play or even just streaming radio is about 70% as load as it was previously when I was running XP. Do I need a different sound driver? Or is this something I jsut have to live with?

secondly:

I installed WoW against my better judgement (trying to quit) and it looks, umm... a bit weird on Ubuntu. I am trying to post screen shots but imageshack won't let me upload .png   files. Essentially If you can imagine out side Orggrimar or even in WSG for Alliance members, the terrain textures in some places are about 10x darker than the area adjacent to it (what its transitioning into). And they are HUGE patchess as well. For example, when I exit Org from the main entrance the width of the doorway leading out from the gate is very dark, but on either side it is properly light like it is supposed to be. I have the Nvidia 177 driver which was marked recommended and am running trough Wine.

Any help given would be much appreciated, but please keep in mind that it is only my second day with Ubuntu so I don't know much of the vocabulary yet. Mostly I am concerned with the sound problem, everything is so soft and must be turned up pretty high relative to what it was before so that I can hear. And I know it isn't my ears giving out on me!

-Sophy

---

### Post by GSI on 2009-02-03
For the first problem :
Try AmaroK : marok 2.0 Released. Its time to install the all new Amarok in Ubuntu. If you are using Ubuntu 8.10 with Amarok then it will not update to its latest version automatically. You have to do a little work. Amarok's new package is called amarok-kde4 not amarok.

Go to System > Administration > Software Sources

Now Go to "Third Party Software" Tab.

Click "Add"

Now paste the following line in the box:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

Click "Add Source" to close the dialogue box and when OS asks to update package list click "Reload".

Now Open Synaptic Package Manager from System > Administration.

Do a small Search with "Amarok" keyword.

You will soon find amarok-kde4 package

NOTE: Dont Forget to go into TOOLS--->EQUALIZER and dont forget to click EQUALIZER ON ;)

For The second problem : I think that its from the video card becouse i have same problems with big 3D games some objects dont appear or i go into space i think that its bcz the game is for widows ;)

---

### Post by sdlong92 on 2009-02-03
> **GSI said:**
> For the first problem :
Try AmaroK : marok 2.0 Released. Its time to install the all new Amarok in Ubuntu. If you are using Ubuntu 8.10 with Amarok then it will not update to its latest version automatically. You have to do a little work. Amarok's new package is called amarok-kde4 not amarok.

Go to System > Administration > Software Sources

Now Go to "Third Party Software" Tab.

Click "Add"

Now paste the following line in the box:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

Click "Add Source" to close the dialogue box and when OS asks to update package list click "Reload".

Now Open Synaptic Package Manager from System > Administration.

Do a small Search with "Amarok" keyword.

You will soon find amarok-kde4 package

NOTE: Dont Forget to go into TOOLS--->EQUALIZER and dont forget to click EQUALIZER ON ;)

For The second problem : I think that its from the video card becouse i have same problems with big 3D games some objects dont appear or i go into space i think that its bcz the game is for widows ;)

Thanks for the help I will try that out. Too bad about the game though, I will just have to live with it! I appreciate you reply and hope you have a nice day.

Edit: I tried adding the line to Software Sources and searched for Amarok but nothing showed up as Amarok-kde4, just Amarok. From what I saw, I don't believe there was a 2.0 version there. Also, will a kde player work for me? I think I am using Gnome. Sorry for these questions, I am still very new to this!

-Sophy

---

