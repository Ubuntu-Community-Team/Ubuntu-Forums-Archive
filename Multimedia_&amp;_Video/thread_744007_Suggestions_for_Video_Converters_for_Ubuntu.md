---
title: "Suggestions for Video Converters for Ubuntu"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by yssida on 2008-04-03
Hey Everybody! I need a free software that works in Ubuntu, specifically for DAT files. I need to convert them to mpeg file.

Thanks!

---

### Post by pbcartwright on 2008-04-03
did you try a google.com/linux search ? try convert .dat to .mpg linux:

[http://ajithc.wordpress.com/2006/09/25/mencoderffmpegtranscode-other-media-relared-scripts/](http://ajithc.wordpress.com/2006/09/25/mencoderffmpegtranscode-other-media-relared-scripts/)


Following is working fine for me (all encompassed in dat2divx script)
Use cdxa2mpeg (from GNUVcdImager) to convert DAT to mpg
$ cdxa2mpeg -v AVSEQ01.DAT AVSEQ01.mpg
A sample XVid conf file was copied from /usr/lib/transcode/xvid4.cfg to ~/.transcode/, modifiy it to taste
$ transcode -i AVSEQ01.mpg -o AVSEQ01.avi -y xvid -R1
$ transcode -i AVSEQ01.mpg -o AVSEQ01.avi -y xvid -R2

of course you need to install transcode

---

### Post by yssida on 2008-04-03
Thanks for providing the utility, however I don't quite understand the code you posted at the bottom. Is that the code specifically for converting dat to mpg? thank you very much

---

