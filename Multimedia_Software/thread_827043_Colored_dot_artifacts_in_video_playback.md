---
title: "Colored dot artifacts in video playback"
date: 2008-06-12
forum: Multimedia Software
---

### Post by xaris106 on 2008-06-12
Hello, I am a new ubuntu user and I have been using it for a few days.
My problem is that when i playback .avi video files in any media player (tried vlc, mplayer, totem) and even .ogm files i get weird red green and blue dots poping around.Like old vhs movies or something similar. i have tried different files working great in windows with same results.
I have this problem from the start and tried disabling compiz and using other drivers for the nvidia card i use (8800GT) but no luck. the weird thing is i dont get those artifacts in HD video files (eg 1280x720, h264, .mkv files)
I also searched for an answer in the forums and google but couldn't find anything similar.
I'm sorry if this is answered somewhere but i couldn't describe the problem well and search for it.
i would hope for a fix to this problem or how i can search for it(eg how this problem is called)

thanks

---

### Post by xaris106 on 2008-06-12
bump. noone else has /had this problem?

---

### Post by Pjotr123 on 2008-06-12
Disable visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

Make sure you have all the codecs:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and then:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by xaris106 on 2008-06-12
Thanks for the help.
But I already have done all this.
I can play any media file, i think, even encrypted DVDs with VLC and autoplay.
I disabled the desktop effect but i still have the same artifacts.
i just checked and also DVDs have the same artifacts. Its not that bad , I can watch a movie nicely and if i go a bit far i can hardly see those dots, but still they are there and i hoped i could get rid of them. After all they aren't there in windows xp.

They might be hard to spot if you dont pay much attention to it i must admit. Can someone watch a video and see if he can see those small colored dots?

Again thanks for the reply

---

