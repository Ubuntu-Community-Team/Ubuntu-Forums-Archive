---
title: "Winff FLV quality poor?"
date: 2009-07-20
forum: Multimedia Software
---

### Post by pcgstudio on 2009-07-20
Is there any other conversion program or a way to create better quality FLVs because when i convert divx quality using winff to FLV it looks poorer than youtube quality (not yt hd) the quality on it is really poor, how can i improve it?

---

### Post by paul.gevers on 2009-07-21
> **pcgstudio said:**
> Is there any other conversion program or a way to create better quality FLVs because when i convert divx quality using winff to FLV it looks poorer than youtube quality (not yt hd) the quality on it is really poor, how can i improve it?

You can do this in WinFF. Easiest test is to use the two pass option. If that doesn't help, you can edit the FlV preset or create a new one (maybe based on it), both possible in the Edit -> presets menu. I assume you use the "Flash Video (flv) for Web use Fullscreen" preset? I am not used to the flv preset, so I am not sure what is allowed by that codec but the easiest thing to try is using the same quality:

```
-vcodec flv -f flv -sameq
```

If that doesn't work, start playing with the other parameters. You could for instance *try* to increase the value behind the -b option (bitrate).
```
                                                      \/\/
-vcodec flv -f flv -r 29.97 -s 320x240 -aspect 4:3 -b 300kb -g 160 -cmp dct  -subcmp dct  -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -ac 1 -ar 22050 -ab 56kb
```

---

