---
title: "Program to convert pdt... to prc??"
date: 2008-10-28
forum: Multimedia Software
---

### Post by rado3105 on 2008-10-28
Hi in windows there is program called mobipocket creator, using it I could convert almost any text file(i need mainly pdf, doc, txt) to prc. In my mobile phone I use mobipocket reader to read books. Can you help me how to make prc file in linux??

---

### Post by jethro10 on 2008-10-31
I found this a bit ago and kept the text, but not sure where I got it from.
Basically Mobi provide a windows command line program to do this that works on linux under wine.
Here is the snippet anyhow. My book reader comes next week, I hope this works

> 
Here's how I run mobigen under Linux, using wine. Mobigen is a CLI program, no graphical interface, so can run in batch mode in the background:

1. Install wine if not installed already
2. Copy or download DLL file msvcp71.dll and copy to ~/.wine/drive_c/windows/system32/msvcp71.dll
3. Download mobigen from [http://www.mobipocket.com/dev/](http://www.mobipocket.com/dev/) and unzip. I installed it under /usr/local/mobigen/
4. Run mobigen as follows:

wine /usr/local/mobigen/mobigen.exe your-source-file.html -c1 -s0

This creates a file your-source-file.mobi (replace your-source-file above with the name of your html file). I converted about 100 ebooks at [http://www.yosemite.ca.us/library/](http://www.yosemite.ca.us/library/) with this program.

Here's the command line options:

Usage : mobigen filename.opf/.htm/.html [-lowpriority] [-nomin] [-c0 or -c1 or c2] [-s0 or -s1 or -s2] [-vouchers=n] [-nocopypaste] [-rebuild] [-onlydeps or -nodeps] [-unicode]
Options:
-c0: no compression
-c1: standard DOC compression
-c2: Mobipocket huffdic compression
-s0: no security
-s1: encrypted content
-s2: PID secured (retargetable) Mobipocket ebook
-vouchers=n: [by default] use DRM v2 with n vouchers (min = 6).
-nocopypaste: does not allow any copy paste of content in Reader
-nomin: do not minimize version
-rebuild: rebuilds all dependencies
-onlydeps: build only needed dependencies
-nodeps: do not check/build dependencies
-unicode: force build of Unicode book
-lowpriority: set the PRCGEN thread priority to low (background build)
-regserver: register the XOPFPlugin Type Library
-unregserver: unregister the XOPFPlugin Type Library
-releasenotes: display release notes
-jpeg: native jpeg support (all images converted to GIF otherwise)


---

