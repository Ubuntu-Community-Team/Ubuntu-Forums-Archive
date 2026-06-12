---
title: "2G ipod shuffle in gtkpod"
date: 2009-11-21
forum: Multimedia Software
---

### Post by mitchv on 2009-11-21
[FONT=Helvetica Neue LT Std]Have had problems getting my new ipod shuffle to work-looked up a few things, tried both amarok and banshee - no joy. 

I managed to transfer music to the ipod using gtkpod (best so far) and by dragging and dropping, but it wouldn't play unless I plug it into itunes (on my windows laptop) first. 

so, restored factory settings, copied music across in gtkpod, still wouldn't play, plugged it into itunes again. That worked. Then added one more album, in gtkpod, and it's back to not playing again. Put it in itunes. It plays.  And now gtkpod doesn't seem to like it at all, saying: 

 extended information file '/media/IPOD/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using SHA1 checksums. This may take a long time.

iPod Database Import Failed: 'iTunesStats file ('/media/IPOD/iPod_Control/iTunes/iTunesStats'): entry length smaller than expected (0<18).'

Newly mounted iPod at '/media/IPOD' could not be loaded into gtkpod.


Two things. It's a newish one - 2GB, and not listed in the options - so maybe there's something different about it that it doesn't like. Banshee came up with a message about this version too new to be supported. 

Also  - maybe there's something I'm simply missing about understanding commands for playing and synchronising - being something of a newbie. 

However, I would like to get it working without having to resort to Windows. Is there anyone out there who can help me. 

Ta
[/FONT]

---

### Post by rbp on 2010-01-11
I am facing the exact same problem. Any progress? I will post back here if I figure it out.

---

### Post by moddie666 on 2010-07-01
Hi There.
Did you figure anything out? anyone?

I use a 1gb silver 2G model and was able to transfer my files to the iPod with ease. However, ejecting it and remounting again I found the changes did not stay. It seems the database is not updated correctly (or at all?).
And YES I did save after I was finished.

----off topic----
This is my first close encounter with an Apple player and the way it connects to the computer is unnecessarily complicated and in-transparent.

What's wrong with simply placing my files in a folder and being able to listen to them? Every other device of this kind (I've seen) does exactly that.
But since the player was free I am not really complaining about about the player but about the twisted mind that conceived such a terrible way to transfer the music.
----on topic----

I am "fortunate" enough to be able to use iTunes in a virtual machine. That at least works.

greetings
/moddie

---

### Post by beadrifle on 2011-01-16
The problem still persists with gtkpod 1.0.0 on Ubuntu 10.10
Any solutions will help, I have scoured the internet considerably in search for an answer to this; bum of a bug.

---

### Post by irvotheturbo on 2011-01-29
Had the same problem here:

iPod Database Import Failed: 'iTunesStats file ('/media/IPOD/iPod_Control/iTunes/iTunesStats'): entry length smaller than expected (0<32)'.

Renaming (or deleting) the mentioned file got rid of the error.

Edit: Turning on your iPod (Shuffle for me) afterwards gives an error and it won't play files anymore. Trying to repair with gtkpod now (check files), but takes a long time.

---

