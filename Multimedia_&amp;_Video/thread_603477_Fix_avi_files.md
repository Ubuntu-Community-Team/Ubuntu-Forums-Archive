---
title: "Fix avi files?"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by shavenlunatic on 2007-11-05
Hi,

I recently downloaded a divx video, there seems to be a couple of corrupt frames (or the indexing is screwed or something) which causes mplayer to not error as soon as it hits a problem (about 10 seconds in).

VLC can play it, it prompts me with the option of "fixing" the video file, it rebuilds the index and starts playing.. but vlc doesn't give me the option of saving the fixed file so neds time I come to open the file I get the same issue (the reason I want it fixing is so I can watch it on my media box)

I thought avidemux would be a good place to start but unfortunately it won't open the file as it is corrupt.

This lead me to wondering if there was a linux equivalent of the avifix software I used to use in windows which rebuilds and reindexes (can you tell I don't know what i'm talking about yet? lol) the avi file and away you go, other than the dodgy frames going a little wobbly the files used to play ok without halting.

Any ideas?

---

### Post by revilodraw on 2007-11-05
Since my upgrade to Gutsy, some avi files are haywire in VLC. Hopefully we will find a fix.

---

### Post by shavenlunatic on 2007-11-05
aye, but VLC was the ONLY software which would play the corrupt .avi file so in this instance, VLC wins :)

it's the actual video file which needs fixing, the players are working fine

---

### Post by shavenlunatic on 2007-11-06
*bump*

---

### Post by shavenlunatic on 2007-11-06
i guess this is score 1 for windows then eh?  i'll have to bite the bullet, boot into XP and run avifix?

i get home from work in 2 hours.. please save me from booting into windows! Help me obi-wan, you're my only hope

---

### Post by harold4 on 2007-11-06
Didn't look to see if there is an alternative, but you could try running avifix in wine.

---

### Post by PowerPanda on 2008-01-25
There is DivFix++ [http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/divfix++_0.26+3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/divfix++_0.26+3v1ubuntu0_i386.deb")
Or newer version on their site 
[http://divfixpp.sourceforge.net/home.htm]("http://divfixpp.sourceforge.net/home.htm")

---

### Post by leprasmurf on 2008-02-08
Came across this thread because I have a bunch of avi files that I need to fix.  The following info came from [http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html#fixing]("http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html#fixing")

7.5 Fixing AVIs with broken index or interleaving

Easiest thing. We simply copy the video and audio streams, and MEncoder generates the index. Of course this cannot fix possible bugs in the video and/or audio streams. It also fixes files with broken interleaving, thus the -ni option won't be needed for them anymore.

Command: mencoder -idx input.avi -ovc copy -oac copy -o output.avi

---

### Post by mixtri on 2008-04-18
Can anyone help please. I mistakenly deleted a number of avi video files from my HD today. I have been able to recover them from ubuntu partition on my hard-disk using photorec via my winxp dual boot.

The only problem now is that the files are broken and possibly corrupt.
The files have been restored to the original sizes they were before they were deleted, but now cannot be played in VLC or any other media player.

I understand DivFix++ may help.
I have just downloaded and installed from a link provided by somebody on this thread using package manager. 
My question is, where do I locate the file on my system and how do I run it?
Its highlighted in synaptic package manaGer, but I can't seem to find the program in the Applications menu or anywhere else.

I tried typing divfix++ in a terminal and that does'nt work either.

I'm using gutsy 7.10.

Also, could anyone advice if it there is a program that identifies broken/corrupt files,  which will then attempt to download and replace the broken/lost fragments of the video files without me having to download them again. there are 72 files each an average 350 Mb.
Please help, it took me a week to get these files using Deluge and I do not want to go through that again.

Thanks in advance

---

### Post by mixtri on 2008-04-19
can anyone help? please see previous posting by me

---

### Post by cor2y on 2008-04-19
never heard of divfix++ but you can use avidemux to repair the file and then save a new version as well as mencoder from the terminal to re-index the file and save a new copy.

---

### Post by mixtri on 2008-04-19
Thanks Cor2y.

i just had a quick look at Avidemux.
Its doesn't seem like its going to do what I want.
I need a program that will not only fix broken/corrupt files but also download missing fragments and patch up the files. 
Do you know anything that will do that. As you know cutting and joining video files means you will miss bits from it.

Also could you advise where to find programs on Ubuntu that I have downloaded and installed using package manager.

I can't seem to find programs i installed. i have looked in the obvious place -  Applications and also did a search but can't seem to find them. 
I know the files have been installed as I can see it checked in synaptic.
Any clue?

---

### Post by cor2y on 2008-04-19
look in your /usr/local/bin folder.
If it was installed with the deb package manager rather than synaptic it should be in the /usr/local/bin folder.

As for downloading missing bits no clue.
The only apps that come close to what you need that i know of are par files that can repair incomplete files or the repair an archive function found in rar/winrar.

---

### Post by mixtri on 2008-04-19
Thanks again.
However, I just checked the /usr/local/bin folder and guess what, its not there.
Very strange indeed.
Could there be some other place perhaps?
It's surprising, when i right clock on the file in synaptic then properties, it doesn't tell me where its located. its got a green shade against the checkbox
Do you think I should reinstall.

---

### Post by mixtri on 2008-04-19
Ok, don't threat, I've found it in usr/bin folder.

---

### Post by swegner on 2008-05-06
Thanks for the mencoder link.  I was having trouble with some AVIs from DVDs I backed up using dvdrip.  Using mencoder seems to be doing the trick.

---

### Post by snktagarwal on 2008-06-04
Hi all......... u can do this too! First let VLC repair the file fo you..... then u can captue the whole stream!!! This is similar to capturing(saving) a broadcast from some cable, or LAN so u would have variety of options with the formats..... i have tried it with a proper file.... but there's no reason it won't work with broken too..... cause the stream works all right!!!!

---

### Post by richardjennings on 2008-07-19
I had a broken avi. Been looking for a native solution for a few weeks & found this thread. Installed [http://3v1n0.tuxfamily.org/pool/feis...untu0_i386.deb](http://3v1n0.tuxfamily.org/pool/feis...untu0_i386.deb)

DivFix++ ran the program, drag / dropped file, clicked fix - worked. Took all of 10 seconds. Excellent program! Suggest it deserves to be in the multiverse repository.

---

