---
title: "Control VLC via command line"
date: 2010-01-03
forum: Multimedia Software
---

### Post by minj on 2010-01-03
Everything is plain and simple. I want to know what's the least painful way to control vlc from local command line while having GUI as well?

I would like to e.g. use something like "vlc --pause" in one of my bash scripts to pause music if something hapens. So rc interface is useless, is it not?


Sorry for not making a thorough search on this as the irrelevance of results is beneath me... Well actually I have made it but it was a while ago and to no avail since the new vlc shipped with karmic got rid of the old http interface which allowed to do this just by using wget on an url....

---

### Post by minj on 2010-01-11
BUMP :popcorn:

---

### Post by superbeppe on 2010-04-23
I do this with the rc interface in combination with a small python script:

```

#!/usr/bin/python

import sys
import socket

#change to your vlc socket (in vlc configuration: UNIX socket command input)
SOCK = "/tmp/vlc.sock"

try:
	command = sys.argv[1]
except:
	print "try: %s help\n" % sys.argv[0]
	sys.exit()

s = socket.socket(socket.AF_UNIX)
s.settimeout(0.5)
s.connect((SOCK))
s.send("%s\r" % command)
out = ""

while 1:
	try:
		line = s.recv(1024)
		out += line
	except socket.timeout:
		break
	if line == "":
		break
	
s.close()

print out

```

---

### Post by minj on 2010-05-19
Thanks for the tip, that worked. Anyway what I found strange is I can't get the rc to work by launching vlc without a terminal, any ideas?

Your help is much appreciated.

---

