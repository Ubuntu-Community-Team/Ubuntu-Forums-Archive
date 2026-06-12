---
title: "[SOLVED] Standalone Download VLC/MPlayer"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by zombrax on 2008-04-21
Hi all,

I'm having all sorta probs downloading programs through the normal update program both graphical and command-line method; my question is 
how can I download programs that are standalone and then run the program from the system say like desktop or a folder?

For some reason,  the network that i'm on doesnt allow me to connect to the internet, to dl updates or new programs. I can however, browse the internet fine through Firefox, use Gaim etc

My question is, where can i go to dl a program like VLC player or mplayer that i can dl the actual program to my laptop and then run the install from there? I know my quest sound like a windows program install, but unfortunately after trying for nearly 2 weeks of frustration now, this is my only choice i can see. 

the next question is that what are the files that i need to dl? and how do i go about installing them?

sorry i know i maybe asking for too much here but its frustrating not being able to watch any single mpg/avi clip on my laptop cause its missing codecs and it wont update directly from the net.

thanks so much in advance :)

---

### Post by HunterThomson on 2008-04-21
Sure, Just download the sorce code:) It will be a .tar or .tar.bz2 file. Then just follow this guide.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by aeiah on 2008-04-21
you could get mplayer from [www.getdeb.net](www.getdeb.net), and perhaps the gnome mplayer front end too (or kmplayer if on kubuntu). be sure to actually get mplayer as well though, not just the front end

---

### Post by aeiah on 2008-04-21
although this wont solve your codec problems, they're just players.

try searching for how to install multimedia codecs without the internet

---

### Post by zombrax on 2008-04-23
hey guys.. got this error while running the ./configure command.. can anyone help please?

checking for mad.h... no
configure: error: Could not find libmad on your system: you may get it from [http://www.underbit.com/products/mad/](http://www.underbit.com/products/mad/). Alternatively you can use --disable-mad to disable the mad plugin.
zombrax@ub-lap:~/Progs/vlc/vlc-0.8.6f$ 

what should i do? many thanks :)

---

### Post by zombrax on 2008-04-23
so i tried to do the ./configure --disable-mad and then i get this err...

checking for ffmpeg/avcodec.h... no
configure: error: Missing header file ffmpeg/avcodec.h.

is it really this difficult to install a simple program from standalone install??? :(

---

### Post by ad_267 on 2008-04-23
You are compiling from the source code, not just installing a binary so there are certain development packages required to compile.

The easier way is to download any of the packages found in the repositories from here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
These are the same packages of pre-compiled binaries that synaptic and apt-get use to install software. Once you have downloaded them you can just double click to install.

Here are the results for vlc: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=vlc](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=vlc)

---

### Post by zombrax on 2008-04-24
thanks for your help ad. i know understand the difference between source and binary packages! i went to this location and downloaded the binary package. however, i get this error msg when running the package

"Error: Dependency is not satisfiable: vlc-nox"

so what dows this mean mate? where do i go from here? many thanks once again :)

---

### Post by ad_267 on 2008-04-24
Sorry I should have mentioned that. The problem with installing packages downloaded rather than using synaptic or apt-get is that the other packages that this package depends on are not automatically downloaded and installed too.

If you go to the download page for gutsy for example ([http://packages.ubuntu.com/gutsy/vlc](http://packages.ubuntu.com/gutsy/vlc)) there is a long list of packages that are marked as a dependency and vlc-nox is one of these. Most of these packages should be installed already but some won't be and you will need to download and install the ones you don't have first.

Edit: If you double click on the file to open if with the GDebi package installer and click on the "details" button by status you can see a list of the dependencies that are not met that you will also have to install.

---

### Post by zombrax on 2008-04-26
ah ok thanks for telling me bud. learning a lot of things these days.. time permimtting that is... trying installing again after installing nox... will let you know mate

---

### Post by zombrax on 2008-04-27
no luck still.. vox attempts to connect straight out to the internet to download another 10 updates!! what the????

my question is this: how come there is no ONE package that has all the updates for a PARTICULAR application? theres gotta be a solution for ppl that would want to do an update from one package rather than connecting to the internet to download updates??????

from a very frustrated user :(

---

### Post by zombrax on 2008-05-18
although it is super hard to download ONE standalone packages, what i found was that when the manager gave you error msgs on downloading all the dependent packages, you can manually copy them all on to a text editor and then download each link one by one. just have to make sure that you download and install them as they are listed in the synpatic manager err output.

i found this out before i sorted out my proxy problems, so i installed th VLC player the way i mentioned above. i would have pasted all the dependent files on here but i deleted them without thinking about posting it on here. 

thanks to all who tried to help :)

---

