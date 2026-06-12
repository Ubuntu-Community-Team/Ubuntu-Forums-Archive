---
title: "ffmpeg Transconding  activated by inotify"
date: 2015-01-19
forum: Multimedia Software
---

### Post by setoja87 on 2015-01-19
I’m trying to automatically transcode videos with are begin uploaded constantly to a server.

  That's why I have came up with the idea of using inotify by checking  every moment for new files on the videos folder, by using this shell  script:
  ```
#!/bin/bash

inotifywait --monitor -e moved_to -e create /usr/local/share/downloads | while read dir;
do
(~/convertvideos/convert.sh)

done
```  When a new file is moved or created over /usr/local/share/downloads, it called to another script over ~/convertvideos/convert.sh.
  The idea of the convert.sh file is to convert every video which is within the /usr/local/share/download directory, and within every single folder.
  The contents of convert.sh is:
  ```
#!/bin/bash
for file in /usr/local/share/downloads/*
do ffmpeg -i "$file" -acodec aac -ac 2 -ar 44100 -ab 128k -strict -2 -vcodec libx264 "$file".mp4 < /dev/null
rm "$file"

done
```  ON my server for the first files within the /downloads/ folder works,  but after it finishes transcoding it starts again transcoding the same  files, and for example if there is one folder down, let say /downloads/Anthony Zimmer FRENCH/  it should search for any video file and transcode it. After that it  should delete the non transcoded file. and perhaps move the transcoded  file to another folder.
  How can I get this to work?

---

