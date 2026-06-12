---
title: "Banshee and iPod Shuffle Sync"
date: 2010-12-27
forum: Multimedia Software
---

### Post by jfranklinvanis on 2010-12-27
Banshee will recognize iPod shuffle 4th gen. It will let me drag songs to iPod and they show up in Banshee as being on my iPod. When I disconnect iPod and hit play, the voice over tells me to please load songs from iTunes. Anyone have any thoughts on my problem?

---

### Post by tld on 2010-12-29
I'm having the same issue with rhythmbox.  When I first plugged it in, it asked me if I wanted to initialize it, so I gave it a name and it clicked the button for initialize.  It went out to never never land at that point.  I copied songs from my hard drive to the ipod.  Now when I plug it in, it starts playing, but if I try to use it with just earbuds, that voice tells me to load the songs from iTunes.  I don't like that voice.  I only want my music in my ears, not crazy corporate apple peeps.

---

### Post by nicki20048 on 2011-07-24
Hello,

I'm having the same problem (i'm running Banshee in Lucid)

All the songs appear to be on my ipod but when I disconnect I get nothng.

Has anybody found a solution to this problem?

Edit: I should also add that i'm running Banshee 2.0 with libgpod 0.8

---

### Post by daniel_w93 on 2011-07-24
I think it might be a problem with the libraries. Because when starting the iPod with gtkPodit the latest default set-up available is the iPod Shuffle 3rd Generation.
As gtkPod and Banshee/Rythmbox use the same libraries for handling iPods that seems to be the problem.

I'm still trying if there is any solution that I can find...and will let you know if I find something

---

### Post by nicki20048 on 2011-07-26
> **daniel_w93 said:**
> I think it might be a problem with the libraries. Because when starting the iPod with gtkPodit the latest default set-up available is the iPod Shuffle 3rd Generation.
As gtkPod and Banshee/Rythmbox use the same libraries for handling iPods that seems to be the problem.
 
I'm still trying if there is any solution that I can find...and will let you know if I find something
 
 
But am I not right in saying that libgpod 0.8 library should support all the current ipods?

---

### Post by daniel_w93 on 2011-07-28
at least that's what they say on the website yes :P
It seems I've got it to work...although I don't really understand how or why^^
- loaded the music onto the iPod...couldn't play it 
- plugged it into computer running itunes...suddenly the music I                                    loaded onto it with banshee was there!

now I'm able to listen to the music and most peculiar if I load new music from banshee onto it it's also recognized...

[UPDATE: My brother had the same problem but he needed to reset the iPod to factory settings via itunes and then load new music on it with banshee]

[UPDATE 2: It seems to work perfectly if you plug the iPod into itunes and there set it to be handled as a filesystem. Then all the stuff you load onto it via banshee rythmbox etc. should play.]

---

