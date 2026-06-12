---
title: "Help with Script"
date: 2009-11-21
forum: Multimedia Software
---

### Post by StreetWise on 2009-11-21
Could anyone help me turn this script into a working kvcd script

['mencoder', '-srate', '44100', '-af', 'lavcresample=44100', '-oac', 'lavc', '-ovc', 'lavc', '-of', 'mpeg', '-mpegopts', 'format=xsvcd', '-ofps', '25', '-vf', 'expand=640:480:0:64,scale=352:288,harddup', '-lavcopts', 'vcodec=mpeg2video:trell:mbd=2:sc_threshold=1000000000:cgop:vstrict=0:vrc_maxrate=1947:vrc_buf_size=917:vrc_minrate=600:vbitrate=1298:keyint=15:acodec=mp2:abitrate=128:aspect=4/3', '-o', '/home/admin/movie_01_01.mpg', '/home/admin/file.avi']

new to ubuntu and realy want to create my first kvcd on it.

---

