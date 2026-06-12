---
title: "Python urllib2 problem: Name or service not known"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by Iskendar on 2012-02-27
Hi all,

 Some time ago I've written some python code to read video data off an IP camera connected via a router to a laptop. Now I try to run this code on a different laptop and router combination, but now I can't access the camera. 
Some minimal example code:
```

import urllib2

url = urllib2.urlopen("http://192.168.1.3/-wvhttp-01-/image.cgi")
```

This fails and returns the error:
```
<urlopen error [Errno -2] Name or service not known
```

When I check further, I cannot access any url via urllib2.urlopen, not the camera nor the router nor localhost. Pinging them poses no problem though, and I can access the video feed and the router admin page in firefox without any issues. 
Searching for the problem turned up [this discussion]("http://forums.gentoo.org/viewtopic-t-556507.html") on the gentoo forums, which didn't provide any solution but did hint that it might be a system-related problem rather than a coding problem. 
I run kubuntu 11.10 on the laptop, the router is not connected to the internet and serves as dhcp server for both the laptop and the camera.

---

### Post by Iskendar on 2012-02-28
Never mind it's a proxy problem. I disabled http_proxy in .bashrc for this, but apparently it was also set in /etc/bash.bashrc and I didn't check for that. 

That did leave me with the problem how I could get my code to work with the proxy enabled. But I found that one too, just put
```

import os
os.environ['http_proxy']=''

```
before importing urllib2.

---

### Post by yaoseq on 2012-12-20
hey Iskendar, I added the import os code into my program but I'm still getting the same error. I'm running ubuntu on a virtual machine and my program is trying to open a lot of urls to try and scrape song lyrics from a site.

```
from bs4 import BeautifulSoup
import os
os.environ['http_proxy'] = ''
from urllib.request import urlopen
from urllib.request import urlretrieve
import re

base = "http://www.hymnal.net/hymn.php/"
ns_urls = []

#this while loop places all the urls for all the new songs into a list
ns = 1
while ns < 391:
	addr = "ns/" + str(ns)
	ns_urls.append(base + addr)
	ns += 1

ns_songs = []
count = 1
#this for loop parses the html found in the urls and places the lyrics into a list
for url in ns_urls:
	soup = BeautifulSoup(urlopen(url))
	print(count)
	count += 1
        """the counter here is see on which url the error arises.
           from what I've seen it changes everytime but is usually around 20 - 40.
	for tag in soup.find_all('div'):
		if tag.has_key('class'):
			if tag['class'][0] == 'main-content':
				str_tag = str(tag)
				ns_songs.append(str_tag)
```

---

