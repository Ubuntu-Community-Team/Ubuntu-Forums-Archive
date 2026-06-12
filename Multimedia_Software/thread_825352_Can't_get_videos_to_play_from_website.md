---
title: "Can't get videos to play from website"
date: 2008-06-10
forum: Multimedia Software
---

### Post by socref on 2008-06-10
Hello, everyone. I am using Ubuntu 7.10. Totally frustrated trying to get videos to play from this site: [www.mlsnet.com](www.mlsnet.com)

On the home page (this is the US pro soccer league) just a little way down on the left there is a section titled: MLS BEHIND THE SCENES VIDEO. Immediately to the right of that is a section titled: VIDEO.

Within both of these sections are various videos, none of which will play on my pooter. I only get a green pop-up screen that has in the middle: "MLSnet.com" and says "loading" in the upper left corner. But nothing happens after that. The screen just stays that way and never loads anything.

The site's "help" link says that you must have Windows Media Player to view videos. But is there a way to get around this Windoze-centric website and view the videos on an Ubuntu 7.10 system?

Many thanks!
socref

---

### Post by socref on 2008-06-16
Anyone? Ideas on how to get these videos to play?
Thanks.
socref

---

### Post by cozmicharlie on 2008-06-16
Have you tried the solutions from this post?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Pjotr123 on 2008-06-16
How-to for 8.04, but mostly applicable to 7.10 as well:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

### Post by wolfen69 on 2008-06-16
works for me.

after many installs of ubuntu on many different machines. the following method is pretty much guaranteed to work. first, do [this]("https://help.ubuntu.com/community/Medibuntu") . then do ```
sudo apt-get remove totem-mozilla
``` then ```
sudo apt-get install mplayer-mozilla vlc
``` you are done.

---

### Post by socref on 2008-06-16
> **cozmicharlie said:**
> Have you tried the solutions from this post?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I'll check this out. Thanks for the URL.
socref

---

### Post by socref on 2008-06-16
> **Pjotr123 said:**
> How-to for 8.04, but mostly applicable to 7.10 as well:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

And I'll check this one too. 
Thanks!
socref

---

### Post by socref on 2008-06-16
> **wolfen69 said:**
> works for me.

after many installs of ubuntu on many different machines. the following method is pretty much guaranteed to work. first, do [this]("https://help.ubuntu.com/community/Medibuntu") . then do ```
sudo apt-get remove totem-mozilla
``` then ```
sudo apt-get install mplayer-mozilla vlc
``` you are done.

And I will give this one a look as well.
Again, thanks. 
socref

---

### Post by socref on 2008-06-16
> **wolfen69 said:**
> works for me.

after many installs of ubuntu on many different machines. the following method is pretty much guaranteed to work. first, do [this]("https://help.ubuntu.com/community/Medibuntu") . then do ```
sudo apt-get remove totem-mozilla
``` then ```
sudo apt-get install mplayer-mozilla vlc
``` you are done.

Didn't work. :confused:  I already had Medibuntu set as a repository. 

Here is the output from the terminal. As you can see at the end, no mplayer-mozilla package was found. Any suggestions?

gil@phred:~$ sudo apt-get remove totem-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  totem-mozilla
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 279kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 98337 files and directories currently installed.)
Removing totem-mozilla ...
gil@phred:~$ sudo apt-get install mplayer-mozilla vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mplayer-mozilla
gil@phred:~$

---

### Post by socref on 2008-06-16
> **Pjotr123 said:**
> How-to for 8.04, but mostly applicable to 7.10 as well:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Tried this. Installed anything I did not already have. Still won't play the videos described in my opening post. :(

Now what, coach? 
Thx.
socref

---

### Post by cozmicharlie on 2008-06-16
> **socref said:**
> 

Now what, coach? 
Thx.
socref

Inbound to Kobe and let him take the three pointer!

I was able to play them but not in mplayer.  When I try and open them in the browser all I get is sound.  So what I did was I right clicked and went to properties and got the url for the video then pasted it into vlc.  I was able to watch the video. This is how I did it:

Open VLC>menu>file>open network stream>network tab>HTTP/HTTPS/FTP/MMS and and paste the url below in the dialog box.  Click OK and play (hopefully).

mms://a1503.v115042.c11504.g.vm.akamaistream.net/7/1503/11504/v0001/mlbmls.download.akamai.com/11504/2008/shows/t280/061508_tfctv_col_postgame.wmv

---

### Post by socref on 2008-06-17
> **cozmicharlie said:**
> Inbound to Kobe and let him take the three pointer!

I was able to play them but not in mplayer.  When I try and open them in the browser all I get is sound.  So what I did was I right clicked and went to properties and got the url for the video then pasted it into vlc.  I was able to watch the video. This is how I did it:

Open VLC>menu>file>open network stream>network tab>HTTP/HTTPS/FTP/MMS and and paste the url below in the dialog box.  Click OK and play (hopefully).

mms://a1503.v115042.c11504.g.vm.akamaistream.net/7/1503/11504/v0001/mlbmls.download.akamai.com/11504/2008/shows/t280/061508_tfctv_col_postgame.wmv

Interesting. Thanks. :) 
Still looking for a one-click means of playing the videos rather than cutting and pasting into the VLC player.
socref

---

### Post by cozmicharlie on 2008-06-17
> **socref said:**
> Interesting. Thanks. :) 
Still looking for a one-click means of playing the videos rather than cutting and pasting into the VLC player.
socref

You could try using the mozilla plugin vlc rather than mplayer.  It is in Synaptic.

---

### Post by socref on 2008-06-19
> **cozmicharlie said:**
> You could try using the mozilla plugin vlc rather than mplayer.  It is in Synaptic.

I'll give it a try and report on the results.
Thx
socref

---

