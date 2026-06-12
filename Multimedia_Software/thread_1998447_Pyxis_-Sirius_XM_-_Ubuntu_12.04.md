---
title: "Pyxis -Sirius XM - Ubuntu 12.04"
date: 2012-06-06
forum: Multimedia Software
---

### Post by cheqmate1 on 2012-06-06
Hi, 

Has anyone gotten Pyxis running on 12.04? 

The version in the repos appears to depend on python 2.5, but 12.04 runs python 2.7.

I have not been able to get it running, though I am considering changing the dependency in the pyxis script to 2.7 (not that I have actually looked at it yet). 

Thanks
Cheqmate

---

### Post by cheqmate1 on 2012-06-06
I was able to get it to run by prefacing the pyxis command with the path to python i.e. /usr/bin/python /usr/bin/pyxis

---

### Post by cheqmate1 on 2012-06-25
The above only worked on a box that I had performed an upgrade from Ubuntu 11.10. For another box that I have which I performed a full install of 12.04 from scratch, I had to do the following.

Get the pyxis source code from GitHub - git clone git://github.com/Kasuko/pyxis

Go into the directory which was just downloaded and run the command - sudo python setup.py install

Install Beautiful soup
sudo apt-get install python-beautifulsoup

Edit the BeautifulSoup import lines in the following two scripts to:
from bs4 import BeautifulSoup

/usr/local/lib/python2.7/dist-packages/pyxis/ProviderCanada.py
/usr/local/lib/python2.7/dist-packages/pyxis/ProviderUSA.py

Works like a charm. 

Hooray Pyxis!!!!


PS. I did also run 'sudo apt-get install python-bs4', but I was getting an import error for BeautifulSoup until after running 'sudo apt-get install python-beautifulsoup'

---

