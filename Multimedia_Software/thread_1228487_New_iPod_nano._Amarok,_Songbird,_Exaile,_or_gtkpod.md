---
title: "New iPod nano. Amarok, Songbird, Exaile, or gtkpod?"
date: 2009-08-01
forum: Multimedia Software
---

### Post by AgentWiggles on 2009-08-01
I need a program that can do a good job of managing my iPod. The program needs to be able to handle a very large music library (4000 songs and growing.) I've been using Exaile to manage my library, but I don't know what it's iPod support is like and as iPods are somewhat finicky I don't really want to be trying 50 different managers. 

The requirements I have for the ideal program are pretty much what you'd expect:

It needs to be able to manage my music library
It needs to be able to get the songs I want on my iPod on my iPod, and ONLY the songs I want on it.
It needs to be able to create playlists and put them on the iPod.

Other features that would be nice, in order of importance:

Nike+ compatibility 
Find and add album art to the tracks that are lacking it (Exaile finds the album art usually, but I don't know if it gets added)
A REALLY nice feature would be if it would convert any .wma files I have to .mp3. I know I can do this manually, but it would be nice if the program had it built in.

Bonus points awarded for ease of use, lightweight (i.e. not hogging half my processing power and my ram), etc.

Right now leaning towards Songbird, although Amarok looks good too, I would just need to know what repositories I'll need to run it on Ubuntu. Exaile and gtkpod are last resort ideas. The only bad thing I've heard about Songbird is it hogs resources, and I don't really know if it's designed to handle 4000 songs kicking around.

Alright, thanks for the help in advance.

---

### Post by Bigtime_Scrub on 2009-08-01
I don't think for what you are asking for you are going to get an application that can do all that and not eat away some resources. 

I use gtkpod and it works for me but you want a more full featured program so I would say go with Amarok. It does everything you want it to.

---

### Post by vinutux on 2009-08-01
> **AgentWiggles said:**
> I need a program that can do a good job of managing my iPod. The program needs to be able to handle a very large music library (4000 songs and growing.) I've been using Exaile to manage my library, but I don't know what it's iPod support is like and as iPods are somewhat finicky I don't really want to be trying 50 different managers. 

The requirements I have for the ideal program are pretty much what you'd expect:

It needs to be able to manage my music library
It needs to be able to get the songs I want on my iPod on my iPod, and ONLY the songs I want on it.
It needs to be able to create playlists and put them on the iPod.

Other features that would be nice, in order of importance:

Nike+ compatibility 
Find and add album art to the tracks that are lacking it (Exaile finds the album art usually, but I don't know if it gets added)
A REALLY nice feature would be if it would convert any .wma files I have to .mp3. I know I can do this manually, but it would be nice if the program had it built in.

Bonus points awarded for ease of use, lightweight (i.e. not hogging half my processing power and my ram), etc.

Right now leaning towards Songbird, although Amarok looks good too, I would just need to know what repositories I'll need to run it on Ubuntu. Exaile and gtkpod are last resort ideas. The only bad thing I've heard about Songbird is it hogs resources, and I don't really know if it's designed to handle 4000 songs kicking around.

Alright, thanks for the help in advance.

Try banshee.......**Banshee....all the way**

```
sudo apt-get install banshee
```

---

### Post by AgentWiggles on 2009-08-01
I'll look into Banshee. And honestly, resources aren't a HUGE deal, it just needs to be able to run without slowing my system down. I'll look at Banshee, and does anyone know which repositories are needed to run Amarok on Ubuntu?

---

### Post by nacho32 on 2009-08-01
> **vinutux said:**
> Try banshee.......**Banshee....all the way**

```
sudo apt-get install banshee
```

I get this when i try that
banshee:
 Depends: libgconf2.0-cil (>=2.20.0) but it is not installable
 Depends: libgnome2.0-cil (>=2.20.0) but it is not installable
 Depends: libmtp7  but it is not installable

---

### Post by vinutux on 2009-08-02
> **nacho32 said:**
> I get this when i try that
banshee:
 Depends: libgconf2.0-cil (>=2.20.0) but it is not installable
 Depends: libgnome2.0-cil (>=2.20.0) but it is not installable
 Depends: libmtp7  but it is not installable

Remove thirdparty repos from Software-sources

system>Administartion>Synaptic>settings>Repositories > third party software tab ....untick all third party repos.....

Reaload package infos...and install banshee from there or run previous command

---

