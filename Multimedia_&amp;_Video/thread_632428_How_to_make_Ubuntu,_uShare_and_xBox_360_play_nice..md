---
title: "How to make Ubuntu, uShare and xBox 360 play nice."
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by jsnwtsn on 2007-12-05
How to make Ubuntu 7.10(Gutsy), uShare and xBox 360 play nice.

Requirements:
* ubuntu 7.10(gutsy)
* ushare 1.1
* xbox 360 w/ fall 2007 update applied

Finally with the xbox 360 fall update it is possible to play divx/xvid videos. Using the latest ushare and re-associating the ".avi" mime type, it will be possible to stream divx media to the xbox 360. Making the xbox 360 the media center it should have always been.

1. Update your xbox 360. By connecting to "xBox Live" it should prompt you to download the update.

2. Install uShare. 

uShare requires the lib "libdlna", so we will download that and install first:
```

wget http://www.geexbox.org/debian/pool/main/libdlna/libdlna0_0.2.3-0ubuntu1_i386.deb
```
```

sudo dpkg -i libdlna0_0.2.3-0ubuntu1_i386.deb
```

Now download and install uShare:

```
wget http://www.geexbox.org/debian/pool/main/ushare/ushare_1.1-0ubuntu1_i386.deb
```

```
sudo dpkg -i ushare_1.1-0ubuntu1_i386.deb
```

3. Configure ushare

Edit the file "/etc/ushare.conf" to your liking(you need to add you content directory):

```
sudo nano /etc/ushare.conf
```

4. Change mime type for ".avi" files

```
sudo nano :/usr/share/mime/packages/freedesktop.org.xml
```

edit the line:
```
<mime-type type="video/x-msvideo">
```

to this:
```
<mime-type type="video/x-ms-wmv">
```

5. Restart Gnome
 
Restart Gnome by logging out or simply reboot.

6. Start ushare

to start ushare with xbox compatibility:
```
ushare -x
```

7. Watch your divx video.
On your xbox, go to the "Media" blade, then select "Video", then press the "X" button to select your media source. The xbox should find your ushare server at this point. 

Enjoy!

---

### Post by TheAL76 on 2007-12-05
Can't wait to go try this at home

I tried uShare right before the new Xbox update, and I had 2 questions that perhaps you can answer:

1. How can I have Pidgin and uShare work at the same time?
2. Is it possible for the Xbox to stream my mp3s? I had heard that the Xbox treats ANY mp3 as if it's pirated, and that you have to rip your music straight to the Xbox from a CD.

---

### Post by ieatkittens on 2007-12-06
How do you edit the mime type if you aren't running gnome?

Do I need to uninstall ushare and build it from source?

---

### Post by jsnwtsn on 2007-12-06
A Better " How to make Ubuntu, uShare(from source) and xBox 360 play nice."


Apologies to everyone for my previous "How-To", it was more of a "How-Not-To". A lot of people where having problems, and my "How-To" only worked if you changed the file extension...which is lame. 

So here is the corrected way to get Ubuntu, uShare & your xbox 360 to play nice. Once installed you should be able to stream divx video files that have the ".avi" extension to your xbox 360. 

Some folks have asked about streaming mp3 files, i have yet ti figure this out, when/if i do i will post how.

Requirements:
* ubuntu 7.10(gutsy)
* xbox 360 w/ fall 2007 update applied
* libupnp
* libdlna
* ushare 1.1 source

Update your xbox 360. By connecting to "xBox Live" it should prompt you to download the update.

Install required libs

Install the UPNP dev libs
```
sudo apt-get install libupnp-dev
```

Download and install the DLNA libs
```
wget http://www.geexbox.org/debian/pool/main/libdlna/libdlna0_0.2.3-0ubuntu1_i386.deb
sudo dpkg -i libdlna0_0.2.3-0ubuntu1_i386.deb
``` 

Download and extract uShare source
```
wget http://ushare.geexbox.org/releases/ushare-1.1.tar.bz2
tar -xvf ushare-1.1.tar.bz2
```

Edit mime.c file. This makes ushare present .avi files to the xbox as a mime type it can play
```

cd ushare-1.1/

nano src/mime.c

```

Change this line:
```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-msvideo:"},
```
to this:
```
{ "avi",   UPNP_VIDEO, "http-get:*:video/x-ms-wmv:"},
```


Now configure, make and install.

```
./configure --log --prefix=/usr --sysconfdir=/etc --disable-dlna
make
sudo make install
```

Edit the file "/etc/ushare.conf" to your liking(you need to set your content directory):
```
sudo nano /etc/ushare.conf
```

start ushare with xbox compatibility:
```
ushare -x
```

On your xbox, go to the "Media" blade, then select "Video", then press the "X" button to select your media source. The xbox should find your ushare server at this point.

