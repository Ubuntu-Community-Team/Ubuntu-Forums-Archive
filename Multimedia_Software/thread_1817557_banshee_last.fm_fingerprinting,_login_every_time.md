---
title: "banshee last.fm fingerprinting, login every time?"
date: 2011-08-03
forum: Multimedia Software
---

### Post by -Sparx- on 2011-08-03
Hi peeps!

So I found banshee and decided to try and manage my old music library for real. 

Many of my imported CDs are really old so they have little to no meta-data connected to them. 
I found the last.fm fingerprinting addon and it seemed like it was the right thing. However I have some problems. 

Every time I try to use the fingerprinting I need to login to last.fm so for an album of 17 tracks I need to login about 17 times.
Connected to this is the problem that banshee doesn't seem to always write the new data to the file. I have checked that I allow it to write meta-data to file and change names of files. But sometimes it doesn't seem to stick. 
Is this how it is suppose to work? If not, how could i fix it?

I haven't found any threads or pages that describe this problem. But I would assume this would be a problem for those with previously unmanaged audio tracks.

On a side note. I would like to convert my mp3 and other formats to ogg or similar free format. What would you recommend for this? Can banshee do this?
I haven't searched for this yet but I thought I'd ask anyway. Is there some nice app that can do this for a whole library or similar?

Thanks!

---

### Post by starang on 2011-09-02
Same issue for me.  It will write 1 or 2 metadatas, but then will quit writing them.

It also asks to login every single time, even though I have logged into my last.fm account in the Library Tree.

Seems as though it should remember that I am logged in.

Anyone?

---

### Post by freakalad on 2011-09-08
My understanding is that Auth is not even necessary for use (there are some pretty basic restriction on use though - like 300 requests a minute or something)

[http://www.last.fm/api/show?service=441](http://www.last.fm/api/show?service=441)
track.getFingerprintMetadata

<quote>
Auth
This service does not require authentication.
</quote>

...but an API key may be required (not sure if gnome/banshee has/need it's own unique value, or already has one).
If push comes to shove, I'll apply for my own key & load it in a config file, if required.

I've filed bugs with last.fm & gnome/banshee:
[https://bugzilla.gnome.org/show_bug.cgi?id=658620](https://bugzilla.gnome.org/show_bug.cgi?id=658620)

Please check to confirm if you're experiencing a similar issue & that I've got it right.

---

### Post by -Sparx- on 2011-09-17
Good! Exactly the problem I am experiencing. I hope a solution will emerge.

---

### Post by freakalad on 2011-09-18
Please comment on the bug-report (& @ the last.fm forum-post) so that we can draw attention to the bug & maybe get some progress going there.

It's pretty messed-up that such an obviously-flawed piece of software made it into the reo's

---

### Post by freakalad on 2012-08-06
was hoping this issue would *finally* be fixed in the 12.04 release & stack, but this is very-much *not* the case, nor does the plugin actually work!
I think a case should be made for the complete removal of this plugin

---

### Post by slgtheindividual on 2013-01-07
I am having exactly the same problem in 12.10, has a solution for this emerged yet?

thank you in advance for any assistance.

---

### Post by bbarrett909 on 2013-02-06
This is a strange workaround... when it asks you for your username, you can click "cancel" (on the dialogue box), and sometimes it still scans and updates your metadata. This only fetches metadata for some (usually most) of the selected tracks.

EDIT: this seems to only work with certain tracks.  There seems to be no pattern. I can confirm that it is not related to the album or artist.

EDIT 2: This also seems to cause banshee to not request authentication every once in a while.

While this is a workaround, it takes a little while. I found it to be far faster then manual entry, though.

---

