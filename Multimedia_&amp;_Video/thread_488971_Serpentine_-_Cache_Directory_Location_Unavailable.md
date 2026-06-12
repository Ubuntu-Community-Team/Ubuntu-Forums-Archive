---
title: "Serpentine - Cache Directory Location Unavailable"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by abbot on 2007-06-30
I burned a CD in Serpentine only last week.  Now I'm trying to burn another one and am getting an error message upon click burn that says:

Cache Directory Location Unavailable
Please check if the cache location exists and has writeable permissions.

I read in another thread that the cache directory is actually /home/ and serpentine just dumps a bunch of .wav files in there temporarily.  I tried changing ownership and permissions of my home directory but that doesn't seem to make any difference.  Can anyone help me out?

---

### Post by numiller on 2007-07-26
I was having this exact same issue.  I could burn some cd and not others all the while getting that error.  After digging around and finding out where the cache is located (your home directory) and screwing with the permissions it still didn't work.

What I did notice, is that the free space on that partion was just about a cd size worth.  I took one song off the list and it burned fine.  So maybe if you increased the fee space to you home directory it would work.

---

### Post by cogumbreiro on 2007-08-13
The cache location that Serpentine uses is kept in this gconf key:

/apps/nautilus-cd-burner/temp_iso_dir

---

### Post by abbot on 2007-08-13
> **numiller said:**
> I was having this exact same issue.  I could burn some cd and not others all the while getting that error.  After digging around and finding out where the cache is located (your home directory) and screwing with the permissions it still didn't work.

What I did notice, is that the free space on that partion was just about a cd size worth.  I took one song off the list and it burned fine.  So maybe if you increased the fee space to you home directory it would work.

this was what the problem was.  i had less than 700mb free in my home directory.  as soon as i deleted some stuff it worked again.

---

### Post by daMask on 2007-10-22
I am having the exact same problem, but I don't know where to look at the size of my Home directory.  And once I find it, how do I change it?


:confused:

---

### Post by BenjaminGTF on 2008-03-18
> **daMask said:**
> I am having the exact same problem, but I don't know where to look at the size of my Home directory.  And once I find it, how do I change it?


:confused:


At the top of the screen click on the Places menu, and select Home Folder

The new window that pops up is the home directory for the user you are logged in as. It should say how much free space you have at the bottom of the window.

---

### Post by Mario Splash on 2008-05-01
Guys, This is easy, all you have to do, is find a directory where there's a lot of space.

i redirected it to one of my USB drives which has a lot of space and it worked for me.

after when you redirected it, try burning it again, it will give you some warning message that if you cancel the burn your CD will get ruined or something, then just continue with the burn.
I GIVE U INFO LIKE A BUNCH OF POPCORN :popcorn:
:lolflag:

---

