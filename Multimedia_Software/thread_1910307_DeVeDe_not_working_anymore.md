---
title: "DeVeDe not working anymore"
date: 2012-01-16
forum: Multimedia Software
---

### Post by Rtedmonston on 2012-01-16
Since I've had to install FFMpeg converter to get download helper to work and convert YouTube videos, DeVeDe program has stopped working, all I get is: 

Can't find the following programs: 

mplayer
mencoder



DeVeDe needs them in order to work. If you want to use DeVeDe, you must install all of them.

I know I have them both installed and updated, This is what I see when I run DeVeDe from terminal: 

[quote=russell@acer.aspire]russell@russell-Aspire-7740:~$ Devede
No command 'Devede' found, did you mean:
 Command 'devede' from package 'devede' (multiverse)
Devede: command not found
russell@russell-Aspire-7740:~$ devede
DeVeDe 3.21.0
Locale: en_US.UTF-8
Using package-installed files
/home/russell/
Cores: 2
Entro en fonts
Salgo de fonts
/home/russell/
Temp Directory is:  /var/tmp
home load:  /home/russell/.devede
linea:  video_format:pal

linea:  temp_folder:/var/tmp/

linea:  multicore:1

linea:  sub_language:EN (ENGLISH)

linea:  sub_codepage:ISO-8859-1

linea:  AC3_fix:0

linea:  erase_tmp_files:1

linea:  use_ffmpeg:1

linea:  
Saving configuration
/home/russell/
Exiting
Have a nice day[/quote]


I've uninstalled everything, tried again and installed DeVede from .deb package, no change. I modified aofc.config and removed "pulse", no difference. replaced alsoftrc.tar.gz with a modified version I found someone posted, still getting the error, changed the paths where DeVeDe looks for mplayer/mencoder, it still can't find them. I've researched it myself and tried all the proposed solutions, still nothing works. I'm using Ubuntu 11.10 (oneiric) if it helps any.

Any ideas?

---

### Post by Rtedmonston on 2012-01-16
This is what I get when trying to run mplayer and mencoder: 

[quote=russell@acer.aspire]russell@russell-Aspire-7740:~$ mplayer
mplayer: relocation error: mplayer: symbol ff_codec_bmp_tags, version LIBAVFORMAT_53 not defined in file libavformat.so.53 with link time reference
russell@russell-Aspire-7740:~$ mencoder
mencoder: relocation error: mencoder: symbol ff_codec_bmp_tags, version LIBAVFORMAT_53 not defined in file libavformat.so.53 with link time reference[/quote]

---

