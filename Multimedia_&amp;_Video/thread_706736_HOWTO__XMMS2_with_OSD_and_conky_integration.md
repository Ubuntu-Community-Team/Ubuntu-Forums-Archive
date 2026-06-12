---
title: "HOWTO:  XMMS2 with OSD and conky integration"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by chocolatetoothpaste on 2008-02-24
[SIZE=6][COLOR=Orange]**HOWTO:  XMMS2 with OSD and conky!!!**[/COLOR][/SIZE]

Hello everyone!!!!

Welcome to my first HOWTO.  I am an intermediate linux user, and this is my first real contribution to the Ubuntu community.  I wrote a bash script a while back to transfer pictures from my camera.  If you need something like this, here is the thread: [http://ubuntuforums.org/showthread.php?t=148949&page=2](http://ubuntuforums.org/showthread.php?t=148949&page=2).  (look at post #16)  Anyway, so a bit about xmms2: [http://wiki.xmms2.xmms.se/index.php/About](http://wiki.xmms2.xmms.se/index.php/About)

I use xmms2, because I tried to make mpd work, but it wouldn't.  It played one song, then choked and I could never fix it.

My system is setup as follows:
Ubuntu 7.10 comman-line install
Openbox 3.4.6.1 & Obconf 2.0.3

I also have conky 1.4.9, compiled from sources, which we will do in this guide!

All right, lets get our hands dirty!

I initially tried to download and compile xmms2 0.4, but after I restarted my computer, it broke and I couldn't fix it :(.  
1.
```

# apt-get install -y xmms2

```This will install all the required files to run xmms2.  Once installation completes, do this:
2.
```

$ xmms2-launcher

```This will start the xmms2 daemon.  Then, type:
3.
```

$ xmms2 add /path/to/your/music/song.mp3 or xmms2 radd /path/to/music

```Make sure you have the proper codecs installed to play your collection.  I replace 'song.mp3' with '*' and it adds all my music.

4.
```

$ xmms2 play

```You should hear music!  Make sure the volume is up, and the proper channels are unmuted.

Now, let's build conky.

1.  Take care of dependencies:
```

 # apt-get install libxmmsclient-dev build-essential libx11-dev libxext-dev libxdamage-dev libxft-dev libglib2.0-dev 
```2.  Download and extract conky:
```

wget http://downloads.sourceforge.net/conky/conky-1.4.9.tar.bz2 && tar xjvf conky*.tar.bz2

```3. cd into conky directory

4.
```

$ ./configure --enable-xmms2 --disable-mpd
$ make
# make install

```5. Optional:  I like to copy the directory to /usr/src so I can uninstall later if I need to.

6.  See if it worked!:
```

conky

```If it worked, that's great!  If not, ask and we'll see if we can get you sorted out.

Now, to configure conky, go here and look up all the xmms2 variables: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

All right, the final step, and the coolest in my opinion: XMMS2 OSD

1. 
```

# apt-get install -y python-xmmsclient python-cairo python-gtk2

```2.
```

wget http://download.gna.org/xmms2-osd/xmms2-osd-1.1b.tar.gz && tar zxvf xmms2-osd-1.1b.tar.gz && cd xmms2-osd*

```3.
```

python setup.py bdist

```4. Create this dir: ~/.xmms2/clients/ and copy defaults.cfg to ~/.xmms2/clients/xmms2-gosd.conf

5. Copy xmms2-gosd.py to an arbitrary dir (I put mine in ~/.scripts, where I store all my little scripts)

6.  Edit ~/.xmms2/clients/xmms2-gosd.conf to make the OSD look how you want.

7.  if you feel comfortable, edit xmms2-gosd.py to display song info how you want, but keep a back up handy

8.  Start the script with:
```

python /path/to/the/script/xmms2-gosd.py

```Voila!  You should have a nice, lightweight music environment!  I mapped some keys in openbox so I can start my music with just a couple key presses.  I also put `python /path/to/the/script/xmms2-gosd.py` in my .bash_profile script so the daemon starts when I login.  Best of luck to you all!  Check back in the future, I'm going to attempt to write a bash (maybe perl or python would be better, since you have to read ID3 tags [or can you do that with bash????]) script that will pull all the albums, randomize the albums, and add the songs (in random album order) to xmms2.  I really like random album playback, as opposed to random songs.  If anyone else wants to take a crack, please share!  We can post it in this thread for future xmms2 converts!  Oh, and please let me know if there are errors.  Please note also, to use opacity with the OSD, you probably have to have a compositor installed.  Since my system is lightweight, I use xcompmgr.  Plus, I don't now of compiz-fusion works under openbox.  If anyone knows, please, share the info!  I'd like to test it out!

[CENTER][LEFT]Keep rocking
[/LEFT]
:guitar:
[/CENTER]

---

### Post by kaivalagi on 2008-03-24
Great how to, worked first time! Thanks a million =D>

Minor typos hardly worth mentioning:
on step 2 of conky build it should read "wget [http://downloads.sourceforge.net/conky/conky-1.4.9.tar.bz2](http://downloads.sourceforge.net/conky/conky-1.4.9.tar.bz2) && tar xjvf conky-1.4.9.tar.bz2"
on step 4 for the OSD setup it should read "4. Create this dir: ~/.xmms2/clients/ and copy defaults.cfg to ~/.xmms2/clients/xmms2-gosd.conf". Just a missing 's' that's all.

This was the icing on the cake for my Conky setup. I first tried to get audacious working but ran into trouble with dependences. I'm kinda glad it didn't work out, cause xmms2 looks like a major step forward from audacious anyway. All we need now is a really nice UI for it, gxmms2 makes it easy but it isn't feature rich yet...

I'll start messing around with the OSD settings soon and post back anything of worth if that's alright? Quick question on the OSD front, do you know if it is possible to have the OSD show for a short time and then go away? I have all the music player details I want in Conky long term so I want just like a simple notifier.

I've attached screenshots and config files for my 2 conky desktop setups in case anyone can find use for them.

Anyway thanks again, very very much appreciated. :)

