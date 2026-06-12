---
title: "How do I convert an ogv file to an ogg or mp3 file (or really ANY audio file)?"
date: 2010-07-16
forum: Multimedia Software
---

### Post by DesiArnez6 on 2010-07-16
I would like to convert OGV files to audio format.If someone knows how, I would really appreciate their help. ;)

-Desi

---

### Post by dv3500ea on 2010-07-17
There is a command line program called [pacpl]("apt:pacpl") that can convert between various audio formats and also convert the sound from various video formats into audio files. Install it, open a terminal and enter ```
man pacpl
```

---

### Post by NFblaze on 2010-07-17
A simple method is to install soundconverter.

```
sudo apt-get install soundconverter
```

It is smart enough to ignore video and just convert the sound.

---

### Post by tlroche on 2011-08-22
> **NFblaze said:**
> install soundconverter.

Thanks! does the job, though slow, but it's scriptable. Here's the bash scriptlet I used to get MP3 from a conference video. (Hopefully tweakable to suit others' needs. Comment out the `eval` to see what you're doing before you do it.)

```
URI="http://www.archive.org/download/IntroductionToRepresentingSpatialObjectsInR/1_3_Bivand_a.ogv"
OUTPUT_MIMETYPE='audio/mpeg'
OUTPUT_SUFFIX='.mp3'
FN="$(basename ${URI})"
DIR='${HOME}/docs/GEOSTAT2011SummerSchool'
# FP="${DIR}/${FN}" # soundconverter chokes on paths
FP="./${FN}" # and pushd/popd
START="$(date)"
echo -e "START=${START}"
for CMD in \
  "mkdir -p ${DIR}" \
  "pushd ${DIR}" \
  "wget -c -O "${FP}" "${URI}"" \
  "soundconverter -b -s '${OUTPUT_SUFFIX}' -m '${OUTPUT_MIMETYPE}' '${FP}'" \
  "popd" \
; do
  echo -e "$ ${CMD}"
  eval "${CMD}"
done
END="$(date)"
echo -e "  END=${END}"
echo -e "START=${START}"
python -c "from datetime import * ; from dateutil import parser ; start=parser.parse(\"${START}\") ; end=parser.parse(\"${END}\") ; print (end-start).seconds"
```

Output was like

```
Length: 31910532 (30M) [video/ogg]
...
2011-08-22 12:40:17 (671 KB/s) - &#8220;./1_3_Bivand_a.ogv&#8221; saved [31910532/31910532]
# download time=46 s, totally dominated by following
$ soundconverter -b -s '.mp3' -m 'audio/mpeg' './1_3_Bivand_a.ogv'
SoundConverter 1.4.4
  using Gstreamer version: 0.10.35, Python binding version: 0.10.21
  using gio
  using 2 thread(s)
...
  END=Mon Aug 22 12:48:59 EDT 2011
START=Mon Aug 22 12:39:30 EDT 2011
569
```

So it took 569 s (~9.5 min) to convert a 30 MB video (of which 46 s (8%) was download time) on my medium-grade laptop

```
me@it:~$ inxi -SCMI
System:    Host: it Kernel: 2.6.39-2-amd64 x86_64 (64 bit) Desktop Gnome 2.30.2 Distro: Linux Mint Debian Edition
Machine:   Mobo: System76 model: Pangolin Performance version: panp5 Bios: Phoenix version: 1.02.22 date: 04/06/2009
CPU:       Dual core Intel Core2 Duo CPU T6500 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4_1 ssse3)
           Clock Speeds: 1: 1200.00 MHz 2: 1200.00 MHz
Info:      Processes: 149 Uptime: 14:47 Memory: 1400.0/3933.9MB Client: Shell inxi: 1.7.23
```

Sound quality equal to original.

---

### Post by dniMretsaM on 2011-08-22
You could also use VLC (which is what I do). [Here](http://www.howtogeek.com/howto/2719/how-to-convert-video-files-formats-to-mp3-with-vlc/) are some instructions (note that you can convert any supported video format to any supported audio format, not just the ones used in this tutorial).

---

