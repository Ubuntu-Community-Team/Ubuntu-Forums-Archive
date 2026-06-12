---
title: "Missing channels in Kaffeine and Me-TV"
date: 2011-12-26
forum: Multimedia Software
---

### Post by Hackerbeavis on 2011-12-26
I recently purchased a HDHomeRun Prime, and installed and activated a CableCard from Comcast for digital cable. Using the hdhomerun_config_gui utility, I can see a number of channels (muxes?), which contain up to 20 "programs" each. I can also view these successfully in VLC. The problem is that I am spinning my wheels trying to get these channels to show up in Kaffeine, Me-TV, or TV Headend. I have tried using the channel scans in those programs, as well as dvbscan and w_scan to try to generate channels files. Nothing I do is working, and I am really lost as to what I am doing wrong.

I would be VERY grateful for any assistance with getting this figured out! Thanks!

FYI, I have Ubuntu 10.10, and I have upgraded the firmware on my HDHomeRun Prime to the latest available from their website, and I am running hdhomerun_confiug_gui 20111025.

---

### Post by Hackerbeavis on 2011-12-27
Did I stump everybody? :confused:

I did find a script called hdhr-mkchan, and this script was able to successfully scan through the channels and programs and appeared to find everything. Unfortunately, the script couldn't handle many program descriptions that contained the text "(encrypted)". Also, the script is designed to output channel stream files (.strm) for XBMC, which doesn't help me with Kaffeine or Me-TV.

If hdhr-mkchan is able to see these, I'm not sure why dvbscan or w_scan aren't seeing these channels/programs. If I could somehow import the output from hdhr-mkchan into Me-TV or Kaffeine, that would be great, but I can't see a way to do that. 

Any help would be appreciated!

---

