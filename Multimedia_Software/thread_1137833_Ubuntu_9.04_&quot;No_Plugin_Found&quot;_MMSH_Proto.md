---
title: "Ubuntu 9.04 &quot;No Plugin Found&quot; MMSH Protocol Source"
date: 2009-04-25
forum: Multimedia Software
---

### Post by coover on 2009-04-25
I have just installed 9.04 and all updates. 

When I open in Firefox [http://beethoven.com](http://beethoven.com) and click on "listen to our free stream", the OS tries to find a plugin for the "MMSH Protolcol Source". It finds none. 

I was able to play this stream with 8.04 and 8.10. 

Any suggestions?

---

### Post by coover on 2009-04-26
I've now checked several streams and all are the same ... all seem to need plug-in, none found.

---

### Post by geirjs on 2009-04-26
Hi.
I had the same problem trying to view webcasts. No plugins found, MMSH protocol source.
 But then I installed "GStreamer plugins for mms, wavpack, quicktime, musepack" from add/remove programs. And then webpages with webcast worked fine...*
Regards Geir.

---

### Post by isTHEr3mOr3 on 2009-04-26
> **geirjs said:**
> Hi.
I had the same problem trying to view webcasts. No plugins found, MMSH protocol source.
 But then I installed "GStreamer plugins for mms, wavpack, quicktime, musepack" from add/remove programs. And then webpages with webcast worked fine...*
Regards Geir.

Indeed, you need the gstreamer0.10-plugins-bad

---

### Post by coover on 2009-04-26
> **geirjs said:**
> Hi.
I had the same problem trying to view webcasts. No plugins found, MMSH protocol source.
 But then I installed "GStreamer plugins for mms, wavpack, quicktime, musepack" from add/remove programs. And then webpages with webcast worked fine...*
Regards Geir.

That did it. THE PROBLEM IS SOLVED.

Interestingly enough, I could not do this through Add/Remove. When I went there, I was told that there was a program conflict and that the installation had to be done through the Synaptic Package Manager, where I had to uninstall a couple of programs and install what was called "gstreamer0.10-plugins-bad". Being a "newbie" Linux guy, this scarred me a bit, but I did it. 

Another problem before actually finding the plugin was that it wasn't called the same name in the SPM that it was in Add/Remove. I originally looked for the "Gstreamer plugins for mms, ..." in the SPM and it wasn't there. I had to go back to Add/Remove" and reread the error message to find the "...plugins-bad" in the SPM.

---

### Post by ballisticprose on 2009-07-07
[FONT=Comic Sans MS][SIZE=3]This solved my [Sirius Radio]("http://www.sirius.com/") problem! Now I can listen to [Howard Stern]("http://www.howardstern.com") while running Ubuntu.  Thanks![/SIZE][/FONT] :lolflag:

---

### Post by 0pul3nce on 2009-07-10
> **geirjs said:**
> Hi.
I had the same problem trying to view webcasts. No plugins found, MMSH protocol source.
 But then I installed "GStreamer plugins for mms, wavpack, quicktime, musepack" from add/remove programs. And then webpages with webcast worked fine...*
Regards Geir.
Thanks...there should be some way to tell people when the ** MMSH Protocol Source** error occurs this is the way to fix it.

---

### Post by Vladimir Hidalgo on 2009-08-27
So sad, automatic codec search from Firefox in Ubuntu should provide the option to install the *-bad package.

Most users will not even bother to search, others would not know what to search for :(

Btw, it's also needed to install "gstreamer0.10-ffmpeg"

---

### Post by andrew.46 on 2009-08-27
Hi,

A very nice radio stream :-). If anybody is interested in saving this one for off-line playback the following might be of interest:

```
mplayer -cache 2048 -cache-min 80 \
        -playlist http://www.beethoven.com/beethoven_ad.asx \
        -dumpstream -dumpfile beethoven.wma
```

I am sure that other applications such as vlc can also do this but my heart has always been with MPlayer :-).

Andrew

---

### Post by Bill-in-Atlanta on 2009-09-23
new to linux 
wanted to listen to coasttocoastam on kfi tongiht and firefox
needed the mmsh plugin but couldn't found it

i downloaded opera and it worked perfect..

hope this helps someone

bill in atl

---

### Post by lenn-art on 2009-10-01
> **Bill-in-Atlanta said:**
> new to linux 
wanted to listen to coasttocoastam on kfi tongiht and firefox
needed the mmsh plugin but couldn't found it

i downloaded opera and it worked perfect..

hope this helps someone

bill in atl

Did you try to install gstreamer bad (search for "gstreamer bad" in Synaptic)?

---

### Post by Rowdy73 on 2009-10-24
> **ballisticprose said:**
> [FONT=Comic Sans MS][SIZE=3]This solved my [Sirius Radio]("http://www.sirius.com/") problem! Now I can listen to [Howard Stern]("http://www.howardstern.com") while running Ubuntu.  Thanks![/SIZE][/FONT] :lolflag:

1!!

:guitar:

---

### Post by astamaja on 2009-11-27
Thanks a lot!

This also worked for me, installed gstreamer0.10-plugins-bad through the terminal, and then firefox prompted me to install the plugin gstreamer0.10-plugins-ugly (I think, ended with ugly at least) as I went to the radio-site again ([www.ruv.is](www.ruv.is)), and now I can listen to radio from back home whenever I want to!

---

### Post by linuxitpro on 2009-12-31
> **coover said:**
> I have just installed 9.04 and all updates. 

When I open in Firefox [http://beethoven.com](http://beethoven.com) and click on "listen to our free stream", the OS tries to find a plugin for the "MMSH Protolcol Source". It finds none. 

I was able to play this stream with 8.04 and 8.10. 

Any suggestions?


Try VLC. In Open Network Stream,just write the [http://beethoven.com/beethoven_ad.asx](http://beethoven.com/beethoven_ad.asx), it should work.

---

### Post by g.oostema on 2010-05-26
using ubuntu 10.04 lucid here and tried this fix.
however i always get this error.

giliam@giliam-laptop:~$ sudo apt-get install gstreamer0.10-plugins-bad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libiptcdata0
The following NEW packages will be installed:
  gstreamer0.10-plugins-bad libiptcdata0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.0kB/1,511kB of archives.
After this operation, 4,678kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://ubuntu-archive.sit.kmutt.ac.th/](http://ubuntu-archive.sit.kmutt.ac.th/) lucid/universe libiptcdata0 1.0.3-1ubuntu1
  403  Forbidden
Failed to fetch [http://ubuntu-archive.sit.kmutt.ac.th/pool/universe/libi/libiptcdata/libiptcdata0_1.0.3-1ubuntu1_i386.deb](http://ubuntu-archive.sit.kmutt.ac.th/pool/universe/libi/libiptcdata/libiptcdata0_1.0.3-1ubuntu1_i386.deb)  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


anyone knows what I can do, i really want to listen to some radio, and most stations here use mms protocol.

tnx for the help

---

### Post by mc4man on 2010-05-27
Open up System - Administration - Software Sources and pick another server to download from. 

Then click close, and reload, then try again

---

### Post by gurugeek on 2010-11-11
Open it with vlc.

---

### Post by kritostar on 2011-06-02
Thanks! I wanted to listen to an online radio and have that problem.

---

