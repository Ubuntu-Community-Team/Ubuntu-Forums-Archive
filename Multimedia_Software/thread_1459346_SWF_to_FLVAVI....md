---
title: "SWF to FLV/AVI/..."
date: 2010-04-21
forum: Multimedia Software
---

### Post by alexthunder on 2010-04-21
I'm trying to convert SWF files which contain slides with audio to some video.

I've tried mencoder, ffmpeg to no avail.

I also tried edit.py from pyvnc2wsf, but it gives me the following error:
```
Using pygame 1.8.1release
Using pymedia 1.3.7.0
Input movie: version=7, size=640x480, framerate=8fps, frames=1922, duration=240.2s.
Output movie size: 640x480
Scanning source swf file: 1-intro.swf...
Traceback (most recent call last):
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/edit.py", line 248, in <module>
    if __name__ == "__main__": sys.exit(main(sys.argv))
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/edit.py", line 243, in main
    debug=debug)
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/edit.py", line 77, in reorganize
    movie.parse_vnc2swf(fname, True, debug=debug)
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/movie.py", line 169, in parse_vnc2swf
    parser.open(fname)
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/swf.py", line 165, in open
    getattr(self, name)(tag, length)
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/movie.py", line 413, in scan_tag19
    self.movie.info.reg_mp3blocks(self.fp, length-4, nsamples, seeksamples)
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/movie.py", line 124, in reg_mp3blocks
    MP3Reader(self.mp3).read_mp3file(fp, length, nsamples, seeksamples)
  File "/home/xxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/mp3.py", line 232, in read_mp3file
    assert totalsamples == totalsamples0
AssertionError
```

Is there any software that can convert SWF files?

---

### Post by Totenkopf on 2010-09-11
I too am always getting error messages whenever I use pyvnc2swf to convert an .swf file to .mpg.  Here's what I get:
> 
xxxx@xxxx:~/Downloads/pyvnc2swf-0.9.5/pyvnc2swf$ python edit.py -o out.mpg yafm.swf
Using pygame 1.7.1release
Input movie: version=5, size=550x400, framerate=20fps, frames=6715, duration=335.8s.
Output movie size: 550x400
Scanning source swf file: yafm.swf...
MP3: stereo=0, samplerate=22050, initialskip=1633
Creating MPEG: 'out.mpg': codec=mpeg2video, size=550x400, framerate=20.0
Traceback (most recent call last):
  File "edit.py", line 248, in <module>
    if __name__ == "__main__": sys.exit(main(sys.argv))
  File "edit.py", line 243, in main
    debug=debug)
  File "edit.py", line 92, in reorganize
    builder.build(r)
  File "/home/xxxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/output.py", line 1004, in build
    self.start()
  File "/home/xxxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/output.py", line 947, in start
    self.stream.open()
  File "/home/xxxx/Downloads/pyvnc2swf-0.9.5/pyvnc2swf/output.py", line 768, in open
    'id':  vcodec.getCodecID(self.mpeg_codec),
AttributeError: 'NoneType' object has no attribute 'getCodecID'I do have all the correct dependencies installed that are required to run pyvnc2swf(pygame 1.7.1, python 2.5, & pymedia 1.3.5).  I am at a total loss as to how to fix this.  Is there anyone who can help me out with this?  Thx.

---

### Post by Totenkopf on 2010-09-13
*bump*

---

### Post by dancook79 on 2010-10-05
Dear all,
 
you might like to try my:
 
[http://sourceforge.net/projects/convertswf/](http://sourceforge.net/projects/convertswf/)
 
Regards,
 
Dan Cook

---

