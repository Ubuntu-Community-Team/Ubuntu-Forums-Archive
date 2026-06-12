---
title: "[FFmpeg] Creating a Video with a Single Image"
date: 2012-05-06
forum: Multimedia Software
---

### Post by dodle on 2012-05-06
Does anyone know how I can take a single png image and turn it into a 6 second video using FFmpeg? I've tried the following but the resulting video only has a single frame:

```
:~$ ffmpeg -f image2 -loop -r 30 -i black.png -f alsa -i hw:0,0 -vcodec huffyuv -acodec pcm_s16le -t 6 black.avi
```

---

### Post by llamabr on 2012-05-06
[http://electron.mit.edu/~gsteele/ffmpeg/](http://electron.mit.edu/~gsteele/ffmpeg/)

---

### Post by dodle on 2012-05-07
Meh! I gave up and decided to write a python script that would do it for me:

[php]#! /usr/bin/env python

import sys, os, subprocess
from subprocess import PIPE

exe = os.path.basename(__file__)
tmpvid = '/tmp/video.tmp.avi'
tmpframe = '/tmp/frame.tmp.avi'

def ShowUsage():
    print('\n\tUsage:\n\t\t%s image framerate duration outfile\n\n\
\tArguments:\n\
\t\timage:\t\tPath to an image file\n\
\t\t\t\t(image type must be supported by FFmpeg)\n\n\
\t\tframerate:\tDesired framerate (fps)\n\n\
\t\tduration:\tLength (in seconds) of output video\n\n\
\t\toutfile:\tFilename for output video file\n\t\t\t\t(.avi automatically appended)\n' % exe)

try:
    if sys.argv[1] in ('-h', '--help'):
        ShowUsage()
        sys.exit(0)
except IndexError:
    ShowUsage()
    sys.exit(1)

if len(sys.argv) != 5:
    ShowUsage()
    sys.exit(1)

image = sys.argv[1]
outvid = '%s.avi' % sys.argv[-1]

if os.path.isfile(outvid):
    overwrite = raw_input('\n%s already exists. Overwrite? ' % outvid)
    if not overwrite.lower() in ('y', 'yes'):
        print('Aborted!\n')
        sys.exit(1)

try:
    framerate = float(sys.argv[2])
except ValueError:
    print('\nArgument 2 (framerate) must be an int/float value\n')
    sys.exit(1)
try:
    duration = int(sys.argv[3])
except ValueError:
    print('\nArgument 3 (duration) must be an int value\n')
    sys.exit(1)
totalframes = int(duration * framerate)
frames = []
if not os.path.isfile(image):
    print('\nCould not find %s, please specify a valid image file\n' % image)
    sys.exit(1)

# Create a temporary single framed video
P1 = subprocess.call([ 'ffmpeg', '-y', '-r', str(framerate), '-i', image, '-vcodec', 'huffyuv', '-an', tmpframe ], stdout=PIPE, stderr=PIPE)

if not os.path.isfile(tmpframe):
    print('\nError: could not create temporary file\n')
    sys.exit(1)

for f in xrange(totalframes):
    frames.append(tmpframe)

# Create the temporary full length video
tmpout = open(tmpvid, 'wb')
for f in frames:
    tmpin = open(f, 'rb')
    tmpout.write(tmpin.read())
    tmpin.close()
tmpout.close()

if not os.path.isfile(tmpvid):
    print('\nError: could not create temporary video\n')
    sys.exit(1)

# Re-index the temporary video and save its output
P2 = subprocess.call([ 'ffmpeg', '-y', '-i', tmpvid, '-vcodec', 'copy', '-an', outvid ], stdout=PIPE, stderr=PIPE)

# Cleanup
if os.path.isfile(tmpframe):
    os.remove(tmpframe)
if os.path.isfile(tmpvid):
    os.remove(tmpvid)[/php]

---

### Post by sudodus on 2012-05-07
It is straight-forward to do it with ***OpenShot***, drag and drop and right-click to modify the time that the picture will be shown.

---