---

### Post by kaivalagi on 2008-03-24
Just come across gx2osd, looks promising...
[http://eclipser.no-ip.org/gx2osd.xhtml]("http://eclipser.no-ip.org/gx2osd.xhtml")

I have also installed xmms2tray, it provides notification with coverart and control of the playlist, I have yet to get the coverart to display (maybe my obscure choice in music :) ) [http://zombiehq.jollybox.de/zhq/projects/xmms2tray]("http://zombiehq.jollybox.de/zhq/projects/xmms2tray")

---

### Post by kaivalagi on 2008-03-25
Finally settled for Esperanza as a front end as it provides notifications etc.

I've just completed writing 2 perl scripts for nautilus, so you can play and queue files and folders in xmms2 easily, see attached. Just pop them in your ~/.gnome2/nautilus-scripts folder, renaming them as you see fit.

Enjoy :)

---

### Post by kaivalagi on 2008-03-26
Sorry for all the posts, this one is kinder important.

I attempted to do the conky build in hardy 8.04 which is a nice fresh install on my PC and found lots of missing dependencies.

I have listed what I installed, other than what you've mentioned above , to get the build to work:

```
sudo apt-get install build-essential
sudo apt-get install libx11-dev
sudo apt-get install libxext-dev
sudo apt-get install libxdamage-dev
sudo apt-get install libxft-dev
sudo apt-get install libglib2.0-dev
```

I now have conky 1.4.9 with xmms2 support in Hardy :)

---

### Post by johnnybirdman on 2008-03-28
> **kaivalagi said:**
> Finally settled for Esperanza as a front end as it provides notifications etc.

I've just completed writing 2 perl scripts for nautilus, so you can play and queue files and folders in xmms2 easily, see attached. Just pop them in your ~/.gnome2/nautilus-scripts folder, renaming them as you see fit.

Enjoy :)

Just stumbled upon xmms2 today and your scripts.  Would like to try but first can you point me to how to install Esperanza?  I d/l'ed the flie and extracted but there is no readme (that I have found).  Any help would be appreciated.
J.

EDIT: never mind, did not realize this was in the repos.!!

---

### Post by kaivalagi on 2008-03-28
I installed the version in the repo's, it is a bit old though

