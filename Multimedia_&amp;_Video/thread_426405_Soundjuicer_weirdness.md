---
title: "Soundjuicer weirdness"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by Keith_Beef on 2007-04-28
I've recently upgraded to 7.04 (Feisty Fawn).

It looks like Grip is not packaged for Fawn, so I tried Soundjuicer.

Weird things happen!

So, I start up Sounjuicer and put in the Modest Mouse CD I bought this morning.

The track names are listed, so it SJ must be looking these up in something like the FreeCDDB, I suppose.

Now, I want to save these as OGG files, but what I've been doing lately, in Grip, is choosing to keep the WAV files, so I can generate a lower bitrate MP3 files for a portable player.

So I go to the Preferences dialog.

First weirdness: nowhere can I specify the address of the internet CD database to connect to.

Second: no option to keep a WAV file. Does SJ do the encoding on-the-fly?

Third weirdness: in the drop-down list for the output format, I had the choice of about five outputs. I didn't see MP3 there, so thought I would edit the "profile" (SJ's terminology for a set of parameters defining the output).

So I click on "Edit Profiles".
The "Edit GNOME Audio Profiles" dialog appears.
Now, I get a list of profiles. There is a profile names "CD Quality, MP3" so I choose that, and click Edit.

The "Editing Profile 'CD Quality, MP3'" dialog appears.

OK, so there is a little checkbox, this profile is Active, so why doesn't it show in the list?

Fourth and weirdest weirdness: I can't do anything in "Editing Profile 'CD Quality, MP3'" dialog. But I can change things if I first of all close its **parent** dialog ("Edit GNOME Audio Profiles" dialog).

Very weird indeed.

No matter how much I try, I cannot get SJ to allow me to encode in MP3.

I tried starting SJ from the commandline. There were no messages to suggest a secret option, just "shift: 96: can't shift that many" repeated a few times.


Beef.

---

### Post by paparucino on 2007-04-29
> **Keith_Beef said:**
> I've recently upgraded to 7.04 (Feisty Fawn).

It looks like Grip is not packaged for Fawn, so I tried Soundjuicer.



Grip is the universe repos.

Append this to your /etc/apt/menu.list (if not present :-) )

```

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

```

then in a terminal type
```

apt-get update
apt-get install grip

```

Enjoy :-)




UAResolved

---

### Post by spd106 on 2007-04-29
Hello,

I suggest that you read through this help docs page, some of the commands are a little dated, but it shouldn't be too difficult to modify [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping).

[Grip]("http://packages.ubuntu.com/feisty/gnome/grip") is in the Universe repository, so if you want to install it you'll have to enable universe in software sources first.

1) SJ uses [MusicBrainz]("http://musicbrainz.org/") first, then falls back to FreeCDDB if that fails. Please help MusicBrainz by submitting cd ids if you can spare a little time. I've no idea if or how you can change the database used.

2) Sorry I've no idea whether SJ users an intermediate format, though I think it's unlikely.

3) If you want to encode to MP3 you will have to install Lame, once again this is in the universe repo.

---

### Post by lorenz.en on 2007-04-29
I have exactly the same problem while trying to modify the edit profile in Sound Juicer, I think this is a bug.
By the way, I installed the codec following the guide in the forum:
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

After that, in the 'Preferences' window 'Output Format' dialog box I can select 'CD Quality MP3 (MP3 audio)' and I can rip the CD to mp3.

---

### Post by pentolino on 2007-05-03
> **lorenz.en said:**
> I have exactly the same problem while trying to modify the edit profile in Sound Juicer, I think this is a bug.
By the way, I installed the codec following the guide in the forum:
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

After that, in the 'Preferences' window 'Output Format' dialog box I can select 'CD Quality MP3 (MP3 audio)' and I can rip the CD to mp3.

Also have the same problem with soundjuicer profile editor but resolved the mp3 encoding problem by following that guide; thnaks for the pointer :-)

---

### Post by stchman on 2007-05-08
> **Keith_Beef said:**
> I've recently upgraded to 7.04 (Feisty Fawn).

It looks like Grip is not packaged for Fawn, so I tried Soundjuicer.

Weird things happen!

So, I start up Sounjuicer and put in the Modest Mouse CD I bought this morning.

The track names are listed, so it SJ must be looking these up in something like the FreeCDDB, I suppose.

Now, I want to save these as OGG files, but what I've been doing lately, in Grip, is choosing to keep the WAV files, so I can generate a lower bitrate MP3 files for a portable player.

So I go to the Preferences dialog.

First weirdness: nowhere can I specify the address of the internet CD database to connect to.

Second: no option to keep a WAV file. Does SJ do the encoding on-the-fly?

Third weirdness: in the drop-down list for the output format, I had the choice of about five outputs. I didn't see MP3 there, so thought I would edit the "profile" (SJ's terminology for a set of parameters defining the output).

So I click on "Edit Profiles".
The "Edit GNOME Audio Profiles" dialog appears.
Now, I get a list of profiles. There is a profile names "CD Quality, MP3" so I choose that, and click Edit.

The "Editing Profile 'CD Quality, MP3'" dialog appears.

OK, so there is a little checkbox, this profile is Active, so why doesn't it show in the list?

Fourth and weirdest weirdness: I can't do anything in "Editing Profile 'CD Quality, MP3'" dialog. But I can change things if I first of all close its **parent** dialog ("Edit GNOME Audio Profiles" dialog).

Very weird indeed.

No matter how much I try, I cannot get SJ to allow me to encode in MP3.

I tried starting SJ from the commandline. There were no messages to suggest a secret option, just "shift: 96: can't shift that many" repeated a few times.


Beef.

MP3 is a proprietary format and must be installed.  Ubuntu does not do MP3 out of the box.

