---
title: "Click repair vs Gnome Wave Cleaner ?"
date: 2010-07-29
forum: Multimedia Software
---

### Post by robert shearer on 2010-07-29
Any-one using the Linux version of Click-Repair ?
[http://www.clickrepair.net/software_download/clickrepair.html](http://www.clickrepair.net/software_download/clickrepair.html)

I have been trying Gnome Wave Cleaner but no matter how I configure it there is unacceptable deterioration of audio quality when used in any auto modes.

In the past I have trialled Wave Repair and found it acceptable though they have no Linux version.
[http://www.delback.co.uk/wavrep/](http://www.delback.co.uk/wavrep/)

Can I expect an improvement over GWC using Click-Repair ? for the outlay of some $$$, or is GWC the best I can hope for using Ubuntu.

Or, is it back to the tedious 'manual de-click' for every LP.

Your thoughts, and any GWC configurations, appreciated. :D

---

### Post by lykeion on 2010-07-29
Sorry I haven't tried GWC but it seems like an ambitious project. 
On the homepage there are lots of restoration tips, and you could also try to contact the author directly I guess.

I see that the version in the Ubuntu repository is not the latest, so you might have a look at the latest version 
and check the changelog for improvements made. 
You'll probably have to compile it manually, but it might be worth the effort.

And btw have you tried the noise removal in Audacity?

---

### Post by robert shearer on 2010-07-29
> **lykeion said:**
> 
On the homepage there are lots of restoration tips.

Been there tried that.
GWC is a fine app and used for **Manual** restoration is as good as any I have tried.
It, and most others, fall short when used in auto-mode.

Manual de-clicking takes soooo looonnngggg. Up to 8 Hours/LP.

I had heard reports on WinForums of acceptable auto-mode from Click-Repair and am interested to hear if users of the Linux version have the same to say.

> I see that the ( GWC ) version in the Ubuntu repository is not the latest, so you might have a look at the latest version 
and check the changelog for improvements made. 
You'll probably have to compile it manually, but it might be worth the effort.

Yes, though the one in the repo works with the Ubuntu sound server and the changelog does not warrant my changing distro for the minor improvements mentioned.

> And btw have you tried the noise removal in Audacity?

Yes and it is not of the quality of any of the others I have noted.

Thanks for your comments btw, appreciated.
Regards, Bob.

---

### Post by lykeion on 2010-07-29
The best noise removal I've used was a directx plugin called sony noise reduction, but that was of course in windows.
And although I prefer a *nix environment over windows for a lot of reasons, there are some areas where they don't deliver. 
And if you do professional sound editing I guess most people use mac.

Here are some links on vinyl restoration:

[http://jhau.maliwi.de/linux/lp2cd.html](http://jhau.maliwi.de/linux/lp2cd.html) 
(audio restoration using gwc)

[http://z80cpu.eu/mirrors/home.att.net/~halbower/music.html](http://z80cpu.eu/mirrors/home.att.net/~halbower/music.html) 
(same subject audacity & gwc)

[http://www.delback.co.uk/lp-cdr.htm](http://www.delback.co.uk/lp-cdr.htm)
(incl a discussion on noise removal software - just like me he concludes that Sony's plugin is among the best)

Another way to find a decent noise removal could be a VST plugin, because Audacity has support (though limited) for them.

---

### Post by robert shearer on 2010-07-29
Thanks for the links :).

The first two re GWC, I had tried their recommendations but the results were not sufficient to embark on the archiving project I face.

I am trying to find something that is both acceptable **and** predictable in its performance and associated artifacts before starting the bulk archiving.

I have used Waverepair some years ago in a Windows past and found it very pleasant and reliable but it would be a pain to have to record on my 'nix set-up then copy/move the files to Windows to process only to have to move back for the rest of the processes in 'nix.

I haven't found anyone using Waverepair with Wine, have you had any experience with it ?.

cheers,  Bob.

---

### Post by lykeion on 2010-07-30
Hi again
I just tried installing WaveRepair 4.93 with wine (v1.1-42) and it worked fine. I haven't tried WaveRepair before so but loading a wav file worked fine. Plus it also seems to have some kind of batch processing so that might be just what you are looking for.

I also checked winedb for reports on running CoolEdit in wine and it seems to work ok but with some errors. CoolEdit was a fine piece of audio software (before Adobe took over) and it has native filters for noise reduction and click/pop removal which I remember worked fine (although they were a bit slow). So if you can find an old version of CoolEdit this could be a way also.

---

### Post by robert shearer on 2010-07-31
Thanks for that.
I installed Wine and then downloaded Waverepair.

Unfortunately, when I try to install it with wine I get this...


 >  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.


Yet the file size is correct for the download.

If I try to extract it I get the same message.

EDIT.. booted to Ubuntu 9.04 and I was able to install Waverepair under Wine there.
Performance is laggy to the point of annoyance. Though the configuration options for declicking are superb.
If GWC had that sort of granularity it would be useful.

---

### Post by lykeion on 2010-07-31
I think the reason for the error message was that you tried to open the exe installer with the archive manager, possibly by doubleclicking it in Nautilus. 
You should try launching from the terminal (that way you can also see any wine specific errors during installation):```
wine wr493install.exe
```The system requirements listed by the author on the homepage doesn't indicate that you shouldn't need some supercomputer to run it. 
I didn't experience any slow performance - and my computer is relatively old - however I only tried loading and editing a wav file, not any recording.   

Do you have Ubuntu 10.04 installed or only 9.04? I think the wine versions are different and it might work better with a later version of wine. 
I seldom use wine myself but from my experience they seem to make it better and better for each new version.

---

### Post by 001robin on 2013-02-09
I have been running ClickRepair for several years now, and I have used  it to process the sound from approaching 100 LPs.  With care, all trace  of clicks can be removed, the sound is clearer, and there is no loss of  brilliance.  I am a big fan of ClickRepair.

I have found, though,  that it is best to use some manual intervention unless  you have a  really pristine LP.  Don't expect to let it run on fully automatic if  you want first class results.  ClickRepair is brilliant at correcting  faults, but not so good at selecting the best start and finish point for  each repair.   I find it best to set "automatic" to around 80 or 90.   This way the start and finish points for the worst clicks can be  adjusted manually before making the repair.  This way the repairs are completely undetectable.    I find it takes up to 1/2  hour to process an LP, sometimes more in a bad case.  The results are,  in my opinion, excellent.

There is a learning curve for ClickRepair,  don't expect to master it in one hour.  If you want the best results,  you need to experiment with different settings, often for each LP.

Until recently, I was running Clickrepair under windoze, but now (at last!) I have it running on my new PC under Ubuntu.

I  have found one bug in the Linux version - sometimes processing stops  when the sound is turned on to listen to samples.  It refuses to  continue, but can still be stopped and restarted from the beginning  (without losing the settings).  This can be worked around by processing  with the sound turned off.  It is still worthwhile playing with the  settings and listening to the results while setting it up though.

In case you are wondering, I am no relation to the author of ClickRepair, and I paid for my copy!

---

### Post by wildmanne39 on 2013-02-09
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

