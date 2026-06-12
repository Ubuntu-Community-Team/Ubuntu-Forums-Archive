---
title: "Why hasn't VLC been made the default video player in ubuntu?"
date: 2011-07-01
forum: Multimedia Software
---

### Post by chazinams on 2011-07-01
I'm a new Ubuntu user. After having a lot of trouble getting Totem to play online video streams and DVDs, I started searching for solutions. Ultimately after reading other people's posts, I installed VLC and now can get everything playing.

I figure there is a good reason that VLC hasn't been made the default video player despite its popularity among ubuntu users. I was wondering what exactly that reason is?

---

### Post by wolfen69 on 2011-07-01
"Ubuntu strives to make all software that meets the licensing terms in the Ubuntu License Policy available. However patent and copyright restrictions complicate free operating systems distributing software to support proprietary formats.

Ubuntu's commitment to only include completely free software by default means that proprietary media formats are not configured 'out of the box'.

Ubuntu can play the most popular non-free media formats, including DVD, MP3, Quicktime, Windows Media, and more by following the instructions below. If this seems like unnecessary work, remember that Ubuntu is a distribution of free software and these packages are (at least arguably) affected by patents and license restrictions in some countries. Avoid formats suppressed by DRM (Digital Rights Management, or Digital Restrictions Management), as they are often unplayable."

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by chazinams on 2011-07-01
> **wolfen69 said:**
> "Ubuntu strives to make all software that meets the licensing terms in the Ubuntu License Policy available. However patent and copyright restrictions complicate free operating systems distributing software to support proprietary formats.

Ubuntu's commitment to only include completely free software by default means that proprietary media formats are not configured 'out of the box'.

Ubuntu can play the most popular non-free media formats, including DVD, MP3, Quicktime, Windows Media, and more by following the instructions below. If this seems like unnecessary work, remember that Ubuntu is a distribution of free software and these packages are (at least arguably) affected by patents and license restrictions in some countries. Avoid formats suppressed by DRM (Digital Rights Management, or Digital Restrictions Management), as they are often unplayable."

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

From what I've read, I was understanding that VLC is completely free and open source. I thought it had the LGPL license, same as Firefox. Is your post saying it is not default because it does not have an open source license?

---

### Post by beew on 2011-07-01
> **chazinams said:**
> From what I've read, I was understanding that VLC is completely free and open source. I thought it had the LGPL license, same as Firefox. Is your post saying it is not default because it does not have an open source license?

Yes, but VLC's strongest selling point is the codecs built into it,--you can throw any crap at it and it plays,--those are not free. To install it in Ubuntu by default they would have to strip it of the codecs and that basically cripples it, why would you want that?  If you strip it of its codecs then it is just another media player. I think mplayer is better than VLC in terms of performance and mplayer2 beats it hands down. 

Anyhow, who cares what default media player Ubuntu uses anyway. I never install multimedia stuffs from the official repos as they are always out of date and almost always crippled and sometimes even broken.

Yeah I agree Totem is crap, but I suspect anything they make the default would be crap anyway, for legal reasons (no codecs) and the conservative update policy (version frozen during the entire lifespan of a release,--1.5 years for normal releases and 3 years for LTS. No new features and no bug fixes except security releated)

BTW, install the gecko-mediaplayer for streaming online videos and the totem plugin is really good for streaming quicktime (like apple trailers) even though it sucks at almost everything else.

---

### Post by Chronon on 2011-07-02
GPL is a distribution license that allows copyright holders to specify conditions under which users can reuse, modify and redistribute copyrighted material.  It's independent of any patent issues, which is the problem facing certain free implementations of codecs.  Source code might be totally free (in the sense that it bears a libre distribution license) yet still overlap with certain patents.  

If I understand correctly, this is the situation faced by VLC.  It (and its bundled codecs) are FLOSS but there are potential patent issues in certain locales.

---

### Post by handy on 2011-07-02
> **Chronon said:**
> GPL is a distribution license that allows copyright holders to specify conditions under which users can reuse, modify and redistribute copyrighted material.  It's independent of any patent issues, which is the problem facing certain free implementations of codecs.  Source code might be totally free (in the sense that it bears a libre distribution license) yet still overlap with certain patents.  

If I understand correctly, this is the situation faced by VLC.  It (and its bundled codecs) are FLOSS but there are potential patent issues in certain locales.

Wolfen69's post is excellent.

To add to that, my understanding is that the primary reason that VLC is not installed by default is that there is *"inference"* that libdvdcss2 is illegal in the U.S. & perhaps some E.U. countries.

