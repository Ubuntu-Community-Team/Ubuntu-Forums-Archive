---
title: "Flash problem with Lubuntu"
date: 2014-06-07
forum: Multimedia Software
---

### Post by asearle on 2014-06-07
I have installed Lubuntu on an older Laptop and am very impressed by the performance!

Most things work (NB "Network Manager" needed to be installed to get the wireless working) but so far I have not got Flash Player to work.

If I de-install Flash (to check installation) then Mozilla tells me Flash is not available so I then re-install.  Mozilla/Flash is then able to connect to the source and starts receiving the stream (Loading ...) but then I get the "Sound of Silence" screen telling me that "there may be a mis-match between this stream, and your device".

I have tried with other browsers (e.g. Chrome which tells me that Flash is not installed even though it is) and can also not get Flash to work.

My suspicion here is that the computer has too limited a capacity (1.2 Mhz processor and 750 Mb RAM) for Flash to run successfully.  Can anyone confirm this (one way or the other) or maybe point me towards a "HowTo" to help me diagnose the problem.

I do hope that I can get Flash to work because in all other respects Lubuntu has really brought this older (but rather nice) laptop back to life.  But, of course, without Flash you are rather stuck when browsing the internet.

Many thanks for any tips that you can give me.

Yours,
Alan Searle
Cologne, Germany

---

### Post by ajgreeny on 2014-06-07
Run the command ```
cat /proc/cpuinfo | grep sse2
``` and show us the output from that.

I suspect there may be no output at all, showing that your cpu is not sse2 enabled and therefore unable to play flash videos with the latest versions of flash, including that in Google-chrome.  There is a workaround for the problem involving using an earlier version of flash, but it does have security risks and is not advised by many.

If you want to risk it, assuming lack of sse2 is your problem, have a look at [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") for the last version that did not need sse2, and you might be lucky.  I do not even know if the download is still available from lovinglinux's server, but I suspect it might not be.  However there is still a script shown on post #101 of that thread that may work.

---

### Post by monkeybrain20122 on 2014-06-08
I would strongly recommend against using old flash even if it 'works' as it is a security hole. Also with the kind of specs you have even if  you can run flash it wouldn't work great.

To play video streams for some popular sites without flash check out these two greasemonkey scripts
[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)
[http://linternamagica.org/](http://linternamagica.org/)

Even if flash works performance is a lot better using mplayer or totem with either or both of the above.

---

### Post by asearle on 2014-06-19
Many thanks for the "Linterna Magica" tip:  The programme installed fine and the audio worked immediately with YouTube.

Having the audio is a positive result because it means that I can listen to music via YouTube but it would be great to get the video too.

However, more important for me is to be able to listen to streaming radio via "Linterna Magica" (instead of Flash), especially this site ...

[http://www.bbc.co.uk/radio4](http://www.bbc.co.uk/radio4)

Here the little Linterna Magica start panel appears but no sound comes.  Maybe this is because this is a dedicated flash audio stream rather than video and audio.

If anyone out there has a tip about fixing these problems then that would be a great help.

Thanks and all the best,
Alan

Cologne, Germany

---

### Post by monkeybrain20122 on 2014-06-19
Linterna Magica may have a bit of issue with youtube since google keep changings and the dev is too busy with other things to catch up (see the bug tracker) so for Youtube I would recommend Viewtube instead of LM (Install Viewtube, then in gresemonkey's manage script option add Youtube to LM's blacklist so only Viewtube would run) The advantage of LM over Viewtube is that it works on more sites (even sites not supported because it detects flash dynamically), the downside is gives less control and the dev is preoccupied with other things atm.  So for sites that both works Viewtube usually works a bit better.

For Youtube you may also consider a standalone player. Install smtube from [https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)
There is a version in the repo, but it is broken as it has not kept up to date.

Unfortunately none of the flash replacements works on the BBC.

---

