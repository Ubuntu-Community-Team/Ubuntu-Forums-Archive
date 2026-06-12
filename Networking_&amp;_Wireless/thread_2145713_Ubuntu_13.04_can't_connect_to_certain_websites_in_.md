---
title: "Ubuntu 13.04: can't connect to certain websites in both Firefox and Chrome"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by oneau on 2013-05-16
Hello,

I installed Ubuntu 13.04 a few days ago, and found that both Firefox(21.0 and version that comes in ISO image) and Google Chrome([COLOR=#303942][FONT=Ubuntu]26.0.1410.63)[/FONT][/COLOR] won't connect to many sites. 

I **can** connect to all these sites from Windows, using Firefox, Google Chrome and Opera.

Firefox continues to indicate that it is loading the web page, but doesn't show any contents. Chrome will try for a while and then displays "This webpage is not available" message and shows the following at the end of that page:

> [COLOR=#777777][FONT=Helvetica]
Error 7 (net::ERR_TIMED_OUT): The operation timed out.
[/FONT][/COLOR]


Examples of sites I can't visit: 


[LIST]
[*][https://github.com/](https://github.com/) (fails in Firefox and Chrome)
[*][https://bitbucket.org/](https://bitbucket.org/) (works in Chrome; fails in Firefox, but the title of the window does change to the title of bitbucket's website)
[*][http://www.500px.com](http://www.500px.com) (some content shows up in both; but all contents are not loaded)
[*][http://pcdn.500px.com](http://pcdn.500px.com) (won't load content from this site; 500px.com serves images from this host)
[*]mail.yahoo.com (can't connect in both; Error in Chrome is: [COLOR=#777777][FONT=Helvetica]Error 101 (net::ERR_CONNECTION_RESET): The connection was reset.[/FONT][/COLOR])
[/LIST]


Other issues
=========

I am listing these here since these may be related to the above.

+ I can clone repositories from bitbucket, but I can't clone from github --- I get "error: operation timed out".

+ I get the following "error" when trying to install Python packages using pip, but the installation did take place:

> $ pip install ipython
Downloading/unpacking ipython
  Could not fetch URL [https://github.com/ipython/ipython/downloads](https://github.com/ipython/ipython/downloads) (from [https://pypi.python.org/simple/ipython/):](https://pypi.python.org/simple/ipython/):) There was a problem confirming the ssl certificate: <urlopen error _ssl.c:489: The handshake operation timed out>
  Will skip URL [https://github.com/ipython/ipython/downloads](https://github.com/ipython/ipython/downloads) when looking for download links for ipython
  Downloading ipython-0.13.2.tar.gz (6.0MB): 6.0MB downloaded
  Running setup.py egg_info for package ipython
    
Installing collected packages: ipython
  Running setup.py install for ipython
    
    Installing ipcontroller script to /home/phn/.virtualenvs/default2.7/bin
    Installing iptest script to /home/phn/.virtualenvs/default2.7/bin
    Installing ipcluster script to /home/phn/.virtualenvs/default2.7/bin
    Installing ipython script to /home/phn/.virtualenvs/default2.7/bin
    Installing pycolor script to /home/phn/.virtualenvs/default2.7/bin
    Installing iplogger script to /home/phn/.virtualenvs/default2.7/bin
    Installing irunner script to /home/phn/.virtualenvs/default2.7/bin
    Installing ipengine script to /home/phn/.virtualenvs/default2.7/bin
Successfully installed ipython
Cleaning up...




Notes
====

I installed Chrome after installing libudev0 (Downloaded "deb" file from [http://packages.ubuntu.com/quantal/i386/libudev0/download](http://packages.ubuntu.com/quantal/i386/libudev0/download)).

Note that I have none of these issues in Windows.


[Edit: 17 May 2013]

Output from running curl on github.com

> [phn@phn ~ ]
$ curl -I [http://github.com](http://github.com)
HTTP/1.1 301 Moved Permanently
Server: GitHub.com
Date: Fri, 17 May 2013 03:33:08 GMT
Content-Type: text/html
Content-Length: 178
Connection: close
Location: [https://github.com/](https://github.com/)
Vary: Accept-Encoding


[phn@phn ~ ]
$ curl -I [https://github.com](https://github.com)
curl: (35) Unknown SSL protocol error in connection to github.com:443 



[Edit May 18 2013]

I tried to connect to github and bitbucket in a Live session using ISO disk, but couldn't connect using either Firefox or wget.


I hope somebody can help me fix this issue. Not having access to these sites, especially Github, makes Ubuntu unusable.

Thanks,
Prasanth

---

### Post by 2F4U on 2013-05-16
How do you connect to the internet? Instead of assumng that there is a problem with the browser (could be valid if only one browser shows such issues) it could also be a network issue.

---

### Post by oneau on 2013-05-16
I have an ADSL2 modem, and my laptop is connected to the modem using an Ethernet cable. As you say there could be some non-browser issue since I can't "git clone" Github repositories.

But as I mentioned above, I don't run into any of the problems on Windows, and it only affect some sites.

---

### Post by bawkbawkboo1 on 2013-05-18
I also have this issue, but I can't seem to find any particular similairity between the effected websites; it seems random.  Some sites work fine in FIrefox in the tab adjeacent to broken ones, and some, but not all, of the borken ones seem to resolve themeselves and work randomly.  The broken tabs all have the "connecting to www.whatever.com" or "Looking up www.example.org" status.

I can confirm I'm also not having any issues on any browser in Win7 and Chromium on Ubuntu 13.04; it's just Firefox on linux.  I do not know what other system info would be relevant for this thread.

---

### Post by tmahmood on 2013-06-07
Facing similer problem on both of my Ubuntu Laptop and Netbook. I have reinstalled Ubuntu on my Netbook, but no use. For me its Google+, Facebook or any Google Searchs and uploading files. it tries to load the page for a while then just stops and Dropbox keeps trying to upload but it does.

It seems to me a problem related with the Kernel rather than Browser or Internet. Because, On my laptop Internet works fine with 3.5.0-26-generic Kernel, but stops working when I try to use any of the new kernels. Same with the netbook, but as I have reinstalled the netbook I don't have the old kernel any more.

---

### Post by rupert-1 on 2013-11-05
Hello
Did anyone find a solution to this?
I am having a similar problem with one website.  I cannot connect to one url "outlook.office365.com" in any browser (Firefox, Chrome, Opera) on my installation of Ubuntu 13.10 however if I reboot the computer in Mint then the site works fine.  
Any suggestions would be welcome.

---

### Post by pinich2 on 2014-03-14
I have the same problem in Ubuntu 13.10!
Firefox, Chrome, Opera can't open github.com, but whan I switch to win at works.

---

### Post by Vadim G on 2014-10-10
Guys, same thing here with 14.04.4 (it was working from start but after update to 37 kernel by time it is broken, rolling back to older kernels doesn't help, so it might be something else in the update).
I managed to get access back to google resources but not facebook.
This trick with NetworkManager helped: [http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html)
But facebook content from cdns (images, scripts etc.) is not loaded still.

---

