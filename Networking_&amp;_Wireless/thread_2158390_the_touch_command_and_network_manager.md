---
title: "the touch command and network manager"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by kestrel_ on 2013-06-28
This probably isn't really supposed to go in this forum but... should be a quick one.

I was just wondering why in this old thread [http://ubuntuforums.org/showthread.php?t=819726](http://ubuntuforums.org/showthread.php?t=819726)

the user utilizes the touch command on the network manager config files?

What is the point of changing the timestamp or is this actually creating those files?

Thanks!

---

### Post by papibe on 2013-06-28
Hi kestrel_

It's hard to say how things worked back then, but it seems 'touch' is used to created an empty file (since right now those files don't exist).

You can do both create a file and put a line command at the same time:
```
echo "hello" > ./file.txt
```
If you want to do it so the file end up owned by root, it is a little different:
```
sudo bash -c 'echo "hello" > ./otherfile.txt'
```
Does that help?
Regards.

---

