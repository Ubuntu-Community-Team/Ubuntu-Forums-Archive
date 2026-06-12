---
title: "iPod Classic and Rhythmbox - no format problem"
date: 2012-02-23
forum: Multimedia Software
---

### Post by kbuster on 2012-02-23
I'm having a small problem with Rhythmbox and my 160GB iPod Classic. Basically, I can read and transfer the files between my Ubuntu computer and my iPod just fine, but the files that I take from my iPod seem to be in no format at all (they don't have .mp3 after the file name). Rhythmbox and Ubuntu somehow know that they're mp3 files, but when I try to transfer them to another computer or device for playback, I have to add ".mp3" to every filename for them to get detected, which is a total pain.

Is there any way to solve this? I've searched around the Internet for someone with the same problem and had no luck whatsoever.

Thanks in advance :)

---

### Post by sanderd17 on 2012-02-23
> **kbuster said:**
> 
but when I try to transfer them to another computer 
= a Windows computer?

Linux doesn't need file extensions in fact. So that's why it works on Linux.

You can in any way bash-rename the files.

If they are all in one directory, you can create a script like this:

```

#! /bin/bash

cd  /path/to/music/directory/

for file in *; do
 mv $file $file.mp3
done

```

Disclaimer: I didn't try this script, it will most likely contain a typo. Try it on a test directory first.

---

### Post by kbuster on 2012-02-23
Yeah, exactly, I was talking about another Windows computer, or also any other type of device (e.g. transferring them to a pendrive for my car stereo to read via USB).

I'll try batch renaming the files, that's a good idea. Is there any way for Rhythmbox to just do this on its own by default, though?

Thanks a lot :)

---

### Post by sanderd17 on 2012-02-23
> **kbuster said:**
> Yeah, exactly, I was talking about another Windows computer, or also any other type of device (e.g. transferring them to a pendrive for my car stereo to read via USB).

I'll try batch renaming the files, that's a good idea. Is there any way for Rhythmbox to just do this on its own by default, though?

Thanks a lot :)

Not that I know, maybe if you use banshee instead of rhythmbox?

---

### Post by Rockin Mike on 2013-04-03
The script will not work if any filenames contain spaces.
It also does not check whether the file is actually an audio file before renaming it.

This one will work better:

```

#!/bin/bash

cd /path/to/music/directory

ls -1 |while read FILE
do
     if [ "`file $FILE |grep Audio`" ]; then
          mv "$FILE" "$FILE.mp3"
     fi
done

```

> **sanderd17 said:**
> = a Windows computer?

Linux doesn't need file extensions in fact. So that's why it works on Linux.

You can in any way bash-rename the files.

If they are all in one directory, you can create a script like this:

```

#! /bin/bash

cd  /path/to/music/directory/

for file in *; do
 mv $file $file.mp3
done

```

Disclaimer: I didn't try this script, it will most likely contain a typo. Try it on a test directory first.

---

