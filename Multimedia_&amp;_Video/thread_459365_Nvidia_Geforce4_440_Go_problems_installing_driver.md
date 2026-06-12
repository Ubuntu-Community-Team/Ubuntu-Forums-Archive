---
title: "Nvidia Geforce4 440 Go problems installing driver"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by Mikimike on 2007-05-30
I've tried everything i can find on the web about this and nothing has worked.  I've completely un-installed everything nvidia, I've reset my xorg.conf file to be generic and use vesa drivers, I've installed from comand line with guides and I've used Envy for both the automatic and manual installs.  Everytime I install the nvidia drivers the computer boots and after the KUBUNTU splash screen loads the display flickers, then it goes back to the splash and sits for about 30 seconds, then it drops to a black screen with a flashing underscore in the upper left corner.  I don't know what else to try, I'm fairly new to linux, I really want to get this working, I love everything else I've learned so far.

I'm attaching my xorg.o.log file and my xorg.conf below, someone please help me out.  If you need more info let me know I'll gladly gather it :)

---

### Post by NewJack on 2007-05-30
I had a similar problem.  Try this:

 Do you have a separate root partition?  If so, backup any necessary files and do a clean install of Ubuntu.  Then before installing any other programs from the Repos, get Envy then run and configure the settings first.  Then you can download any other programs/utilities that you had before

Hope that helps?
Joe

---

### Post by Mikimike on 2007-05-30
I was kinda hoping to save the reload as a last resort type thing, although I'm afraid you may be right and that would be my best bet at this point.

Thanks for your reply NewJack.

---

### Post by NewJack on 2007-05-30
No problem.  Trust me, I tried everything to avoid a clean install too.  I just so happened to finish with that combo after 2 hours of self troubleshooting.  I wish I would have thought of it first.  :)

---

### Post by dannyboy79 on 2007-05-31
and I hope you read the bottom of the troublehsooting guide regarding your exact video card?
[http://doc.gwos.org/index.php/Latest_nvidia_feisty#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_nvidia_feisty#PROBLEMS_SECTION)

---

### Post by Mikimike on 2007-05-31
Yep I read the bottom, I've tried every combination of those lines in the xorg.conf file.  The one I posted might not have it in there, I had tried so many things at that point and my frustration level was through the roof.  I can set everything back like that guide shows and post my xorg.conf and xorg.0.log file again if needed.

---

### Post by Mikimike on 2007-05-31
Ok I followed the instructions for method 2, installing from nvidia package downloaded from nvidia.com and this time I got my x server up and running with the nvidia drivers!  Problem (of course) is that the desktop doesn't fit my monitor, it's smaller and has a black bar on the left and the right, and part of the top of the desktop repeats at the bottom, and the far right past the black bar is a bunch of vertical lines all different colors like a rainbow, about 2 inches of the right hand side of the screen.  I'm getting closer!  Any ideas on these bars and lines?

---

### Post by dannyboy79 on 2007-05-31
what native resolution does your card and monitor suppost? You should be able envoke nvidia-settings from the command line and then chose that resolution? DON'T click on the save xorg.conf option that's within the nvidia-settigns dialog box, it messes up the xorg.conf file I have read. other than that and making sure you gogled 440 Go and ubuntu and read all the troubleshooting tips I can't suggest anything more, sorry.

---

### Post by Mikimike on 2007-05-31
I finally got it!  I googled "nvidia geforce 4 440 linux driver problems" and the very first page had a custom EDID file that Kelvin created especially for dell latitude 840 laptops.  This the page [http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2) incase anyone else needs this fix.  Works perfectly!  I am now running nvidia drivers at 1600x1200 resolution, and it's never looked better.  Thanks for your help Dannyboy, you poked me in the right direction twice and I appreciate it. :)

---

### Post by dannyboy79 on 2007-05-31
glad I could help, that's why I stick around in the forums because I enjoy helping others.

---

