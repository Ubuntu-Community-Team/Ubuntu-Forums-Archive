---
title: "FDK AAC (M4A) format on SoundConverter"
date: 2018-10-30
forum: Multimedia Software
---

### Post by LwIh%*7 on 2018-10-30
OK I need some help with this, 

Since 18.10 the asunder software can now rip in m4a with the fdkaac package installed on Arch Linux with fdkaac asunder rips in m4a format and SoundConverter can convert in m4a but on Ubuntu 18.10 it can't and doesn't show up in the "Type of Result" Format list I've installed gstreamer1.0-plugins-* and recently gstreamer-plugins-bad1.0 from the terminal. On the actual terminal dpkg-query --show soundconv\* gstreamer1.0-plugins\* shows the following list of components:

```

dpkg-query --show soundconv\* gstreamer1.0-plugins\*
gstreamer1.0-plugins-bad:amd64    1.14.4-1ubuntu1
gstreamer1.0-plugins-bad-dbg:amd64    1.14.4-1ubuntu1
gstreamer1.0-plugins-bad-doc    1.14.4-1ubuntu1
gstreamer1.0-plugins-bad-faad    
gstreamer1.0-plugins-bad-videoparsers    
gstreamer1.0-plugins-base:amd64    1.14.4-1ubuntu1
gstreamer1.0-plugins-base-apps    1.14.4-1ubuntu1
gstreamer1.0-plugins-base-dbg:amd64    1.14.4-1ubuntu1
gstreamer1.0-plugins-base-doc    1.14.4-1ubuntu1
gstreamer1.0-plugins-good:amd64    1.14.4-1ubuntu1
gstreamer1.0-plugins-good-dbg:amd64    1.14.4-1ubuntu1
gstreamer1.0-plugins-good-doc    1.14.4-1ubuntu1
gstreamer1.0-plugins-ugly:amd64    1.14.4-1
gstreamer1.0-plugins-ugly-amr    
gstreamer1.0-plugins-ugly-dbg:amd64    1.14.4-1
gstreamer1.0-plugins-ugly-doc    1.14.4-1
soundconverter    3.0.0-2

```

Could any experienced users who have m4a on his/her soundconverter tell me how to get it on Ubuntu 18.10 so that I can have the option appear on the list menu? Any help would be appreciated as I'm basically stuck with this situation.

---

### Post by Yellow Pasque on 2018-10-31
Here on Debian, you have to use a 3rd party version of gstreamer to get FDK AAC (because of the patent situation). I believe it's the same on Ubuntu.

```
gst-inspect-1.0 fdkaac
```
^should show you whether your gstreamer is built with support for FDK AAC.

---

### Post by LwIh%*7 on 2018-10-31
> **Temüjin said:**
> Here on Debian, you have to use a 3rd party version of gstreamer to get FDK AAC (because of the patent situation). I believe it's the same on Ubuntu.

```
gst-inspect-1.0 fdkaac
```
^should show you whether your gstreamer is built with support for FDK AAC.

This is what that command shows: 

```

gst-inspect-1.0 fdkaac
No such element or plugin 'fdkaac'

```
What's the next step?

---

### Post by Yellow Pasque on 2018-11-01
I don't know of a PPA off the top of my head
Rather than  FDK-AAC, maybe you should consider using ffmpeg's AAC encoder, or qaac for a high quality AAC encode: [http://www.andrews-corner.org/linux/qaac.html](http://www.andrews-corner.org/linux/qaac.html)

---

### Post by mc4man on 2018-11-01
While it would be trivial to add fdkaac support to gstreamer soundconverter doesn't seem to support that, at least soundconverter in Ubuntu.
So even with 
 ```
gst-inspect-1.0 fdkaac
Plugin Details:
  Name                     fdkaac
  Description              Fraunhofer FDK AAC Codec plugin
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstfdkaac.so
  Version                  1.14.4
  License                  LGPL
  Source module            gst-plugins-bad
  Source release date      2018-10-02
  Binary package           GStreamer Bad Plugins (Ubuntu)
  Origin URL               https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad1.0

  fdkaacenc: FDK AAC audio encoder
  fdkaacdec: FDK AAC audio decoder
ect.

```
Sc would not show AAC (.m4a) in it's pref's. as seen in it's --debug
 > using GTK version: 3.0
  using Gstreamer version: 1.14.4.0
  using gio
  "faac" gstreamer element not found, disabling AAC output.