I am now trying to compile and install version 4 , I'll post what I find out

Cheers

---

### Post by kaivalagi on 2008-03-28
I have version 0.4 working in Gutsy, I went through the following steps:

1) You need the dependencies installed and to remove esperanza if you  have installed from the repo's previously, run the following:

```

sudo apt-get install libqt4-dev
sudo apt-get install libxmmsclient++-dev
sudo apt-get remove esperanza
```

2) download the source: 

```
wget http://exodus.xmms.se/~tru/esperanza/0.4/esperanza-0.4.0.tar.gz
```

3) Extract the esperanza 0.4 source and "cd" to the new folder containing the source code:

```
tar xfvz ./esperanza-0.4.0.tar.gz 
cd esperanza-0.4.0
```

4) compile the code, this should not fail as you have the dependencies. if it does fail read the details, you should be able to figure out what other dependencies you may need to satisfy. It will always be a -dev package you'll need:

```
./configure
make

```

5) Copy the binary file to the bin folder so it can be run from anywhere. I am not sure why a make install didn't suffice, but it really doesn't matter:

```
sudo cp ./src/ui/esperanza /usr/bin
```


You can now run esperanza with last.fm support etc. You might want to create a menu item as well, your choice, personally I run it in a session script so it is there when I login.

Hope that helps, post back any issues and I'll try to help

---

### Post by chocolatetoothpaste on 2008-04-10
> **kaivalagi said:**
> Sorry for all the posts, this one is kinder important.

I attempted to do the conky build in hardy 8.04 which is a nice fresh install on my PC and found lots of missing dependencies.

I have listed what I installed, other than what you've mentioned above , to get the build to work:

```
sudo apt-get install build-essential
sudo apt-get install libx11-dev
sudo apt-get install libxext-dev
sudo apt-get install libxdamage-dev
sudo apt-get install libxft-dev
sudo apt-get install libglib2.0-dev
```I now have conky 1.4.9 with xmms2 support in Hardy :)


Sorry about that.  I forgot about the dependencies :)  I'll add this to the main guide.

---

### Post by LinuX-M@n1@k on 2008-04-28
Excellent ! Thanks for the HOWTO ;)

---

### Post by kg00005 on 2008-06-01
Hello All,

Starting conky I have these messages:

[B]Conky: unknown variable xmms2_title
Conky: unknown variable xmms2_artist
Conky: unknown variable xmms2_album
Conky: unknown variable xmms2_status
Conky: unknown variable xmms2_tracknr
Conky: unknown variable xmms2_elapsed
Conky: unknown variable xmms2_bitrate
Conky: unknown variable xmms2_bar
[/B]
--and conky is not showing xmms2 informations!

Xmms2 working fine.
I use gxmms2

ps -ef|grep xmm2:
*/usr/bin/xmms2d --status-fd=4*

I have installed conky with Synaptic.

See my conkyrc attached.

Thanks,
G

---

### Post by kaivalagi on 2008-06-03
> **kg00005 said:**
> Hello All,

Starting conky I have these messages:

[B]Conky: unknown variable xmms2_title
Conky: unknown variable xmms2_artist
Conky: unknown variable xmms2_album
Conky: unknown variable xmms2_status
Conky: unknown variable xmms2_tracknr
Conky: unknown variable xmms2_elapsed
Conky: unknown variable xmms2_bitrate
Conky: unknown variable xmms2_bar
[/B]
--and conky is not showing xmms2 informations!

Xmms2 working fine.
I use gxmms2

ps -ef|grep xmm2:
*/usr/bin/xmms2d --status-fd=4*

I have installed conky with Synaptic.

See my conkyrc attached.

Thanks,
G

Did you follow the instructions above?

The conky found in the repos is not compiled to support xmms2! You need to manually compile it from the sources.

Running a configure command like this (before you make) will give you the functionality:

```
./configure --enable-xmms2 --disable-mpd

```

Please follow the full instructions provided by chocolatetoothpaste above...if you follow them to the letter you shouldn't go wrong :)

If you have already followed the instructions and failed, I suggest you run the configure command again and see what text output you get. It should tell you that xmms2 is supported if it is...

---

