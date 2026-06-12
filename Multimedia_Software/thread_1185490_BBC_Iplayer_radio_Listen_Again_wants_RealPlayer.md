---
title: "BBC Iplayer radio Listen Again wants RealPlayer?"
date: 2009-06-12
forum: Multimedia Software
---

### Post by candtalan on 2009-06-12
This is wierd. I use bbc listen again (radio) a lot, and have only just recently begun to have problems. Both in 8.04.2 and 9.04

An example of how crazy things are is
[http://www.bbc.co.uk/iplayer/episode/b00ks1kx/You_and_Yours_12_06_2009/](http://www.bbc.co.uk/iplayer/episode/b00ks1kx/You_and_Yours_12_06_2009/)
which gives access to three episodes of (you and yours).All are offered in Listen Again facility. The oldest one plays ok. 
The two more recent ones bring up a message that RealPlayer has to be installed first.

!!

Ok, what the hell? I installed realplayer. And what do you know? it still did not work.

Is it possible to identify what th eproblem really is please?

The sad thing is I really want to hear the latest episode (item on prostate cancer). 

So I am actually going now to try and find a windows machine and use firefox on that!

---

### Post by drs305 on 2009-06-12
candtalan,

I was interested in your post as I recently updated the RealPlayer [wiki]("https://help.ubuntu.com/community/RealPlayerInstallationMethods").

I visited the site you referenced and got the same "Install RealPlayer" message. I have contacted the BBC to call their attention to this error. The BBC, RealPlayer and Linux have had longstanding issues, although I thought they were slowly being resolved.

I haven't found a workaround to this latest setback but will post a solution here if I find one.

Added: I tried running this link in MoviePlayer and the failure is the same on both: lack of an encoder for text/html;charset=utf-8. I am still searching for an answer.

---

### Post by candtalan on 2009-06-12
Thanks
I hav etried to post s message on the Radio message boards, but after logging in with Ubuntu and FF I do not get a working 'start new topic' window!

I have just seen this on their site:
fwiw:
[http://iplayerhelp.external.bbc.co.uk/templates/bbciplayer/seo/feedbackSubmit](http://iplayerhelp.external.bbc.co.uk/templates/bbciplayer/seo/feedbackSubmit)

* Announcement: BBC iPlayer availability on 11 June 2009
* Announcement: We have recently upgraded BBC iPlayer. BBC iPlayer Desktop now replaces Download Manager. click here

What a PITA!

---

### Post by MickS on 2009-06-12
I just found the same problem, tried installing the deb and it wouldn't have it, then I thought I would try installing it through Synaptic and that seems to have worked fine, listening to your item on prostate cancer right now so try installing through Synaptic NOT from the site.


Mick

---

### Post by candtalan on 2009-06-12
> **MickS said:**
> I just found the same problem, tried installing the deb and it wouldn't have it, then I thought I would try installing it through Synaptic and that seems to have worked fine, listening to your item on prostate cancer right now so try installing through Synaptic NOT from the site.Mick
thanks

Tried it with ubuntu 8.04.2, no joy, same response. Will try it with 9.04 and maybe 8.10 later, must go  now. thanks again.

---

### Post by candtalan on 2009-06-13
Possible workaround:

Another thread about Firefox crashing (ubuntu 9.04) may help also with some clues for the problem.

BBC Iplayer crashes firefox:
[http://ubuntuforums.org/showthread.php?p=7449891#post7449891](http://ubuntuforums.org/showthread.php?p=7449891#post7449891)

In ubuntu 9.04 at least, which has the FF  crashing problem, that thread has offered a solution to the FF crashing. However, when I removed 
mozilla-mplayer plugin and replaced it with gecko-mediaplayer, not only did the FF crashing cease, but I could now play the particular troblesome ListenAgain BBC radio items!!

horay!

note: I did notice that when closing FF it tended to hang, and  needed force quit at least once. But hey, I can hear bbc stuff. Great!

---

### Post by wrathkeg on 2009-06-19
just in case it's relevant:  trying to use listen live facility on the BBC site,  I got the message about needing RealPlayer.  I donwnloaded RealPlayer from the Real site and installed it.  Restarted Firefox, went to the BBC site, and still got told that I needed RealPlayer.  I ran RealPlayer from the command line, and this took me through various set-up stages for RealPlayer, including configuring Firefox for using RealPlayer.  The BBC listen live facility now works for me (for the moment at least!)
WK

---

