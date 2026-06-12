---
title: "mencoder output naming"
date: 2008-06-16
forum: Multimedia Software
---

### Post by ResilientBiscuit on 2008-06-16
I am new to Linux and am trying to figure out how to do something here...

I know the very basics of mencoder, so I can successfully 

```
mencoder input.avi -o output.avi -ocv blah blah balh
```

and it works on one file. (I am trying to update some old .avi files to play on my Xbox 360 if anyone is wondering why I am doing this.)

But lets say I have a directory of files I want to re-encode and they are named 1.avi, 2.avi and so on... and I want to, in one go, re-encode all of them and name them like 1-new.avi, 2-new.avi etc.

Is there a way to do this?  I assume I must be able to do like ```
mencoder *.avi -o something
``` but I don't know what to put there.

Thanks for any help you might be able to provide!

Justin

---

### Post by hypocratus on 2008-06-17
Here is a script that should work. Just put the following lines in a file with the extension .sh and make that file executable.

#!/bin/bash
for i in *.avi; do
     mencoder -ovc <whatever> -oac <whatever> -o new-$i $i
done

Put the script file in the directory where you have the video files and run it. That should do it. Remember to replace the <whatever> with the settings you want. Hope that helps.

---

### Post by donkeyX on 2008-07-08
Hey don't you have to convert the video to wmv and the audio to wma to play on the 360. As this is exactly what i am trying to do and have been for days now :( . Anyway, i have gotten this far atm but still no luck as the audio is still in ac3.

mencoder test.avi -o output.wmv -ovc lavc -lavcopts vcodec=wmv2 acodec=wmav2 -oac copy

I thought this would get it because i have the acodec=wmav2 but it just seems to be ignored. I have no idea what all of the options are so i might be way of but at the moment it will convert the video to windows media format but the audio stays the same. 

Any help would be appreciated.

Cheers Dave

---

### Post by Creative2 on 2008-07-08
see at fuoco tools it has a any to wmv2 it should work

---

### Post by forger on 2008-07-08
Use something like this:
```
i=test.avi; filename=`basename $i|sed -e 's/\.avi$/\.wmv/i'`; echo $filename
```

---

### Post by donkeyX on 2008-07-14
Hey Guys,

I just posted to another thread something that worked for me and seems pretty good.

[http://ubuntuforums.org/showthread.php?p=5382706#post5382706]("http://ubuntuforums.org/showthread.php?p=5382706#post5382706")

Hopefully this helps.

Cheers Dave

---

