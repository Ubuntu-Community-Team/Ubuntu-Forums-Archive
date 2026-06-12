---
title: "Ripping a Video"
date: 2011-04-12
forum: Multimedia Software
---

### Post by aMovieMan on 2011-04-12
I've had Ubuntu for a few weeks now and never encountered major problems - except this one, which I've been unable to solve since I first installed.
I've been trying to rip DVDs, but my DVD Drive is busted. Therefore I've copied the files from the Disc using another computer, then transferred across via a removable storage device and dumped an exact replica of the CD in a folder in /~/Videos. Then I used Thoggen DVD Rip, selecting to rip from the folder (the one whose contents are VIDEO_TS and AUDIO_TS) but it didn't like it, requesting the files that are stored in VIDEO_TS. So I fed it the VIDEO_TS folder and it told me it was all fine, but then when I started the rip I just got a blue screen, no progress and no details. I also tried putting the contents of my DVD on a .iso using brasero, but brasero wouldn't even load the files in, let alone create the .iso. Finally I installed AcidRip, who didn't even like the VIDEO_TS directory.
I have no idea what's going on (I have tried with multiple DVDs etc.) and would be very grateful for some help so that I can watch some movies :)
:popcorn::popcorn::popcorn::popcorn:

---

### Post by Fire_Chief on 2011-04-12
Probably not the answer you're directly looking for but a new DVD/RW drive can be had for $22 + tax (if applicable) at NewEgg.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204")

You may want to try dvd::rip.
[http://www.exit1.org/dvdrip/]("http://www.exit1.org/dvdrip/")
[https://help.ubuntu.com/community/DVD%3A%3ARip]("https://help.ubuntu.com/community/DVD%3A%3ARip")

Cheers!

---

### Post by aMovieMan on 2011-04-12
I can't find dvd::rip in the ubuntu software centre and on the website it looks very complicated. I've downloaded dvdrip-0.98.11.tar.gz and extracted, now what should I do?
I'm not sure if it would work anyway since two rippers have already failed...

---

### Post by Fire_Chief on 2011-04-12
In the software center or in synaptic it's probably called dvdrip.

However I agree that it may still not work for you since the files are not in an image or on a DVD. Also, be sure you install the additional files mentioned in the bottom half of the Community Doc on DVD::Rip since that will help with encrypted DVD files and such.

Cheers!

---

### Post by aMovieMan on 2011-04-12
No worries, I've found it in the centre!

---

### Post by aMovieMan on 2011-04-12
Do you think I should install all the tools from that table (ffmpeg, xvid4conf etc.)? Looking at the descriptions I don't think I need the features, but in the preferences page it says my lack of RAR is 'Not OK' - annoyingly synaptic and software centre have only got the new version, which the documentation says doesn't work - but it says RAR is used for compressed vobsub subtitles, and I don't use subtitles.

---

### Post by kelvin spratt on 2011-04-12
what format are you trying to rip them to

---

### Post by Fire_Chief on 2011-04-12
I wouldn't worry about the RAR utility unless you are planning to compress the video.

---

### Post by aMovieMan on 2011-04-12
I've tried both AVI and MPEG, DVD::rip won't work either. Here's the log from DVD::rip:
Tue Apr 12 21:09:50 2011 Detected transcode version: 10105
Tue Apr 12 21:10:05 2011 Project file saved to '/home/gabriel/dvdrip-data/Being_Earnest.rip'
Tue Apr 12 21:10:05 2011 Project temporary dir '/home/gabriel/dvdrip-data/Being_Earnest/tmp' created
Tue Apr 12 21:10:06 2011 Project Being_Earnest created
Tue Apr 12 21:10:29 2011 Start job 'Read TOC (lsdvd|tcprobe)'
Tue Apr 12 21:10:29 2011 Start job 'Read TOC (lsdvd)'
Tue Apr 12 21:10:29 2011 Executing command: execflow lsdvd -a -n -c -s -v -Op \/media\/DVDVolume_ 2>/dev/null &amp;&amp; echo EXECFLOW_OK
Tue Apr 12 21:10:29 2011 Start job 'Read TOC (tcprobe)'
Tue Apr 12 21:10:29 2011 Successfully read DVD TOC
Tue Apr 12 21:10:29 2011 WARNING: no IFO files found - vobsub feature disabled.
Tue Apr 12 21:10:29 2011 Copying IFO files from {src_dir} to /home/gabriel/dvdrip-data/Being_Earnest/tmp/ifo
Tue Apr 12 21:10:29 2011 Job 'Read TOC (lsdvd|tcprobe)' finished
Tue Apr 12 21:10:29 2011 Job 'Read TOC (tcprobe)' finished
Tue Apr 12 21:10:29 2011 Job 'Read TOC (lsdvd)' finished
Tue Apr 12 21:10:41 2011 Start job 'Rip selected title(s) / chapter(s)'
Tue Apr 12 21:10:41 2011 Start job 'Process title #2'
Tue Apr 12 21:10:41 2011 Start job 'Rip - title #2'
Tue Apr 12 21:10:41 2011 Executing command: rm -f /home/gabriel/dvdrip-data/Being_Earnest/vob/002//Being_Earnest-???.vob &amp;&amp; execflow -n 19 tccat -t dvd -T 2,-1,1 -i \/media\/DVDVolume_ | dvdrip-splitpipe -f /home/gabriel/dvdrip-data/Being_Earnest/tmp/Being_Earnest-002-nav.log 1024 /home/gabriel/dvdrip-data/Being_Earnest/vob/002//Being_Earnest vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm &amp;&amp; echo EXECFLOW_OK&#65533;&#65533;&#65533;&#65533;&#65533;ht

---

### Post by kelvin spratt on 2011-04-12
Ogrip will rip from drive or a ts folder to xvid

---

