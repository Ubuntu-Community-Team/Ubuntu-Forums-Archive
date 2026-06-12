---
title: "avconv unable to encode aac even with lib installed"
date: 2016-02-19
forum: Multimedia Software
---

### Post by accounts0 on 2016-02-19
Hi,

I've installed libav-tools & libfdk-aac0 but when I do:
```
avconv -formats
```

I get:
```

 D  aac             raw ADTS AAC (Advanced Audio Coding)

```

Instead of:
```

[FONT=monospace][COLOR=#000000] DE  aac             raw ADTS AAC (Advanced Audio Coding)[/COLOR]
[/FONT]
```[FONT=monospace]

Which shows avconv unable to encode in aac.

What do I have to install to get avconv to be able to encode in aac?

Screenshots:

[/FONT]https://imgur.com/a/sN5Bx[FONT=monospace]

Thanks.
[/FONT]

---

### Post by Yellow Pasque on 2016-02-20
Have you installed libavcodec-extra package? Then, you should be able to use 
```
-acodec libvo_aacenc
```

Note that it's a different AAC encoder than the FDK one, but if you want that, you would need to build libav yourself or use a version from a PPA.

---

### Post by accounts0 on 2016-02-20
> **Temüjin said:**
> Have you installed libavcodec-extra package? Then, you should be able to use 
```
-acodec libvo_aacenc
```

Note that it's a different AAC encoder than the FDK one, but if you want that, you would need to build libav yourself or use a version from a PPA.


I installed libavcodec-extra, & it uninstalled some other related libs (with a 54 at the end of them) & installed fine, but I still get:

```
avconv -formats
```

I get:
```

 D  aac             raw ADTS AAC (Advanced Audio Coding)

```

Like it's unable to encode in aac.

---

### Post by mc4man on 2016-02-20
run 
```
avconv -codecs |grep aac
```

---

