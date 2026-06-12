---
title: "Movie Player is throwing up errors"
date: 2010-11-26
forum: Multimedia Software
---

### Post by timbo59 on 2010-11-26
Hi there,
            I installed the latest version of Ubuntu on a Dell PC about a month ago, and everything has been going along swimmingly until recently.

As it's a secondary unit set up next to my main computer, I often like to toss in a DVD and watch something on the other monitor while I'm working in the evening on my own computer. It worked perfectly until last week, when some sort of little bug started creeping in. Every now and then, but not always, DVD's would get rejected with the message 'An error occurred. Could not read from resource'. At first I thought it might be the DVD's, then with the on again off again behavior I thought the resident Movie Players was just being temperamental. But it's now reached a point over the last week where it simply won't play any DVD's at all. Oddly enough though, it does at least recognize which DVD has been inserted, because it lists the title on the icon that appears on the desktop. 

I downloaded VLC media player to see if Movie Player was the issue, but the problem remained. I plugged the DVD/CD player/burner, which is an external unit, to my other computer and it worked like a charm, so the fault doesn't lie with the hardware. Everything seems to point to some sort of issue within the OS. Has anyone encountered this problem before?

Any thoughts on the matter would be much appreciated.


Thanks...........Tim

---

### Post by timbo59 on 2010-11-27
No takers? Maybe I should try a reinstall of Ubuntu,

---

### Post by mc4man on 2010-11-27
Before that.. 
Try opening vlc from the terminal, then playing a dvd and see what shows up.

First go into home folder -> view -> show hidden files, locate the .dvdcss folder and delete it.
Then try vlc

---

### Post by timbo59 on 2010-11-28
Sorry mc4man,
                       I have absolutely no idea how to accomplish what you're asking. I've only just switched over to Ubuntu from Windows-world, so am still feeling my way with this OS.

 I know how to open the terminal, but how do I make it run a program? As for accessing the hidden folder you mentioned, in Windows I'd know exactly how to get there, but through Ubuntu I'm lost. I tried opening up the file system in 'computer' as I would in Windows, but the files I saw were just nonsensical to me. I expected to find something like 'programs' but I can't see an equivalent. 

Sorry for trying your patience.

---

### Post by mc4man on 2010-11-28
> As for accessing the hidden folder..

Edit: before deleting .dvdcss folder put a dvd in the drive, close out any player if it opens, then  ->
In top panel go Places -> Home Folder
When there either do the "View -> show hidden files," or just Ctrl+h on keyboard. This will expose . (hidden) files.

Scroll down a bit - you'll see .dvdcss, right click -> move to trash.
Screen

Then open a terminal, type vlc then press enter on keyboard

---

### Post by timbo59 on 2010-11-28
Hi again,
            Okay, more confused than ever. I followed your instructions, went to the Home folder, checked the hidden files box, but found no .dvdcss file or folder in there. The only 'D's were Documents, Downloads, and .dbus. Is the dvdcss file supposed to be there?

---

### Post by mc4man on 2010-11-28
> Is the dvdcss file supposed to be there
If libdvdcss2 is installed then yes.
Your orig. description lead me to think you had.

Maybe read here
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

(for libdvdcss2 installation open a terminal, copy and paste this in, press enter
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by timbo59 on 2010-11-29
Hi again,
             Thanks, that worked like a charm.

Went through and punched in that line you gave me, then followed up by deleting the folder you mentioned earlier. After that VLC worked perfectly. Only issue is that Movie Player no longer seems to function. The error message went away, but it just won't respond when I try to get it to play a DVD. Seeing as VLC is doing the job I might as well delete Movie Player - worked fine until it developed that bug. 

Again, my thanks. One of the things I like immensely about dealing with the Ubuntu community is that not only is everyone so helpful, but also pretty civil. I get sick and tired of dealing with forums elsewhere bristling with mindless and ego-driven morons using the anonymity of their keyboards and monitors to indulge in the kind of odious behavior they wouldn't dream of displaying face to face. Nice for a change to frequent a place where everyone by and large remembers how to deal with each other in a polite manner. That's one of the intangibles that adds to the luster of switching to a Linux-based system. 

Cheers..........Tim

---

### Post by mc4man on 2010-11-29
While vlc is a superior dvd player over totem (Movie Player), if you'll have occasion to view online video's you may want to keep totem installed for the 'totem-mozilla' plugin.
something to consider..

---

