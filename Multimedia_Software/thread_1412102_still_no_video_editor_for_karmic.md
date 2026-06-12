---
title: "still no video editor for karmic"
date: 2010-02-20
forum: Multimedia Software
---

### Post by jim h on 2010-02-20
Installed pitivi.  It takes 20 minutes to put a 3-minute clip on the timeline and the sound is totally messed up.  Installed lives, it loads the clip but insists there is no audio plus the black on dark gray menus are almost unreadable.  Installed kdenlive, it loads the clip but playback produces a short squawk then crash, and I gather I'd have to risk destroying my sound by uninstalling pulseaudio.  Someone suggested OpenShot.  Followed the instructions there:
 ~> sudo add-apt-repository ppa:jonoomph/openshot-e
[sudo] password for me: 
HTTP Error 404: Not Found
Installed Open Movie Editor, it won't even read the clip.  Now, Movie Player handles that clip (a VOB file from a DVD I had made from a miniDVB tape) perfectly as long as I don't touch the time slidebar, so I would imagine if there were a usable video editor out there something would work.  I am kind of fried at this point, any suggestions would be appreciated.  Thanks.

---

### Post by BenAshton24 on 2010-02-20
OpenShot is the best IMO...

I think that you might have copied the commands incorrectly...

sudo add-apt-repository ppa:jonoomph/openshot-edge
sudo apt-get update
sudo apt-get install openshot openshot-docs

If you still can't get the ppa to work then just download the debs.

---

### Post by uMany on 2010-02-20
Hi,
I'm a total newbie in Linux/Ubuntu and I'm looking for a video editor too, the only one you don't mention in your post is Cinelerra, I've never used it yet but a friend of my told me that it works good enough.
I'll check it out as soon as I can get a couple of problems with Karmic Koala out of my way.
If you get to install it, please tell us if it is worth it

---

### Post by BenAshton24 on 2010-02-20
> **uMany said:**
> Hi,
I'm a total newbie in Linux/Ubuntu and I'm looking for a video editor too, the only one you don't mention in your post is Cinelerra, I've never used it yet but a friend of my told me that it works good enough.
I'll check it out as soon as I can get a couple of problems with Karmic Koala out of my way.
If you get to install it, please tell us if it is worth it

Cinelerra is good but it isn't very user friendly, here is a video about cinecutie which is basically a nicer looking version of cinelerra: [http://www.youtube.com/watch?v=m7LtmUswWAk](http://www.youtube.com/watch?v=m7LtmUswWAk)

---

### Post by jim h on 2010-02-20
Thanks, don't know how the command got truncated.  Maybe you know what to do about the next:
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/share/openshot/classes/thumbnail.py", line 174, in run
    mlt.Factory().init()
NameError: global name 'mlt' is not defined

-------------------------------------------------------
Error:  OpenShot has not been installed in the Python path.
(Both the site-packages and /usr/share/openshot folders were checked)

Use the following command to install OpenShot:
  $ sudo python setup.py install

That command also failed:
~> sudo python setup.py install
[sudo] password for me: 
python: can't open file 'setup.py': [Errno 2] No such file or directory

More searching reveals that there is a troublesome dependency problem involving python-mlt.  Downloaded that, make can't find g++. Installed g++.  Make now claims errors in filter_sox.c.  I am too old for dependency hell.

Clearly there is a way to install openshot on 9.10, but I'm sure not finding it.  Again, help would be very much appreciated.

---

### Post by afrodeity on 2010-02-22
Live is such a waste of time. Yesterday spent a couple of hours trying to cobble a video together. The programme went and lost the files in the tmp folder when I shut down. Today, I moved the default working directory to my Video directory. Half way through compositing all my clips together after settting up some titles which took about two hours, the programme quit. Now I can't recover my work. Can't seem to be able to load the layout which I saved. I can see it in my Video directory, but the programme can't see it. No directory scroll capablity. @#$%%&*( programme.

---

### Post by jim h on 2010-02-22
I later tried a slightly different install procedure on the openshot page, still the dreaded 
  Use the following command to install OpenShot:
  $ sudo python setup.py install
message when I try to run it.  Elsewhere is suggested using gdebi to install openshot-mlt but when I try that it complains it would break some previously installed version of mlt.  This is getting crazy.

---

### Post by afrodeity on 2010-02-22
Apparantly there's a major bug in early versions. I've been told to use the latest release.
[http://www.xs4all.nl/%7Esalsaman/lives/current/LiVES-1.2.0.tar.gz](http://www.xs4all.nl/%7Esalsaman/lives/current/LiVES-1.2.0.tar.gz)

---

### Post by Kenjitamura on 2010-02-22
Openshot was the best for me, it was the only one that could open 1080p video without crashing and the timelines are simple.  The audio is still glitchy though, made it difficult to make music videos when the audio would be crackling and freezing.  It also has some of the best potential for effects by supporting transparency in png images.  That being said it's not all the way refined yet so i ended up cutting all the clips in avidemux and making all the effects with avisynth, I just used the timeline from it to assemble them together.  Great export options, can set everything from fps to dimensions to codec and container.

---

