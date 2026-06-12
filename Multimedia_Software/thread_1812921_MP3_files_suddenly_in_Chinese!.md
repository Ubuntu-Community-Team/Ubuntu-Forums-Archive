---
title: "MP3 files suddenly in Chinese!"
date: 2011-07-27
forum: Multimedia Software
---

### Post by skullmunky on 2011-07-27
Well, the title and author data, anyway.  I loaded up some tracks in mixxx to play around with, and they appeared with Chinese names.  Now they also appear in Chinese in Amarok as well.  It's just one album, all the rest of my files are normal; and the filenames themselves are still in English.  

For example, this track:

"02. Greco Roman - Love Will Save The Day - Bass Up! Club Mix.mp3"

shows this info in Amarok:

Title:&#65533;&#19456;&#28416;&#30208;&#25856;&#8192;&#22272;&#26880;&#27648;&#27648;&#8192;&#21248;&#24832;&#30208;&#25856;&#8192;&#21504;&#26624;&#25856;&#8192;&#17408;&#24832;&#30976;&#8192;&#11520;&#8192;&#16896;&#24832;&#29440;&#29440;&#8192;&#21760;&#28672;&#8448;&#8192;&#17152;&#27648;&#29952;&#25088;&#8192;&#19712;&#26880;&#30720;
Artist:&#65533;&#18176;&#29184;&#25856;&#25344;&#28416;&#8192;&#20992;&#28416;&#27904;&#24832;&#28160;
Album:&#65533;&#17664;&#27648;&#25856;&#25344;&#29696;&#29184;&#28416;&#8192;&#10240;&#17408;&#26880;&#29184;&#29696;&#30976;&#8192;&#18432;&#28416;&#29952;&#29440;&#25856;&#8192;&#19712;&#29952;&#29440;&#26880;&#25344;&#10496;
Genre:&#65533;&#20480;&#29184;&#28416;&#26368;&#29184;&#25856;&#29440;&#29440;&#26880;&#30208;&#25856;&#8192;&#18432;&#28416;&#29952;&#29440;&#25856;

is there a quick way to regenerate the ID3 tags from the filenames?

Solution:

Fixed using Kid3 to batch edit the tags.  The v1 tags were correct, just the v2 ones corrupted.  Copied the v1 over the v2 tags, all is well.

---

