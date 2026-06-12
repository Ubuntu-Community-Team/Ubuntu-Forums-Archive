---
title: "/dev/adsp and /dev/adsp2"
date: 2009-01-27
forum: Mythbuntu
---

### Post by stevanbt on 2009-01-27
Hi,
I've just replaced my nova-t 500 with two nova-s plus cards.  A single card works ok, two cards are causing Myth to get confused.

The problem I have at the moment is that when the pc boots I don't know if I will get a sound device at /dev/adsp or /dev/adsp2 (I can change Myth's config, but the next time it boots I may be referencing a non-existent device).  I assume this problem is caused by the two identical cards.

I have used udev to identify a specific card for using the IR remote - should I do something similar with the sound device?

I can link to the missing device:-
```
sudo ln -s /dev/adsp2 /dev/adsp
```

(or the other way round depending on which device I get) and I get sound.

But I would much prefer to have the same device name each time the box boots.  

Thanks in advance, Steve.

---

### Post by jMon54 on 2009-03-25
Did you ever solve this?  I am having the same issue.

---

### Post by stevanbt on 2009-03-26
Yes I sorted this, it ain't pretty and I'm sure there's a better way, but it works.  All I did was to create an /etc/rc.local like this:-
```

steve@barnaby:~$ more /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# added by sb because audio device doesn't always have the same device name
if [ ! -f /dev/adsp2 ]
then
   ln -s /dev/adsp /dev/adsp2
fi
# sb end

exit 0

```

Then in the audio selection page in myth I link to /dev/adsp.

Hope this helps, Steve.

---

