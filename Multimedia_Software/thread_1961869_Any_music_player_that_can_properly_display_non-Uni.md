---
title: "Any music player that can properly display non-Unicode ID3 tag?"
date: 2012-04-20
forum: Multimedia Software
---

### Post by csh on 2012-04-20
I have a lot of Chinese musics which ID3 tag is non-Unicode.

Currently using gmusicbrowser. This software cannot properly display the non-Unicode ID3 tag. It display those ID3 tag in garbled text.

I don't want to convert those ID3 tag to Unicode.

Is there any Linux music player that can properly display non-Unicode id3 tag?

---

### Post by andrew.46 on 2012-04-20
Interesting... can you post a sample?

---

### Post by csh on 2012-04-20
> **andrew.46 said:**
> Interesting... can you post a sample?

Due to copyright issue, I cannot post it here. I used this forum's email feature to send you the download link to the sample. Therefore, please check your email. The email subject is "Sample music as requested".

---

### Post by andrew.46 on 2012-04-20
Unfortunately I can only confirm the problem as all of the players at my disposal have the problem you describe:

```

andrew@skamandros~/media/testing$ mpg123 &#37073;&#23569;&#31179;\ -\ &#20174;&#19981;&#25918;&#24323;\ -\ &#22825;&#22320;&#30007;&#20799;&#20027;&#39064;&#26354;.mp3 
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	version 1.13.3; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes

Playing MPEG stream 1 of 1: &#37073;&#23569;&#31179; - &#20174;&#19981;&#25918;&#24323; - &#22825;&#22320;&#30007;&#20799;&#20027;&#39064;&#26354;.mp3 ...
Title:   ´Ó²»·ÅÆú                        Artist: Ö£ÉÙÇï
Comment:                                 Album:  
Year:    0                               Genre:  Other
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz stereo

```

Hopefully somebody else will have a solution :(.

---