### Post by Bernhard.Wernitznig on 2011-02-10
Just found some suggestions in this post: [http://ubuntuforums.org/showthread.php?t=1466151](http://ubuntuforums.org/showthread.php?t=1466151)

Some sayx to try Floola - that's not an explanation, but maybe it works.

---

### Post by Emanuele_Z on 2011-02-26
> **irvotheturbo said:**
> Had the same problem here:

iPod Database Import Failed: 'iTunesStats file ('/media/IPOD/iPod_Control/iTunes/iTunesStats'): entry length smaller than expected (0<32)'.

Renaming (or deleting) the mentioned file got rid of the error.

Edit: Turning on your iPod (Shuffle for me) afterwards gives an error and it won't play files anymore. Trying to repair with gtkpod now (check files), but takes a long time.

Same issue here.
Any suggestion?
Should I delete the file?

Cheers,

---

### Post by reptileqc on 2011-05-17
> Had the same problem here:

iPod Database Import Failed: 'iTunesStats file ('/media/IPOD/iPod_Control/iTunes/iTunesStats'): entry length smaller than expected (0<32)'.

Renaming (or deleting) the mentioned file got rid of the error.

Edit: Turning on your iPod (Shuffle for me) afterwards gives an error and it won't play files anymore. Trying to repair with gtkpod now (check files), but takes a long time.

I saw similar posts on a lot of different forums, so hopefully people will be able to find this thread and solve their issue.

So as you are all aware, the "ITunesStats" file is the first symptom of the problem and the list of songs on the IPod will not appear in Rhythmbox (blank list). Exploring the IPod drive and deleting the ITunesStats file manually seems to temporary solve the issue but after ejecting the drive, it won't play any songs.

I found the problem to be present (at least) on Ubuntu 10.10 (as well as Linux Mint "Julia") and it seems to affect the IPod Shuffle 2nd Gen (I tried with my IPhone 3G and it's not affected).

I found that the problem occurred when using Rhythmbox but also gtkpod. When looking for similar issues everywhere, I also found another music manager called Clementine that was affected with the same issue. So I figured three different pieces software couldn't get wrong all at the same time. It had to be a common library. I then found the common library is called "libgpod4". More specifically the version affected is 0.7.95. (the issue seems to have been inserted between 0.7.90 and 0.7.95 and might or not be fixed in 0.8.0)

Realizing that everything was working fine back in Ubuntu 9.10 Karmic Koala. I wanted to go back and use the current version of the libray back then. So here is how to do that :

Add the following line to your package repository : (either from modifying /etc/apt/sources.lst directly or from Synaptic under Settings -> Repository)

```
deb http://archive.ubuntu.com/ubuntu karmic main restricted universe multiverse
```

When done, search for the library called "libgpod" in synaptic and uninstall both "libgpod4" and "libgpod-common". It will also uninstall the "rhythmbox-plugins". Confirm and process.

Then reselect the "libgpod4" and "libgpod-common" librairies and go to Package -> Force version. Select the version "0.7.2-1ubuntu1" for both packages. Then apply.

If you are using rhythmbox make sure you re-install "rythmbox-plugins".

Apply everything and enjoy! Should work perfectly now. (not sure if you need to add or remove at least one song for the database to update....)

Confirm if that works for you too.

reptileqc

PS: Someone can probably come up with the command-line equivalent... :)

---

### Post by Br0ziliy on 2012-03-23
Registered on the forum specailly to share this knowledge.

Since archive.ubuntu.com does not have Karmic packages anymore - and I'm too lazy to google these - I used following dirty hack to make my 2nd gen IPod Shuffle work:

first, we're going to compile the older libgtkpod (0.7.90).
Please note you might need to install some more dependencies, apt-get command below is the one I used for my environment - yours might miss more development packages:
```

sudo apt-get install intltool  libglib2.0-dev libplist-dev
wget 'http://sourceforge.net/projects/gtkpod/files/libgpod/libgpod-0.7.9x/libgpod-0.7.90.tar.gz/download'
mv download libgpod-0.7.90.tar.gz
tar zxvf libgpod-0.7.90.tar.gz 
cd libgpod-0.7.90/
./configure --prefix=/opt/
make 
sudo make install 

```
The above lines will install the older libgpod version to the /opt/ directory - just so not to interfere with the normal system libraries.
Next, we have to do - is to add a helper script which will set up a corect environment for gtkpod to run (just copy and paste the whole code block below):
```

cat > /tmp/gtkpod<<EOF
#!/bin/bash
LD_PRELOAD=/opt/lib/libgpod.so.4.2.0 /usr/bin/gtkpod.bin
EOF
chmod 755 /tmp/gtkpod
sudo mv /tmp/gtkpod /usr/bin/gtkpod

```
Voila, your gtkpod will now be able to manage songs on your 2nd generation iPod Shuffle.

PS: Apple had to make it easier for users to listen to music using their hardware and NOT using their software.

---