If faac support is added to gstreamer bad plugin the you'd see AAC(.m4a} as an option in Sc's pref's

```
$ gst-inspect-1.0 faac
Factory Details:
  Rank                     secondary (128)
  Long-name                AAC audio encoder
  Klass                    Codec/Encoder/Audio
  Description              Free MPEG-2/4 AAC encoder
  Author                   Ronald Bultje <rbultje@ronald.bitfreak.net>

Plugin Details:
  Name                     faac
  Description              Free AAC Encoder (FAAC)
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstfaac.so
  Version                  1.14.4
  License                  LGPL
  Source module            gst-plugins-bad
  Source release date      2018-10-02
  Binary package           GStreamer Bad Plug-ins source release
  Origin URL               Unknown package origin

```

Better to just use ffmpeg or an app that uses ffmpeg to encode aac using fdkaac

---

### Post by LwIh%*7 on 2018-11-02
> **mc4man said:**
> While it would be trivial to add fdkaac support to gstreamer soundconverter doesn't seem to support that, at least soundconverter in Ubuntu.
So even with 
 ```
gst-inspect-1.0 fdkaac
Plugin Details:
  Name                     fdkaac
  Description              Fraunhofer FDK AAC Codec plugin
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstfdkaac.so
  Version                  1.14.4
  License                  LGPL
  Source module            gst-plugins-bad
  Source release date      2018-10-02
  Binary package           GStreamer Bad Plugins (Ubuntu)
  Origin URL               https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad1.0

  fdkaacenc: FDK AAC audio encoder
  fdkaacdec: FDK AAC audio decoder
ect.

```
Sc would not show AAC (.m4a) in it's pref's. as seen in it's --debug
 

If faac support is added to gstreamer bad plugin the you'd see AAC(.m4a} as an option in Sc's pref's

```
$ gst-inspect-1.0 faac
Factory Details:
  Rank                     secondary (128)
  Long-name                AAC audio encoder
  Klass                    Codec/Encoder/Audio
  Description              Free MPEG-2/4 AAC encoder
  Author                   Ronald Bultje <rbultje@ronald.bitfreak.net>

Plugin Details:
  Name                     faac
  Description              Free AAC Encoder (FAAC)
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstfaac.so
  Version                  1.14.4
  License                  LGPL
  Source module            gst-plugins-bad
  Source release date      2018-10-02
  Binary package           GStreamer Bad Plug-ins source release
  Origin URL               Unknown package origin

```

Better to just use ffmpeg or an app that uses ffmpeg to encode aac using fdkaac

Hi,

Some of the feedback led me in the right direction but after issuing this command "gst-inspect-1.0 -b" I received:

```

Blacklisted files:
  libgstfaac.so

Total count: 1 blacklisted file

```

I believe this is the reason for the m4a support not working for soundconverter is there a way to remove that file from the blacklist and then I can see if it then can be enabled on soundconverter? This is now from a clean install of Ubuntu 18.10 so how can I remove it? I don't have a .gstreamer1.0 folder with the registery subfolder on my Home folder according to when I looked at the hidden files. Which someone stated that the registry folder within gstreamer should be removed according to one of Debian's mailing list. Further help would be appreciated!

Also further to the help request how do I get the actual commands you've posted? gst-inspect-1.0 faac for me just shows:
```

No such element or plugin 'faac'

```
And the gst-inspect-1.0 fdkaac just shows:
```

No such element or plugin 'fdkaac'

```
So how did you get those working on your system so that I can replicate it on mine?

