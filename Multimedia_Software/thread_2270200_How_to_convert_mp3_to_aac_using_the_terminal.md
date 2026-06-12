---
title: "How to convert mp3 to aac using the terminal?"
date: 2015-03-21
forum: Multimedia Software
---

### Post by remmas-sido on 2015-03-21
Hello guys 
Is there a way or a command line that let me convert a mp3 audio file to aac audio file?

---

### Post by speartip on 2015-03-21
Not sure about the command line. But I have just tried the program soundconvertor which is in the repos & it converts mp3 to m4a (aac) just fine.

---

### Post by remmas-sido on 2015-03-21
> **speartip said:**
> Not sure about the command line. But I have just tried the program soundconvertor which is in the repos & it converts mp3 to m4a (aac) just fine.

Are you sure,because the last time I tried it I wasn't given the option to convert mp3 to aac. Maybe in the recent version of this software you have this option since you are using 14.04 and I'm using 12.04.

---

### Post by ajgreeny on 2015-03-21
In its simplest form you use command ```
avconv -i filename.mp3 filename.m4a
```using the full pathway if you are not in the folder containing the input file.

You can also use command ```
avconv -i filename.mp3 filename.aac
```though I admit to some confusion over all these different filetypes for audio; I'm not sure of the difference between .m4a and .aac so will leave to to investigate that if you need to or want to.

All of this assumes you have the correct codecs for decoding and encoding audio files of the kind you are dealing with.You may need to ensure you have the libav*-extra packages to be able to encode all these formats.

---

### Post by remmas-sido on 2015-03-21
Is turn out I was wrong

---

### Post by remmas-sido on 2015-03-21
> **ajgreeny said:**
> In its simplest form you use command ```
avconv -i filename.mp3 filename.m4a
```using the full pathway if you are not in the folder containing the input file.

You can also use command ```
avconv -i filename.mp3 filename.aac
```though I admit to some confusion over all these different filetypes for audio; I'm not sure of the difference between .m4a and .aac so will leave to to investigate that if you need to or want to.

All of this assumes you have the correct codecs for decoding and encoding audio files of the kind you are dealing with.You may need to ensure you have the libav*-extra packages to be able to encode all these formats.

Thank you very much, I always like terminal way,because I feels it is more powerful and advanced,but stiil I have one more thing to ask for. For example if I have a folder which contains 25 audio files it will take a long time to convert each file individually,so is there a command line for batch converting?

---

### Post by SeijiSensei on 2015-03-21
```

#!/bin/bash

DIR=/path/to/your files

mkdir $DIR/new

cd $DIR
for f in *.mp3
do
    NAME=$(basename $f)
    avconv -i $f new/$NAME.m4a
done

```

---

