---
title: "recordmydesktop has exited with status: 3328"
date: 2012-01-01
forum: Multimedia Software
---

### Post by beeznet on 2012-01-01
When I had Ubuntu 11.04 I was able to use RecordMySesktop without problems. In fact I have videos in YouTube recorded by this software. Now that I've upgraded to 11.10, I can't use RecordMyDesktop. Error message that shows is:

recordmydesktop has exited with status: 3328

Please advice. Thanks!

---

### Post by beeznet on 2012-02-07
Why hasn't this been answered yet? It's not important for you guys? I'm giving up on Ubuntu! Too bad. I had thought it was a great OS. Apparently no one gives a rat's ***.

---

### Post by anotheruser1 on 2012-05-08
> **beeznet said:**
> When I had Ubuntu 11.04 I was able to use RecordMySesktop without problems. In fact I have videos in YouTube recorded by this software. Now that I've upgraded to 11.10, I can't use RecordMyDesktop. Error message that shows is:

recordmydesktop has exited with status: 3328

Please advice. Thanks!

Maybe it sounds stupid but I've got the same problem on 12.04 and the solution is leave blank the overwrite files box and when you create new capture remove the previous files to prevent overwriting in the same folder where is the working directory. I know it sounds stupid but it is works for me

---

### Post by Vahagn_IV on 2012-10-29
Open Nautilus, go to your home directory, press Ctrl+H to reveal the hidden files. Open .recordMyDesktop for editing or simply type
> gedit ~/.recordmydesktop in the terminal.
There is a field #Filename, which is most likely set to a directory which does not exist. Replace it with /home/yourusername/filename.ogv.

---

