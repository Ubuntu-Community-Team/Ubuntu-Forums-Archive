---
title: "AviDemux not working under Ubuntu 10.10"
date: 2011-04-15
forum: Multimedia Software
---

### Post by swright007 on 2011-04-15
I recently formatted and installed Ubuntu 10.10 straight from CD.  I installed several key files I use regularly either with apt-get or using the Synaptic package manager.(AviDemux, DeVeDe, MythTv, VLC, etc...) Following FakeOutDoorsman's guide for installing FFmpeg  I used apt-get install to install the latest version of FFmpeg then went to his guide and 

B. Installing the unstripped or extra libraries
This is the quickest option for most users. FFmpeg from the repository does not include many restricted encoders, formats, and codecs which may include: H.263, aac (libfaac), mp3 (libmp3lame), H.264 (libx264), xvid (libxvid), and mpeg4. You can fix this by installing the unstripped or extra (Ubuntu Karmic renamed unstripped to extra) FFmpeg libraries that will enable these restricted encoders. Open up Terminal and enter:

Ubuntu Maverick Meerkat 10.10, Ubuntu Lucid Lynx 10.04 & Ubuntu Karmic Koala 9.10
Code:

sudo apt-get install ffmpeg libavcodec-extra-52

AND THEN I did this

C. Medibuntu
This option is available for Ubuntu Maverick Meerkat 10.10, Ubuntu Lucid Lynx 10.04, Ubuntu Karmic Koala 9.10, and Ubuntu Hardy Heron 8.04. Medibuntu is a third-party repository that contains packages that are unable to be included in the official Ubuntu repositories. To install FFmpeg from Medibuntu open Terminal (Applications -> Accessories -> Terminal) and run the following:

Code:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

With all of this now in place I tried editing some videos with avidemux.  when I had the finished product, I saved to .AVI because it just saves faster.  I could encode from there to (and actually did at one point to test something)  then using this code that has always worked to get my recording in the correct format for NTSC DVD to be burned to a disk:

ffmpeg -i start.avi -target ntsc-dvd -ps 2000000000 -aspect 4:3 -deinterlace done.mpg

at 24 min into the "time" indicator the 42 min recording stopped processing "time" and just the "frames" indicator kept incrementing.
Then it just bottomed out.  I literally had to X out of the Terminal because it locked up at the end of the run.

Wait.. new strategy... I encoded everything that I had encoded to AVi with AviDemux with Mencoder.  Mencoder complained less and encoded perfectly.  THEN, to further test my theory took those very files and encoded them with FFmpeg.  Again, flawless results.   AviDemux is broken, so broken that it can't even take 2 files it created and append them together.  Can anyone tell me the best way, under Ubuntu 10.10 to get a solid functional copy of AviDemux running?   I really enjoy using that as a video editor. 
                                                Scott

I tried to install the latest version of AviDemux from their website (version 2.5.4).  All that happened was Synaptic removed my current version (2.5.3) and reinstalled 2.5.3   Apparently I am doing something wrong in my attempt to get the new version.   Has anyone else experienced this?  Can someone please help step me through getting the new version to see if that fixes the other issues? Thank you in advance for any assistance !

---

### Post by swright007 on 2011-04-15
I was able to download from a mirror site the correct files.  After getting the newest version of AviDemux properly installed, it seemed to fix my problems.

---

