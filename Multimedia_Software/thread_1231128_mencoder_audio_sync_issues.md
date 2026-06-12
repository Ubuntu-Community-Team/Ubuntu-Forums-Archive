---
title: "mencoder audio sync issues"
date: 2009-08-04
forum: Multimedia Software
---

### Post by aaronp on 2009-08-04
Hi all,
I'm trying to convert a whole host of RMBV files to DIVX format to play on a DIVX DVD player.
I have been donig some searching about mencoder and tried plenty of options but keep getting "small" AV sync issues. They are not huge but just enough to be annoying to watch.

Can anyone see anything that might help? I've already tried -mc 0 and it seemed to make it slightly worse.

```

#!/bin/bash

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")

for i in *.rmvb
do
	filename=$(echo $i | cut -d'.' -f1)".avi"

	mencoder $i -o /dev/null -ovc lavc -oac mp3lame -ffourcc DX50 -lavcopts mbd=0:vbitrate=1152:vpass=1 -lameopts vbr=2:aq=3:q=3 -vf harddup=1 -channels 2 -srate 32000 -ofps 30.00
	mencoder $i -o $filename -ovc lavc -oac mp3lame -ffourcc DX50 -lavcopts mbd=0:vbitrate=1152:vpass=2 -lameopts vbr=2:aq=3:q=3 -vf harddup=1 -channels 2 -srate 32000 -ofps 30.00
	rm divx2pass.log
done

IFS=$SAVEIFS
```

I have seen advice that -oac copy on the first pass will assist but if i do this i get the error that copy is not available and to use -fafmttag to override. Couldn't figure this bit out.

Thanks
Aaron

---

### Post by aaronp on 2009-08-06
bump

---