hopefully this time it works! ... have fun ;)

---

### Post by JacksonDane on 2007-12-06
Still having trouble, building from source makes my DivX movies show up. But they will not play, I know the files work because I've played them without a problem from a data DVD.

---

### Post by bitshifter1001 on 2007-12-07
My guess is that you have files with the ".divx" extension. Looking at the mime.c file the following

```

{ "divx",  UPNP_VIDEO, "http-get:*:video/x-msvideo:"},

```

has the same content type as avi. Have you tried renaming the files to have an avi extension? If that works, you can either rename all your files or update the divx mime type to x-ms-wmv, recompile and go.

---

### Post by JacksonDane on 2007-12-07
hmmm

I'll look over everything I did again when I get home

They were definitely avi files though (and when I renamed the extension to .wmv they played :confused:)

---

### Post by cornfield on 2007-12-07
It sounds like by changing to .wmv it's a temporary fix. windows software recognises .avi without renaming to .wmv.

Is it truly an open upnp protocol if it were you'd think it would be easier to play files that the console now supports. (is this something on the 360's end?)

Is anyone currently able to stream both music and video (divx/xvid) files to the xbox360 from ubuntu?

Does it work with xubuntu?

finally, is it possible to have ushare run in the background at boot without having to login. I plan on running it on a headless media server. Also will it work with samba? 

would have been so much easier if the xbox 360 understood samba. Like xbmc. 

thanks for the tutorial and all the information guys. :-D

---

### Post by JacksonDane on 2007-12-07
> **cornfield said:**
> It sounds like by changing to .wmv it's a temporary fix. windows software recognises .avi without renaming to .wmv.

Is it truly an open upnp protocol if it were you'd think it would be easier to play files that the console now supports. (is this something on the 360's end?)

Is anyone currently able to stream both music and video (divx/xvid) files to the xbox360 from ubuntu?

Does it work with xubuntu?

finally, is it possible to have ushare run in the background at boot without having to login. I plan on running it on a headless media server. Also will it work with samba? 

would have been so much easier if the xbox 360 understood samba. Like xbmc. 

thanks for the tutorial and all the information guys. :-D

Well it does support the codecs now, and the .avi files works perfectly when burned on a DVD or put on a USB thumb drive. 

And I believe ushare can be run as a daemon

Can't help with the other questions

---

### Post by jabeez on 2007-12-07
For those wondering about MP3 streaming, I've been using TwonkyMedia to stream MP3's and pics to my 360 for a long time and it works great. It also supposedly streams video but I haven't messed with that as I have no need (have a mythtv box hooked to my tv).

---

### Post by Rileymd on 2007-12-07
Ok I am stuck at the step where you need to change the line..Anyone mind telling me how to do this I'm a linux newb :(

---

### Post by bitshifter1001 on 2007-12-07
You need to edit the file mime.c. Use your favorite text editor. Some examples:

change directory to when mime.c resides.

```

# use vi or vim
vi mime.c 


# use pico
pico mime.c


# use nano
nano mime.c

```


Hope that helps.

---

### Post by bartoni on 2007-12-08
This is soo frustrating.

I had this working the other day, I updated mime.c and was happily watching Divx movies. Great.

The next day I get an error from ushare :

"bind: Address already in use"

Lots of tearing of hair, eventually found it was something to do with the telnet connection? Well at least I think it was, disabling with -t and ushare starts up... but now the xbox cannot see the computer!  Do we need telnet on? Or is there something else wrong?

EDIT:  Success!  Some notes :
It works if I disable telnet and web : ushare -t -w -x -f /etc/ushare.conf 
Even then it doesn't always connect, the xbox seems to remember previous connections so it's useful to use the same port number and/or select a different ushare name each time. I seem to get the best results if I start ushare after the xbox.   Lots of old divx files just won't play, and after a failed attempt of an old file it'll often refuse to play a new valid file with the same error. Restarting and going straight to the new file plays without a problem.

---

### Post by Hubris2 on 2007-12-08
For some of us, installing the latest from the repository has changed Ushare from running as an application to running automatically as a Daemon.  On my system, I'm still having problems getting the Daemon to run with the -x parameter so it's in the Xbox-compatible profile.

When you get the 'bind - Address already in use' error it's because Ushare is already running.  You can either kill the process manually, or use /etc/init.d/ushare stop to stop the daemon - then your manual entry will work.

---

### Post by theelk801 on 2007-12-08
I've gotten it to work, but now my xbox doesn't see the files. What should I do?

EDIT: Alright, this is weird. I change the extension on one of them to see if that would fix the problem. Now I can play that file, and all of the files that come after it show but are not playable. Am I gonna have to change all of the extensions?

---

