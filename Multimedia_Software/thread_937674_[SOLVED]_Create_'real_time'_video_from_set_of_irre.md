---
title: "[SOLVED] Create 'real time' video from set of irregulary timed pictures"
date: 2008-10-04
forum: Multimedia Software
---

### Post by Colbrac on 2008-10-04
I have a set of timecoded jpegs that I would like to turn into a video. Normal mencoder *.jpg -> videofile, e.g. 1 picture per frame is not what I want. The set of pictures spans roughly 2 hours. The first 10 minutes I have about 1 picture per 10 seconds, the rest of the time is roughly 1 picture per minute.
What I want is to convert the pictures into a realtime video, e.g. if the interval between picture 3 and 4 is 12 seconds, I want picture 3 to show for 12 seconds. Between picture 75 and 76 it's 63 seconds, I want to see picture 75 for 63 seconds.
I guess the video could be 1 fps but if I understand video encoding correctly, normal 24/29.97 fps is equally possible since codecs save repeating frames only once.
Are there programs that can do this for me? I found the stopmotion program but that seems exclusively 1 picture per frame. Same for the commandline tools like mencoder. If at all possible I'd rather not put >100 pictures on a video editor timeline by hand, thank you very much. :)
I found [http://pymedia.org/tut/src/make_video.py.html](http://pymedia.org/tut/src/make_video.py.html) which seems like a interesting starting point since I may adapt this one to repeat frames the needed number of times. However, pymedia seems a bit unmaintained. Is this my best chance? Or is there another (preferably python) scriptable solution? Like, scripting in cinerella or something.

---

### Post by Colbrac on 2008-10-06
No one knows?

---

### Post by Colbrac on 2008-10-06
I solved it the 'quick' and DIRTY way by creating a jpg for every frame I need (e.g. 1 jpg per second so from 99 originals to over 5000 jpegs).

The following script is how I do it. It's still rough around the edges but works. It creates a 25 fps mjpeg video file (350 MB in my case) and a 1 fps xvid file (4.2 MB only!).

```
#! /usr/bin/env python
# Jasper Groenewegen <colbrac@xs4all.nl>
# Creates all the needed jpeg files for a continuous 1 fps jpeg stream
# Depends on filenaming as 'DDHHMMSS.jpg'
# Convert into movie with 'mencoder mf://*.jpg -mf w=640:h=480:fps=1:type=jpg -ovc copy -o output.avi'
# Or to xvid:
# mencoder mf://*.jpg -mf w=800:h=600:fps=1:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:mv0:trell:v4mv:cbp:last_pred=3:predia=2:dia=2:vmax_b_frames=2:vb_strategy=1:precmp=2:cmp=2:subcmp=2:preme=2:qns=2 -o output.avi


import os
import time
import sys
import shutil
from subprocess import call

def create_filler_jpegs(folder):
    """Create filler jpegs for the folder specified in the input"""
    
    tmpfolder = 'vidtmp'
    
    files = [file for file in os.listdir(folder) if file.lower().endswith('.jpg')]
    files.sort()
    if not os.path.isdir(tmpfolder):
        print "Creating tmp folder %s..."%tmpfolder
        os.mkdir(tmpfolder)
    
    print "Copying pictures to tmp folder..."
    for idx, filename in enumerate(files):
        tc = filename.lower().rstrip('.jpg')
        timetuple = (2008, 10, int(tc[0:2]), int(tc[2:4]),int(tc[4:6]), int(tc[6:8]), 0, 0, 0)
        filetime = int(time.mktime(timetuple))
        try:
            nexttc = files[idx+1].lower().rstrip('.jpg')
            timetuple = (2008, 10, int(nexttc[0:2]), int(nexttc[2:4]),int(nexttc[4:6]), int(nexttc[6:8]), 0, 0, 0)
            nexttime = int(time.mktime(timetuple))
            #print nexttime
        except:
            nexttime = filetime+30
        
        delta_t = nexttime - filetime
        
        for i in xrange(delta_t):
            shutil.copyfile(os.path.join(folder,filename), os.path.join(tmpfolder, time.strftime("%d%H%M%S.jpg", time.localtime(filetime + i))))

def create_videos(filenameprefix):
    """Create videos with mencoder using jpgs in $tmpfolder"""
    tmpfolder = 'vidtmp'
    print "Creating mjpeg file..."
    mjpeg = call(["mencoder",
                   "mf://%s/*.jpg"%tmpfolder, "-mf", "w=800:h=600:fps=25:type=jpg", "-ovc", "copy", 
                   "-o", "%s.accel.avi"%filenameprefix,
                   ])
    print "Creating xvid file..."
    xvid = call(["mencoder",
                   "mf://%s/*.jpg"%tmpfolder, "-mf", "w=800:h=600:fps=1:type=jpg", 
                   "-ovc", "lavc", "-lavcopts", 
                   "vcodec=mpeg4:mbd=2:mv0:trell:v4mv:cbp:last_pred=3:predia=2:dia=2:vmax_b_frames=2:vb_strategy=1:precmp=2:cmp=2:subcmp=2:preme=2:qns=2",
                   "-o", "%s.realtime.avi"%filenameprefix,
                   ])


if __name__== '__main__':
    if not len(sys.argv)==3:
        print "Usage: createvideos.py <imagefolder> <outputfilenameprefix>"
    else:
        create_filler_jpegs(sys.argv[1])
        create_videos(sys.argv[2])

```

---

