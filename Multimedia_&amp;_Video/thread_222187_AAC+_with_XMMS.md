---
title: "AAC+ with XMMS"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by brotakul on 2006-07-24
i'm using ubuntu 6.06 dapper and i'n quite new with linux.
i'm trying to play aac streams with xmms but it seems that i don't have the aac codec[plugin for xmms]. aac streams work just fine with other players but i want to make in run on xmms. i also searched the web for some days now, asked people, but got no answers. i hope someone could help..
thanks

---

### Post by jordilin on 2006-07-24
I have asked google and that's what it says:
[http://aacplugin.sourceforge.net/](http://aacplugin.sourceforge.net/)
take a look, and let us know. I did not know there were aac streams. I knew about mp3 and ogg audio streaming but not aac. :-D

---

### Post by sp4rd on 2006-07-26
The xmms mp4 plugin won't play raw aac streams like the streams you rip with a program like streamripper.  You will need a program called MP4Box to mux the aac stream into a mp4/m4a container then the xmms/mp4 plugin will read your aac/mp4/m4a file.

MP4Box can be found in a program called gpac, just 'apt-get install gpac'.  It's all command line driven, so open a terminal and issue this command
MP4Box -new -sbrx -add <infile.aac> <outfile.m4a>
where <infile.aac> is the name of the aac stream file you want to mux and <outfile.m4a/mp4> is the name of the output file.  VLC and gxine/xine will play raw aac streams, xmms just needs a little help.
Gpac just came out with a new version of their software, the latest version is 4.2 not the 4.0 in the ubuntu archives, but 4.0 should work fine for HE-AAC v1 streams.

---

### Post by brotakul on 2006-07-26
ok guys. thanks. i guess i'll just stick to rhythmbox then..

---

