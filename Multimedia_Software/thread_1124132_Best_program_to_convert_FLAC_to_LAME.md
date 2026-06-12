---
title: "Best program to convert FLAC to LAME?"
date: 2009-04-13
forum: Multimedia Software
---

### Post by villainy on 2009-04-13
I usually convert FLAC to LAME with foobar2000 in Windows, but would much rather do it in Ubuntu for obvious reasons :P

What is the best program to do this with? Any program similar to foobar in easiness?

I'd rather convert them to vbr, preferably -v2.

---

### Post by jocheem67 on 2009-04-13
I'm a foobar fan( which runs pretty smoothly with wine , even converting )

However the easiest proggie would be soundconverter, it does flac to mp3 through lame ( or liblame )...

---

### Post by cotcot on 2009-04-13
```
ffmpeg -i filetoconvert.flac -ac 2 convertedfile.mp3
```

In case you want a specific bitrate add -ab xxx with xxx the bitrate you want have.

---

### Post by logos34 on 2009-04-14
> **villainy said:**
> I usually convert FLAC to LAME with foobar2000 in Windows, but would much rather do it in Ubuntu for obvious reasons :P

What is the best program to do this with? Any program similar to foobar in easiness?

I'd rather convert them to vbr, preferably -v2.

I vote for k3b first, since it's a native linux burner/converter app.  

You just need libk3b2-extracodecs and lame for mp3 support

But as stated above. foobar runs great on wine so you could continue to use that.

Or:

Here's a simple python script you can run in the terminal to batch convert a whole directory of flacs to mp3 (@-V 2):

[ATTACH]109746[/ATTACH]

Save it to $HOME and then:

sudo chmod +x flac2mp3.sh


cd /music/dir/flacs

~/./flac2mp3.sh *.flac

Done.  ID3 tags and everything.

---

