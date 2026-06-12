---
title: "What is the best production program"
date: 2007-07-26
forum: Multimedia Production
---

### Post by toddbmobile on 2007-07-26
I am running Ubuntu 7.04. I want to be able to create videos in .avi, .mpg, .wmv from inputted formats such as .avi, .mpg, .wmv, or pictures, and be able to add audio comantary, text, and graphics over the video. I guess a program something like Adobe Premiere.

---

### Post by MrFSL on 2007-07-26
Good Luck!

I suppose I would have to say "Kino" but then I heavily rely on ffmpeg and mencoder from the CLI. I have heard things about "cinerella" but I have never gotten it working well. Pitivi is useless (IMHO). I would tell you to grab avidemux... but it won't really give you what you want either.

I've been looking for awhile and that's why I am so negative.

---

### Post by toddbmobile on 2007-07-26
Thank you for the reply. I loaded "Kino" I'll give it a whirl. Yes, the other programs you mentioned I hear are bears to install and get working. Have you ever used stopmotion? Id like to make animations from pictures but the last time I tried using stopmotion it crashed every time you opened it.

---

### Post by Cryophallion on 2007-07-27
You might also try kdenlive. It is the only program (other than the discontinued main actor, which you had to pay for, and is no longer available anyway - I was going to buy it, but 3 days later it gets killed) that offers the razor tool. They are working on v. 0.5 right now, which will add more titling support, but they do allow you to import titles from gimp, etc.

Cinelerra is ok, if a little buggy, but the workflow for me left something to be desired (I also used premiere for quite a long time).

I have had very little luck doing fluid editing in lives, jashaka, pitivi, etc. Kino is great for importing video, but is a little too basic for a person used to premiere. kdenlive is definitely your best shot.

[www.kdenlive.org](www.kdenlive.org)

---

