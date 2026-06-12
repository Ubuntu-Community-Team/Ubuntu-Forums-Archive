---
title: "Problems with m2tstoavi"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by benz0 on 2008-03-22
I've got a Panasonic HD video camera and I'm trying to use m2tstoavi to convert the .mts files to .avi's so I can edit them.  I've gotten it installed from the walk through [here]("http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/") and I can run it but when it gets to the end I get a message that says:

-x264encopts is not an MEncoder option

Exiting... (error parsing command line)
/usr/local/bin/m2tstoavi complete.


and there is no output file.  Anyone have any advice?

Thanks

---

### Post by xc3RnbFO8P on 2008-03-22
Try [Avidemux]("http://www.getdeb.net/app/Avidemux")
You may need codecs:
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
> sudo apt-get install w32codecs

---

### Post by benz0 on 2008-03-22
From what I can tell Avidemux doesn't support the .mts files.  Even after installing w32codecs I'm not able to open the files in Avidemux.  The reason I was using m2tstoavi is because I was under the impression that there aren't any video editing programs that will support the .mts files.  Did I miss something or is that an accurate statement?

---

### Post by xc3RnbFO8P on 2008-03-23
I was wrong, I tried to play .m2ts file in Avidemux and it didn't work.
But it says it dos: [http://avidemux.en.softonic.com/?adv_search=1]("http://avidemux.en.softonic.com/?adv_search=1")

---

### Post by wesleybailey on 2008-03-29
Have you tried using the FIFO script ```
m2tstoavi.fifo movie.mts 
``` instead of the /usr/local/bin/m2tstoavi script. This might bypass your problem and save you a lot of disk space?

---

### Post by benz0 on 2008-03-30
It does indeed bypass my problem.  Thanks!  Now I'm presented with a new issue though.  The resulting video is, for lack of a better term, slow.  The audio sounds fine and matches up with the video but it seems to be at about half speed.

---

### Post by petah on 2008-05-17
Hello Everyone.  I'm trying to use the m2tstoavi.fifo to concert some files but am having a tough time.  I'm using hardy, 64 bit and was able to get m2t installed well enough to cnvert the sample video at the end of the installation (after my second attempt) but keep getting an error when i try to run m2tstoavi.fifo:

/usr/local/bin/m2tstoavi.fifo: line 1: &#65279;#!/bin/csh: No such file or directory
/usr/local/bin/m2tstoavi.fifo: line 11: syntax error near unexpected token `(’
/usr/local/bin/m2tstoavi.fifo: line 11: ` set files=($*)’

here’s the file itself:
&#65279;#!/bin/csh

#The scripts and instructions in this package are free to use and
#redistribute AT YOUR OWN RISK!! Standard disclaimers apply.
#NO WARRANTY!

if ( $#argv == “0&#8243; ) then
echo usage: $0 filename.m2ts …
exit
else
set files=($*)
endif

I do have a csh file in the bin folder (a link to executable actually), but I can’t create a folder due to that link being there.

If I try just m2tstoavi it seems to just hang:
petah@desky:/media/SataTwo/Camcorder/BDMV/STREAM$ m2tstoavi *using:
/usr/local/bin/xporthdmv
/usr/local/bin/ldecod
/usr/bin/ffmpeg
/usr/local/bin/m2tstoavi Starting.
 
xporthdmv -hn 00000.MTS 1 1 1
Unsupported Option: n
Cannot open video output file <bits0001.mpv>
ldecod -i bits0001.mpv -o /tmp/00000.yuv


petah@desky:/media/SataTwo/Camcorder/BDMV/STREAM$ m2tstoavi *
using:
/usr/local/bin/xporthdmv
/usr/local/bin/ldecod
/usr/bin/ffmpeg
/usr/local/bin/m2tstoavi Starting.
 
xporthdmv -hn 00000.MTS 1 1 1
Unsupported Option: n
Cannot open video output file <bits0001.mpv>
ldecod -i bits0001.mpv -o /tmp/00000.yuv

If anyone has any suggestions I’d be much obliged.

---

### Post by petah on 2008-05-17
Ok, finally got the script to run again by deleting the first line of script and retyping it but now I get the following problem: 

Cannot open Annex B ByteStream file 'bits0001.mpv'

Any suggestions?

Thanks!

---

### Post by wesleybailey on 2008-05-22
Hi Petah

The m2tstoavi script needs to be installed as root. That is why you are receiving the error message:
> Cannot open Annex B ByteStream file 'bits0001.mpv'

There was an error with step 5 of my tutorial. I apologize for any inconvenience .

---

### Post by DangerWill on 2008-06-22
> **wesleybailey said:**
> Hi Petah

The m2tstoavi script needs to be installed as root. That is why you are receiving the error message:


There was an error with step 5 of my tutorial. I apologize for any inconvenience .

You might be missing a libc-library. Run the install script and look for clues.

---

### Post by DangerWill on 2008-06-22
I too have a problem with the resulting AVI. There is no sound and the picture is garbled. The picture is tripled horisontaly and verticaly and overlayed with changing colours.

Any suggestions?

---

### Post by zakeen on 2008-06-23
would anyone know why I get this?

adam@tz-ubuntu:~/Videos$ sudo m2tstoavi.fifo 00001.MTS
[sudo] password for adam: 
using:
/usr/local/bin/xporthdmv
ldecod: Command not found.
adam@tz-ubuntu:~/Videos$

---

### Post by DangerWill on 2008-06-24
> **DangerWill said:**
> I too have a problem with the resulting AVI. There is no sound and the picture is garbled. The picture is tripled horisontaly and verticaly and overlayed with changing colours.

Any suggestions?

OK, I solved the problem sith garbled video.

It seems m2tstoavi is preset to import video in 1440x1080. Since my camera is a later model, my input should be 1920x1080.

"which m2tstoavi" will tell you where the file is at.
'sudo vi m2tstoavi' and set the size correct. That did it for me.

---

### Post by itpaul on 2008-07-07
it didn't do it for me.

still garbled. in fact after i changed it as you suggested, the resulting avi file was merely kilobytes in size. the garbled mess was at least a huge file so something must have been working somewhere before i changed the dimensions.

any suggestions?

by the way, this footage is from an NTSC camera if it matters.

---

### Post by itpaul on 2008-07-07
oops

i ran out of disk space.

it works :)

---

