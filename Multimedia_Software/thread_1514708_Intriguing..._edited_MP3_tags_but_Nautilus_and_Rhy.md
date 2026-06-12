---
title: "Intriguing... edited MP3 tags but Nautilus and Rhythmbox still see previous values."
date: 2010-06-21
forum: Multimedia Software
---

### Post by leorolla on 2010-06-21
I had a problem yesterday and I really don't know what could be the cause.

I edit my ID3 tags inside MP3 files with EasyTag and QuodLibet.

Yesterday I was changing the tag from some of my albums but every time I restarted Rhythmbox it would see the old value. Nautilus also sees the old value.

I have changed the tags several times using with EasyTag with different options, ID3v1, ID3v2, Unicode/Latin, re-edited the tags, also used QuodLibet and even Rhythmbox itself.

Is there any other type of metadata embedding that Nautilus seeks first and that are ignored by EasyTag?

Thanks.

---

### Post by leorolla on 2010-06-22
Nobody?

---

### Post by Dngrsone on 2010-06-22
I found out that some .mp3 files will have several sets of ID3 tags, and apparently Rhythmbox reads the wrong one.

For .mp3 files, I'd try MP3 Diags-- see if you get error 'ga' on the problem files and remove the multiple ID3 tags.

My problem right now is that Rhythmbox doesn't read .wma file tags correctly... I have a bunch of compilation album titles that show "Various Artists" under the Artist heading but any other program (Picard, Exaile, WMP in XP) reading the file headers sees the correct information.

---

### Post by leorolla on 2010-07-01
Thanks!!!!

That tool is just great!

I had multiple TAGs of the same format (ID3v2.4).

---

### Post by Dngrsone on 2010-07-01
Happy to be of service.

---

### Post by leorolla on 2010-07-02
I got a question, maybe you know...

When I set Easytag to update my tags to ID3v2.3, MP3Diags tells me that it is actually ID3v2.4.

The question is not just useless curiosity... it's two reputed editors making edition wars over my files, after I have set them to fix the songs automatically to ID3v2.3.

Do you know whish one is telling the truth?

---

### Post by ron999 on 2010-07-02
This has me confused also.
I've installed mp3diags.
It shows some of my files have ID3v2.4.0 tags too. I thought that EASYtag had set them to ID3v2.3.0.

There's another program named Kid3.
This has an option
Tools > 'Convert ID3v2.4 to ID3v2.3'.
After using that, mp3diags shows the tags as ID3v2.3.0.

---

### Post by leorolla on 2010-07-02
And I guess when you open with EasyTag again (if it is configured to automatically update to id3v2.3) then all files appear in red and it prompts you whether to save them, and after that mp3diags complains again... ?

And do you get a lot of "ej - Picture description is ignored in the current version"?
Is this any bad? How to get rid of this?
The brute force way is to just replace the picture by a copy of itself, but this is too stupid, time consuming, and I don't know if it is any important in first place.


Oh, by the way:

I started this thread because of these immutable files... well... mp3diags told me on the spot what the problem was. I had two ID3v2.3 entries, so I just had to remove the duplicate one.

But now I found a lot of crap in all the files and decied to clean them more properly.

---

### Post by ron999 on 2010-07-02
> **leorolla said:**
> And I guess when you open with EasyTag again (if it is configured to automatically update to id3v2.3) then all files appear in red and it prompts you whether to save them, _**and after that mp3diags complains again... ?**_



Nope
mp3diags shows the tags are id3v2.3.0, not id3v2.4.0.
No complaints.

---

### Post by EllyBilateralCI on 2010-07-29
Wow...MP3 Diags is great and so easy to install from the Ubuntu Software Centre.

One thing though I've installed the MP3 Diags Documentation as well but how do you open it?  Sorry I haven't a clue when it comes to documentation installations from Ubuntu Software Centre.

If you could help me then you're a star!   :KS

---

