---
title: "Amarok Refulses to Play CD - settings are in order - missing plugin"
date: 2008-11-22
forum: Multimedia Software
---

### Post by navneeth on 2008-11-22
**Nautilus**

```
 Edit -> Preferences -> Media (tab) CD Audio: Open Amarok
```

**Amarok**: 

```
Settings -> Configure Amarok-> Engine -> Audio CD Configuration Default Device: /dev/cdrom *
```

Amarok won't play a normal audio CD when one is inserted.

But what happens is this. A new line is added to my play list with the title **from scd0/**.

A "slide-up" appears with the message

> **Error Loading Media**

No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
cdda://scd0/

Kindly help. I don't like Rythmbox. 


*Actually, I see that it's /dev/cdrom1 in my computer. Appending a 1 in Amarok's settings doesn't help.

---

### Post by mc4man on 2008-11-22
Amarok can be set to autoplay though you need to set things up a little differently.
The first reason is the default launch command of amarok is unsuitable for autoplaying cd's.

The second centers around  the location of the audio files in an autoplay event.

see here for a small how to. (for 8.04, if using 8.10 let me know and I'l see if any changes are needed

[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

Edit: will work just fine in 8.10. Note that at this point you will already have the folder (applications), the file (mimeapps.list) and the line (x-content/audio-cdda=) already created so no need to worry about that. (just need to add amarok-cd.desktop; to end of line

---

### Post by navneeth on 2008-11-22
Thank you very much, mc4man. That worked! 

One last question: Do you know how to stop Amarok from actually playing the CD - I mean, I would be happy if it would only recognise the CD and list the tracks and not start playing immediately. I want to have control of that. :)

---

### Post by mc4man on 2008-11-22
> One last question: Do you know how to stop Amarok from actually playing the CD - I mean, I would be happy if it would only recognise the CD and list the tracks and not start playing immediately. I want to have control of that. 

I've got to go out, ck. back later. It's may be  possible to write a new script though I doubt I know enough to implement it correctly. 
 I'd think it's possible one way or the other

Basically you'd need an  "amarok -s " command to run right after the playlist is populated

Maybe post a new thread, there any many talented script writers here and it would be a good way to learn (you and me both

The only key here is amarok needs to be started from a script for the 'auto play ' on cd insertion. What the script is,  is irrelevant as long as it works

If nothing comes up a simple and silly 'hack' would be to create a 2nd script with command of amarok -s, stick it in home , and make a desktop launcher for it. (hoping to see a new script though - more interesting, see screen for launcher

---

### Post by navneeth on 2008-11-23
Hey, thanks again, mc4man. I don't know how to write scripts on my own, so I think I'll post a new thread.

---

