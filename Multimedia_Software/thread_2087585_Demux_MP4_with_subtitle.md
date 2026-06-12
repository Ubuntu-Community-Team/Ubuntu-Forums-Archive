---
title: "Demux MP4 with subtitle"
date: 2012-11-24
forum: Multimedia Software
---

### Post by LoungeLizard on 2012-11-24
Perhaps as an alternative to my earlier question, I maybe able to extract the subtitle from the MP4.  Does anyone know how this may be done?  

My research shows a product for Windows that claims to do such a thing and mencoder should also - but I've not successfully create either SUB/IDX nor SRT files using mencoder 
{something like this to create SUB/IDX files does create the files but the SUB don't work}:

```
 mencoder videofile.mp4 -nosound -ovc frameno -o /dev/null -slang yourlanguage -vobsubout outputfilename 
```-- da Lizard

---

