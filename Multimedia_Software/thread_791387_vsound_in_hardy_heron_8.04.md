---
title: "vsound in hardy heron 8.04?"
date: 2008-05-12
forum: Multimedia Software
---

### Post by Jaymoid on 2008-05-12
Hi,

I used vsound quite a lot and I've just upgraded to hardy heron and vsound has vanished, and is no longer listed in apt.

Does this mean it is no longer supported or is there a way to install it?

Cheers

James

---

### Post by benylin on 2008-06-16
I am using it heavily on dapper ... I'm not yet sure if this is a solution, but this is where I am at now on a hardy machine.

1] I downloaded dapper source package, which I found here 
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4939970](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4939970)
I just took vsound_0.6.orig.tar.gz
(I do not know whether I should be using this, patching with the .diff file, or what ... just guessing a little here).

2] I then unpacked the tar file:
```
mkdir ~/vsound
mv ~/Desktop/vsound_0.6.orig.tar.gz ~/vsound
cd ~/vsound
gunzip vsound_0.6.orig.tar.gz
tar -xvf vsound_0.6.orig.tar
cd vsound-0.6
```

3] Obtained build essentials, and sox (required for vsound)
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install sox
```

4] Configure / Build / Install
```
./configure --host=i686-pc-linux
make
sudo make install
```

Of course, I don't know if this actually works yet ... but it certainly installs.

---

### Post by Jaymoid on 2008-08-04
Very slow reply from me here - just tried to use vsound after installing it using the above method and I am getting the following error.

Opening ALSA PCM device default
Opening ALSA PCM device default
Missing file ./vsound17415.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

Now I'm running the command with the -t option so that the first point isn't an issue.

I've tried running the command as root also.

I'm not sure if its because I am using ALSA, I've tried to switch to OSS, but it still says that it is using ASLA.

---

### Post by Dafydd on 2008-10-03
> **Jaymoid said:**
> Very slow reply from me here - just tried to use vsound after installing it using the above method and I am getting the following error.

Opening ALSA PCM device default
Opening ALSA PCM device default
Missing file ./vsound17415.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

Now I'm running the command with the -t option so that the first point isn't an issue.

I've tried running the command as root also.

I'm not sure if its because I am using ALSA, I've tried to switch to OSS, but it still says that it is using ASLA.


I had the same problem and googled a lot. I think the problem is Realplayer 11 (as opposed to Realplayer 10).

But to solve it - or at least this worked for me - open up Realplayer, choose "tools", then "preferences and then select "hardware". 

Here you have to change "ALSA" to "OSS".

Apparently vsound only records from /dev/dsp under OSS.

Now I can use vsound again.

Hope this works for other people

Dafydd

---

### Post by saurabhgeo on 2008-12-20
i tried opening a .ram file and a error message appeared

The playback of this movie requires a PNM protocol source plugin which is not installed 

Could you let me know how to fix this ?

---

### Post by balldunker on 2010-02-21
???

---

### Post by benylin on 2010-02-22
This is slightly off topic I know, but I use the following two scripts these days instead of vsound, and get the links from the iplayerconvertor site for shows I missed. I edit list.py and run it ... then listen on mp3 player ... and on karmic.

**iplayer.py:**

```
#!/usr/bin/env python
import sys
if len(sys.argv)==3:
    url = sys.argv[1]
    name = sys.argv[2]
else:
    url  = raw_input("enter stream:\n")
    name = raw_input("enter name:\n")
import os
os.system("mplayer -cache 2048 -bandwidth 9999999 -playlist %s"%url +
          " -vc null -vo null -ao pcm:fast:waveheader:file=%s.wav"%name)
os.system("lame -V 0 %s.wav %s.mp3"%(name, name))

```

**list.py:**

```
#!/usr/bin/env python
import os
d = [
    ["http://www.iplayerconverter.co.uk/pid/<I edit this>/stream.aspx", "<and I edit this>"]
    ]
for url,name in d:
    print "./iplayer.py %s %s"%(url,name)
    os.system ("./iplayer.py %s %s"%(url,name))

```

---

