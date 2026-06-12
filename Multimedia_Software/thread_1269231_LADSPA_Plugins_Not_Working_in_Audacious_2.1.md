---
title: "LADSPA Plugins Not Working in Audacious 2.1"
date: 2009-09-18
forum: Multimedia Software
---

### Post by booksnmore4you on 2009-09-18
Hi all.  

I'm a Linux convert of 5 months, having finally been able to make the switch after [Zotero]("http://www.zotero.org/")  bibliographic software reached a point in its development where I could abandon Windows.

I'm also a music lover and have been reluctant to give up what [iZotope Ozone]("http://www.izotope.com/products/audio/media/ozone.html") does with WinAmp.  

Yet when I discovered what LADSPA host plugins can do coupled with Audacious, I made the switch.

**My trouble is that**, after switching from Linux Mint to Ubuntu Jaunty some days ago, and upgrading from Audacious 1.5 to 2.1, the LADSPA host plugins no longer work. They appear to have installed...at least they are viewable within Audacious.  Yet they have no effect on the sound as they did when I used Mint and Audacious 1.5.

I've also installed Audacious 1.5 on my Jaunty machine, which also has Audacious 2.1.  The LADSPA plugines work in neither.

I'm stumped and would very much appreciate any assistence you might give. :)

---

### Post by booksnmore4you on 2009-09-18
Bump :)

---

### Post by n0l4n on 2009-10-28
[http://jira.atheme.org/browse/AUDPLUG-2](http://jira.atheme.org/browse/AUDPLUG-2)

---

### Post by booksnmore4you on 2009-11-09
Bingo!  That's the fix.  Thanks! :popcorn:

---

### Post by booksnmore4you on 2009-12-31
Since glib was updated, the back version of the plugin no longer works. This means that Audacious basically sucks now, since you have to configure the LADSPA plugins each time you open the program. :(

---

