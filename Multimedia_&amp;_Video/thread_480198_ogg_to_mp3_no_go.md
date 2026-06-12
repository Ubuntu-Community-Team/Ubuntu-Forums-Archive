---
title: "ogg to mp3 no go"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by buuntuu! on 2007-06-21
hi everyone,
being keen on free formats i converted to ripping to .ogg a while ago.
recently i have been bestowed with an ipod nano and was really happy until i found out that 2nd generation is not yet supported by ipondlinux, so no portable .ogg for me :( (for now)

i know that i will lose quality and still:  i need to convert some ogg files into mp3 but have run into a problem i didn't find mentioned anywhere: 
soundkonverter provides me with the error message: "oggdec 1.0.1 error: failed  to open input as vorbis"
soundconverter pretends to do its stuff but does not create the files...

any ideas of what might be wrong??

---

### Post by Ross1 on 2007-06-22
quick course of common sense:

Try playing the .ogg files. If you can play them back without any hiccups, they can decode just fine, and the program lies with soundkonverter. 

If in fact they cant play, its quite probable they are corrupt. The good thing to take out of that is then soundkonverter has an option at the very least NOT to decode through errors. At least it told you they were corrupt instead of wasting your time converting useless files!

---

### Post by HermanAB on 2007-06-22
See this: [http://aeronetworks.ca/ogg2mp3-howto.html](http://aeronetworks.ca/ogg2mp3-howto.html)

Cheers,

Herman

---

### Post by kevinlyfellow on 2007-06-22
> **buuntuu! said:**
> 
soundconverter pretends to do its stuff but does not create the files...

any ideas of what might be wrong??

Not meant to insult, but just to be sure, are sure its not creating the files?  Have you configure it to put the mp3s in a custom folder?  Just trying to get the obvious out of the way...

---

### Post by buuntuu! on 2007-06-23
thanks everyone for responding!
@ ross1: the ogg files play just fine, that's why i wondered about c/konverters refusal to work in the first place.
@kevinlyfellow: no offence taken, but yes, i double-checked where converter would output the files to
@hermanab: thanks for the link, let's see if i can get somewhere from there...

---

### Post by buuntuu! on 2007-06-25
ok, it just came to my mind that when soundconver refuses to work it complains about missing tags... 
i don't know why tags are missing only in some folders, though. i ripped several cds in a short period of time with sound juicer and i didn't change any options, not that there were any that allowed to rip with or without tags...
could this be the root of all evil? and if yes how do i add tags??
regards, buuntuu!

---

### Post by kevinlyfellow on 2007-06-25
> **buuntuu! said:**
> ok, it just came to my mind that when soundconver refuses to work it complains about missing tags... 
i don't know why tags are missing only in some folders, though. i ripped several cds in a short period of time with sound juicer and i didn't change any options, not that there were any that allowed to rip with or without tags...
could this be the root of all evil? and if yes how do i add tags??
regards, buuntuu!

Is the naming scheme based on the tags?  That can be changed in the preferences

---