This a link to very well researched info', that is a few years old, though even so it gives a very good run down on the situation re. libdvdcss & the win32codec packages:

[http://www.psychocats.net/ubuntucat/the-legality-or-illegality-of-w32codecs-and-libdvdcss2/](http://www.psychocats.net/ubuntucat/the-legality-or-illegality-of-w32codecs-and-libdvdcss2/)

---

### Post by mc4man on 2011-07-02
> that there is "inference" that libdvdcss2 is illegal in the U.S.
Just to mention - libdvdcss has never been challenged or declared 'illegal' in the U.S. though illegal and legal are more aptly seen from the 'is there any money to be had or not' perspective

decss is illegal in the U.S., but a different thing altogether from libdvdcss

---

### Post by SeijiSensei on 2011-07-02
Whether it's been challenged in court or not, libdvdcss2 pretty clearly violates the "[anti-circumvention]("http://www.law.cornell.edu/uscode/html/uscode17/usc_sec_17_00001201----000-.html")" provisions of the US Digital Millenium Copyright Act (section (a)(2) in particular).

---

### Post by mc4man on 2011-07-02
> **SeijiSensei said:**
> Whether it's been challenged in court or not, libdvdcss2 pretty clearly violates the "[anti-circumvention]("http://www.law.cornell.edu/uscode/html/uscode17/usc_sec_17_00001201----000-.html")" provisions of the US Digital Millenium Copyright Act (section (a)(2) in particular).

In the context of this thread it's irrelevant, that's not why vlc isn't the 'default', libdvdcss is not built-in to ubuntu's vlc

As far as libdvdcss - it been widely distributed and used by 100's of thousands of U.S. citizens and never has or will be taken to task, either from those using or distributing it.
(and never will

---

### Post by handy on 2011-07-02
> **mc4man said:**
> Just to mention - libdvdcss has never been challenged or declared 'illegal' in the U.S. though illegal and legal are more aptly seen from the 'is there any money to be had or not' perspective

decss is illegal in the U.S., but a different thing altogether from libdvdcss

You obviously didn't read the page I linked to in my previous post!

You are just doing a repeat, without the details.

---

### Post by handy on 2011-07-02
> **SeijiSensei said:**
> Whether it's been challenged in court or not, libdvdcss2 pretty clearly violates the "[anti-circumvention]("http://www.law.cornell.edu/uscode/html/uscode17/usc_sec_17_00001201----000-.html")" provisions of the US Digital Millenium Copyright Act (section (a)(2) in particular).

Yes, the U.S. is the most dangerous place for VLC & its associated files.

> **mc4man said:**
> 
In the context of this thread it's irrelevant, that's not why vlc isn't the 'default', libdvdcss is not built-in to ubuntu's vlc 

I beg to differ. I'd be pretty sure that, that, IS the reason why VLC isn't included in Ubuntu.

> **mc4man said:**
> 
As far as libdvdcss - it been widely distributed and used by 100's of thousands of U.S. citizens and never has or will be taken to task, either from those using or distributing it.
(and never will

That means nothing. 

There are millions of people around the world (very many of them living in the U.S.) at this very moment who are down/uploading illegal torrents. They haven't been taken to task by the U.S. courts either.

So, what are you trying to say?

---

### Post by chazinams on 2011-07-02
The Linux questions' Wiki says DVD encryption "was developed so that an encrypted DVD could only be played on a licensed player. Licenses are granted by The DVD Forum."

What is the point of making a player obtain a license? Does it ensure the player meets certain specifications? Or is it simply another way for a Corporation to make more money?

---

### Post by SeijiSensei on 2011-07-03
> **chazinams said:**
> The Linux questions' Wiki says DVD encryption "was developed so that an encrypted DVD could only be played on a licensed player. Licenses are granted by The DVD Forum."

What is the point of making a player obtain a license? Does it ensure the player meets certain specifications? Or is it simply another way for a Corporation to make more money?

Licensing DVD players was intended to insure that no players were sold that would allow people to make unauthorized copies.  There have been many such efforts by the media industries to restrict what people can do with their licensed content.  The [HDCP]("http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection") protocol, for instance, provides for end-to-end encryption of high-definition material. That means that not only a Blu-ray player but the television or monitor must also conform to the HDCP protocol to display HD content.

Licensing for a patented technology like MP3 or H.264 has a more direct commercial purpose, earning patent royalties to cover the costs of development and, as you say, "make more money."

---