### Post by realityisok on 2007-12-09
There is a new version of ushare available now (1.1a). The avi and divx problem has been fixed.

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

---

### Post by theelk801 on 2007-12-09
How do you update?

---

### Post by realityisok on 2007-12-09
> **theelk801 said:**
> How do you update?

download the the new version from the link above. for some reason the .deb were outdated versions when i updated so you might have to compile the source yourself.

in terminal:

./configure
make install

---

### Post by illbashu on 2007-12-09
i am on the stuck on the part where you type "sudo nano /etc/ushare.conf" in turminal, how do i exit when i am done? there is no exit button and if i just close the turminal it doesn't save.. :(

---

### Post by nodegamra on 2007-12-10
just press Ctrl + X to exit and save after you made your changes by typing Y then hit enter

---

### Post by theelk801 on 2007-12-10
It stopped working for me all of a sudden. Now when I start it it says "Error: no content directory to be shared"

---

### Post by Hubris2 on 2007-12-11
What happens when you start it manually, with the parameter and identify a valid content directory?  Perhaps there's a typo in your config file when identifying the directory?

---

### Post by eldron on 2007-12-13
My error during setup is
Error, libupnp < 1.4.2

Can anyone help me with this?  I am sure it is something simple, but I am still learning.  Thanks!

EDIT:
Got it.  I needed to do a "apt-get install pkg-config" to upgrade the version.

---

### Post by bgreenwood on 2008-01-08
I'm running into the problem where my music is not being displayed correctly. I can add video and pictures without a problem, but when I add music which contains a space in the file name, it does not play. I also am not getting the ID3 tab information from the MP3 file (although upnp may not use ID3). I'm left with music which I can only find by file name.

My video and pictures are also shown in my music list (obviously the .jpeg and .avi are not a music format) and I don't know why. I've configured everything to what the walkthrough says.

Anyone else have the same problem?

Great walkthrough.

---

### Post by scottgun on 2008-01-13
> **eldron said:**
> My error during setup is
Error, libupnp < 1.4.2

Can anyone help me with this?  I am sure it is something simple, but I am still learning.  Thanks!

EDIT:
Got it.  I needed to do a "apt-get install pkg-config" to upgrade the version.

I've got the same issue as eldron.  I installed libupnp v 1.6.3.  For some reason, the config script thinks that 1.6.3 is less than 1.4.2!  

I already have pkg-config installed.  That doesn't seem to be the issue.

```

root@gun1:./configure --enable-dlna --with-libupnp-dir=/usr/local/lib/
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Checking for libthreadutil ...
Checking for libupnp >= 1.4.2 ...
Error, libupnp < 1.4.2 !

```
:confused:

---

### Post by mkzimms on 2008-01-13
same issue here... bump

```
mikez@twinkie:~/ushare-1.1$ ./configure --log --prefix=/usr --sysconfdir=/etc --disable-dlna
Checking for compiler available...
Checking for locales ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Checking for libthreadutil ...
Checking for libupnp >= 1.4.2 ...
Error, libupnp < 1.4.2 !
See file "config.log" produced by configure for more details.

```

from my config.log

```
pkg-config libupnp --atleast-version=1.4.2
./configure: 642: pkg-config: not found
Error, libupnp < 1.4.2 !

```

---

### Post by scottgun on 2008-01-13
I've been researching this all day.  First, it's worth mentioning that I'm running dapper lts 6.0.6.  The only reference I could find related to this issue is from [a linuxquestions.org thread]("http://www.linuxquestions.org/questions/ubuntu-63/howto-install-ushare-0.9.6-in-ubuntu-6.06-lts-for-newbies-like-myself-550484/").  The only way that guy could get this to work was to revert to ushare version 0.9.6.

I tried this and I was able to configure and install a makefile.  The first time that I tried to run uShare, I received some missing library errors.  The libraries were there, just not where uShare was looking for them.  I fixed the errors with symlinks like this:

```

root@gun1:/lib/ushare-0.9.6# ushare --help
ushare: error while loading shared libraries: libupnp.so.3: cannot open shared object file: No such
file or directory
root@gun1:/lib/ushare-0.9.6# whereis libupnp.so.3
libupnp.so: /usr/local/lib/libupnp.so.3 /usr/local/lib/libupnp.so
root@gun1:/lib/ushare-0.9.6# ln -s /usr/local/lib/libupnp.so.3 /usr/lib/libupnp.so.3
root@gun1:/lib/ushare-0.9.6# ushare --help
ushare: error while loading shared libraries: libixml.so.2: cannot open shared object file: No such
file or directory
root@gun1:/lib/ushare-0.9.6# whereis libixml.so.2
libixml.so: /usr/local/lib/libixml.so.2 /usr/local/lib/libixml.so
root@gun1:/lib/ushare-0.9.6# ln -s /usr/local/lib/libixml.so.2 /usr/lib/libixml.so.2

```

