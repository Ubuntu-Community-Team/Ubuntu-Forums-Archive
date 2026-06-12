---
title: "Shotwell importing photos from Shotwell?"
date: 2011-04-08
forum: Multimedia Software
---

### Post by idef1x on 2011-04-08
Is there a way to import photos into Shotwell from another Shotwell and keep all the information (Events, Tags, etc)?

I've 2 computers with ubuntu Shotwell: a "big" one for normal work and a netbook for during travel. I've on the big one all my photos in Shotwell with events, tags, etc and during my travel  store photos on the netbook and use Shotwell to preselect/delete/tag/etc the photos during travel so i don't have to do all at home. So now I've 2 places with Shotwell information....

Any suggestions?

---

### Post by eric-yorba on 2011-04-08
Take a look at the Shotwell FAQ, which contains an answer to this very question:
[http://trac.yorba.org/wiki/Shotwell/FAQ#HowcanImovemyphotofilesfromonedirectoryorharddrivetoanother](http://trac.yorba.org/wiki/Shotwell/FAQ#HowcanImovemyphotofilesfromonedirectoryorharddrivetoanother)

Let me know if you need any further help.

---

### Post by idef1x on 2011-04-08
Hello Eric-Yorba,

Thanks for replying, but the faq is referring to moving pictures around. I have 2 shotwell libraries and want to make one out of it without loosing the event names, tags,etc,....

---

### Post by eric-yorba on 2011-04-08
Gotcha.  Unfortunately there isn't exactly a way to do this at the moment.

There is one option that will be able to save *some* of that information, however.  There's an option in the preferences to write your titles and tags out to the EXIF data in the JPEG file itself (this only works for JPEG files at the moment.)  Once it finishes writing out your library, you can take those photos and import them into the new Shotwell library.

However, that metadata doesn't include events, and won't work for RAW, AVI, MOV, and many other formats.

Importing an existing Shotwell database seems like an excellent idea for a feature to me.  I've ticketed the item here:
[http://trac.yorba.org/ticket/3481](http://trac.yorba.org/ticket/3481)

---

### Post by idef1x on 2011-04-09
That' s indeed what i meant :-)
Thanks for ticketing it and since you wrote it' s an excellent idea, i will see it in the next release then? ;)

---

### Post by eric-yorba on 2011-04-11
Sorry, it's not scheduled for 0.10.  But perhaps the near future.

FYI, the bug report turned out to be a duplicate (oops!) so please refer to the original bug here:
[http://trac.yorba.org/ticket/3393](http://trac.yorba.org/ticket/3393)

---

### Post by Teabicky on 2011-04-12
I'd like to see this too.  I have my photos stored on four computers and don't want to have to edit the event data far ALL my photos on each one, and then every subsequent computer after that.

However, I do think that Shotwell is better than F-Spot.  Its looks nicer and seems to run smoother too!

---

