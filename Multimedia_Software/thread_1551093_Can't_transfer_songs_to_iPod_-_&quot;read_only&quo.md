---
title: "Can't transfer songs to iPod - &quot;read only&quot; file error"
date: 2010-08-11
forum: Multimedia Software
---

### Post by Devi 710 on 2010-08-11
Hi,

I use **Rhythmbox** to transfer songs to my **iPod** (nano 1st gen). 

I installed **Mediatomb** the other day so I could stream music and video on my **PS3** (which is awesome btw). Unfortunately, using Mediatomb my PS3 would only find a small portion of my music collection.

So I ran ```
sudo nautilus
``` then right clicked on my music folder, and changed the Group category to "Create and delete files" under the Permissions tab. After, my PS3 found my entire music collection. Great.

:( But now in Rhythmbox I get an **error** about the mp3 files being **read-only** and can't transfer them to my iPod :(

I've tried reversing the steps (with and without 'sudo'), but no luck. 

Under the **File Access** section of **Permissions**, I can never change anything (like to "read only" or "read and write"). No matter what I choose it always stays at "---"

[IMG]http://dl.dropbox.com/u/1483214/Linux/Music_PropertiesB.png[/IMG]

Any ideas??

Devi

---

### Post by alexrb on 2010-09-14
i have the same error with my ipod nano 1gen.
did you initialize your ipod on Mac or PC?

---

### Post by Devi 710 on 2010-09-19
> **alexrb said:**
> i have the same error with my ipod nano 1gen.
did you initialize your ipod on Mac or PC?

To get it to work again I had to use the Disk Utility on a mac and restore the ipod (I think I also had to turn 'journaling' on or off, don't remember). Then I plugged it into linux, rebuilt it in Banshee (but couldn't transfer songs), and transfered songs using Rhythmbox. 

A lot of trouble, but at least it still works. Rhythmbox doesn't transfer cover art though :(

---

### Post by zo3adams on 2012-12-07
I was able to resolve same problem by just forcing a remount in rw mode, with command below.   This was on a brand new IPOD in Ubuntu 12.04.

mount -oremount,rw /media/IPOD

---

### Post by Sambol on 2013-02-04
I had the same problem with an ipod that was formatted Mac-stylez, ie HFS+ (a .journal file should be visible when you cd into the ipod then ls -a)

Ubuntu, or at least the distro I was working with (12.04) could read but not write to this format.

Solution :

I plugged the ipod into a Windows 7 computer, and launched iTunes. Windows also dislikes working with HFS+, so it offered to reformat the little beast in FAT32. Note that this wiped the iPod's memory (see [http://www.linuxjournal.com/article/8160](http://www.linuxjournal.com/article/8160) for more details).

After that, things ran like clockwork when I attempted to sync with rhythmbox. I hope this helps!

---

### Post by wildmanne39 on 2013-02-04
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

