---
title: "Creative Zen on 9.04?"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Dagonus on 2009-05-02
So I searched around and I found a couple how-tos but most of them date to atleast a year plus ago so I'm a a touch leary of how well they'll work. I tried one and it didn't at all. 

I just bought a Creative Zen and I'm trying to get it to talk to Ubuntu. 

At first, Ubuntu auto mounted it and I could copy stuff on and off of the drive but the Zen wouldn't recognize it to play it. This prompted my looking in the first place. 

I tried Gnomad2: It told me there was no jukebox loaded. 

I tried KZenExplorer: It also told me there was no jukebox loaded. 

I tried Amarok: But for the life of me I couldn't figure out how to get it to look. Maybe it was and not finding anything since it wasn't auto loading anything. 

Then the Zen stopped auto-mounting. I don't know why. Gnomad, KZen and Amarok still aren't showing me anything. 

Maybe I'm missing something big and obvious, which wouldn't surprise me. 

So, how does one get any of the above programs to talk to a Creative Zen and/or is there an up to date how to somewhere that I missed?

---

### Post by Dagonus on 2009-05-02
ok. It figures. I spend 4 hours trying to get it to connect. Make a post. Solve 2 minutes later. 

I got it to connect by running Gnomad2 as root.

This brought me to a new problem though. It crashes. A lot.

Once it crashed as a result of creating a folder (listed as a segmentation fault). Every other time it seems to crash when i try to transfer an image off of the Zen onto the hdd. the Terminal reports the latter as an abort. 

It also crashed(Segmentation fault) as a result of browsing higher up the tree on the Zen.

Thoughts on any of this?

---

### Post by TusharG on 2009-05-05
I'm not sure why exactly you are facing issues. Here is my blog that covers how I'm managing my Zen really well with 9.04

[http://tusharg.blogspot.com/](http://tusharg.blogspot.com/)

Yes and I tried GNomad2 in 9.04 and it crashes often but i was not surprised with that cause I have always seen GNomad2 crashing when it tries to delete or try to copy file names with special characters.

---

### Post by granny6989 on 2009-05-18
Don't bother running as root... You currently have to unmount the Zen (Gnome can't wait to mount it when plugged in). Once it is unmounted, but still powered up and connected by USB, you should be able to use Rhythmbox and Gnomad2 just fine.

This is a problem of the cart leading the horse. Gnome made some significant USB changes before allowing certain programs to have the knowledge that they would have to change. So until rhythmbox, gnomad2, etc.. get on the new Gnome USB scheme, the only good way to use these programs is to unmount after you plug it in.

Unmount by right clicking the icon, or going to 'Places' and choosing the device, and then clicking the eject button.

PS- you have to hit eject after using with Rhythmbox, and must enable the MTP plugin to use it in the first place.

PSS- don't bother trying to get Gnomad2 0.9.4 or Rhythmbox 0.12.0 - this problem still persists in the current versions.

S*

---

### Post by Elep.Repu on 2009-08-06
> **granny6989 said:**
> Don't bother running as root... You currently have to unmount the Zen (Gnome can't wait to mount it when plugged in). Once it is unmounted, but still powered up and connected by USB, you should be able to use Rhythmbox and Gnomad2 just fine.

Thanks for the tip, this worked for me as well.
Where does Gnomad mount it?

---

### Post by cjminton on 2009-08-06
ubuntu automatically mounts the player on your desktop which you then must unmount by right clicking on the player on your desktop and clicking unmount. now try using gnomad.

:)

---

### Post by Elep.Repu on 2009-08-06
> **cjminton said:**
> ubuntu automatically mounts the player on your desktop which you then must unmount by right clicking on the player on your desktop and clicking unmount. now try using gnomad.

:)

Gnomad *works*. I just want to know where the program mounts it, because I can't find it any other way.

---

### Post by Elep.Repu on 2009-08-06
{UPDATE}
My issue was that I was selecting Data Transfer, instead of Music Transfer in Gnomad2.
So, after unmounting the automounted Creative Zen, and letting Gnomad2 mount it by scanning, I was able to transfer, and everything worked out wonderfully.

---

### Post by granny6989 on 2009-08-14
Guess you got your Zen all figured out. The gvfs-gphoto file system mounts it initially. It doesn't really show up anywhere in the file system that you can see. If it's powered on and connected, either mounted or not, it will show up under the Places tab. Once it powers off, it doesn't neccesarily show up anywhere, until you power it up or plug it back in, at which point the filesystem (gvfs), will immediately mount it again.

Supposedly this new mount system under gvfs and gphoto makes your device more accessible to more programs. However, so far, Gnomad and Rhythmbox (at least) do not have any updates or code to get those programs to work with the Zen mounted. Hopefully they'll get around to it soon enough. 

:?

S*

---

### Post by v1nsai on 2009-08-15
Cool, I was just trying to decide if I wanted to ditch my Zune and get another Zen.  Glad I found this thread :guitar:

---

### Post by tom purl on 2009-09-25
I just wanted to state that I'm having the same problem. My Zen worked *really* well with Ubuntu 8.04 + Amarok, but not so well in 9.04.  

I actually have to unmount my Zen *multiple times* when I first plug it into my machine.  After that, I have had very little luck using the Zen with either Banshee or Rhythmbox.  It works pretty well with Gnomad2, and today I'm having luck with Amarok (although I can't figure out why they screwed up the interface so much in the latest version).

I just wanted to share my experiences down in case anyone else is having the same issues.

---

