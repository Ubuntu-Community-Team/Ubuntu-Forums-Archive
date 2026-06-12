---
title: "Import SKY.fm streams into Amarok"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by aurelieng on 2008-02-15
Quick hack to import  SKY.fm streams into Amarok :)
1. make sure Amarok is not running
2. save and execute this script
```

#!/bin/bash
echo " <category isOpen=\"true\" name=\"SKY.fm\" >"
PLSFILES=`wget -O - http://www.sky.fm 2>/dev/null | grep "http://www.sky.fm/mp3/" | grep -v "_low.pls" | sed -e "s;^    <td><a href=\";;" -e "s;.pls\".*$;.pls;"`;
for i in $PLSFILES;
do
        REALNAME=`echo $i | sed -e "s;http://www.sky.fm/mp3/;;g" -e "s;.pls;;g" -e "s;_; ;g"`;
        echo "  <stream name=\"$REALNAME\" >";
        echo "   <url>$i</url>";
        echo "  </stream>";
done;
echo " </category>";

```
3. insert its output to ~/.kde/share/apps/amarok/streambrowser_save.xml , before the last tag ```
</category>
```
4. Relaunch Amarok and enjoy the content of Playlists/Radio Streams/SKY.fm :)

Aurel.

---

