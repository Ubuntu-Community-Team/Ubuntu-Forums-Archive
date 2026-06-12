---
title: "KDE detected that one or more internal sound devices were removed"
date: 2011-01-22
forum: Multimedia Software
---

### Post by sutachan on 2011-01-22
p, li { white-space: pre-wrap; } Hello,
I am new here and also ubuntu is quite new to me. I hope someone can help me with this. Rhythmbox plays some music (not all of it) and it sounds crappy. And when I start Amarok I get this: 

KDE detected that one or more internal sound devices were removed.
 Do you want KDE to permanently forget about these devices?
 This is the list of devices KDE thinks can be removed:
 
[LIST]
[*]Output: HDA Intel (INTEL HDMI)
[*]Output: HDA Intel, INTEL HDMI (HDMI Audio Output)
[/LIST]
What to do?

---

### Post by SeijiSensei on 2011-01-22
System Settings > Multimedia > Phonon

You'll see the devices the operating system detected.  If there are multiple entries for a particular function, say Music, use the Prefer/Defer arrow buttons to make one of them the default (top of the list).  See if things play correctly.  If not, try choosing a different device.

---

### Post by sutachan on 2011-01-22
> **SeijiSensei said:**
> System Settings > Multimedia > Phonon

You'll see the devices the operating system detected.  If there are multiple entries for a particular function, say Music, use the Prefer/Defer arrow buttons to make one of them the default (top of the list).  See if things play correctly.  If not, try choosing a different device.

Okay... This is going to be a very nooby question... (I just just started with ubuntu) Where do you find "system settings" ? Do you mean under system -> preferences? :oops:  (thanks a lot in advance)

---

### Post by SeijiSensei on 2011-01-23
It's on the front page (the "Favorites" page) of the main KDE menu that you see when clicking the "K" icon in the lower left-hand corner of the screen.  

What version of Ubuntu are you running?  I know System Settings is there in Lucid (10.4) and Maverick (10.10), and probably back though 9.x as well.

---

### Post by pwabrahams on 2011-04-26
I too have gotten this message -- more than once.  I think there's a design problem behind it.  In my case, the "devices" were USB codecs.  And once I got the message, my sound has usually been messed up.

The message might be helpful if the devices were actually permanently attached hardware devices.  But removing the devices if they're USB devices might be the wrong thing to do, since USB devices are often attached and detached repeatedly.  It's also the wrong thing to do if the "devices" are any kind of software entity.

What disturbs me about this message is how one can know what the consequences are of removing the devices, or -- even more drastically -- telling KDE not to ask for them again.  Does telling KDE to forget about the devices mean that it will fail somehow if they are reattached? How can a user make an intelligent decision on how to answer the question?

My guess is that this message should never be issued for USB devices or for anything that isn't definitely implemented in hardware.  Also, is it correct to refer to "devices" in this context rather than "device drivers"?

---

