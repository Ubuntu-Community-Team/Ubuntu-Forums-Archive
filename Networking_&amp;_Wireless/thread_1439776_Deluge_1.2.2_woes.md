---
title: "Deluge 1.2.2 woes"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by steve0961 on 2010-03-26
I've run Deluge for as long as I've used Linux and love this program to death, but 1.2.2 has officially stumped me. Every time I try to connect to the host in the connection manager after running the program, this is what the terminal displays.

```
/usr/local/lib/python2.6/dist-packages/deluge-1.2.2-py2.6.egg/deluge/ui/gtkui/mainwindow.py:62: GtkWarning: Attempting to read the recently used resources file at `/home/steve0/.recently-used.xbel', but the parser failed: Error reading file '/home/steve0/.recently-used.xbel': Is a directory.
  "glade/main_window.glade"))
[ERROR   ] 15:35:09 connectionmanager:454 Connection to host failed..
[ERROR   ] 15:35:10 connectionmanager:454 Connection to host failed..
[ERROR   ] 15:35:10 connectionmanager:454 Connection to host failed..
[ERROR   ] 15:35:11 connectionmanager:454 Connection to host failed..
[ERROR   ] 15:35:11 connectionmanager:454 Connection to host failed..
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.UserError: User aborted connection.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.
[ERROR   ] 15:35:12 connectionmanager:454 Connection to host failed..
[ERROR   ] 15:35:12 connectionmanager:454 Connection to host failed..
```

Any ideas as to what caused this? Or better yet, a solution? Thank you.

---

### Post by steve0961 on 2010-03-26
bump, anyone?

---

### Post by steve0961 on 2010-03-27
bump. no?

---

### Post by McButt on 2010-03-27
It may be a long shot, but are you sure the daemon is running?
Also it might be worth checking the daemon's logs. I don't know if and where it logs by default but you can make it log like this.
```
deluged -d -l /home/USERNAME/deluged.log
```
You have to make sure the log file exists and can be written to by the program before starting it. By putting it in your home directory you should have write access to it.
```
touch /home/USERNAME/deluged.log

```

---

### Post by steve0961 on 2010-03-27
I enabled it to keep a log, this is what it says:

```
[ERROR   ] 11:30:20 main:216 This version of Deluge requires libtorrent >=0.14.9.0!
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/deluge-1.2.2-py2.6.egg/deluge/main.py", line 209, in start_daemon
    Daemon(options, args)
  File "/usr/local/lib/python2.6/dist-packages/deluge-1.2.2-py2.6.egg/deluge/core/daemon.py", line 136, in __init__
    from deluge.core.core import Core
  File "/usr/local/lib/python2.6/dist-packages/deluge-1.2.2-py2.6.egg/deluge/core/core.py", line 36, in <module>
    from deluge._libtorrent import lt
  File "/usr/local/lib/python2.6/dist-packages/deluge-1.2.2-py2.6.egg/deluge/_libtorrent.py", line 60, in <module>
    check_version(lt)
  File "/usr/local/lib/python2.6/dist-packages/deluge-1.2.2-py2.6.egg/deluge/_libtorrent.py", line 53, in check_version
    raise ImportError("This version of Deluge requires libtorrent >=%s!" % REQUIRED_VERSION)
ImportError: This version of Deluge requires libtorrent >=0.14.9.0!
```

So apparently I don't have a new enough version of libtorrent. I'm looking through the repositories in synaptic and the only version of libtorrent I see is 0.12.2, how would I go about finding and installing 0.14.9 or higher?

Thank you for the suggestion too McButt!

---

### Post by McButt on 2010-03-27
How did you install 1.2.2? I'm guessing you downloaded a single .deb file from somewhere?
Anyway, I suggest you add the deluge ppa repository to your /etc/apt/sources.list
Open /etc/apt/sources.list in your favourite text editor (with sudo power) and add these two lines. Replace karmic with your version of ubuntu if you're not on karmic.
```
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu karmic main 
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu karmic main
```
Save the file and run this in a terminal:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
```
Now just run apt-get update and upgrade (or use synaptic if you like). That should give you the files you need and fix your problems :)

---

### Post by steve0961 on 2010-03-27
I actually already have those added to my sources list. That was how I installed the program, through synaptic after adding those repositories. The newest version of libtorrent available in synaptic though is 0.12.2. I even just went an uninstalled, deleted and readded the deluge ppa repositories, and reinstalled all my deluge packages, and it still says the same thing. Terminal still returns the same thing while running the program too:

```
[ERROR   ] 12:42:43 connectionmanager:454 Connection to host failed..
[ERROR   ] 12:42:43 connectionmanager:454 Connection to host failed..
[ERROR   ] 12:42:44 connectionmanager:454 Connection to host failed..
[ERROR   ] 12:42:44 connectionmanager:454 Connection to host failed..
[ERROR   ] 12:42:45 connectionmanager:454 Connection to host failed..
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.
Unhandled error in Deferred:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectionRefusedError: Connection was refused by other side: 111: Connection refused.
[ERROR   ] 12:42:45 connectionmanager:454 Connection to host failed..
[ERROR   ] 12:42:46 connectionmanager:454 Connection to host failed..

```

---

### Post by Cas07 on 2010-03-27
there is libtorrent and libtorrent-rastabar and the latter is the one that Deluge uses. 

check these are installed:
python-libtorrent 0.14.10
libtorrent-rastabar5 0.14.10 


I am in the middle of writing a quick guide to Ubuntu installation but a snippet of this may help you

> 
This command will add the Deluge PPA repository and install the key:
sudo add-apt-repository ppa:deluge-team/ppa

Breakdown of Deluge Packages:
deluge - installs deluged, deluge-common and deluge-gtk

deluged - the deluge daemon
deluge-common - common data files for all interfaces

deluge-gtk - gtk interface
deluge-web - webui interface
deluge-console - console interface

deluge-torrent - a metapackage to handle switching over from the package in previous versions of Ubuntu/Debian
deluge-webui - a metapackage (same as above)

deluge-core - for v1.1.9, do not install

python-libtorrent - required by deluge
libtorrent-rastabar5 - required by deluge


---

### Post by lotharmat on 2010-03-27
I've got similar problems with deluge 1.2.2

I cannot get it to even connect

---

### Post by Cas07 on 2010-03-27
This is actually the same conversation that is being held [here]("http://forum.deluge-torrent.org/viewtopic.php?f=7&t=30525"), i am not going to yoyo between them so i will only answer in the official Deluge support forum.

---

### Post by steve0961 on 2010-03-27
Anyone else have any ideas? this seems to be going nowhere fast.

---

### Post by lotharmat on 2010-03-27
I've just managed to cure mine by:

removing the folder ~/.config/deluge
sudo dpkg -r deluge
restarting deluge.

---

### Post by steve0961 on 2010-03-27
> **lotharmat said:**
> I've just managed to cure mine by:

removing the folder ~/.config/deluge
sudo dpkg -r deluge
restarting deluge.

You have a completely different problem than me? What was the point of telling me this?

---