Presto! I've got uShare.  Unfortunately, my problems aren't over.  I tried to mount my first directory and I get the "Cannot register UPnP device" error.

```

root@gun1:/lib/ushare-0.9.6# ushare --help
Warning: can't parse file "/etc/ushare.conf".
uShare (version 0.9.6), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2006, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.

Usage: ushare [-n name] [-i interface] [-p port] [-c directory] [[-c directory]...]
Options:
 -n, --name=NAME        Set UPnP Friendly Name (default is 'uShare')
 -i, --interface=IFACE  Use IFACE Network Interface (default is 'eth0')
 -p, --port=PORT        Forces the HTTP server to run on PORT
 -c, --content=DIR      Share the content of DIR directory
 -w, --no-web           Disable the control web page (enabled by default)
 -v, --verbose          Set verbose display
 -D, --daemon           Run as a daemon
 -V, --version          Display the version of uShare and exit
 -h, --help             Display this help
root@gun1:/lib/ushare-0.9.6# ushare -n gun1 -c /mnt/ntfs3/Scott/
Warning: can't parse file "/etc/ushare.conf".
uShare (version 0.9.6), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2006, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.1.101:49152
Cannot register UPnP device
Stopping UPnP Service ...
root@gun1:/lib/ushare-0.9.6#
```

Note the 'Warning: can't parse file "/etc/ushare.conf"' error.  [Further research]("http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/") leads me to believe this can be corrected by uninstalling and recompiling with the correct --prefix= parameter.

Thoughts:
[LIST=1]
[*]Help with the above would be helpful
[*]Help getting the dependency issues with version 1.1a resolved would be ideal.
[/LIST]

---