I have a procedure to download the codecs and configure Sound Juicer to rip your audio CDs to MP3s using the LAME encoder for VBR.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

It works.

---

### Post by regomodo on 2007-06-02
I thought i'd say i have exactly the same problem. It's on my laptop and PC. I noticed it in Edgy but i had no major need to do cd ripping back then

It's a nice simple app, just being able to edit the profiles would be nice. You click to edit them and then you are locked out of the dialog.

Has anyone reported the bug yet?

---

### Post by ConnyBK on 2007-06-20
I've got the same problem, too.

I can add the MP3 profile and edit it (after closing its parent window) like described in the help. After that I restarted Soundjuicer but couldn't choose the newly created MP3 profile. I also tried to restart X but this didn't help either.

To me this seems like two bugs:
1. Need to close parent window to be able to edit a profile
2. Unability to choose a newly created (and active) profile

Did anyone find a workaround yet?

---

### Post by ConnyBK on 2007-06-20
I did a little more research and found out that this is a rights issue.

If you start sound-juicer by typing
```
sudo sound-juicer
```
into a console you can choose the newly created MP3 profile.

---

### Post by Major_Kong on 2007-06-20
> **ConnyBK said:**
> I've got the same problem, too.

I can add the MP3 profile and edit it (after closing its parent window) like described in the help. After that I restarted Soundjuicer but couldn't choose the newly created MP3 profile. I also tried to restart X but this didn't help either.

To me this seems like two bugs:
1. Need to close parent window to be able to edit a profile
2. Unability to choose a newly created (and active) profile

Did anyone find a workaround yet?

Use gconf-editor. Then go to system > gstreamer > 0.10 > audio > profiles. Edit the profile there.


> Second: no option to keep a WAV file. Does SJ do the encoding on-the-fly?

Yes. Or at least it tries... 

That's not weird, Sound-juicer allows encoding to FLAC format, wich is lossless. [http://en.wikipedia.org/wiki/FLAC](http://en.wikipedia.org/wiki/FLAC)
The creator probably didn't see the need for a WAV PCM option.


> Third weirdness: in the drop-down list for the output format, I had the choice of about five outputs. I didn't see MP3 there, so thought I would edit the "profile" (SJ's terminology for a set of parameters defining the output).

You have to install gstreamer-ugly.

---

### Post by ConnyBK on 2007-06-21
> **Major_Kong said:**
> Use gconf-editor. Then go to system > gstreamer > 0.10 > audio > profiles. Edit the profile there.

If I look into gconf-editor as you suggest the MP3-profile is there. But I cannot choose this profile if I open Sound Juicer as normal user. If I open SJ with sudo I can choose the MP3-profile and I can rip the CD as MP3 without problems.

So there seems to be a rights problem somewhere...

---

### Post by Major_Kong on 2007-06-21
Yes, that is weird...


Stupid question: You did check the active box, right ? (sorry, for asking...)

---

### Post by ConnyBK on 2007-06-22
> Stupid question: You did check the active box, right ? (sorry, for asking...)

Yes the active box is checked (would have been my first question, too...). 

And if I use sudo for calling SJ I see the profile and I can choose and use it.

---

### Post by Major_Kong on 2007-06-22
Gstreamer-ugly and the multiverse variant installed ?

---

### Post by ConnyBK on 2007-06-22
> Gstreamer-ugly and the multiverse variant installed ?

Both of them are installed. And as I already wrote: with sudo sound-juicer everything works fine. I can choose the MP3 profile and I can rip the CD as MP3...

---

### Post by dorakyura on 2007-06-22
Hey everybody,

I'm having exactly the same problems, i.e.

- the "parent window"-bug (which is easy to ignore either by closing it or by using gconf-editor), but more severe
- the "SJ doesn't like lame as long as I'm an unprivileged user"-problem ;)

Every attempt to correct the latter failed: The – as far as I gathered – critical gstreamer plugins ugly and ugly-multiverse are both installed. Maybe it really is a permission problem. Hopefully someone is able to pinpoint the problem.

cheers,
Tobias

---

### Post by ConnyBK on 2007-06-22
The problem seems somehow related to other installed software. 

I've installed a new Ubuntu Feisty on a virtual machine and only installed gstreamer0.10-plugin-ugly (multiverse) on it. With that system Sound Juicer worked as it should do (i.e. as "normal" user and not only with sudo).

---

### Post by Major_Kong on 2007-06-22
Try to reinstall sound juicer. (out of ideas...)

---

### Post by dorakyura on 2007-06-22
Forgot to mention: Tried that as well (as you already said: that's what you do when you're running out of ideas ;-) – several times actually ... I even tried an edgy version of SJ ... to no avail.

---

### Post by Major_Kong on 2007-06-23
> **dorakyura said:**
> Forgot to mention: Tried that as well (as you already said: that's what you do when you're running out of ideas ;-) – several times actually ... I even tried an edgy version of SJ ... to no avail.

See if you can find more recent Sound-Juicer packages.

---

### Post by dorakyura on 2007-06-23
I appreciate the suggestion, Kong. However, "newer" packages would mean to get them from gutsy and that in turn would cause some other dependencies to be installed. Seeing that gutsy is still unstable I don't want to mess up my stable work system.

I considered compiling it from source for a moment – but seeing that version 2.16.3 is the most recent I didn't see much use in that either.

After all there is a way to make it work. Not that it's beautiful, but it works ;)

---

### Post by Gweeper64 on 2008-06-30
Well, here we are one year later, and this STILL seems to be a problem in Hardy (at least for me, where I did an upgrade from Gutsy to Hardy). No matter what I do, I can't create/edit new options for "output format". Has anyone figured this out yet?????

---

