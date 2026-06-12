---
title: "Get ffmpeg to fake stereo from mono"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2006-12-29
Using Ubuntu, I'm using ffmpeg to convert Google Videos (from FLV format) into MP3 files. However, what I discover is that these are mono MP3 files. Is there an Ubuntu way to copy the file twice and somehow fuse them with a slight microsecond delay on one channel in order to "fake stereo" or do some other means to "fake stereo" from a mono MP3 file?

To help you see what I mean, the YouTube ripper script I found looks like:

```

#!/bin/bash
bu="http://youtube.com/get_video.php?"
mkdir -p ~/mp3
cd ~/mp3
read -p "YouTube url? " ur
read -p "Name? " nv
echo;echo;
wget ${ur} -O /tmp/y1
uf=${bu}`grep player2.swf /tmp/y1 | cut -d? -f2 | cut -d\" -f1`
wget "${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -f mp3 -vn -acodec copy "${nv}.mp3"
echo;echo;
echo "Your new MP3 file is saved in your home directory in the 'mp3' folder."
read

```

---

### Post by SuperMike on 2006-12-29
Here's **[[COLOR="Red"]something[/COLOR]]("http://www.blazeaudio.com/howto/mono-stereo.html")** I turned up, but I need to figure out the command line trick for this, and which works with MP3s in Ubuntu.

---

### Post by SuperMike on 2006-12-30
Eureka! By jove I have it!!! \\:D/ 

First, add something called 'ecasound' to your system. You may or may not have to turn on Universe option to get this -- I don't recall.

$ sudo apt-get install ecasound

# CONVERT input.mp3 MONO FILE TO SIMULATED STEREO out.mp3 OUTPUT FILE.
# WIDEN THE -etf OPTION UP TO ABOUT 20 FOR WIDER SEPARATION
# BUT SUFFER MORE DISTORTION.
$ ecasound -i input.mp3 -etf:8 -o out.mp3

Now the out.mp3 is in simulated stereo. Not bad at all!

---

### Post by SuperMike on 2006-12-30
Here's the final script:

```
#!/bin/bash
bu="http://youtube.com/get_video.php?"
mkdir -p ~/mp3
cd ~/mp3
read -p "YouTube URL For Video To Rip? " ur
read -p "Name Prefix of MP3 File? " nv
echo;echo;
wget ${ur} -O /tmp/y1;uf=${bu}`grep player2.swf /tmp/y1 | cut -d? -f2 | cut -d\" -f1`
wget "${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -f mp3 -vn -acodec copy "/tmp/${nv}.mp3"
ecasound -i "/tmp/${nv}.mp3" -etf:8 -o "${nv}.mp3"
echo;echo;
rm -f "/tmp/${nv}.mp3"
echo "File is saved in your home directory in the 'mp3' folder."
read

```

I'm sure someone with some Python/PyGTK skills, who understands piping out a process, could whip up a GUI fairly quick for this.

---