### Post by mkzimms on 2008-01-13
got it working with this tutorial... [http://domesdomain.de/blog/2008/01/08/howto-xbox-360-videostreaming-mit-ushare/](http://domesdomain.de/blog/2008/01/08/howto-xbox-360-videostreaming-mit-ushare/)

as far as ive been reading, unfortunately due to Microsoft's crappy implementation of upnp all your songs come up in one single folder... so when you hit songs, you get all your pictures moves, and any other files you have sitting in the path.  no sorting of any kind, that's crap.  if anyone knows a work around to this other than setting up different ushare process with a different path for each type of media then let me know.  

until then looks like ill be uninstalling all of this and setting up fuppes because it supports vfolders.

---

### Post by scottgun on 2008-01-13
I took a look at that link again.  I manually constructed my ushare.config file and that removed my 'Warning: can't parse file "/etc/ushare.conf"' error.  It's still not working though...

```

root@gun1:/home/scott# ushare -n gun1 -c /mnt/ntfs3/Scott/
uShare (version 0.9.6), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2006, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.1.101:49592
Cannot register UPnP device
Stopping UPnP Service ...

```

---

### Post by toran on 2008-01-22
I've installed and configured ushare, but when I look for media sources on my xbox I don't see any. Would this have something to do with the fact that I'm on a university campus network with dynamic IPs and such? Is there any way to make it work?

---

### Post by steelmole on 2008-01-25
I'm trying to get this to work.  It seems like it's installed ok, I did it from apt-get.  When I try to run it it says 

```
laurie@laurie-desktop:~$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.100:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/sda5
Found 3578 files and subdirectories.

```

How can I sort out the eht0 is down part?

---

### Post by Eluzion on 2008-01-29
Mine says eth0 is down as well but works... kinda.

I have to type in ushare -t or -x or -w (just ushare alone doesn't work even though my config file is setup) a few times and eventually my 360 will see it.

Is there any way to make uShare start up on boot? Not at login, but at boot since I'm running it on a dedicated Ubuntu server install.

---

### Post by sic777 on 2008-02-02
I'm getting this error when attempting so star t Ushare
```
sic@sic-linny:/$ ushare -p 49154 -o -n sic -x -c /home/sic/Videos
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Cannot initialize UPnP subsystem
Stopping UPnP Service ...

```
I have installed upnp by 
```
sudo apt-get install libupnp-dev
```
Am i missing something?

---

### Post by Toniio on 2008-02-03
I've got a problem with ushare.

When I try to play music on my xbox 360, my music are not ranked by albums or artists...
It's horrible when you've got more than 1000 musics on your computer!!


PS:

Sorry for my english, I'm french :(

EDIT : We are two

> **bgreenwood said:**
> I'm running into the problem where my music is not being displayed correctly. I can add video and pictures without a problem, but when I add music which contains a space in the file name, it does not play. I also am not getting the ID3 tab information from the MP3 file (although upnp may not use ID3). I'm left with music which I can only find by file name.

My video and pictures are also shown in my music list (obviously the .jpeg and .avi are not a music format) and I don't know why. I've configured everything to what the walkthrough says.

Anyone else have the same problem?

Great walkthrough.

---

### Post by cub on 2008-02-07
> **realityisok said:**
> There is a new version of ushare available now (1.1a). The avi and divx problem has been fixed.

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)
Does that mean that I didn't need to do the mime change? I just installed ushare 1.1a following the instructions on the first page and it works great. However I'm curious if the mime change wasn't necessary?

---

### Post by tubo on 2008-02-11
i use fuppes , not ushare. Works well for me for both 360 and ps3. 

[http://fuppes.ulrich-voelkel.de/features/](http://fuppes.ulrich-voelkel.de/features/)

Also the UPNP server built into MythTV works for PS3, havent tried if it also does for 360, but i think it would

tubo

---

### Post by slick_nick on 2008-02-16
I'm still having the "ushare: error while loading shared libraries: libixml.so.2: cannot open shared object file: No such file or directory" problem.  
Symbolic links are up; "whereis libixml.so.2" returns:  /usr/lib/libixml.so.2 /usr/local/lib/libixml.so.2

Any ideas?

---

### Post by dahli.llama on 2008-02-18
I'm going through this with an Ubuntu 7.10 Server install and when I do the ./configure, I get the following output:

```

Checking for compiler available...
Checking for locales ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Error, can't find libixml !
See file "config.log" produced by configure for more details.

```

Config.log has this at the end:
```

BEGIN /tmp/ushare--12919-.c
     1  #include <upnp/ixml.h>
     2  int x;
END /tmp/ushare--12919-.c
gcc -I.. -W -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_GN$
/tmp/ushare--12919-.c:1:23: error: upnp/ixml.h: No such file or directory
Error, can't find libixml !

```

Any ideas?

Edit:  I got it to work.  I just needed to do sudo apt-get install libupnp-dev.  And then it worked great.

---

### Post by slick_nick on 2008-02-18
> **slick_nick said:**
> I'm still having the "ushare: error while loading shared libraries: libixml.so.2: cannot open shared object file: No such file or directory" problem.  
Symbolic links are up; "whereis libixml.so.2" returns:  /usr/lib/libixml.so.2 /usr/local/lib/libixml.so.2

Any ideas?

Nevermind...installed libupnp-dev and it started up.

---

### Post by cub on 2008-03-01
When I start my computer ushare starts automatically. However I can't connect to it from my xbox360 then so each time I have to kill the ushare process and manually start it with ushare -x. And it works like a charm.

Can I stop ushare from autostarting and only start it manually? Or can I configure something so when it autostart it starts "working"?

---

### Post by NaterGator on 2008-03-04
Ushare users who are looking for wma metadata support (sorting by artist, album, genre, etc) on the Xbox360 should check out this thread about fuppes:
[http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=2&t=13#p97](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=2&t=13#p97)

We've made progress and I've been able to make fuppes do what the ushare developers seem resilient to do.


Best of luck!
-----Nate

---

### Post by Rogers on 2008-03-05
I just followed the first post and made a KICKASS media machine out of my XBOX.  

NOTE TO ALL: if your messsing with(restarting/changing stuff) the server the xbox will stop talking to it.  
[B]
Make sure to cycle the power on the xbox if you cycle the server or you'll get REALLY frusterated.[/B]

---

### Post by cub on 2008-03-12
> **cub said:**
> When I start my computer ushare starts automatically. However I can't connect to it from my xbox360 then so each time I have to kill the ushare process and manually start it with ushare -x. And it works like a charm.

Can I stop ushare from autostarting and only start it manually? Or can I configure something so when it autostart it starts "working"?

Noone??

---

### Post by Dawnrazor on 2008-04-18
I do not understand Point 3

```

3. Configure ushare

Edit the file "/etc/ushare.conf" to your liking(you need to add you content directory):

Code:

sudo nano /etc/ushare.conf


```

is there an Example out there what lines I have to edit

---

### Post by Dawnrazor on 2008-04-19
OK i have it

but now the XBOX360 tells me by every File (avi, mpg...) it is not supported

whats wrong?

---

### Post by Dawnrazor on 2008-04-19
Me again :D

I found the solution


I must download an update from XBOX Live


1. Go to the Marketplace area of the Xbox Dashboard and select Game Store, All Games.
2. Select Optional Media Update twice (once from All Games and again from the Optional Media update screen), then Confirm Download.
3. Once your download is complete, select Continue and return to the Xbox Dashboard (press BACK or B three times).

---

### Post by The Fold on 2008-04-21
I just install ushare directly from the repository and setup the shares in /etc/ushare.conf

If I start it via the service (i.e. sudo /etc/init.d/ushare start) then my 360 can't see it, but if I start from the terminal with just ushare -x it works fine!

I'm not sure what is working differently between the config file running the service and running it normally :confused:

---

### Post by cosmicthoughts on 2008-04-24
> **cub said:**
> Noone??
Now you need to edit /etc/init.d/ushare

 gksudo gedit /etc/init.d/ushare

You’ll see a bunch of variables PATH, NAME, DESC…. You need to ADD under CONFIGFILE..

 CONFIGFILE=/etc/ushare.conf
 USHARE_OPTIONS="-x"

---

### Post by fenrir12 on 2008-04-26
Does anyone know if the new rhythmbox upnp plugin can be configured to work with xbox 360?

---

### Post by fenrir12 on 2008-04-29
bump

---

### Post by cub on 2008-05-04
> **cosmicthoughts said:**
> Now you need to edit /etc/init.d/ushare

 gksudo gedit /etc/init.d/ushare

You’ll see a bunch of variables PATH, NAME, DESC…. You need to ADD under CONFIGFILE..

 CONFIGFILE=/etc/ushare.conf
 USHARE_OPTIONS="-x"

I did that when installing but it doesn't change anything. Still need to kill the runnin ushare and start it manually everytime I reboot.

---

### Post by ogi010 on 2008-05-08
I would also like to know how I can go about getting uShare to automatically start upon boot up.  I'm a bit of a linux n00b, so I may need some hand holding (although I did get it to work when manually started :D ).

Ogi

---

### Post by vh1 on 2008-05-10
you shouldn't edit the /etc/init.d/ushare script when there is a perfectly good (and expected) ushare.conf in /etc

in /etc/ushare.conf change ENABLE_XBOX= to USHARE_ENABLE_XBOX= on line 41. now if you use /etc/init.d/ushare start or just plain run the ushare command they will both load the xbox 360 profile

---

### Post by cub on 2008-05-10
> **vh1 said:**
> you shouldn't edit the /etc/init.d/ushare script when there is a perfectly good (and expected) ushare.conf in /etc

in /etc/ushare.conf change ENABLE_XBOX= to USHARE_ENABLE_XBOX= on line 41. now if you use /etc/init.d/ushare start or just plain run the ushare command they will both load the xbox 360 profile
Yes, but I still need to kill the ushare running on startup otherwise my xbox 360 won't find anything.

---

### Post by stewils on 2008-05-16
I've added content /media/sbd where my media is in the 

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2

USHARE_DIR=/media/sbd/

bit of the config file, but upon starting ushare it says:

Error: no content directory to be shared.

WHY?????

---

### Post by Baelus on 2008-05-16
USHARE_DIR=/media/sbd/

Maybe it should be /media/**sdb**

---

### Post by stewils on 2008-05-19
nope, media sbd is where my external usb is mounted to....

---

### Post by Baelus on 2008-05-19
Right you are. I'm sharing an external usb hdd as /media/wd and ushare sees it. No offense, but the external is mounted, yes?

The only way I can recreate the "Error: no content directory to be shared" message is to not specify any directory at all (either in /etc/ushare.conf or on the command line).

If I give it an incorrect directory (such as /media/glarb, which doesn't exist on my system :)) it gives this error: ```
scandir: No such file or directory.

```
Judging from that it looks like Ushare thinks nothing has been set for it to share.

Try from the command line with this:

```
ushare -c /media/sbd
```

That's about all I can think of right now.

- B

---

### Post by stewils on 2008-05-19
Cheers, that got it....almost :)
An errant thought...could the not finding prob be due to how I've set up my fstab file to mount the external usb?
now i get, but the xbox dosn't pick it up, and my interface eth0 is down.

```

Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.1.3:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/sbd
Found 200 files and subdirectories.

```

---

### Post by Baelus on 2008-05-19
Alright, we have some progress.

I also get the "eth0 is down" and "recheck configuration" errors, but it still seems to stream just fine.

Try adding a -x to the cli, like this:

```
ushare -c /media/sbd -x
```

That should get the xbox friendly mode to kick in. The output should have this in it:

```
Listening on telnet port 1337
Initializing UPnP subsystem ...
**Starting in XboX 360 compliant profile ...**
UPnP MediaServer listening on 10.0.0.5:49152
Sending UPnP advertisement for device ..
```

To make it permanent set the option to ENABLE_XBOX=yes in /etc/ushare.conf

That should do it. In theory, anyway.

- B

---

### Post by stewils on 2008-05-20
Yep, thats hit the spot.  Streaming video sucess.  Thank you.

---

### Post by Baelus on 2008-05-20
Glad to hear it. Enjoy.

- B

---

### Post by vineethtuluri on 2008-05-22
Guys i keep getting this message
```
vineeth@vineeth-laptop:~$ ushare -x -f /etc/ushare.conf
Can't find interface eth0.
Recheck uShare's configuration and try again !

```

This is how my ushare.conf looks like

```
# /etc/ushare.conf
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49592

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/vineeth/Music,/home/vineeth/Pictures,/home/vineeth/Videos

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=TRUE

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=


# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=yes

```

I am trying to get my Xp machine to say that " Ushare upnp sevice is available. I am new to ubuntu so i am just getting started.

---

### Post by Baelus on 2008-05-22
My /etc/ushare.conf file has this at the beginning:

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare
```

Try this:

```
sudo dpkg-reconfigure ushare
```

That will take you through a setup process in the command line window.

It will eventually ask you to choose a network interface to use and then list those available.

See if eth0 is in there. If it is then things may be more complicated.

If not then you'll need to bring up eth0 using this:

```
sudo ifconfig eth0 up
```

and then try again.

See how that goes.

- B

---

### Post by vineethtuluri on 2008-05-22
> **Baelus said:**
> My /etc/ushare.conf file has this at the beginning:

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare
```

Try this:

```
sudo dpkg-reconfigure ushare
```

That will take you through a setup process in the command line window.

It will eventually ask you to choose a network interface to use and then list those available.

See if eth0 is in there. If it is then things may be more complicated.

If not then you'll need to bring up eth0 using this:

```
sudo ifconfig eth0 up
```

and then try again.

See how that goes.

- B

Thank you

I got it to work. I forgot to plug in my ethernet cable. Sometimes i can be dumb:lolflag:. My windows computers popped up the messages. But i cant get the media to display and play. 
How can i set it for wireless access? Do i change eth0 to eth1?

---

### Post by Baelus on 2008-05-22
Don't worry. You're not alone when it comes to 'facepalm moments'! #-o

I'm not familiar with sharing to a windows machine, but from what I gather you need a UPNP client on XP to access ushare. It looks like the built-in Windows upnp backend is working fine if it's giving you those pop-up messages. I've seen posts that say Windows Media Player 11 can act as a upnp server, but there are conflicting reports on whether it can behave as a client as well.

Is there a reason you'd prefer to use ushare instead of a regular samba network share? 
You can use ushare for the 360 and a samba share for the XP machine. They won't have a problem with each other.

Wireless is quite the challenge in itself. We'll get to that after sorting out sharing with the XP machine.

- B

---

### Post by vineethtuluri on 2008-05-22
> **Baelus said:**
> Don't worry. You're not alone when it comes to 'facepalm moments'! #-o

I'm not familiar with sharing to a windows machine, but from what I gather you need a UPNP client on XP to access ushare. It looks like the built-in Windows upnp backend is working fine if it's giving you those pop-up messages. I've seen posts that say Windows Media Player 11 can act as a upnp server, but there are conflicting reports on whether it can behave as a client as well.

Is there a reason you'd prefer to use ushare instead of a regular samba network share? 
You can use ushare for the 360 and a samba share for the XP machine. They won't have a problem with each other.

Wireless is quite the challenge in itself. We'll get to that after sorting out sharing with the XP machine.

- B

Making Upnp work on Ps3 and 360 was not tough. I can access and play some of my media. 

My goal is make my ubuntu laptop act like a service to get media on my network. Samba works perfect, but there is a reason why i am not taking that approach. Let me just say, being able to access media on a commercial product and also able to add/remove media on that device. It is just how you use a USB drive. When there is a USB drive on ur computer, the computer notifies its presence and u can play/add/remove whatever content is on it. I achieved the first step with ur help i.e device discovery, now i am figuring out how to play the media. I will have to see whether WMP 11 detects my media server. I also heard vlc is a good upnp player. 

I have never used ubuntu or linux before and it is a big learning curve.

---

### Post by Baelus on 2008-05-22
Check this entry in wikipedia:

[http://en.wikipedia.org/wiki/UPnP_AV_MediaServers]("http://en.wikipedia.org/wiki/UPnP_AV_MediaServers")

It has a list of servers and clients for upnp media sharing. Might be something in there you can use.

For someone new to linux you're not doing too bad. Keep going.

- B

---

### Post by CyphirX on 2008-05-22
I've been following this guide and unfortunately I'm getting no joy :(
I've avoided making any entries in the route file as people have been able to get away without doing that.  

Here's the output:
```

me@myserver:~/tmp/ushare-1.1a$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.9:49200
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /vol/Storage/Movie
Found 72 files and subdirectories.

```

I've tried following the other things said here about the eth being down.  Here's the ouput of ifconfig -a
```

me@myserver:~/tmp/ushare-1.1a$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:49:17:4c:e3  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:49ff:fe17:4ce3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112013468 (106.8 MB)  TX bytes:20028792 (19.1 MB)
          Interrupt:18 Base address:0xf000 

eth1      Link encap:Ethernet  HWaddr 00:50:fc:e5:a7:60  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116746 (114.0 KB)  TX bytes:31184 (30.4 KB)
          Interrupt:17 Base address:0xf200 

eth2      Link encap:Ethernet  HWaddr 00:15:58:25:23:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109156 (106.5 KB)  TX bytes:19057 (18.6 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2415 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133236 (130.1 KB)  TX bytes:133236 (130.1 KB)

```

Lastly, here's the ushare.conf that I've run it against a few times
```

# /etc/ushare.conf
# Configuration file for uShare

USHARE_NAME=Media
USHARE_IFACE=eth0
USHARE_PORT=49200
USHARE_TELNET_PORT=
USHARE_DIR=/vol/Storage/Movie
USHARE_OVERRIDE_ICONV_ERR=
ENABLE_WEB=no
ENABLE_TELNET=no
ENABLE_XBOX=yes
ENABLE_DLNA=no

```


I guess is there anything obvious that someone can suggest to try?

---

### Post by Baelus on 2008-05-23
That all looks fine.

The first time I set things up I did add the 239.0.0.0 using route. Looking at it now, though, I don't see it listed, so I'm not sure if it persists or not.

How are you trying to connect from the 360 though?

What tripped me up at first was thinking I had to go through the Media Centre option. I couldn't get past a page that gave some sort of code to use and advice on how to get a Windows Media Centre pc working with it (which I didn't have of course).

After a lot of confusion I realised I had to select Video and then press the X button to "Change Video Source". That gave me a page where I could select Console or ushare to connect to. In your case though it would show "Media" (i.e. USHARE_NAME= is used).

Just a thought. Otherwise, the config files look ok.

- B

---

### Post by CyphirX on 2008-05-23
Ya, I've gone through Video then hit the X button.  Unfortunately though it isn't grabbing anything. 

In what order are you starting the application and console up?

---

### Post by Baelus on 2008-05-23
Usually 360 first, ushare second. But play around with it.

I can change share directories while the xbox is connected (bring down ushare, make changes, restart ushare) and I don't have to restart the console to see the changes.

Some things I can think of:

1 My xbox is using static ip, not dhcp. Don't think it makes a difference though.

2 Is ushare serving a local or network share? I remember old windows connect didn't like network shares. Maybe try local just to troubleshoot.

3 Iptables firewall set to let things through?

4 What version of ushare are you using? I'm using 1.1a from the .deb on the geexbox site. [http://ushare.geexbox.org/]("http://ushare.geexbox.org/")

Right now I'm kinda taking shots in the dark.

- B

Oh wait! If I start ushare from the command line (ie ushare -x) everything's cool.

If I use "sudo /etc/init.d/ushare start" then nothing works at all. Don't know why, but there it is.

---

### Post by CyphirX on 2008-05-24
1: I haven't hardset the ip address on the xbox, but I'll try that in the morning

2:  The files are all locally mounted

3: No firewall to speak of

4: I've run via source and apt-get

I've got a solution that kinda works I guess running Connect 360 on my Mac laptop, but it's far from ideal and I think it's probably something to do with the damn server.

---

### Post by Baelus on 2008-05-24
> **CyphirX said:**
> 
Lastly, here's the ushare.conf that I've run it against a few times
```

# /etc/ushare.conf
# Configuration file for uShare

USHARE_NAME=Media
USHARE_IFACE=eth0
USHARE_PORT=49200
USHARE_TELNET_PORT=
USHARE_DIR=/vol/Storage/Movie
USHARE_OVERRIDE_ICONV_ERR=
ENABLE_WEB=no
ENABLE_TELNET=no
ENABLE_XBOX=yes
ENABLE_DLNA=no

```


Maybe try ```
ENABLE_DLNA= 
```

Leave it blank.

I get the impression DLNA is necessary for PS3. If you're just trying to link up with a 360 maybe leave it out of the equation.

See if that does something good.

- B

---

### Post by glittalogik on 2008-06-20
Worked perfectly first try in Hardy with uShare and both libs downloaded via APT/Synaptic. Thank you!

---

### Post by Moezzie on 2008-07-13
Installation through apt-get works perfectly and Video streaming works out of the box. Cant seem to get the music and pictures to cooperate though :(

---

### Post by durilka on 2008-07-17
Looks like recent xbox kernels do not work with DLNA(this is PS3 compatibility mode for ushare) set on so turn it off.

As for the /etc/ushare.conf to be used, modify the /etc/init.d/ushare file to following:

USHARE_OPTIONS="-f /etc/ushare.conf" instead of 

USHARE_OPTIONS=

---

