---
title: "Play music from iPod"
date: 2008-06-10
forum: Multimedia Software
---

### Post by frogitts on 2008-06-10
I have a friend whose WindowsXP died on her, and we're 'stranded' in Germany without an OS reinstall CD. So I installed Ubuntu on her computer. The problem is that she's a music enthusiast. She has a ton of music that she bought from iTunes, and I want her to be able to listen to that music. The last thing I want is to tell her, 'Linux isn't good enough to play this music.'

I know this isn't Linux's fault, it's the fault of the DRM. However, if Linux is the superman of OS's, there should be a way, right? Even considering that Sharpmusique has died?

My guess is that she should be able to play the songs from her iPod over her computer speakers. Is that possible? Or is there a better way to solve this problem?

---

### Post by Therion on 2008-06-10
Have you tried using [GTKPod](http://www.gtkpod.org/about.html) for this?  

I'm not sure how well it deals with DRM-laden music, but if I was in your situation, it would be the first thing I'd try.

Oh, and of course Rhythmbox will do much the same...  Almost forgot about good old Rhythmbox.

---

### Post by cozmicharlie on 2008-06-10
> **frogitts said:**
>  The problem is that she's a music enthusiast. She has a ton of music that she bought from iTunes, and I want her to be able to listen to that music. The last thing I want is to tell her, 'Linux isn't good enough to play this music.'

I know this isn't Linux's fault, it's the fault of the DRM. However, if Linux is the superman of OS's, there should be a way, right? Even considering that Sharpmusique has died?

My guess is that she should be able to play the songs from her iPod over her computer speakers. Is that possible? Or is there a better way to solve this problem?

Friends don't let friends buy music from iTunes.  When you buy music from itunes you are not buying the music you are buying a license and that license restricts you from playing on multiple platforms.  So you are correct that the only way she can play it is to run it through the ipod which she can do in gtkpod.  A few other items you must add though.  I assume she has the music in mp3.  After you install Ubuntu you need to follow these steps to play mp3:

Install the medibuntu repository
Open the terminal (Applications > Accessories > Terminal  and cut and paste these wget commands into it:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


Next, go to the Synaptic package manager menu>system>administration and install the "Ubuntu Restricted Extras".  

In Synaptic also install gtkpod

Plug in the ipod and it should be detected.  Rythmbox will probably open when you do but just close it and open gtkpod menu>applications>sound & video>launcher for gtkpod

If she has some problems post back and we will make sure your friend is rock'n

---

### Post by frogitts on 2008-06-10
Well, thanks for the awesome suggestions, it's exciting to know that that would work. Unfortunately, after having talked with my friend about using her iPod to play her music, she told me her iPod has, since our previous conversation, died. So unfortunately no iPod, no iTunes music. However, I'm very encouraged that this is at least possible despite Apple's best efforts! After using Linux and having my eyes opened, I don't think I would ever support the iTunes store because of problems like these.

---

