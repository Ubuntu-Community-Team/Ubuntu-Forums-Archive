---
title: "why is dvd playback not smooth in 8.04?"
date: 2008-07-08
forum: Multimedia Software
---

### Post by lazertek on 2008-07-08
everytime i play any dvd on ubuntu if it plays its distorted and lagging... I have XP virtualized with virtualbox and it plays distorted on xp too but when xp or vista is installed on its own it plays fine? Is this a bug if it is any fixes?

---

### Post by nikgare on 2008-07-10
Which graphics card and driver do you have?
Is dma enabled on your system?
Try starting totem (or you video player of choice) in a terminal, playing a dvd and looking for any error messages

---

### Post by ByteJuggler on 2008-07-10
Are you playing the videos natively also (and is it choppy there too), or only in the XP VM?  I would not recommend playing videos in a VM generally, because the VM's virtual video adapter won't be accelerated (at least, they aren't generally, at present) giving rise to video issues for things like movies, and which is why games in a VM is generally not workable.  

Make sure your native Linux video drivers are sorted out/fully working/fully accelerated, and your native Linux playback should then be pretty smooth.

---

### Post by Prefix100 on 2008-07-10
Is this from the same buggy DVD drive that you mention in your other topic?

---

### Post by lazertek on 2008-07-10
> **Prefix100 said:**
> Is this from the same buggy DVD drive that you mention in your other topic?
no this is on another computer

---

### Post by eldragon on 2008-07-10
run on a terminal 
```

$ metacity --replace

```

and try playing the video then. if you have compiz enabled, there are some bugs concerning video playback, especially with intel hardware.

---

### Post by lazertek on 2008-07-10
> **eldragon said:**
> run on a terminal 
```

$ metacity --replace

```

and try playing the video then. if you have compiz enabled, there are some bugs concerning video playback, especially with intel hardware.
I tried that and didn't work... I though it might compiz even before  I posted but that didn't help... I then though it might be because I am virtualizing xp switched that off even restarted and tried no luck... I also made sure it was the correct region...

---

### Post by nikgare on 2008-07-10
What program are you using to virew the dvds?
I've found that the output from vlc is better than totem-xine here

---

### Post by J A Smith on 2008-07-10
I can also second the VLC option, I had similar problems and VLC worked straight away.

---

### Post by lazertek on 2008-07-10
> **J A Smith said:**
> I can also second the VLC option, I had similar problems and VLC worked straight away.
what do i type next to vlc to play the dvd on the command line so i can get some error message i can show

---

### Post by lazertek on 2008-07-10
> **nikgare said:**
> What program are you using to virew the dvds?
I've found that the output from vlc is better than totem-xine here
i tried mplayer totem vlc none work... i was trying to fix my microphone and now my mp3's don't work either although sound works... however all required plugins are installed so I am confused what the problem is... how do i play an mp3 on command line too so i can find out the problem

---

### Post by J A Smith on 2008-07-10
VLC is a program, you can download it from the repositories. Use the installed program to play the DVD.

---

### Post by lazertek on 2008-07-10
> **J A Smith said:**
> VLC is a program, you can download it from the repositories. Use the installed program to play the DVD.
i already have vlc player... i meant how do i play the dvd from the terminal

---

### Post by mc4man on 2008-07-10
>  i meant how do i play the dvd from the terminal
For troubleshooting purposes just type vlc in an open terminal and press enter. Then after it opens use as normal, any error mess. will appear in the terminal.
For some add. info while open go view -> messages and or view -> stream and media info -> statistics.
Usually the terminal output is sufficient to point to the problem.
...................................

Worst case you go vlc -vv in the terminal,  the problem with that command is the amount of info is huge and some errors and warnings are to be expected and are of no consequence.

---

### Post by Prefix100 on 2008-07-10
vlc dvd:///dev/scd0

---