I already installed fdkaac on the system along with faad, faac and all of the gstreamer1.0-plugins-* but the actual plugin still won't show, this is a learning curve for me so any further help from you lot will greatly help with my understanding of Ubuntu and Linux in general.

---

### Post by mc4man on 2018-11-02
> Some of the feedback led me in the right direction..ect.
Well what did you do that lead to 
> Blacklisted files:
  libgstfaac.so

Total count: 1 blacklisted file
The easiest way to add faac to gst would be to get the gstreamer1.0-plugins-bad source, install the build-dep for gstreamer-plugins-bad, install libfaac-dev

Then configure the gstreamer1.0-plugins-bad source, (just a plain ./configure) & run make on it.
After compiling go into the source > /gst-plugins-bad1.0-1.14.4/ext/faac/.libs folder. Inside will be a libgstfaac.so file.

Copy it as root to /usr/lib/x86_64-linux-gnu/gstreamer-1.0

If you also wanted fdkaac in gst (no use for soundconverter that I see) then before compiling
 also install libfdk-aac-dev , after the make the .so would be in /gst-plugins-bad1.0-1.14.4/ext/fdkaac/.libs  i.e, libgstfdkaac.so  
It also would be copied to same location as above.

But you 1st  need to undo whatever you did to get   libgstfaac.so blacklisted..

Edit: if compiling isn't for you, after resolving the blacklist deal, download attached file, extract folder. Inside are the 2 .so's for 64 bit system. Copy them as root to the mentioned   gstreamer-1.0 folder. Make sure that  libfaac0 & libfdk-aac1 packages are installed. To make sure all other deps are installed you can run 
ldd /path/to/the/.so  
Look for any 'not found' lines. If none you're good to go..

---

### Post by LwIh%*7 on 2018-11-03
> **mc4man said:**
> Well what did you do that lead to 

The easiest way to add faac to gst would be to get the gstreamer1.0-plugins-bad source, install the build-dep for gstreamer-plugins-bad, install libfaac-dev

Then configure the gstreamer1.0-plugins-bad source, (just a plain ./configure) & run make on it.
After compiling go into the source > /gst-plugins-bad1.0-1.14.4/ext/faac/.libs folder. Inside will be a libgstfaac.so file.

Copy it as root to /usr/lib/x86_64-linux-gnu/gstreamer-1.0

If you also wanted fdkaac in gst (no use for soundconverter that I see) then before compiling
 also install libfdk-aac-dev , after the make the .so would be in /gst-plugins-bad1.0-1.14.4/ext/fdkaac/.libs  i.e, libgstfdkaac.so  
It also would be copied to same location as above.

But you 1st  need to undo whatever you did to get   libgstfaac.so blacklisted..

Edit: if compiling isn't for you, after resolving the blacklist deal, download attached file, extract folder. Inside are the 2 .so's for 64 bit system. Copy them as root to the mentioned   gstreamer-1.0 folder. Make sure that  libfaac0 & libfdk-aac1 packages are installed. To make sure all other deps are installed you can run 
ldd /path/to/the/.so  
Look for any 'not found' lines. If none you're good to go..

Thank yo so much for the help both of you. Since you've provided the files as an attachment I've downloaded it and did what you asked me to and placed it in the gstreamer-1.0 folder in /usr/lib and rebooted the system I've checked gst-inspect-1.0 to see if it detected it and it did and then installed soundconverter due to this being a clean install and it now actually shows up on the drop down list. So my matter is now solved, I can now rip in m4a through using the Asunder software which I like and now can convert into m4a with soundconverter. Thank you! Marking as solved.

---

### Post by Yellow Pasque on 2018-11-03
Note that faac isn't the best quality AAC encoder. You'd be better off using abcde to rip to AAC in terms of audio quality:
[http://www.andrews-corner.org/linux/abcde/abcde_aac.html](http://www.andrews-corner.org/linux/abcde/abcde_aac.html)

---

### Post by plrndl on 2018-11-24
Thank you, thank you, thank you.  

I've been looking for this for several YEARS!

---