### Post by Rtedmonston on 2012-01-17
bump, nobody? :(

---

### Post by drhiggins on 2012-01-18
> **Rtedmonston said:**
> bump, nobody? :(

I have the same problem. After recent updates I didn't even realize that OpenShot no longer worked and neither did Kdenlive.

I had just given a demo of Kdenlive on the weekend (without rendering - what an embarrassment it would have been if rendering was part of the demo) - I had just rendered and burned a training video in the previous week.

It's sad that this issue of coordinating updates of dependent softwares is done so poorly and then for those of us left hanging, there is no easy documented path to solution.  *** END B*TCHING ***

So, first I wanted Kdenlive to render. For that I used this info to update ffmpeg:

[https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric](https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric)

Then when I went to use DeVeDe, I got the same errors as reported here.

As much as I'm tempted to go borrow an old Windows machine (I need to get this DVD created!) I'm going to continue to do what I've been doing since the mid 90s - get Linux to work (jeesh, I thought we were past this hack-it stuff).

Thinking that new mplayer and new mencoder might be needed I sudo apt-get remove'd them and then ran sudo apt-get update - I discovered during the remove, mplayer2 was reinstalled. And it works.

So now I'm looking at suggestions that mencoder may have to be taken back to an earlier version - I'm considering that.

In the mean time I tested Kino and it seemed to work, and I tested Kmediafactory and it seemed to work too (very particular about format of the input video file, though) - I never got a burn out either - because I want DeVeDe to work!!

I'll update here when I learn more.

---

### Post by drhiggins on 2012-01-18
Seems this is deja vu all over again - threads from Sept. 2010

[http://ubuntuforums.org/showthread.php?t=1557846](http://ubuntuforums.org/showthread.php?t=1557846)

I tried variations on what they reported at that time, but found no working mencoder (there is an mplayer2 that works) ... but I don't want those, I wanted DeVeDe

But now - I'm ditching DeVeDe - I'll get Kino or Kmediafactory to do it.

---

### Post by syerges on 2012-01-18
i don't know what to say. I updated today as well and DeVeDe is still working. perhaps try uninstalling them and then reinstalling using synaptic as this is how i fixed my install problems. i'll still use usc for installing, but when something's wrong i'm going with synaptic as it shows you more information.

---

### Post by drhiggins on 2012-01-18
Hi syerges ...

I think it is because I installed the unofficial ffmpeg as per:

[https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric](https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric)

I did that because Kdenlive and OpenShot stopped working properly.

Wasting a lot of productive time on this unfortunately. I'm dumping mencoder and mplayer because they seem to have a history of not keeping up.

If I discover anything else, I'll let people here know.

---

### Post by drhiggins on 2012-01-19
Fortunately I have two installations of Ubuntu Studio 11.10 cause after updates on one, when Kdenlive and OpenShot stopped working properly, I went through tons of useless old online discussions, tried tons of ppa and repository choices, and all that left one machine almost crippled in terms of audio/video work. It will take me hours to get it back to the wonderful year-long stream of successful updates and work that I'd gotten used to.

On the other machine, I just did the ffmpeg upgrade:

[https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric](https://launchpad.net/~jon-severinsson/+archive/ffmpeg/+index?field.series_filter=oneiric)

Got rid of mplayer, mencoder, and DeVeDe.

Then started editing again in Kdenlive, rendered it to DVD PAL 16:9 VOB, created a simple DVD Play menu, got a .iso, and then selected Burn - which started up Brasero and burned the DVD.

---

### Post by Rtedmonston on 2012-01-26
Bump, still no working solution to this I'm afraid :(

---

### Post by SeijiSensei on 2012-01-26
Did you try installing the .deb from the [DeVeDe home page]("http://www.rastersoft.com/programas/devede.html")?

For those who want a more recent version of mplayer there's mplayer2, which is distributed from ppa:ripps818/coreavc.  No mencoder version in this build, though.

---

### Post by Rtedmonston on 2012-01-26
> **SeijiSensei said:**
> Did you try installing the .deb from the [DeVeDe home page]("http://www.rastersoft.com/programas/devede.html")?

For those who want a more recent version of mplayer there's mplayer2, which is distributed from ppa:ripps818/coreavc.  No mencoder version in this build, though.


well, that's one step in the right direction, now it tells me it's missing just mencoder now. Can't remove or install mencoder without mplayer though, they have to come together :mad:

Edit: Reading the mplayer2 install page, MEncoder has since been discontinued due to it's broken state, is there a working substitute for it? or an earlier version of both mplayer/mencoder that'll let DeVeDe work again?

---

### Post by Rtedmonston on 2012-01-26
The only thing I can find that others have reported working is to downgrade the version of devede/mplayer/mencoder to an earlier version. I guess that's what I'll do as a last resort. How would I do that?

---

### Post by gbrowning on 2012-02-26
Bump and same problem.   I have read through many a post, tried many a solution and still Devede cannot find mencoder despite that it has been removed and re-installed many times.
I am now trying to use VLC player to do what DeVeDe does easily and not having success with some of what I am trying to do.
Please, it seems to be a package incompatibility problem.  Something needs to be removed and something else needs to replace it but what those somethings are is beyond me. 
  Ideas are welcome

---

### Post by gbrowning on 2012-02-26
OK, found a solution.  The problem lies with a compatibility issue started by mencoder2. 
    Use synaptic package manager to un-install any and all of these packages on your system  Devede, mplayer, mencoder and mencoder2.
    reinstall mplayer, mencoder and DeVeDe.  When I did this I installed them sequentially to ensure the dependencies were updated before taking he next step.
    I am sorry, too lazy to come up with the CLI instructions right now.

---

