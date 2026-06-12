---
title: "dvd-video creating problem"
date: 2008-05-26
forum: Multimedia Software
---

### Post by asipi on 2008-05-26
Hi,

In advance let me say I often have to make short dvds for presentations at my workplace. One month ago I upgraded to Hardy. Unfortunatelly I did not need to make dvd until last friday, and the nightmare has begun...

With Feisty (and as I remember with Gutsy too) I could make my dvds with K3b at any time without any problem.

I use qdvdauthor or simply dvdauthor to create the video folder structure. To achieve this prior I use mencoder to prepare the video files so I have practice to do this process.

Last friday I made the encodings (3 files) ran dvdauthor to make the folder structure and burn a disc with k3b as dvd-vide project. I checked back the result with kaffeine, it worked well. Then I gave it to my boss and he called back me that he was unable to play it (OMG!) with a normal dvd-player box.

I thought "hey WTF happened?" and started to investigate the case.

I have read man pages of dvdauthor, growisofs, genisoimage again if I missed something or if the current k3b version had bug related to the dvd video discs.

I made a very simple xml for dvdauthor and burn the disc from the commandline with growisofs.

Wasn't a success, dvdplayer still says it is unsopperted format.
I used a dvd+rw disc for testing to spare with discs (the first was a dvd-r media).

Remarks: I have more dvd+rw discs what I made with the same burner drive what are work well. I made them with feisty. I use the kubuntu releases but I guess the cli tools are the same in all versions.

My tip is that the current versions of the tools had problems...

Do you have any idea how to continue?
Any help would be appreciated.

---

### Post by ingrid_ozikem on 2008-06-07
Similar problem... K3B creates a video disc (either from VIDEO_TS directory structure or from an ISO image).. plays well in any Ubuntu program (VLC, Totem etc etc)

but open it in Windows and it sees an empty disc. (It also calls the disk as UDF format.. not sure if this is a bad thing).

Is there some command line option for growisofs or mkisofs or whatever we are all missing??

is it -dvd-compact or -dvd-video?

---

### Post by reiki on 2008-06-08
In Hardy, *something* is definitely broken when it comes to actually creating the DVD. I have run into similar issues using tovid/todisc and then makedvd. The result in any player other than the one on my computer is "unsupported".

If I do all of the preparation work in Hardy as far as any ripping I need to do, and any conversions (like AVI to mpeg) and even as far as having todisc create the disc structure and menus... all is well.

But I have to boot to Gutsy to burn that DVD. So I'm booting to Gutsy just to run makedvd -burn

In Hardy again once I have a DVD mastered, I can use GnomeBaker to make a copy to iso and then burn those iso to DVD with no problems at all.

---

### Post by cotcot on 2008-06-08
I had a similar problem with a VIDEO_TS made by devede. Qdvdauthor is working well.

Maybe check if the dvd you burned was closed. It might be that the dvd does not get closed when there is not enough free space. I has this issue with a dvd with 2 hours and 3 minutes video on it.

---

### Post by ingrid_ozikem on 2008-06-08
Hey cotcot!

 That sounds like that might be the problem! I'm experiencing the same problems as above and notice that Windows shows the problem DVDs as DVD+R instead of DVD+ROM which is used for DVDs that do work.

 I was using K3B or DVD95 which create an image just large enough to fill a 4.7 GB disk.. so how do I finalize it? How do I finalize a DVD I've already created? Is there a command line option with growisofs or mkisofs or something? K3B annd other GUIs dont seem to give me the option directly...

---

### Post by cotcot on 2008-06-10
Not as far as i know. I burn them with k3b. K3b closes automatically.

---

### Post by ingrid_ozikem on 2008-06-11
@cotcot,

So you burn using K3B in Hardy and the DVD plays  in Windows / set-top boxes?

Do you burn an ISO image or a directory structure? (I've tried both without success..)

Thanks!

---

### Post by alegallo on 2008-06-19
I guess it is a genisoimage bug in version 1.1.6-1ubuntu6, which ships with hardy and replaces mkisofs

A solution has been found here:

[http://ubuntuforums.org/showthread.php?p=5217002#post5217002](http://ubuntuforums.org/showthread.php?p=5217002#post5217002)

---

