---
title: "Using iconv to convert euc-kr to utf-8 and failing"
date: 2010-10-03
forum: Multimedia Software
---

### Post by kudzu on 2010-10-03
Hey everyone,

I'm still pretty new at Ubuntu, and I've been trying forever to get my Korean subtitles working with VLC media player.  I think I might need to convert my euc-kr .smi subtitle file to a utf-8 .srt subtitle file.  I found a command for this:

```
sudo iconv -f euc-kr -t utf-8 Forgetting.Sarah.Marshall[2008][Unrated.Edition]DvDrip-aXXo.smi > sarahmarhsallsubs.srt
```

But after I enter the command, I get this: "bash: sarahmarshallsubs.srt: Permission denied"

I tried to chmod +x "sarahmarshallsubs.srt," but of course that didn't do anything, because "sarahmarshallsubs.srt" doesn't exist.  I also used chmod +x on my /home folder, where the subtitle file is located, but that didn't fix the problem either.  I don't really have any idea what I'm doing.

Does anyone know what I might need to do to successfully convert my file?  Thanks.

---

### Post by kudzu on 2010-10-05
Any ideas, anyone?  Is there another program I could use for this other than iconv?

---

