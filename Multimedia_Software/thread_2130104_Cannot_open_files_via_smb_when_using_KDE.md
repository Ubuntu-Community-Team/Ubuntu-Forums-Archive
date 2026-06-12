---
title: "Cannot open files via smb when using KDE"
date: 2013-03-28
forum: Multimedia Software
---

### Post by elefant23 on 2013-03-28
Hi folks,

First, thanks so much for providing *Ubuntu and this forum; it's awesome.

So my question/problem is:
I have Ubuntu 12.10 and have KDE SC installed. I try to open video/audio files that are located on SAMBA server (linux as well), but fail to open. For example, I tried to open Music clip file by VLC, but I get the following:
```
Your input can't be opened:
VLC is unable to open the MRL
```
In contrast, files can be played few seconds after I "open" them when using GNOME.
In other words, I want to play/open files by "streaming" (if this expression makes sense...). It works fine in when using GNOME, but fails when using KDE.
I'd very much appreciate any advices/hints/pointers/etc. Thanks very much in advance!

---

### Post by SeijiSensei on 2013-03-28
Try using an smb URL like this:

smb://server/share/

That works in Dolphin.  I don't know about apps like VLC.

---

### Post by elefant23 on 2013-03-30
Thanks very much SeijiSensei,

Actually, I am using URL format you've given me both in Dolphin and Nautilus (from KDE), but with no luck. I've also tried other movie/sound players, but same results.
Again, seems I can open files almost instantly (i.e., streaming is available) when using GNOME; it doesn't work when using KDE.
What are the possible reasons?

SeijiSensei and fellow experts, much appreciated for further help. Thanks in advance!

---

### Post by elefant23 on 2013-04-01
Hi folks and SeijiSensei,

I'd appreciate if you would tell me where I should be asking this question. Maybe my question is not relevant to Multimedia & Video. Any thoughts?
Thanks in advance!

---

### Post by cody1233 on 2013-04-02
can you access the files via the file manager in KDE or does that also not work?  This might also be responded to better in the networking section...maybe...

---

### Post by elefant23 on 2013-04-06
Hi cody1233,

Thanks very much for your help, and sorry for the late reply.

I do see files via the file manager in KDE (i.e., Dolphin). I can open/view small files such as txt, jpeg and the like instantly.
So here is what I'm observing (in KDE using Dolphin or even Nautilus):
* when I use "smb" (i.e., smb://server/path/), I cannot open files and get error messages.
* when I use "fish" (i.e., fish://server/path/), I can open files; local copies are made (thus larger the file, longer it takes). 

In GNOME, however, it seems even local copies are not made. Files are played as if they are being "streamed" (meaning files would be opened earlier than they are locally copied).

I'd consider posting in the Network section if it's hard to find solutions in this section.
Fellow experts and Ubuntu people, I'd appreciate any help/suggestions/ideas. Thanks in advance!

---

### Post by oshunluvr on 2013-04-12
It sounds to me like you're possibly blaming the DE for the video player's issue?

You say "streaming is available when using Gnome" but AFAIK, Gnome doesn't stream or play anything. Neither does KDE. You need a media player for that. You didn't say that you're using VLC in both instances, are you? Still, even if you are, VLC has a long standing problem with samba. See if you have this line in your VLC .desktop file:

**X-KDE-Protocols=http,ftp,smb**

If not, add or edit it and try again.

---

### Post by Roasted on 2013-08-19
> **oshunluvr said:**
> It sounds to me like you're possibly blaming the DE for the video player's issue?

You say "streaming is available when using Gnome" but AFAIK, Gnome doesn't stream or play anything. Neither does KDE. You need a media player for that. You didn't say that you're using VLC in both instances, are you? Still, even if you are, VLC has a long standing problem with samba. See if you have this line in your VLC .desktop file:

**X-KDE-Protocols=http,ftp,smb**

If not, add or edit it and try again.

The problem is Gnome has a "stream ready" type of response due to the existence of .gvfs. That's what allows media players to play the files without question because .gvfs is actually doing the magic in the background. Compare that to KDE, which uses KIO, this is not the case. I too have had a long standing issue with KDE as KDE has been unable to stream media from ANY media player for the last 3 years. There is an open bug report on the subject that I am unable to find at the moment, but the issue definitely exists.

Unfortunately, I know of no work around to this. To be quite frank, this issue is a tremendous, tremendous problem, and one of the handful of reasons why I cannot bring myself to use KDE full time. In Gnome, I don't have these problems. I can stream without issue. All of my media is on a local server in my house, so streaming is a must-have.

I am typing this from a Kubuntu install right now as I wanted to check out KDE 4.11 running in a native instance. Even with KDE 4.11 and all of the available updates, there is indeed no way to stream using Dolphin and the regular smb://server/share process. I can only hope KDE fixes this issue in the near future, but until then, I'll be on other DEs that handle these seemingly simple tasks with ease. ;)

---

