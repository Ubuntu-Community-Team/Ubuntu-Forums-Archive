---
title: "flvtool2 help"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by brentcee23 on 2007-10-01
I am having trouble adding the metadata and cuepoints to any .flv video. 

I've tried various different commands but when I play the .flv file its still streaming and I can't use cuepoints. I am pretty new to this and I am sure I am screwing up somewhere. any help would be much appreciated. Heres one that I tried with results 

prolite@Africa:~$ flvtool2 -UPAk '/home/prolite/Desktop/Torrents/FFmpeg/steripenexample.flv' 
---
/home/prolite/Desktop/Torrents/FFmpeg/steripenexample.flv: 
  hasKeyframes: true
  cuePoints: 
  audiodatarate: 56.2751219512195
  hasVideo: true
  stereo: false
  canSeekToEnd: true
  framerate: 12
  audiosamplerate: 22000
  videocodecid: 2
  datasize: 2169658
  lasttimestamp: 61.5
  audiosamplesize: 16
  audiosize: 458498
  hasAudio: true
  audiodelay: 0
  videosize: 1709246
  metadatadate: Mon Oct 8 16:26:44 GMT-0600 2007
  metadatacreator: inlet media FLVTool2 v1.0.6 - [http://www.inlet-media.de/flvtool2](http://www.inlet-media.de/flvtool2)
  lastkeyframetimestamp: 61.5
  height: 240
  filesize: 2182047
  hasMetadata: true
  keyframes: 
    times: 
      - 0
      - 1
      - 1.083
      - 1.167
      - 2.167
      - 3.167
      - 4.167
      - 5.167
      - 6.167
      - 7.167
      - 8.167
      - 9.167
      - 10.167
      - 11.167
      - 12.167
      - 13.167
      - 14.167
      - 15.167
      - 16.167
      - 17.167
      - 18.167
      - 19.167
      - 20.167
      - 21.167
      - 22.167
      - 23.167
      - 24.167
      - 25.167
      - 26.167
      - 27.167
      - 28.167
      - 29.167
      - 30.167
      - 31.167
      - 32.167
      - 33.167
      - 34.167
      - 35.167
      - 36.167
      - 37.167
      - 38.167
      - 39.167
      - 40.167
      - 40.667
      - 41.667
      - 42.667
      - 43.667
      - 44.667
      - 45.667
      - 46.667
      - 47.667
      - 48.667
      - 49.667
      - 50.667
      - 51.667
      - 52.667
      - 53.667
      - 54.667
      - 55.667
      - 56.667
      - 57.667
      - 58.667
      - 59.667
      - 60.667
      - 61.333
      - 61.417
      - 61.5
    filepositions: 
      - 1897
      - 21002
      - 23884
      - 30075
      - 125936
      - 177195
      - 236436
      - 282280
      - 328553
      - 370461
      - 403420
      - 439958
      - 474807
      - 508379
      - 545922
      - 588553
      - 622524
      - 651741
      - 683381
      - 713959
      - 742677
      - 776552
      - 803991
      - 844350
      - 873272
      - 905809
      - 941464
      - 986256
      - 1014459
      - 1046783
      - 1077249
      - 1107436
      - 1143492
      - 1171241
      - 1197558
      - 1228880
      - 1266513
      - 1300523
      - 1345725
      - 1384692
      - 1421525
      - 1454365
      - 1488702
      - 1509456
      - 1538609
      - 1572479
      - 1603260
      - 1632548
      - 1670802
      - 1704277
      - 1739316
      - 1763522
      - 1793626
      - 1823736
      - 1856206
      - 1886346
      - 1916469
      - 1948034
      - 1980160
      - 2019824
      - 2048416
      - 2080153
      - 2114216
      - 2149013
      - 2174725
      - 2177753
      - 2180038
  audiocodecid: 2
  videodatarate: 221.283512195122
  duration: 61.583
  hasCuePoints: false
  width: 320
...
ERROR: can't convert nil into String
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:60:in `initialize'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:60:in `open'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:60:in `add'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:47:in `send'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:47:in `execute!'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:46:in `each'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:46:in `execute!'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:239:in `process_files'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:225:in `each'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:225:in `process_files'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2/base.rb:44:in `execute!'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2.rb:168:in `execute!'
ERROR: /usr/local/lib/site_ruby/1.8/flvtool2.rb:228
ERROR: /usr/bin/flvtool2:2:in `require'
ERROR: /usr/bin/flvtool2:2

---

### Post by brentcee23 on 2007-10-08
bump

---