### Post by xaris106 on 2008-06-12
Ok I searched a bit more and found out that I have the exact same problem with this [http://ubuntuforums.org/showpost.php?p=1223650&postcount=1]("http://ubuntuforums.org/showpost.php?p=1223650&postcount=1")

the picture shows the exact same problem.
Sadly no fix..any ideas?

---

### Post by xaris106 on 2008-06-13
bump again

---

### Post by xaris106 on 2008-06-25
bump again again. what could cause this? could it be the decoder?how can i test the decoder?

---

### Post by xaris106 on 2008-06-29
help guys i have tried everything and tose dots persist. here is how it looks. those dots pop and vanish everywhere on the video..

[[IMG]http://www.imageshack.gr/files/vbg0zojjtzm9p9idtete.png[/IMG]](http://www.imageshack.gr/view.php?file=vbg0zojjtzm9p9idtete.png)

---

### Post by xaris106 on 2008-07-02
bumping again.this guy has the same problem but mine only happens in ubuntu. 

[http://ubuntuforums.org/showthread.php?t=215965&highlight=colour+artifacts]("http://ubuntuforums.org/showthread.php?t=215965&highlight=colour+artifacts")


when i boot in win xp videos wotk great . also i tested win xp in virtualbox on top of ubuntu and videos work great there too.

please help

---

### Post by TheHappyEater on 2008-07-05
> **xaris106 said:**
> bump. noone else has /had this problem?

I do. So: Bump.

I have the same problem, even when I'm watching png and jpg files. I have an ATI Radoen 1950X graphics card. 
Perhaps there is something wrong with my (our?) driver? Which driver is recommended with this card? 

I have those blue dots when watching videos, pictures and when playing a game with 3D graphics (neverwinter nights). In spite of that, GNOME itself shows no problems and with my windows XP I have no problems, either.

---

### Post by UncleX on 2008-08-28
Hi,
I have since a few weeks exactly this problem, the same I see in the screendump with blue dots on this formum.

I get blue and red dots during video playback. I use the K-Lite mega codec pack.

I know it happened since Microsoft updted their DRM (Digital Content Management) becouse hackers hacked it.

Problem is, this happens also by non DRM protected files all my video's have this problem now. Most are not DRM protected. (You can check that in media player, press properties on playing file last tab)

So I get the same corruption on non protected files as on protected files.

Probably Microsoft does not like you to use other codecs, for DRM purposes. But it might be just a nasty bug in the DRM system.

I don't know what the cause, but I do know ocassionally I get the blue screen of death pointing to my NVIDIA driver, during video playback.

If anyone has a better conclusion, lost of people have this problem now. I need a fix I cannot normally view any video without the risk of blue death.

And all Video's are corrupted with blue red dots even home made video's, surly they can't be DRM protected. :mad:

I just want to view my video's....

Uncle X

---

### Post by UncleX on 2008-08-28
I have included a screendump of the same problem while playing a movie.

So it is a problem not bound to a single user.

My system is up to date, latest drivers bios windows updates and latest K-lite mega codec pack.

My system is always very up-to-date, so it must be a problem with one of the updates.

Witch one that is the question, I could then uninstall this update.

Unfortunate my system restore does not go far back enough for me to check.

I bet it is the DRM fix update from Microsoft. If I just new the KB article, I could then unistall this update.

Uncle X

---

### Post by UncleX on 2008-08-28
DRM of course being: Digital Rights Management.

DRM is soooo bad, a virus like copyright protection system linked to files.

Microsoft is gone crazy.... Protecting the RIAA, instead of the paying Microsoft customers.

That whle forcing mediaplayer like this gave them a multi-million dollar EU fine cause it is illegal.

Media player in Windows is illegal, DRM in mediaplayer is thus also illegal.

Talking about rights....

But now DRM scrambling my legal and even selfmade pictures with red and blue dots.....While I uses a mediaplayer not from Microsoft.....

Harms customers with legal files also, why should I have blue red dots and system crashes while watching a unprotected file??? In a not DRM supporting mediaplayer not from Microsoft???

Microsoft this needs to be fixed. It will result in another multi million dollar EU fine.

---

### Post by UncleX on 2008-08-28
Hey!

I fixed the problem! And stopped DRM (Digital Right Management) in Vista x64 (It might work for Vista also)

How to proceed:
-In folder options un-check "Hide protected operating system files"
-Goto c:\ProgramData\Microsoft\
-From this folder a folder DRM must now be visible, delete the folder. Then replace folder by file included in the zip file.
-It will be hard for media player to re-make the DRM folder now.
-Uninstall K-Lite and other codec packs.
-Delete the codecpacks folder(s), from the program files folder.

Now the blue red dots are gone in windows media player. And I can even play protected files with no visual artifacts. In Media Player 11.

I have not tried re-installing K-lite codec pack, but I will now and post my findings.

For now the dots are gone, but so is my codec pack.

DRM is disabled!! How easy a hack can be...... It is never hard to make someting stop functioning... LOL I'm good in demolition!

Uncle X(NL)

---

### Post by UncleX on 2008-08-28
Ok,
I now tried reinstalling K-Lite codec pack. Red dots are back again. 

I uninstalled K-Lite codec pack, red dot gone.

Well since I can now play DRM protected content by above trick.

Who needs K-Lite codec pack??

I just wait for a new version of the K-Lite codec pack. For now I keep it un-installed and use Windows Mediaplayer 11 with no probs!!

The problem lies in K-Lite codec pack, caused by a recent update of DRM.

It's fixed for me now! And DRM does not spy on me anymore!

Uncle X

---

### Post by UncleX on 2008-08-28
K-Lite codec pack now also usable.

Re-installed with lots of options.
Selected (Use System default) where possible.

Great:
- DRM "fixed".
- Red Blue dot problem gone
- KLR Codec still usable

I'm a trouble free computer user again....

Uncle X(NL)

---

### Post by UncleX on 2008-08-28
Update KLR codec pack still causes dots only reduced.... I just noted.

And with it mediaplayer 11 does funny without it I can even play DRM protected content.

---

### Post by brendanpiater on 2009-01-02
Hi All,

Was wondering, how in the blazers you got DRM working. Can you confirm a few quick steps and your set-up? Been trying for ages to help out a friend who I converted to Ubuntu, but the one issue we having is that he gets some his football highlights in DRM format...it's a big issue for him.

Thanks in advance!

Regards
Brendan

---

