---
title: "HOWTO:  Convert video suitable for playing on Cowan D2"
date: 2008-05-16
forum: Multimedia Software
---

### Post by bmckee on 2008-05-16
Just got a Cowan D2 portable media player.  Liking it so far.

Thought I'd save somebody else wading through a pile of various documentation to figure out how to get video converted to play on it.

The video that comes with it is 320x240 xvid at 30fps.  You can check this with a simple
```
==> file d2-cf.avi 
```
> 
d2-cf.avi: RIFF (little-endian) data, AVI, 320 x 240, ~30 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 44100 Hz)


To convert a file to that format try using mencoder like this
```
==> mencoder  input.mov -o output.avi -ovc xvid -xvidencopts bitrate=688  -oac mp3lame -vf scale=320:240
```

Note I'm no video guru - and mencoder has lots of other options like two pass encoding - but it looks pretty good to me :-)

---

### Post by Rodney9 on 2008-12-27
Thank You

---

### Post by washakie on 2009-11-01
Here's a simply python script I wrote. Nothing sophisticated, and could clearly be made more 'configurable', but for now it seems to work. Just need to make sure you have all the appropriate codecs ([see here for trouble shooting]("http://https://help.ubuntu.com/community/Medibuntu")) installed.

```
#!/usr/bin/env python
# Convert an input file to Cowan D2 output avi
# USAGE: avi2cowan.py input.avi
# will output a "input_D2.avi" file suitable for viewing on the D2
import os,sys


def run_ffmpeg(infile,outfile):
    """ use a system call to convert an avi input file
    to a renamed outputfile
    """
    cmd = 'ffmpeg -v 2 -i %s -s 320x240 -vcodec mpeg4 -vtag xvid \
           -b 500kb -bf 0 -mbd 2 -flags mv4 -flags aic -cmp 2 \
           -subcmp 2 -g 300 -acodec libmp3lame -ab 128kb -ac 2 \
           -async 1 %s' % \
           (infile.replace(" ","\ "),outfile.replace(" ","\ "))
           #NOTE: I prefix spaces in the strings with a backslash
           #for the system call to the command line

    os.system(cmd)

def main():
    " run the script "
    infile = sys.argv[1]
    head,tail = os.path.split(infile)
    ## I am using this to create smaller AVIs for my Cowan D2, so I just
    ## rename the file with a _D2.avi extension
    outfile = os.path.join(head,''.join(tail.split('.')[:-1])+'_D2.avi')
    print "Coverting: %s to:\n %s" %  (infile,outfile)
    run_ffmpeg(infile,outfile)

if __name__ == "__main__":
    main()

```

---

