---
title: "Totem Movie Player mp3 scrolling issue"
date: 2011-09-19
forum: Multimedia Software
---

### Post by binzing on 2011-09-19
Can anyone help me figure this out? Even if there's no solution, I'd at least like to know a reason. So for my main music player I use Rhythmbox, which works pretty well, despite a few occasional hiccups (any suggestions as to something better are totally welcome) but when I'm downloading new mp3s to my desktop and I want to check them out I normally just click on them and have them open in Totem. Now sometimes I don't want to listen to the whole track and I'll just skip forward on the play bar to whatever point in the song. But here's the issue. By and large it will let me do as I please, but for some reason some mp3s (which, as far as I can tell are totally the same as the rest of mine) won't let me advance the song in that manner. Does anyone else experience this, know the cause, and/or a solution? Thanks so much.

---

### Post by mikewhatever on 2011-09-19
That probably happens because you try listening to the part of the file that hasn't downloaded yet.

---

### Post by binzing on 2011-09-20
No, these are downloaded files...

---

### Post by mikewhatever on 2011-09-20
> but **when I'm downloading** new mp3s to my desktop and I want to check them out...

You have to decide which it is, cause it doesn't say downloaded above.

---

### Post by binzing on 2011-09-20
Ok, disregard the WHOLE statement about downloading... If I have a single mp3 I want to listen to, as opposed to firing up Rhythmbox (or if the file is on my desktop as I described, and so doesn't show up in Rhythmbox's library) I will use Totem. Now, some files play just fine and allow me to skip wherever I choose, and others won't budge, they'll only play forward from the start. Now, does that clear things up? Any ideas?

---

### Post by dniMretsaM on 2011-09-20
It's possible that it has something to do with the codec that was used to encode the file? You might check the metadata to see if it lists a codec. If you see a pattern (i.e. the ones that use x codec don't support fast forwarding), that's most likely your problem. The next step would probably be a bug report. If that's not it, you could (a) Right click on the file and open with Rhythmbox. I don't think that imports it to the library. If you choose this method, you can set that as the default method for opening MP3 files. (b) You could try a different media player like VLC and use that instead of Totem. (c) Use a different media format like Ogg Vorbis (<- better than MP3 in a lot of ways). Or (d) wait for someone smarter than me who can give you a helpful answer.

As for some other default media players to try, here's a small list:
[QUOTE=Tech-Freedom (my blog)]Amarok
Banshee
Clementine 
Exaile
gmusicbrowser
Guayadeque
Xnoise[/QUOTE]

---

### Post by binzing on 2011-09-21
Thanks! I'll look into the metadata. As far as formats, I'm just stuck on mp3s because thats what I download everything as, and for issues of compatibility with this funky mp3 player I have.

---

### Post by binzing on 2011-09-22
The only difference I noticed between songs that allowed me to skip and those that didn't was different bitrates. If anyone has any ideas, I'd love to hear them. Thanks all!

---

### Post by MakOwner on 2011-09-29
> **binzing said:**
> The only difference I noticed between songs that allowed me to skip and those that didn't was different bitrates. If anyone has any ideas, I'd love to hear them. Thanks all!

Yea, what the heck??  I had mp3 files that allowed me to fast forward and reverse, but in the last two days none of them will fast forward or reverse.

There was a kernel update in the last couple of days, along with a lot of other packages - did that do it?

---

### Post by MakOwner on 2011-10-05
Hello?
Anyone have any idea?
I have mp3 files that will no longer fastforward/reverse in totem, but will just fine in mocp - "music on console" player.

---

### Post by Gareth_2007 on 2011-10-05
i have the same problem! some you can skip through some you can't! all the same format

---

### Post by MakOwner on 2011-10-05
> **Gareth_2007 said:**
> i have the same problem! some you can skip through some you can't! all the same format

I haven't found any I can scroll with -- and most of them could scroll prior to the last Ubuntu update. 
They all appear to be streaming content to totem.

---

### Post by Gareth_2007 on 2011-10-05
yeah ill agree with that! the problem started around that time

---

### Post by MakOwner on 2011-10-05
If you find this thread first when looking for an answer, go here: [http://ubuntuforums.org/showthread.php?p=11313660#post11313660](http://ubuntuforums.org/showthread.php?p=11313660#post11313660)

---

### Post by Gareth_2007 on 2011-10-05
> sudo apt-get install ubuntu-restricted-extras

thanks

---

### Post by follencavale on 2011-12-06
Hello,

I have got the same issue here.
Most of the time, I can't scroll into my mp3s. But sometimes I can.
For sure: it doesn't depend on the mp3 file, but it's just random.

Actually, I am always playing the same mp3 file with Totem. Sometimes it works, many times it doesn't... :(

Do you have any clue? any log file i could check?

Thanks.

---

### Post by MakOwner on 2011-12-07
> **follencavale said:**
> Hello,

I have got the same issue here.
Most of the time, I can't scroll into my mp3s. But sometimes I can.
For sure: it doesn't depend on the mp3 file, but it's just random.

Actually, I am always playing the same mp3 file with Totem. Sometimes it works, many times it doesn't... :(

Do you have any clue? any log file i could check?

Thanks.

That was what was happening to me -- when I reinstalled the packages listed above, it corrected the issue.  Or at least it hasn't happened again.
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by follencavale on 2011-12-09
It doesn't work for me... :evil:
Anyway, thank you MakOwner.

---

### Post by MakOwner on 2011-12-09
> **follencavale said:**
> It doesn't work for me... :evil:
Anyway, thank you MakOwner.

That command is just the install.  You can force a reinstall or uninstall and install again.  It fixed my 10.10 install on a laptop.

---

