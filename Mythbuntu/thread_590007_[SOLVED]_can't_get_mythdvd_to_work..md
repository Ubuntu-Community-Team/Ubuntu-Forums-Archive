---
title: "[SOLVED] can't get mythdvd to work."
date: 2007-10-24
forum: Mythbuntu
---

### Post by fusion_05 on 2007-10-24
I'm kind of clueless when it comes to this.  I've got mythbuntu control center installed, and I've got dvd's playing in VLC just fine, and I've downloaded the mythdvd plugin with the mythbuntu control center.  However, when I go into the mythdvd, I select play dvd and the screen just flashes.  I'm not sure what I'm missing.  I would really appreciate some help.

---

### Post by tgm4883 on 2007-10-24
Sounds like mythtv isn't pointed to the dvd drive.

Check the setup in Mythdvd settings

---

### Post by fusion_05 on 2007-10-24
For location of the DVD device it says /dev/dvd.  I've got a cd-rw drive and a dvd-rw drive, and that sounds right to me.  How do I figure out what the location of my dvd drive is?

EDIT:  I looked at the device location under places>computer, and it says the location is computer:///  is that right?

---

### Post by superm1 on 2007-10-24
Well look in /dev

You can have anything ranging from a /dev/dvd, /dev/dvdrw, /dev/dvd1 /dev/dvdrw1

See what the right name is for you.

---

### Post by Meph1st0 on 2007-10-24
My memorex dvd-rw dl is apparently /dev/scd0. Is this normal?  

I've sort of had a hard time getting MythDVD working correctly as well.  VLC plays my DVDs just fine if I have it play /dvd/scd0.  But in Mythbuntu it'll open the disk and start playing but it's choppy and unstable.  It's crashed on me twice now.  It's using the Internal command to play DVDs.  Should I change this?

I've got xine, mplayer and vlc selected and installed in MCC.  Some people have suggested xine but I've never had much success with xine.  But I do want to have access to DVD menus and I've heard mplayer won't do dvd menus.

Is there a VLC command I could use instead?  I imagine I'd need to modify my lircrc to include VLC with my remote.

libdvdcss is installed as well if that matters.

---

### Post by fusion_05 on 2007-10-24
> **superm1 said:**
> Well look in /dev

You can have anything ranging from a /dev/dvd, /dev/dvdrw, /dev/dvd1 /dev/dvdrw1

See what the right name is for you.
I'll try this out when I get home, right now I'm at work, I'll be back home in a few hours.

---

### Post by superm1 on 2007-10-24
> **Meph1st0 said:**
> My memorex dvd-rw dl is apparently /dev/scd0. Is this normal?  

I've sort of had a hard time getting MythDVD working correctly as well.  VLC plays my DVDs just fine if I have it play /dvd/scd0.  But in Mythbuntu it'll open the disk and start playing but it's choppy and unstable.  It's crashed on me twice now.  It's using the Internal command to play DVDs.  Should I change this?

I've got xine, mplayer and vlc selected and installed in MCC.  Some people have suggested xine but I've never had much success with xine.  But I do want to have access to DVD menus and I've heard mplayer won't do dvd menus.

Is there a VLC command I could use instead?  I imagine I'd need to modify my lircrc to include VLC with my remote.

libdvdcss is installed as well if that matters.
Yeah you can set an external player such as vlc.  Its in the mythdvd options.

---

### Post by fusion_05 on 2007-10-24
> **superm1 said:**
> Well look in /dev

You can have anything ranging from a /dev/dvd, /dev/dvdrw, /dev/dvd1 /dev/dvdrw1

See what the right name is for you.

This worked great for me.  For the record, it was /dev/dvd1.  Thanks a lot for the help, I'm now watching Reign Over Me just fine!

---