### Post by Red Moose on 2007-07-29
What about [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage")?

---

### Post by luisbg on 2007-07-29
MrFSL: why do you consider PiTiVi useless?

luisbg

---

### Post by MrFSL on 2007-07-29
@luisbg

Are you really asking me this question? I just installed PiTiVi v0.10.3 to see if I had missed out on some major improvements in a more recent release.

I imported 3 small video clips... 2 where in Apple Quicktime (.mov) format and one was a DIVX (mpeg4) format created by ffmpeg.

My first complaint is... what does PiViTi do? Compare this program to iMovie on Mac or Windows Movie Maker on Windows and you will see that this software is 99% lacking in functionality. So I can string my movie clips together in whatever order I would like and encode them off as one file. This simple is not that impressive and is much faster to do at the CLI using simple 'cat' commands or ffmpeg or mencoder or mplayer etc.

I won't even compare this software to pay-cash-for products such as Magix and Adobe Premier (or even the less expensive Adobe Premier Elements):
[http://site.magix.net/english-us/home/video/movie-edit-pro-12/](http://site.magix.net/english-us/home/video/movie-edit-pro-12/)
[http://www.adobe.com/products/premiereel/](http://www.adobe.com/products/premiereel/)

FURTHERMORE: After dragging my video clips to the time-line I tried to reorganize them and this made PiViTi crash! After that I tried to import a photograph to use in my movie and this made PiViTi crash. I tried every format I could think of and all of them made PiViTi crash. I opened PiViTi and then tried closing it (having done nothing in the program whatsoever) and PiViTi crashed... I mean seriously?

The above really is not a good assessment. I honestly feel that I could do a much better comparison which even included some off-the-wall "bargain-basement" applications in Windows and Mac and PiViTi would still be just as feeble, just as feature-less, just as unstable, and (as I originally said) USELESS (In my opinion that is).

---

### Post by BobSongs on 2007-07-29
> **MrFSL said:**
> @luisbg

Are you really asking me this question?<snip>

</snip>The above really is not a good assessment. I honestly feel that I could do a much better comparison which even included some off-the-wall "bargain-basement" applications in Windows and Mac and PiViTi would still be just as feeble, just as feature-less, just as unstable, and (as I originally said) USELESS (In my opinion that is).

[FONT=Verdana] Okay. Over here at BobSongs labs I've just opened up the mysterious PiTiVi. Here are some of the interesting effects I've noted so far:
[/FONT][LIST]
[*][FONT=Verdana]Adding a clip (DivX .avi file of 175 Mb) by dragging it to the application did not cause PiTiVi to crash. In fact the film began to play in the viewer area flawlessly (no skips, hiccups, burps or any other sign of indigestion). The odd thing is that the green [/FONT][FONT=Verdana][COLOR=Lime]**<play>**[/COLOR][/FONT][FONT=Verdana] button lights up but the rest... don't and are non-functional. Very weird.[/FONT][/LIST][LIST]
[*][FONT=Verdana]However adding a second clip by dragging it to the application partially failed. It merely "pushed out" the first in order to allow me to "edit" the second.  This does not appear to be how it was supposed to work though (it would appear that one would be merging several films together). But only one clip can be edited at a time. The option to import an entire folder is what clued me into this as a failure.[/FONT][/LIST][LIST]
[*][FONT=Verdana]Dragging in the same way TWO film clips together resulted in only the importing of the first film.[/FONT][/LIST][LIST]
[*][FONT=Verdana]Adding clips to form a list of editable clips fails:[/FONT][/LIST][INDENT][LIST=1]
[*][FONT=Verdana]Clicking the <Add> button in the main windows opens the file manager. A file is selected, the <Add> button is clicked and... nothing happens. I wait and give the application time to load the film. No go. So I click <Cancel> to make the "Import a File" dialog box to vanish.[/FONT]
[*][FONT=Verdana]I click the <Add Folder> button with exactly the same results.[/FONT][/LIST][/INDENT][FONT=Verdana]While I haven't experienced the same level of failure I haven't had much success with it. I will now attempt to cut the film apart and see how PiTiVi stands up to that challenge.

Editing
All I can say is: weird. With just one file dragged to the windows (and the film is playable) expanding the video and audio bars underneath results in the software displaying no video or audio content. So, I cannot edit it. There are no visible tools to do so even if I could. While I'm not getting the crashing MrFSL has experienced, I must admit that my preliminary experience with the software is extremely disappointing. Even more so in light that I'm experienced with iMovieHD (flawed as much as that program is).

Edit:
System: UbuntuStudio Feisty Fawn
RAM: 512 Mb
Processor: Celeron 1.7 Ghz
Video card: NVidia GeForce 2 MX 400 using proprietary drivers.
[/FONT]

---

### Post by toddbmobile on 2007-07-31
Cryophallion do you know if KDEnlive will work with Ubuntu (Gnome)? Is there an order for the .deb packages in the .zip file you get from KDENLIVE.org.

---

### Post by stmiller on 2007-08-02
[LiVES]("http://lives.sourceforge.net/") lets you do text overlay, and tons of other effects. It's in the apt-get repos I believe. Check it out!

---

### Post by Red Moose on 2007-08-02
I just heard of LiVES the other day and I thought, "Why haven't I heard of this before?!"
I'm going to download it as soon as I can.
I sure hope it's as good as it looks!

Open Movie Editor is a pretty good simple movie tool, but it wasn't very stable in Gusty.

---

### Post by Cryophallion on 2007-08-04
> **toddbmobile said:**
> Cryophallion do you know if KDEnlive will work with Ubuntu (Gnome)? Is there an order for the .deb packages in the .zip file you get from KDENLIVE.org.

Yes, I run it under gnome on several computers.

If I remember correctly - Mlt, mlt++, kdenlive

When you open the debs, they tell you the dependencies up top (at least in gnome), so you can kind of do a process of elimination that way too.

Good luck, let me know if I can help any more. Their forums are very good also.

---

### Post by dabl on 2007-08-05
Cryophallion, have you installed Kdenlive on a 64-bit Ubuntu system?  I'm getting a "lame not found" error (actually this is in the mlt phase of installing).  I've removed and reinstalled lame twice -- it's here.  But the mlt stuff isn't seeing it.  :confused:

---

### Post by Cryophallion on 2007-08-05
I have not. You might want to try installing from source in that case. I believe someone on the kdenlive forums has a script to do all of it for you, although I have found installing from source easier than I expected.

---

### Post by dabl on 2007-08-05
> **Cryophallion said:**
> You might want to try installing from source in that case. I believe someone on the kdenlive forums has a script to do all of it for you

Got it -- thanks.  I'm off to the kdenlive forums. :)

---

